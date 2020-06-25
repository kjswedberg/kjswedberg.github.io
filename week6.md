# Week 6

## Monday, June 22, 2020
This morning, I re-started Telegraf on the Raspberry Pi. Due to a power outage yesterday, Telegraf had stopped sending data from the Shelly meter and the temperature/humidity sensors to InfluxDB. Re-starting Telegraf today involved updating the config files and Grafana to the new IP address, publishing the data from the sensors to a MQTT server, and starting Telegraf with the two config files. 

I also started working on creating slides for a presentation about the Shelly 1PM meter.

During the afternoon, I started the Intermediate Python course with DataCamp. I also attending a meeting at the Solar Site. 

## Tuesday, June 23, 2020
This morning, I started the final report that I am required to write as part of this internship. 

During the late morning and early afternoon, I completed the Intermediate Python course through DataCamp. 

I also worked on finishing the slides for a presentation about the Shelly 1PM meter.

## Wednesday, June 24, 2020
This morning, I went over information about three-phase voltage and power. On a amplitude versus angle plot, for a single-phase sinusoidal voltage wave (assuming sine), the peak amplitude is at 90 degrees. For a three-phase sinusoidal voltage wave, the peak amplitudes are at 90 degrees, 210 degrees, and 330 degrees. When plotting the phase versus time plot, the graph should look very similar to the amplitude versus angle plot. As the angle increases, the voltage also increases. Some information about three-phase and single phase, along with plots that show these observations, can be found [here](https://circuitglobe.com/difference-between-single-phase-and-three-phase.html). Based off of the information on that site and my current knowledge of three-phase systems, it makes sense to overlay the voltage of phase a with the voltage of phase b and phase c. Similarly, the current of phase a can be overlaid with the current of phase b and phase c, and the power of phase a can be overlaid with the power of phase b and phase c. Tomorrow, I am planning on calculating how many Dashboards would be needed for Grafana to do this when there are three dashboards per sensor and see if there may be a more effective way to overlay the data for analysis.

This afternoon, I worked on DataCamp's Introduction to Git course. I also proofread and made some edits to the final report that I started yesterday.
