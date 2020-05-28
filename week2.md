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

Late morning and during the afternoon, I worked on the Shelly 1PM power meter. I connected the power meter to an extention cord. This enables me to be able to switch what load is attached to it. It also has a switch attached to it, so that the load can be turned on or off. The power meter can be controlled from the Shelly Cloud app over WiFi. The amount of power that the load uses is read from the app. The app can also turn the load on or off. When using the app to control the load or to read the load's power usage, there is a delay time that ranges from approximately 6 seconds to 12 seconds. 

![Power_Meter_Assembled](https://user-images.githubusercontent.com/65566903/83200241-6035fc00-a0ef-11ea-9c0c-948faa3fbfef.JPG)
**Figure 1: The set-up for the power Shelly 1PM power meter**


