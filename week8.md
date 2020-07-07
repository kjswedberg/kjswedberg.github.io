# Week 8

## Monday, July 6, 2020
Today, I worked on setting up the Raspberry Pi that was with the stuff that I picked up earlier. I put the Raspberry Pi in the case that it came with. I also attached the heat sinks and the fan to the Raspberry Pi, so that it is less likely to overheat. I initially set it up with the screen that came with the T3 kit. On the Raspberry Pi, I installed the RTL_SDR and RTL_433 packages, so that it would work with the two SDRs.

Using the Shelly 1PM meter, I determined the power being used by just the Raspberry Pi, the screen that came with the T3 kit, and the two SDRs. This was done with the Shelly 1PM meter by taking the average of 10 power measurements. The power being used by the Raspberry Pi was measured directly. The power being used by the screen was then determined by measuring the power being used by the Raspberry Pi and the screen, and then subtracting the power being used by the Raspberry Pi. The power being used by the silver RTL_SDR was determined by measuring the total power being used by the Raspberry Pi with the screen and the silver RTL_SDR plugged in. That value was then subtracted from the power being used by the Raspberry Pi and the screen. This process was repeated for the NESDR Nano 3. 

The NESDR Nano 3 did not seem to get as hot as the silver RTL-SDR, but it did get warm. It also uses about 70 mW of less power than the silver RTL_SDR uses. I tried it with the smaller and the larger antenna, and both used the same power. So far, it has not had the error issue saying "rtlsdr_read_reg failed with -7". The silver RTL_SDR also did not display that error, however it was only plugged in once. The NESDR Nano 3 was plugged in and out several times. 

I also worked more on DataCamp's Data Manipulation with Pandas course.

## Tuesday, July 7, 2020

My plans for today are to set up the two screens with the Raspberry Pi and measure the power being used by them. 

I am also planning to measure the power that is used by the Wireless N Nano Router and the Vodafone Mobile Broadband USB Stick.

