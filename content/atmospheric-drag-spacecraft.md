+++
title = "Atmospheric Drag on LEO Spacecraft"
date = 2020-06-01

[taxonomies]
categories = ["Propulsion Sizing"]
tags = ["VLEO", "Drag", "EP"]
+++

Spacecraft lifetime in LEO is highly dependent on the atmospheric drag force and it's removal of energy from the satellite's orbit. Understanding the impact of drag on a design is important for early propulsion sizing estimates for spacecraft operating in the very low earth orbit ([VLEO](https://en.wikipedia.org/wiki/Low_Earth_orbit#/media/File:Orbitalaltitudes.jpg)) range of 250-450 km.

<!-- more -->
## Atmospheric Drag Model
Lifetime at very low altitudes is dominated by the exponentially increasing atmospheric drag, which acts to remove energy from a spacecraft's orbit. Atmospheric density and, hence, spacecraft drag depends strongly upon the prevailing solar conditions which vary throughout a given 11 year solar cycle. Here we use data from the last 5 solar cycles to construct an 'average cycle' by which to calculate the drag force acting on a given spacecraft. The atmospheric model used in [NRLMSISE-00](https://ccmc.gsfc.nasa.gov/modelweb/models/nrlmsise00.php) and a plot of the solar radio flux (F10.7) index and geomagnetic index (ap) for the last 5 solar cycles is shown in Figure 1. 

{% figure(src="/img/solar_model_data.png", title = "Figure 1: F10.7 and Ap of Last 5 Solar Cycles with Average Cycle Spline") %}
<!-- caption here -->
{% end %}

Given a specific mission duration requirement it would make sense to assume dierent launch times and calculate time-dependent atmospheric density using the mean solar cycle (e.g. assume a 5 year mission begins at the peak of a cycle and calculate density vs time from the mean prole over that 5 year duration). For this paper a 'per-year' approach is taken and it makes sense to bracket the expected density with a 'high' and 'low' condition. Here, 'high' is defined as the normalized cycle time of 50%, which uses the mean parameters denoted by the spline curve in Figure 1 at the 0.5 cycle time point. The 'low' condition uses the mean parameter spline at a normalized cycle time of 0%. Note, these bracket conditions are not the worst case, they are the high and low points of the average solar cycle. The atmospheric density at these two points in an average solar cycle is shown in Figure 2.

{% figure(src="/img/density.png", title = "Figure 2: Atmospheric Density of an Average Solar Cycle") %}
<!-- caption here -->
{% end %}

## Impact of Propulsion Sizing
The atmospheric drag force acts to remove energy from a spacecraft's orbit, and if un-compensated for, will reduce the energy/semi-major axis over time. To maintain a stable orbit at very low altitudes (230 to 400 km), drag compensation becomes a large part of a mission's CONOPS. The drag force exerted by the atmosphere on a spacecraft is calculated as shown in Equation 1.

{% katex(block=true) %} \tag{1} F_{d} = \frac{1}{2} \rho v^2 C_{d} A {% end %}

where {% katex(block=false) %} \rho {% end %} is the atmospheric density from Figure 2, {% katex(block=false) %} v {% end %} is the spacecraft velocity at a given altitude, {% katex(block=false) %} C_{d} {% end %} is the dimensionless [coefficient of drag](https://en.wikipedia.org/wiki/Drag_coefficient), and {% katex(block=false) %} A {% end %} is the apparent or wetted (or reference) area of the spacecraft.

Given a spacecraft geometry in terms of {% katex(block=false) %} C_{d} {% end %} and {% katex(block=false) %} A {% end %}, Equation 1 is used to calculate the drag force and thereby determine how much thrust a propulsion system must generate to compensate and keep altitude stable over time. 

### Normalized Drag Force
It is useful to extend the analysis to arbitrary geometries to better understand the scaling and remove
the effects of individual spacecraft geometry, so it is convenient to normalize the drag force shown in
Equation 1 by {% katex(block=false) %} C_{d} A {% end %} as:

{% katex(block=true) %} \tag{2} \dfrac{F_{d}}{C_{d} A} = \frac{1}{2} \rho v^2 {% end %}

Using the density from Figure 2 and the spacecraft velocity for a circular orbit given as:

{% katex(block=true) %} \tag{3} v = \sqrt{ \dfrac{\mu}{r_{earth} + a} } {% end %}

the normalized spacecraft drag is calculated as shown in Figure 3.

{% figure(src="/img/normal_drag_force.png", title = "Figure 3: Atmospheric Drag Force Normalized by CdA") %}
<!-- caption here -->
{% end %}

### Normalized Drag Power
A physics based analysis of the power required to compensate for the drag force of Equations 1 and 2 is useful without specifying anything about the type of propulsion system to be employed. 

The effect of drag on the spacecraft is to reduce the orbital kinetic energy and the rate at which energy is removed is known as drag power, given by Equation 4. It describes the power exerted by the atmosphere on the spacecraft and is shown in watts. To offset drag and remain in orbit, the spacecraft propulsion system must supply **at least** this much power.

{% katex(block=true) %} \tag{4} P_{d} = \vec{F_{d}} \vec{v} {% end %}

Normalizing the drag power from Equation 4 can be thought of as the power, in watts, that much be continually supplied to maintain the orbit of a spacecraft having {% katex(block=false) %} C_{d} = 2 {% end %} and {% katex(block=false) %} A = 0.5 m^2 {% end %} and is shown in Figure 4.

{% figure(src="/img/normal_drag_power.png", title = "Figure 4: Steady State Atmospheric Drag Power Acting on Spacecraft Normalized by CdA") %}
<!-- caption here -->
{% end %}

The dotted lines in Figure 4 are interesting because they represent the power **any** electric propulsion system technology must impart to the spacecraft to maintain orbit. The solid lines in Figure 4 represent the power that must be input into an electric propulsion system having a total efficiency of {% katex(block=false) %} \eta_{t} = 35 {% end %}% (chosen because low power EP systems operate at some total efficiency between 20% and 40% after accounting for all losses). 

It is important to note that the solid lines in Figure 4 represent the steady state power, meaning it is the power that must be supplied continuously in the case that the EP system thrusts continually to exactly offset drag. If the system is operated at some duty cycle less than 100%, then the power demand during operation must scale inversely with the duty cycle in order to replace the lost kinetic energy. The total energy required is the same whether the thruster fires continuously or intermittently. For instance, if the EP thruster operates for 20% of the time and is off for 80% of the time, then the power draw during operation is 5X.

### Normalized Drag Impulse
The EP system must consume stored propellant to provide impulse **at least** equal to the drag impulse, and more if other uses of propellant like stationkeeping, collision avoidance, phasing, etc are required for the mission. The drag impulse is given by Equation 5 as:

{% katex(block=true) %} \tag{5} I_d = \int F_{d} \, dt {% end %}

and the normalized impulse to compensate for drag over the course of 1 year is shown in Figure 5.

{% figure(src="/img/normal_drag_impulse.png", title = "Figure 5: Impulse per Year to Counter Drag Normalized by CdA") %}
<!-- caption here -->
{% end %}

### Normalized Single Orbit {% katex(block=false) %} \Delta V {% end %}
It is also useful to extend the 1 year drag impulse shown in Figure 5 to {% katex(block=false) %} \Delta V {% end %} and shrink the time scale from 1 year to 1 orbit. Figure 6 shows the normalized drag compensation {% katex(block=false) %} \Delta V {% end %} required per orbit.

{% figure(src="/img/normal_drag_deltaV_single_orbit.png", title = "Figure 6: Single Orbit Drag Makeup Velocity Change Normalized by m/CdA") %}
<!-- caption here -->
{% end %}

### Normalized Propellant Mass
The propellant mass required to compensate for drag is determined by equating the propulsion system impulse to the drag impulse shown in Figure 5. Here the approximation is made that *the total spacecraft mass does not appreciably change between the start and end of any individual thruster burn (i.e. the propellant consumed per-burn is small compared to the spacecraft mass)*. This allows the calculation of propellant mass without using the rocket equation and therefore the results are independent of spacecraft mass. In this approximation the impulse delivered by the propulsion system during an individual burn translates entirely into {% katex(block=false) %} \Delta V {% end %}. which offsets the {% katex(block=false) %} \Delta V {% end %} imposed by drag on the same-mass spacecraft prior to the burn. Then the drag impulse is balanced by the thrust impulse over the full mission duration. This approach is valid even though the spacecraft mass does change significantly from start to end of the mission. This approximation will slightly over-estimate the required propellant mass since, in an actual burn, the spacecraft mass will decrease throughout the burn and the same impulse will translate into a larger {% katex(block=false) %} \Delta V {% end %}. The normalized propellant mass required for 1 year of drag compensation is shown in Figure 7.

{% figure(src="/img/normal_drag_oneyear_propellant.png", title = "Figure 7: Propellant Mass per Year to Counter Drag Normalized by CdA") %}
<!-- caption here -->
{% end %}

### Normalized Duty Cycle
As shown in Figure 7, the propellant mass is reduced by using a system with high {% katex(block=false) %} I_{sp} {% end %}. However, there is an intrinsic physics based trade-off in any EP system that relates specific impulse, power, and thrust. The thrust of an electric propulsion system is shown in Equation 6. 

{% katex(block=true) %} \tag{6} F = \frac{2 \eta_{t} P_{in}}{g I_{sp}} {% end %}

It is important to note that for a given electrical power input, the thrust of an EP system is inversely proportional to the specific impulse. This means that high {% katex(block=false) %} I_{sp} {% end %} systems will have a lower thrust at the same power and will thus need to operate for a longer duration to offset drag. Using Equation 6, the relationship between the time an EP system must operate to the total mission time can be found by equating the thrust impulse to the drag impulse as:

{% katex(block=true) %} \tag{7} \frac{t_{thrust}}{t_{mission}} =\frac{F_{d}}{F} = \frac{F_{d} g I_{sp}}{2 \eta_{t} P_{in}} {% end %}

For an EP system, Equation 7 is typically referred to as thruster duty cycle. At various normalized input powers each altitude of interest can be plotted to assess the required thruster duty cycle in terms of whatever mission time fraction CONOPS allows. The fraction of mission time spent thrusting (and therefore consuming power) with a given spacecraft at 250 km is plotted in Figure 8.

{% figure(src="/img/normal_dutycycle_250.png", title = "Figure 8: Mission Time Spent Compensating for Drag at 250 km Normalized by CdA at 0.35 Efficiency") %}
<!-- caption here -->
{% end %}

In Figure 8, the contours can be thought of as the electrical power, in watts, that must be supplied for a spacecraft of {% katex(block=false) %} C_{d} A = 1m^2 {% end %}. Therefore, if it is desired to keep the electrical power consumption near 100W and the thrust time less than 10% of the total mission time (i.e. by thrusting for 1 hour every 10 hours, or for 9 minutes every orbit) then the specific impulse of a 35% efficient system must be less than about 1200 seconds. 

Another way to look at it given a specific EP technology, say a thruster that operates at 100W and 1000 seconds, the mission duty cycle for a {% katex(block=false) %} C_{d} A = 1m^2 {% end %} spacecraft to compensate for drag at 250 km is about 9%.

## Summary
The analysis above has been done in a spacecraft geometry agnostic manner and the results apply to any spacecraft operating in these altitude ranges with any given EP system (other than assuming a 35% efficiency factor). 