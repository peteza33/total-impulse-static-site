+++
title = "ADN-Based LMP-103S Green Propellant Implementation on SkySat"
date = 2020-06-02

[taxonomies]
categories = ["Propulsion Design", "Chemical Propulsion"]
tags = ["HPGP", "LMP-103S", "ADN", "Firsts!"]
+++
SkySat-3, launched in June 2016 on PSLV, was the first commercial spacecraft to load and fly ECAPS' [ADN](https://en.wikipedia.org/wiki/Ammonium_dinitramide) based green monopropellant known as LMP-103S. Previously the technology had flown on the Swedish Space Corporations [PRISMA](https://en.wikipedia.org/wiki/Prisma_(satellite_project)) mission, which launched in June 2010. 
<!-- more -->

## Evolution of SkySat
In November 2013 Skybox Imaging launched SkySat-1 from Yasny, Russia. Eight months later SkySat-2 was launched from Baikonur, Kazakhstan. Shortly afterward Skybox Imaging was [aquired](https://www.washingtonpost.com/news/morning-mix/wp/2014/06/11/google-buys-skybox-for-500-million-the-deal-could-be-about-more-than-maps/) by Google and rebranded to Terra Bella. To enhance mission flexibility and increase on-orbit life, the next design iteration of the SkySat platform incorporated a chemical propulsion subsystem. 

## Need for Propulsion
A critical requirement identified in the evolution from SkySat-1 and SkySat-2 towards a full constellation (SkySat-3 thru SkySat-21) was the inclusion of a highly performant propulsion system capable of maximizing available {% katex(block=false) %} \Delta V {% end %} within a tight volume and low power restrictions. The chief capabilities enabled by inclusion of such a propulsion system are:

- Constellation Phase Management
    - Launching multiple spacecraft on a single rocket requires the use of propulsion to phase the spacecraft within each orbit plane and then overcome orbit perturbations to maintain their relative spacing
- Mission Flexibility
    - A high thrust to spacecraft mass propulsion system enables the constellation to take advantage of a wide range of primary or secondary launch opportunities with established providers and emerging new entrants. The ability to correct for large orbit injection errors or accept injection into a wide range of altitudes and quickly absorb those individual launch differences without significant delay to incorporation of spacecraft into the constellation’s product is a tremendous value

## ECAPS System Used on SkySat-3 to SkySat-21
The resulting system was designed and manufactured by ECAPS AB in [Solna, Sweden](https://goo.gl/maps/Ug7F6h8M2tqrdFYY7). It is a fully integrated, modular drop-in to the existing SkySat bus design, which was extended in height to include the propulsion system. 

The system provides a total impulse of approximately 21 kN-s at a satellite internal volume fraction of about 11% and a mass fraction of approximately 10% dry and 19% wet. Four 1N HPGP thrusters are blowdown pressure fed LMP-103S from 3 tanks holding 10.5 kg of propellent total. The schematic and physical layout is shown in Figure 1. 

{% figure(src="/img/schematic.png", title = "Figure 1: HPGP Propulsion System for SkySat") %}
<!-- caption here -->
{% end %}

## Cumulative Time in Space
At the time of posting, SkySat-3 to SkySat-15 are operating in-space and SkySat-16 to SkySat-21 are scheduled to be launched in summer of 2020 on SpaceX Falcon 9 vehicles (SkySat-1 and 2 are excluded because they do not have propulsion systems). The total on-orbit years for the ECAPS propulsion systems are tabulated below:


| Satellites                  | Vehicle  | Site                  | Date      | Sat Years In Space |
|-----------------------------|----------|-----------------------|-----------|-------------------:|
| SkySat-3                    | PSLV     | [Sriharikota, India](https://goo.gl/maps/kb8g2LzifdUspTME6)    | June 2016 |               3.9 |
| SkySat-4, 5, 6, 7           | Vega     | [Kourou, French Guiana](https://goo.gl/maps/3HRMf9RvyKeNFw2F9) | Sept 2016 |              14.9 |
| SkySat-8, 9, 10, 11, 12, 13 | Minotaur | [Vandenberg, USA](https://goo.gl/maps/FpDtL1BTeQUwVSJZ8)       | Oct 2017  |              15.5 |
| SkySat-14, 15               | Falcon 9 | [Vandenberg, USA](https://goo.gl/maps/FpDtL1BTeQUwVSJZ8)       | Dec 2018  |               3.0 |
|                             |          |                       | **Total** |               37.3 |

## Further Reading
For more detailed information and on-orbit operation results, take a look at these conference papers:

["On-Orbit Operation and Performance of Ammonium Dinitramide (ADN) Based High Performance Green Propulsion (HPGP) Systems"](http://sci-hub.tw/10.2514/6.2017-4673), Peter Friedhoff, Alisa Hawkins, John Carrico, Jonathan Dyer, Kjell Anflo, 2017 Joint Propulsion Conference. July 2017

["Growing Constellation of Ammonium Dinitramide (ADN) Based High Performance Green Propulsion (HPGP) Systems"](https://sci-hub.tw/10.2514/6.2018-4754), Peter Friedhoff, Kjell Anflo, Peter Thormahlen, Mathias Persson. 2018 Joint Propulsion Conference. July 2018