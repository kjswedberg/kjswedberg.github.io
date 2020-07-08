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







