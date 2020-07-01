# Week 7

## Monday, June 29, 2020

Today, I work more on learning about WireViz. I tried out the options for the wire gauge and the connector type on the wiring diagram for the Shelly 1PM meter. The connector type seems to be treated as a string. Whatever is inserted for it is then put on the diagram and the bill of materials. This would allow for custom connectors to be inserted for the type. After this, I worked on figuring out how to do a demo of this. I think that the easiest way is to show the yml file, the command to run WireViz, the files generated, and the resulting diagram and bill of materials.

I also started DataCamp's Data Processing in Shell course.

## Tuesday, June 30, 2020

This morning, I listened to the Grafana 7.0 webinar. 

I also worked on changing the Raspberry Pi's localhost IP address from a dynamic to a static IP address. When using Raspberry Pi's with kits that requires internet and the actual value of the localhost IP address, then it may be worth making sure that the localhost IP address is static. To do this, I edited /etc/dhcpcd.conf by uncommenting the following lines and changing the IP address to match the current ones: <br>
    `interface wlan0` <br>
    `static ip_address=192.168.1.116/24` <br>
    `static routers = 192.168.1.1` <br>
    `static domain_name_servers=192.168.1.1` <br>
The ip_address was found using `ifconfig` and the routers was found with `route -n`. 

Today, I finished DataCamp's Data Processing in Shell course.

On the Shelly Cloud app, I set the Correction Coefficient to 0.85. The reason behind this was to try to make the Shelly Meter more accurate. Using a Clamp-On Amp meter and a digital multimeter, I measured the current and the voltage of a hair dryer on three settings. I then calculated the power and compared that power with what the Shelly Meter measured. Table 1 contains the data that was collected to make the Shelly meter more accurate. The measured power was calculated by taking the product of the measured voltage and the measured current. The percent error is between the measured power and the power that was measured by the Shelly. The theoritical max power was calculated with the formula P=2*V*I. The measurements are RMS values. To get the peak value from RMS, the RMS value is multiplied by the square root of 2. So the formula for the max power has an addition 2 in it. From the measurements that were taken, the highest percent error was 4.62 %. The power that was measured by the Shelly is always lower than the theoritical max power. 

**Table 1: The data collected and used to make the Shelly more accurate.**
| Hair Dryer Setting | Measured Voltage | Measured Current | Measured Power | Power Measured by Shelly | Percent Error | Theoritical Max Power | 
| ------------------ | ---------------- | ---------------- | -------------- | ------------------------ | ------------- | --------------------- | 
|     Low, Cool      |     119.5 V      |      3.2 A       |    382.4 W     |           396 W          |     3.56 %    |        768 W          | 
|     Low, Warm      |     117.5 V      |      5.8 A       |    681.5 W     |           713 W          |     4.62 %    |        1,392 W        | 
|     Low, Hot       |     116.2 V      |      8.7 A       |    1,011 W     |          1,000 W         |     1.09 %    |        2,088 W        | 

After setting up the Shelly Meter with the Raspberry Pi again, the power was measured by the Shelly Meter to be 9.360 W. The current measured by the meter on the USB power adapter for the Raspberry Pi read 1.71 A. Assuming that it is accurate and that the voltage really is 5 V, then the power should be 8.55 W. This is less than a watt difference. When the clamp-on amp meter was used to try to measure the current, the meter did not measure the current. Before when this meter did not work to measure things, it was because the load had a variable resistor in it or the load did not pull enough current for the meter to read. These reasons may be the case with the Raspberry Pi. 

When using the Shelly meter to measure the power that needs to be supplied by a battery, it would probably be an idea to use the max power. Because a percent error does still exist between the measured power and the power measured by the Shelly Meter, it may also be an idea to go use a value slightly higher than the value for the max power. 


## Wednesday, July 1, 2020






