# Week 8

## Monday, July 6, 2020
Today, I worked on setting up the Raspberry Pi that was with the stuff that I picked up earlier. I put the Raspberry Pi in the case that it came with. I also attached the heat sinks and the fan to the Raspberry Pi, so that it is less likely to overheat. I initially set it up with the screen that came with the T3 kit. On the Raspberry Pi, I installed the RTL_SDR and RTL_433 packages, so that it would work with the two SDRs.

Using the Shelly 1PM meter, I determined the power being used by just the Raspberry Pi, the screen that came with the T3 kit, and the two SDRs. This was done with the Shelly 1PM meter by taking the maximum of 10 power measurements. The power being used by the Raspberry Pi was measured directly. The power being used by the screen was then determined by measuring the power being used by the Raspberry Pi and the screen, and then subtracting the power being used by the Raspberry Pi. The power being used by the silver RTL_SDR was determined by measuring the total power being used by the Raspberry Pi with the screen and the silver RTL_SDR plugged in. That value was then subtracted from the power being used by the Raspberry Pi and the screen. This process was repeated for the NESDR Nano 3. 

The NESDR Nano 3 uses slightly less power than the silver RTL_SDR uses. I tried it with the smaller and the larger antenna, and both used the same power. So far, it has not had the error issue saying "rtlsdr_read_reg failed with -7". The silver RTL_SDR also did not display that error, however it was only plugged in once. The NESDR Nano 3 was plugged in and out several times. 

I also worked more on DataCamp's Data Manipulation with Pandas course.

## Tuesday, July 7, 2020

Today, I had to change the spreadsheet that I had started yesterday. Instead of using the average, I used the maximum value. However, this started creating an issue with finding the power being used by the SDRs. As a result, I subtracted the maximum power measurement from the average value that the Raspberry Pi and screen used.

Today, the NESDR Nano 3 did get hot. 

When usig the 7 Inch Touchscreen Display, the icons are small. As a result, it is difficult to use the touchscreen to close programs. It also does not contain a touchscreen keyboard, so a keyboard is still necessary for typing. For some programs, the bottom of the picture goes past the edge of the screen. A config file may need to be edited to fix this. The 13.3 Inch HDMI Display does use more power. Around the picture, there is a black box. To fix the black box, a config file may need to be edited. 

I tried to set up the Wireless N Nano Router with the Raspberry Pi, so that I could measure the power being used by the Router. I did succeed in setting it up and measuring the power. However, when I tried to change the password for the WiFi login, it stopped working. I reset the device, and I am planning to try to set up the device again, when I measure its power with the other meter. 

When I plugged it in the Vodafone Mobile Broadband USB Stick today, the Raspberry Pi did not find it. Sometime later this week, I am planning on looking more into this device. 

