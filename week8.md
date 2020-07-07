# Week 8

## Monday, July 6, 2020
Today, I worked on setting up the Raspberry Pi that was with the stuff that I picked up earlier. I put the Raspberry Pi in the case that it came with. I also attached the heat sinks and the fan to the Raspberry Pi, so that it is less likely to overheat. I initially set it up with the screen that came with the T3 kit. On the Raspberry Pi, I installed the RTL_SDR and RTL_433 packages, so that it would work with the two SDRs.

Using the Shelly 1PM meter, I determined the power being used by just the Raspberry Pi, the screen that came with the T3 kit, and the two SDRs. This was done with the Shelly 1PM meter by taking the maximum of 10 power measurements. The power being used by the Raspberry Pi was measured directly. The power being used by the screen was then determined by measuring the power being used by the Raspberry Pi and the screen, and then subtracting the power being used by the Raspberry Pi. The power being used by the silver RTL_SDR was determined by measuring the total power being used by the Raspberry Pi with the screen and the silver RTL_SDR plugged in. That value was then subtracted from the power being used by the Raspberry Pi and the screen. This process was repeated for the NESDR Nano 3. 

The NESDR Nano 3 did not seem to get as hot as the silver RTL-SDR, but it did get warm. It also uses slightly less power than the silver RTL_SDR uses. I tried it with the smaller and the larger antenna, and both used the same power. So far, it has not had the error issue saying "rtlsdr_read_reg failed with -7". The silver RTL_SDR also did not display that error, however it was only plugged in once. The NESDR Nano 3 was plugged in and out several times. 

I also worked more on DataCamp's Data Manipulation with Pandas course.

## Tuesday, July 7, 2020

Today, I had to change the spreadsheet that I had started yesterday. Instead of using the average, I used the maximum value. However, this started creating an issue with finding the power being used by the SDRs. As a result, I subtracted the maximum power measurement from the average value that the Raspberry Pi and screen used.

I tried to set up the Wireless N Nano Router with the Raspberry Pi. However, the Raspberry Pi did not accept the default password. As a result, I am going to try to set it up with another device tomorrow, so that I can measure its power with the Shelly. I also could not get the Vodafone Mobile Broadband USB Stick to work with the Raspberry Pi. This USB stick is designed for Windows and MAC systems and so it may not work on a Linux system. 

When usig the 7 Inch Touchscreen Display, the icons are small. As a result, it is difficult to use the touchscreen to close programs. It also does not contain a touchscreen keyboard, so a keyboard is still necessary for typing.
