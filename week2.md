# Week 2

## Monday, May 25, 2020
Memorial Day

## Tuesday, May 26, 2020
This morning, I set up a Raspberry Pi computer. This involved putting together the box, which was designed as a 3D jigsaw puzzle. The lid of the box is the computer's screen. After attaching the mouse, keyboard, and screeen to the Raspberry Pi and turning everything on, the computer worked. However, the HDMI mini port on the Raspberry Pi and the HDMI Mini to HDMI cord plugged into the port were acting extremly finicky. After 30 seconds of messing with the cord where it entered the HDMI mini port, I was able to make the screen display the desktop. As soon as I let go of the cord, the screen turned black. I was able to confirm that the HDMI Mini to HDMI cord functioned properly by using it to connect a different computer to the screen. When I tried an HDMI Mini to HDMI (female) adaptor with a regular HDMI cord, the Raspberry Pi and the screen functioned properly together. With the screen working with the Raspberry Pi, I confirmed that the Raspberry Pi could connect to the WiFi and had speakers pre-attached to it. I also explored some of the programs that were pre-installed on the Raspberry Pi.

During the afternoon, I worked with the Node-Red software that was on the Raspberry Pi. This software allows for the sensors to be programmed, so that the Raspberry Pi knows what pins are inputs and what it should output to where. To start learning how to do this, I found [instructions on the T3 website](https://t3alliance.org/lessons/rpi-node-red-inject-debug-hello-world/) that showed how to set some of the sensors up and what some of the sensors do. While doing this, I started inventorying the sensors that came with the Raspberry Pi kit. 

## Wednesday, May 27, 2020
This morning, I worked more with the Raspberry Pi and with the Node-Red software. I used the resources on the T3 website as a reference, and tried different combinations of the different sensors. I tried to test my understanding of the sensors by programming the LEDs and temperature sensor to output when a button was pressed. When the button was used with the temperature sensor, data was outputed when the button was pushed and when it was released. However, the goal was to only output the data when the button was pressed. I also experemented with the different time settings in the inject node settings, so that the temperature was read once per minute. 

During the afternoon, I set up a Chromebook with Linux. After installing Linux, I installed Docker on the Chromebook by using the command terminal. After confirming that Docker was installed properly, I went through some [documentation on Docker](https://docs.docker.com/get-started/). Although the first two parts seemed to work correctly, the last two steps in Part 3 of the documentation did not work. The two parts involve pushing the image to Docker Hub. Instead of pushing the image, the terminal gave an error that suggested that the terminal could not find the image. I found a [different tutorial](https://docker-curriculum.com/#our-first-image) that had a slightly different synax for pushing an image, and I am planning to try that synax tomorrow morning. 

## Thursday, May 28, 2020
This morning, I spent about an hour trying to figure out how to push an image to Docker Hub. Using the two tutorials that I had found yesturday, I was able to push an image to Docker Hub. The syntax on the [second tutorial](https://docker-curriculum.com/#our-first-image) worked. However, when I went to view the application in a browser, the browser did not find the application to display.  Currently, viewing the application in a browser is the only thing that I cannot get to work. 

Late morning and during the afternoon, I worked on the Shelly 1PM power meter. I connected the power meter to an extention cord. This enables me to be able to switch what load is attached to it. It also has a switch attached to it, so that the load can be turned on or off. Figure 1 shows a picture of how the power meter was set-up and Figure 2 is the schematic showing how I set-up the power meter. The power meter can be controlled from the Shelly Cloud app over WiFi. The amount of power that the load uses is read from the app. The app can also turn the load on or off. When using the app to control the load or to read the load's power usage, there is a delay time that ranges from approximately 6 seconds to 12 seconds. 

![Power_Meter_Assembled](https://user-images.githubusercontent.com/65566903/83200241-6035fc00-a0ef-11ea-9c0c-948faa3fbfef.JPG) <br>
**Figure 1: The set-up for the Shelly 1PM power meter** <br>

![Schematic](https://user-images.githubusercontent.com/65566903/83217763-f0d50200-a118-11ea-8b3e-10218a79d6c0.jpg) <br>
**Figure 2: The schematic showing how the Shelly 1PM power meter was set-up** <br>

To measure the accuracy of the Shelly 1PM meter, I measured the resistances of two doghouse heaters. Assuming that the maximum voltage that the heaters recieved was 170, I calculated the theoritical maximum power. After confirming the the power meter ratings would not be exceeded, I set up the power meter and I measured the actual voltage with a multimeter accross the O and N pins. Using the app, I found the measured power. Using the actual voltage and the resistances, I calculated what the power should be. The current was also calculated from the calculated power and the measured power with the measured resistance values. Figure 3 shows the graph of the theoritical, calculated, and measured power. There is a positive correlation between the resisance and the percent error between the measured power and the calculated power and a negative correlation between the current and the percent error. As resistance increases, the percent error increases. As current increases,the percent error decreases. These observations are shown in Figure 4 and Figure 5. [This spreadsheet](https://docs.google.com/spreadsheets/d/18iAUlNeXVuwcHnIn5Dq_sifxuT0lpsdiY69VjYQrYO4/edit?usp=sharing) summarizes all of this and shows all of my calculations. 

![Doghouse Heater Power Meter Graph](https://user-images.githubusercontent.com/65566903/83215880-67bbcc00-a114-11ea-933b-3366475d4155.png) <br>
**Figure 3: The graph showing the theoritical, calculated, and measured power** <br>

![Percent Error vs  Resistance ](https://user-images.githubusercontent.com/65566903/83278941-d46cb000-a180-11ea-8c00-32f0b18e8718.png)<br>
**Figure 4: The graph showing the relationship between the percent error and the resistance.** <br>

![Percent Error vs  Current](https://user-images.githubusercontent.com/65566903/83278958-d9316400-a180-11ea-8506-975868852b91.png) <br>
**Figure 5: The graph showing the relationship between the percent error and the current** <br>

Based off of [this site](https://www.pjm.com/-/media/committees-groups/task-forces/mtf/20151113/20151113-item-08-ansi-and-ieee-standards.ashx), the acceptable range for a power meter is plus/minus 2 %. The basic accuracy rating for the multimeter used is specified to be plus/minus 0.5 %. The lowest percent error for the three points that were measured with the Shelly 1PM power meter was calculated to be 6.66 %. However, in order to make an accurate conclusion regarding the accuracy of the power meter, more points are needed. As a result, the next thing that should be done in this analysis is to collect more points to add to the graphs. The power meter has been determined to be precise, since the values remained constant during measurements throughout the day.

## Friday, May 29, 2020
Today, I set up a Telegraf, InfluxDB, and Grafana on a Chromebook. I followed the directions on the Time Series Wiki document that Matt Perry shared with me on Google Docs. When installing Telegraf, the option to install it via GitHub was the only option that I could get to work to install it on the Chromebook. I also read through any documentation that was linked in the document. When doing this, I learned that the Chromebook does not use http://localhost:3000. Instead, it uses http://penguin.termina.linux.test:3000.

I also installed Telegraf, InfluxDB and Grafana on my Raspberry Pi. As with the Chromebook, the GitHub instructions were the only instruction that I could get to work. InfluxDB was set up using the instructions that the Time Series Wiki document said to follow. Grafana was set up using [this guide](https://simonhearne.com/2020/pi-influx-grafana/). The instruction in the Time Series Wiki document did not work to install Grafana on the Raspberry Pi. I also set up docker on the Raspberry Pi by using the same commands that I used to install it on the Chromebook. 