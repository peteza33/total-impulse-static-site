+++
title = "Simple Blowdown System Performance Estimate"
date = 2020-06-22

[taxonomies]
categories = ["Chemical Propulsion", "Propulsion Sizing"]
tags = []
+++
Here we'll briefly walk through a simple performance estimate for a blowdown propulsion system. This is useful for assessing the orbital maneuver capability of a proposed design and determining the end-of-life (EOL) pressure.  
<!-- more -->

In this case we'll assume the system is using LMP-103S and the associated monopropellant thrusters for {% katex(block=false) %} \Delta V {% end %} burns. 

## Model Definition
We start with importing a few packages and declaring the characteristics of the propellant & pressurant as:

```python
import numpy as np
import matplotlib.pyplot as plt

import itertools
from math import exp, sqrt, pi, acos, sin, cos, log

class Propellant(object):
    def density(T):
        # Input: T = temperature in deg C
        # Output: density in kg/m3
        return 4E-15 * T ** 2 - 0.8436 * T + 1259.1

    def vapor_press(T):
        # Input: T = temperature in deg C
        # Output: vapor pressure in bar
        return 0.000002 * T ** 3 - 0.00003 * T ** 2 + 0.0032 * T + 0.0418

    def helium_z(p):
        # Input: p = pressure in bar
        # Output: non dimensional compressibility factor
        return -5E-17 * (p * 100) ** 3 + 3E-12 * (p * 100) ** 2 + 5E-6 * (p * 100) + 1
```

Now we'll write the performance models for the thrusters our system is using, here we have the 1N HPGP thruster:

```python
class ECAPS_Model(object):
    def thrust(p):
        # Input: p = pressure in bar
        # Output: thrust in N (from ATP family data)
        return -0.000214 * p ** 2 + 0.052037 * p - 0.019460

    def isp(p):
        # Input: p = pressure in bar
        # Output: isp in seconds (steady state)
        return (243.68 * np.log(p) + 1594 - 0.1 * p ** 2.15) / 9.806
```

With the propellant and the performance models finished, we need to write a simple function that takes a given system definition and calculates the blowdown performance at discrete propellant mass steps:

```python
def Delta_V(tank_vol, m_dry, m_prop, temp, initial_press):
    # Inputs: tank volume in liters, spacecraft dry mass in kg, propellant mass in kg, 
    #         temperature in C, and intiitaly system pressure in bar
    # Output: Delta-V profile in m/s, propellant mass profile in kg,
    #         system pressure profile in bar 

    def ullage(tank_vol, m_prop, temp):
        # Inputs: take volume in liters, propellant mass, and propellant temperature in C
        # Outputs: ullage volume in m3
        return (tank_vol * 0.001) - (m_prop / Propellant.density(temp))

    # calculate helium mass in the system
    m_helium = ((initial_press * 100 - Propellant.vapor_press(temp) * 100) \
    * ullage(tank_vol, m_prop, temp)) / (Propellant.helium_z(initial_press) \
    * 2.0772 * (temp + 273.15))

    # define stop condition, we'll assume 98% expulsion
    residual = m_prop - (m_prop * 0.98)

    # total dry mass of the spacecraft as residual could be large depending on design
    m_dry = m_dry + m_helium + residual
    
    # define results storage
    DV_total = [0]
    m_prop_list = [m_prop]
    pressure_profile = [initial_press]

    # calculate delta-V with the rocket equation through the blowdown
    while m_prop >= residual:
        
        # step through propellant mass
        step_start_mass = m_dry + m_prop
        m_prop -= 0.1
        step_end_mass = m_dry + m_prop

        # calculate new system pressure after mass is consumed
        press = ((m_helium * Propellant.helium_z(initial_press / 2) * \
        2.0772 * (temp + 273.15)) / ullage(tank_vol, m_prop, temp)) / 100

        # calc the delta-V imparted by this mass 'chunk' at this system state
        DV_step = ECAPS_Model.isp(press) * 9.806 * np.log(step_start_mass / step_end_mass)

        # store results
        m_prop_list.append(m_prop)
        DV_total.append(DV_total[-1] + DV_step)
        pressure_profile.append(press)

    return DV_total, m_prop_list, pressure_profile
```
The above function is a good estimate of the blowdown system's performance given an initial state.

## System Design Evaluation

With our model completed, we can evaluate the performance of a given system design by taking the following as inputs:

| **Parameter**       | **Value** | **Unit** |
|---------------------|-----------|----------|
| Spacecraft Dry Mass | 100       | kg       |
| Propellant Mass     | 10        | kg       |
| Total Tank Volume   | 11\.5     | liters   |
| Temperature         | 20        | C        |
| Initial Pressure    | 18\.5     | bar      |

Now we call our Delta_V function defined about to step through the blowdown curve as mass is expelled from the system:

```python
DV_total, m_prop_list, pressure_profile = Delta_V(total_tank_vol, m_dry, m_prop, \
                                                  temp, initial_press)
```

And we plot the results with:

```python
# define the axes
fig, ax1 = plt.subplots(figsize = (16, 8))
ax2 = ax1.twinx()

# plot the data
ax1.plot(m_prop_list, pressure_profile, color = 'blue')
ax2.plot(m_prop_list, DV_total, ls = '--', color = next(colors), label = 'Thruster Mode: SS')

# dress up the axes
ax1.set_ylabel('Tank Pressure [bar]', fontsize = 14)
ax1.set_xlabel('Propellant Remaining [kg]', fontsize = 14)
ax1.set_title('Estimated System Performance', fontsize = 14)
ax1.grid(True)
ax1.set_xlim(xmin = 0)
ax1.set_ylim(ymin = 4)

ax2.set_ylabel('Cumulative Delta V [m/s] (dashed line)', fontsize = 14)
ax2.set_ylim(ymin = 0)
ax2.invert_xaxis()
ax2.legend(loc = 9, prop = {'size': 14})

ax1.tick_params(axis = 'both', which = 'major', labelsize = 14)
ax2.tick_params(axis = 'y', which = 'major', labelsize = 14)
```
Which displays a plot of the pressure profile and cumulative {% katex(block=false) %} \Delta V {% end %} similar to:

{% figure(src="/img/estimated_system_performance.png", title = "Estimated System Performance - Example Plot") %}
<!-- caption here -->
{% end %}