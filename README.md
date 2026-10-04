<h1 align="center">Solar-Powered Smart Irrigation System</h1>

<p align="center">
  <b>Built by Pranavi Bhagavathula & Arhanth Kanda</b>
</p>

<p align="center">
  Solar-powered plant watering system that utilizes soil moisture readings to determine when to autonomously water your garden, while also    being able to monitor and control it from your phone.
</p>

---

<h3>Table of Contents</h3>

1. [Why We Built This](#why-we-built-this)
2. [How it Works](#how-it-works)
3. [Features](#features) 
4. [Parts List](#parts-list)
5. [Wiring](#wiring)
6. [Software Setup](#software-setup)
7. [Building](#building)
8. [Calibration](#calibration)
9. [Challenges](#challenges)
10. [Results](#results)
11. [Community Impact](#community-impact)
12. [Contributing](#contributing)
13. [License](#license)


<h3>Why We Built This</h3>

When it comes to water waste, we do it too often, whether it's leaving the tap on while brushing our teeth or letting our shower heat up before we hop in. The amount we waste racks up subtly but meaningfully, especially when it comes to caring for our gardens. According to the United States Environmental Protection Agency, watering an average-sized lawn **20 minutes a day for a week** equals the amount of water the average family needs for **1 year's worth of showers**! 

This water use is alarmingly inefficient, with experts estimating that as much as 50% of that water is lost to evaporation, wind, or runoff due to overwatering. Automatic sprinklers make this worse, as they run on a timer, so they water at a set time even if it rained yesterday, or the soil is already wet. **According to the EPA, homes with automatic sprinkler systems use about 50% more water outdoors than homes without them.**

This matters close to home; as of August 26, 2026, the EDP had Berks, Lebanon, Lehigh counties under a drought warning, as well as nine more, asking for people to conserve water where they can.

**We wanted to build something low-cost and have it be solar powered (so that it works anywhere), and so that anyone can build one to help save more water!**

---

<h3>How it Works</h3>

```mermaid
graph TD;
    A([Soil Moisture Sensor sends reading to ESP32])-->B([Reading gets compared to a pre-set threshold])
    B-->C([Soil Reading is DRY]);
    B-->D([Soil Reading is WET]);
    C-->F([Soil gets watered]);
    D-->E([Nothing happens]);
```
---

<h3>Wiring</h3>

<h4 align="center">All Connections</h4>

<div align="center">

| From | To |
| --- | --- |
| Solar Panel `+ Wire` | WaveShare `IN+` |
| Solar Panel `- Wire` | WaveShare `IN` |
| WaveShare `5V` | ESP32 `5V`, MOSFET `+` |
| WaveShare `GND` | ESP32 `GND`, MOSFET `-` | 
| ESP32 `GPIO 1` | MOSFET `IN+` |
| ESP32 `GND 1` | MOSFET `IN-` |
| ESP32 `3V3/5V` | Soil Sensor `VCC` |
| ESP32 `GND 2` | Soil Sensor `GND` |
| ESP32 `GPIO 2` | Soil Sensor `AOUT` |
| MOSFET `+/- Terminal` | Pump `+/-` | 
| `1N4007` Diode | MOSFET `+/- Terminals` |

>Note: For the connections between WaveShare and ESP32/MOSFET (entries 3 and 4), two wires must be stripped and twisted together in the same WaveShare terminal.

</div>

---