The spreadsheet that contains the power measurements for the Raspberry Pi and the different devices can be found [here](https://docs.google.com/spreadsheets/d/17GJ9YTvDMcEH1WpFeCocZOULSqIYiJgjLDqLi2Exdtg/edit?usp=sharing).


## Wednesday, July 8, 2020

Today, I worked on setting up the PZEM-016 Modbus RTU Meter. This involved wiring it to a load, connecting the USB device to the meter, connecting the current clamp to the meter, and finding the software to view the data. The load is connected to 2 sections of an extension cord. I did a search in Google Images to find other wiring diagrams for setting up the meter. The one that I followed is on the [AliExpress](https://www.aliexpress.com/i/32912734749.html) website. I also used the notes that [PDAControl](https://pdacontrolen.com/initial-review-meter-pzem-016-modbus-rtu-rs485-by-peacefair/) made to set it up the meter and my Windows computer with the Peacefair software. T I set it the software on a Windows computer, since the [PDAControl notes](https://pdacontrolen.com/initial-review-meter-pzem-016-modbus-rtu-rs485-by-peacefair/) said that the software was for Windows. he software can be downloaded at the end of the [PDAControl](https://pdacontrolen.com/initial-review-meter-pzem-016-modbus-rtu-rs485-by-peacefair/) page or from [Mediafire](http://www.mediafire.com/file/dh4jezdiumq49i0/PZEM014%252C016-Master-English.zip/file). The Mediafire download contains a text file that contains the instructions for installing the software. To install and run the software, the PZEM-016 meter is plugged into a computer.  After the device is installed, the file run.bat  was opened by selecting "run as administrator". After running the run.bat file, the PZEM014-Master.exe could be ran. 

Part of the afternoon was spent updating the final report and the presentation slides. I also worked some on one of DataCamp's courses that involves Pandas.

## Thursday, June 9, 2020

Today, I used the PZEM-016 Modbus RTU Meter to repeat the measurements that I did with the Shelly 1PM on Monday and Tuesday. The spreadsheet that am putting my measurements in can be found [here](https://docs.google.com/spreadsheets/d/17GJ9YTvDMcEH1WpFeCocZOULSqIYiJgjLDqLi2Exdtg/edit?usp=sharing). 

I am still having issues getting the Vodafone Mobile Broadband USB Stick to work, so I have not been able to compare the power usage of the Wireless N Nano Router with that. The Raspberry Pi sees the Vodafone USB Stick as a drive. However, when I try to open the drive, the Raspberry Pi says that it is not a valid drive. The instructions that I am trying to follow can be found [here](https://github.com/acep-uaf/acep_config/tree/master/cell_modem). After following them, the log file makes it sound like the Raspberry Pi cannot find the device.

I looked some into moving data to the tig-playground today. On the Grafana webpage, there is a [page](https://grafana.com/docs/grafana/latest/reference/export_import/) that contains instructions for exporting an importing dashboards. Tommorrow, I am planning on setting the Raspberry Pi to collect data from the temperature and humidity sensors. I want to then use the Shelly 1PM meter to measure the power usage of the Raspberry Pi over the weekend. I want to then send that power data to the tig-playground. If importing the dashboard does not work, then there is an Influx datasource set up for me that I can learn to use.

## Friday, June 10, 2020

Today, I worked on getting the power measurements from the Shelly 1PM onto the Tig-Playground. Currently, the Shelly 1PM meter is measuring the power that is being consumed by the Raspberry Pi with the Silver RTL-SDR and the 13.3 Inch Display. The Raspberry Pi does have a screensaver enabled and the screensaver is set to a black screen. I am planning on collecting data with the 13.3 Inch Display until Monday morning. Figure 1 shows the dashboard of the power usage that was set up on the TIG Playground. Figure 2 shows the dashboard containing the temperature and humidity sensors that the Raspberry Pi is collecting with the Silver RTL-SDR. I am planning on collecting data with the 13.3 Inch screen over the weekend.

![image](https://user-images.githubusercontent.com/65566903/87207229-ebdaa500-c2b7-11ea-8f78-5b0f1693f22e.png) <br>
**Figure 1: The Power Usage Panel for the Shelly 1PM Raspberry Pi Measurements Dashboard on the TIG-Playground.** <br>

![image](https://user-images.githubusercontent.com/65566903/87207497-7d4a1700-c2b8-11ea-9dbe-85635531ccc9.png) <br>
**Figure 2: The Temperature and Humidity Panels for the Acurite Weather Sensors Dashboard on the Tig Playground.** <br>

Three times this morning, the Shelly Meter did not seem to be actually sending data to the MQTT server. When running the mosquitto_sub command to view the Shelly data, an error saying that the network is unreachable would appear. The only fix to this problem that I could find was to unplug the Shelly meter, delete the Shelly meter device from the app, and re-set up the device with the app. This also included re-setting up the MQTT settings on the web interface. So far, after completing these steps three times, it has not had this issue again. 

I also worked some more on DataCamp's Python courses on Pandas
