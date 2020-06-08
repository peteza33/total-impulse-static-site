+++
title = "First In-FEEP Thruster Demonstration On-Orbit"
date = 2020-06-08

[taxonomies]
categories = ["Electric Propulsion"]
tags = ["EP", "FEEP", "Firsts!"]
+++
In Jan 2018, [Planet](https://www.planet.com/company/) launched a [technology demonstration](https://www.enpulsion.com/news/feep-first-successful-in-orbit-demonstration-of-a-feep-thruster/) of a 1U indium FEEP thruster module designed and built by [Enpulsion](https://www.enpulsion.com). The thruster was integrated into a modified Planet 3U "Dove" satellite and launched on a [PSLV](https://www.isro.gov.in/launcher/pslv-c40-cartosat-2-series-satellite-mission).
<!-- more -->

## Background on FEEP Thrusters
Enpulsion designs and manufactures a type of electric propulsion system called field emission electric propulsion (FEEP) which uses indium as the propellant. Field emission electric propulsion is an electrostatic propulsion concept based on field ionization of a liquid metal from the tips of a porous tungsten crown. The core of the thruster is a Liquid Metal Ion Source (LMIS). LMISs are used for a variety of applications, for example mass spectrometers use LMIS to create their ions. When a LMIS is used in a propulsion application it is referred to as FEEP. Dedicated In-FEEP thrusters based on space proven miniaturized LMISs have been under development since 1995. Indium LMISs were first successfully demonstrated in space aboard MIR in 1991 and have fown on a number of satellites as part of spacecraft potential control and mass spectrometer devices.

## Indium as Propellant
In-FEEP thrusters use indium as the propellant for a variety of reasons:

- high atomic mass (114.818 amu = 1.9E-25 kg)
- low ionization potential (5.78 eV)
- good wetting properties
- can be handled in atmosphere risk free
    - unlike cesium or gallium which can also be used in FEEP thrusters but cannot be openly handled in atmosphere
- low melting temperature of 156.6C with extremely low vapor pressure at that temperature (5E-11 Pa)

## Operation
Thrust is produced by exhausting a beam of mainly singly ionized indium atoms produced by field evaporation. The thruster operates along this workflow:

1. The indium is heated above its melting point at which capillary forces drive the liquid indium to the thruster's emitter tips
2. When a sufficiently high electric potential (on the order of 5-10 kV) is applied between the emitter and the extractor electrode the equilibrium between surface tension forces and electrostatic force forms a Taylor cone on the surface of the liquid indium with a jet protruding due to space charge
3. Atoms are then ionized at the tip of the jet and accelerated away from the tip by the same electric field that created them resulting in an ion beam
4. An external source of electrons provides negative charges to maintain global electrical neutrality of the thruster assembly
5. The expellion ions are replenished by the hydrodynamic flow of the liquid metal and mass flow rate require no active control as the extracted particles are replaced by capillary actions from the propellant reservoir at a rate sufficient to maintain dynamic equilibrium

Contrary to other electric propulsion systems, ionization and acceleration takes place in one step using the same electric field. This leads to very high electric efficiency of >95%. Indium ions are 98% singly charged along the complete thrust range.

## Performance
The initial demonstration consisted of a series of characterization startups, operational box sweeps, and increasingly long burn durations. The first 15 minute burn operated at a 2 mA emitter current. 

In preparation of the 15 minute burn (or any burn in normal operation) the indium temperature was commanded to 170C to liquify and flow the propellant to the emitter's porous tips. The liquification point can be seen in the enthalpy step shown around 155C in Figure 1:

{% figure(src="/img/15minBurn_temperatures.png", title = "Figure 1: Temperature Profile") %}
<!-- caption here -->
{% end %}

Following propellant liquefaction, the emitter voltage was capped at 10 kV and the current was commanded to 2 mA as shown in Figure 2:

{% figure(src="/img/15minBurn_emitter_voltage&current.png", title = "Figure 2: Emitter Voltage & Current") %}
<!-- caption here -->
{% end %}

Commanded the emitter to 2 mA with a 10 kV limit produced a thrust of about 225 uN over the 15 minute burn duration. The mean specific impulse over the burn was approx 4400 seconds. 

{% figure(src="/img/15minBurn_thrust.png", title = "Figure 2: Emitter Voltage & Current") %}
<!-- caption here -->
{% end %}

## Further Reading
More detailed results and discussion of this demonstration was published as a conference paper in 2018:

["Demonstration of the IFM Nano FEEP Thruster in Low Earth Orbit"](https://www.researchgate.net/profile/David_Krejci/publication/325486881_DEMONSTRATION_OF_THE_IFM_NANO_FEEP_THRUSTER_IN_LOW_EARTH_ORBIT/links/5b11210caca2723d997970f7/DEMONSTRATION-OF-THE-IFM-NANO-FEEP-THRUSTER-IN-LOW-EARTH-ORBIT.pdf), David Krejci, Alexander Reissner, Bernhard Seifert, David Jelem, Thomas Hörbe, Florin Plesescu, Peter Friedhoff, Steve Lai. 4S Symposium 2018

A good primer on In-FEEP can be found here:

["Development, Production, and Testing of the IFM Nano FEEP Thruster"](https://scholar.google.com/scholar?oi=bibs&cluster=1628240575605084354&btnI=1&hl=en), Tony Schönherr, Bryan Little, David Krejci, Alexander Reissner, Bernhard Seifert. IEPC 2019