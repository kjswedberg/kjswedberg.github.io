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
This morning, I went over information about three-phase voltage and power. On a amplitude versus angle plot, for a single-phase sinusoidal voltage wave (assuming sine), the peak amplitude is at 90 degrees. For a three-phase sinusoidal voltage wave, the peak amplitudes are at 90 degrees, 210 degrees, and 330 degrees. When plotting the phase versus time plot, the graph should look very similar to the amplitude versus angle plot. As the angle increases, the voltage also increases. Some information about three-phase and single phase, along with plots that show these observations, can be found [here](https://circuitglobe.com/difference-between-single-phase-and-three-phase.html). Based off of the information on that site and my current knowledge of three-phase systems, it makes sense to overlay the voltage of phase a with the voltage of phase b and phase c. Similarly, the current of phase a can be overlaid with the current of phase b and phase c, and the power of phase a can be overlaid with the power of phase b and phase c. To overly the data this way, each meter will have three dashboards. This would be a total of 90 dashboards, since there are 30 meters. A way to minimize the about of dashboards may want to be found.

This afternoon, I worked on DataCamp's Introduction to Git course. I also proofread and made some edits to the final report that I started yesterday.

## Thursday, June 25, 2020
Today, I tried to figure out the [WireViz tool](https://github.com/formatc1702/WireViz) on the Chromebook. First, I created directory named wrk. I then cloned the GitHub project into that directory. I created a yml file, test.yml, that contained the code from one of the exampes on the WireVize GitHub tool's [Tutorial page](https://github.com/formatc1702/WireViz/blob/master/tutorial/readme.md). I then ran the command `$ python3 wireviz.py ~/wrk/test.yml` from the ~/wrk/WreViz/src directory. Instead of outputing files, it produced the output shown in Figure 1. It seems that the reason why it did not work is because it could not find the dot.py file in the ~/wrk/WreViz/src/graphviz directory. I am planning on examining the wireviz.py file tomorrow. I am thinking that the file cross references to the other files thoughout the project.

![Screenshot 2020-06-25 at 4 08 22 PM](https://user-images.githubusercontent.com/65566903/85807422-57d8dd00-b6fe-11ea-9663-159fb45ebfa1.png) <br>
**Figure 1: The outputs when trying to use WireViz** <br>

This afternoon, I worked on DataCamp's Introduction to Bash Scripting course.

## Friday, June 26, 2020
This morning, I got the [WireViz tool](https://github.com/formatc1702/WireViz) to work on the Chromebook. I started out by seeing if there was a cross reference error in the wireviz.py file. I scanned through the file, and found that the dot reference did not seem to be referencing a Python file. I looked around online to see if anyone else was having a similar issue. The solution that people were giving was to install Graphviz. As a result, I first tried `pip install Graphviz`, which is how the [graphviz.readthedocs.io](https://graphviz.readthedocs.io/en/stable/#installation) site said to install it. When WireViz still didn't work, I tried installed the graphviz package using `sudo apt-get install graphviz`, as recommended [here](https://stackoverflow.com/questions/35064304/runtimeerror-make-sure-the-graphviz-executables-are-on-your-systems-path-aft). After that, WireViz worked. WireViz provides two images, a PNG and a SVG, of a diagram of the wiring. It has an HTML file that shows the diagram and the Bill of Materials. The Bill of Marerials is basically a parts list and a legend for the diagram. It also provides a gv and a tsv file. I do not know what those two files do.

This afternoon, I worked on learning how to use the [WireViz tool](https://github.com/formatc1702/WireViz). I used the tool to show how I installed an extension cord to the Shelly 1PM meter. I then experiemented with the different color options. The resulting diagram is shown in Figure 2. On Monday, I am planning on learning and experiementing with some of the other settings, like the wire gauge and the connector type.

![Shelly](https://user-images.githubusercontent.com/65566903/85906187-03933300-b7ba-11ea-8655-a36b352f8520.png) <br>
**Figure 2: The wiring diagram for the Shelly 1PM meter.



