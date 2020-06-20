# Week 5

## Monday, June 15, 2020
The main reason that MQTT would not connect on Friday is because another package of mosquitto needed to be installed. Before, only the mosquitto-clients package was installed. This morning, I installed the mosquitto package to try to fix this issue. 

At first, the command that was used to publish the data was `rtl_433 -F "mqtt://localhost:1883, events=sensors"`. The main error that was found was that the timestamp,which was being sent to MQTT, was not being recognized as a valid time stamp. As a result, the command to publish the data was changed to `rtl_433 -F "mqtt://localhost:1883, events=sensors" -M time:unix`. For part of the day, this command was changed to `rtl_433 -F "mqtt://test.mosquitto.org:1883, events=acep/sensors" -M time:unix`. 

The majority of the day was spent editing and troubleshooting the config file for Telegraf. The config file had to be set up for the json data format. The same config file was edited that was used for the Shelly 1PM meter. The edits that worked included changing the server to `["tcp://test.mosquitto.org:1883"]`, the subscribed topics to `"sensors"`, and the data format to `"json"`. In addition the following lines were added: `json_time_key = "time"`, `json_time_format = "unix"`, `json_time_format = "unix"`, `json_string_fields = ["model", "channel", "mic", "id"]`, and `tag_keys = "id"`. 

Sometimes, there would be a connection error with MQTT. as an attempt to fix this, the command to publish the data was changed back to `rtl_433 -F "mqtt://localhost:1883, events=sensors" -M time:unix`. After making this edit, the data was stil being posted to Grafana. So far, this edit has resolved that issue.

I moved the Shelly 1PM meter from a clock radio to the Raspberry Pi. I am not certain if the power fluxuation that is occuring is normal with the Shelly 1PM meter or if the Shelly prefers a load that pulls more current. By moving it to another object, I should be able to determine this. 

## Tuesday, June 16, 2020
This morning, I attended the ACEP-USARC Virtual Alaska Electric Vehicle (EV) Workshop. 

I also worked more on editing config files for Telegraf. When I edited that file yesterday, I committed out the lines that were associated with the data from the Shelly 1PM meter and I added the lines that were associated with data from the temperature and humidity sensors. I decided that I wanted to try to collect data from the Shelly 1PM meter and the sensors at the same time. So, I made two copies of the current config file. One copy is set up for the data being collected by the sensors and the other is set up for the data being collected by the Shelly 1PM meter. The two config files have been uploaded to the Research Workspace for reference.

The config file that is set up for the temperature and humidity sensors is named sensorstelegraf.conf. It sends data to InfluxDB and it uses the mqtt database that is set up with Influx. In the "Service Input Plugins" section, the server is set to `["tcp://192.168.1.118:1883"]`. The data format is set to json. To start Telegraf with this file, the command `telegraf --config sensorstelegraf.conf` is used. As with before, the data is sent to the MQTT server with the command `rtl_433 -F "mqtt://localhost:1883, events=sensors" -M time:unix`.

The config file that is set up for the Shelly 1PM meter is named shellytelegraf.conf. It also sends data to InfluxDB with the mqtt database. In the "Service Input Plugins" section, the server is set to `["tcp://test.mosquitto.org:1883"]`. The data format is set to value of type float. To start this Telegraf with this file, the command `telegraf --config shellytelegraf.conf` is used. The data from the Shelly meter is sent to the MQTT server. from the web interface. So, no additional command needs to be ran to sent the data to the MQTT server.

All that needed to be done to have Telegraf send InfluxDB the data from both the sensors and the Shelly meter was run `telegraf --config shellytelegraf.conf` in one command terminal window and run `telegraf --config sensorstelegraf.conf` in a different command terminal window. A third command terminal window is needed to run `rtl_433 -F "mqtt://localhost:1883, events=sensors" -M time:unix`, so that Telegraf can recieve the data with the sensorstelegraf.conf file. After I had completed these steps, Grafana was able to collect the data from the sensors and from the Shelly meter at the same time. Grafana is set up to collect the data using two Dashboards. Tomorrow, I will post screenshots of the panels in the two Dashboards. I am waiting till tomorrow, so that 24 hours of uninterrupted data will be available for the screenshots for both the sensors and the Shelly meter. 

This afternoon, I started working through DataCamp's Introduction to Python course.

## Wednesday, June 17, 2020
This morning,  I collected screenshots of the data from the temperature and humitiy sensors and the Shelly 1PM meter from Grafana to include in this post. Figures 1 and 2 contain the data from the sensor in my bedroom. Figures 3 and 4 contain the data from the sensor in the living room. Figures 5 and 6 contain the data from the sensor that is outside. Figures 7 through 11 contain the data from the Shelly 1PM meter, when it is plugged into the Raspberry Pi. In Figure 7, power decreases at 10:38:40, spikes at 16:11:20, increases at about 19:00, and increases at 7:00:00. There is still some flucuation with the power, however the amount of flucuations seems less, but the amount does vary thoughout the day. As a result, I think that the flucuation is associated with both the Shelly 1PM meter and with the amount of current that the load pulls. This flucuation is minimal enough to where it should not be an issue. With some multimeters, some flucuation can be normal.

![image](https://user-images.githubusercontent.com/65566903/84924285-c8d02300-b074-11ea-92b9-b5ed78d79b48.png) <br>
**Figure 1: The temperature data from the sensor in my bedroom.** <br>
![image](https://user-images.githubusercontent.com/65566903/84924512-15b3f980-b075-11ea-8833-073c5cb1b5bd.png) <br>
**Figure 2: The humidity data from the sensor in my bedroom.** <br>
![image](https://user-images.githubusercontent.com/65566903/84924542-21072500-b075-11ea-9ab9-7e580dfa072f.png) <br>
**Figure 3: The temperature data from the sensor in the living room.** <br>
![image](https://user-images.githubusercontent.com/65566903/84924550-25cbd900-b075-11ea-982f-8fc77b0b05cd.png) <br>
**Figure 4: The humidity data from the sensor in the living room.** <br>
![image](https://user-images.githubusercontent.com/65566903/84924570-2ebcaa80-b075-11ea-8080-2f60a57cc754.png) <br>
**Figure 5: The temperature data from the sensor outside on the porch.** <br>
![image](https://user-images.githubusercontent.com/65566903/84924611-3e3bf380-b075-11ea-80ef-f19a15ece02a.png) <br>
**Figure 6: The humidity data from the sensor outside on the porch.** <br>

![image](https://user-images.githubusercontent.com/65566903/84927329-249cab00-b079-11ea-8839-898d6415584b.png) <br>
**Figure 7: The power data from the Shelly 1PM meter** <br>
![image](https://user-images.githubusercontent.com/65566903/84927358-2ebea980-b079-11ea-8291-f00bcb4f8501.png) <br>
**Figure 8: The incrementing energy counter data from the Shelly 1PM meter** <br>
![image](https://user-images.githubusercontent.com/65566903/84927378-38481180-b079-11ea-8240-d2798bd26a29.png) <br>
**Figure 9: The temperature data in fahrenheit from the Shelly 1PM meter** <br>
![image](https://user-images.githubusercontent.com/65566903/84927398-41d17980-b079-11ea-84fc-0ef5af95c081.png) <br>
**Figure 10: The temperature data in celsius from the Shelly 1PM meter** <br>
![image](https://user-images.githubusercontent.com/65566903/84927422-4b5ae180-b079-11ea-92ab-b5daec2acd0c.png) <br>
**Figure 11: The overtemperature data from the Shelly 1PM meter** <br>

This morning, I attended the ACEP-USARC Virtual Alaska Electric Vehicle (EV) Workshop. During the afternoon, I worked more on the Introduction to Python course and I completed the required lab worker training found at [https://www.uaf.edu/safety/training/required-lab-worker-training.php](https://www.uaf.edu/safety/training/required-lab-worker-training.php). I also read through the "Electrical Safety In The Laboratory" document that was sent over Discord.

## Thursday, June 18, 2020
Last night at about 22:21:58, the Grafana stopped recieving data from the Shelly 1PM meter and the temperature and humidity sensors. This morning, I tried to figure out why this happened. This morning, the Raspberry Pi was on, but the command terminals had closed. In the Shelly Cloud app, cloud was disabled and the IP address for the web interface had changed. On the web interface, the checkbox that enabled the MQTT server had to be re-checked. The settings for the MQTT server were not changed. After checking these things, I started sending the data from the sensors to the MQTT server running on the Raspberry Pi's localhost IP address. After starting Telegraf with both config files, Grafana started recieving data agian.

One reason why this issue might of occured could be due to a very brief power glitch. This would cause the Shelly 1PM meter to turn off for a brief moment and cause the Raspberry Pi to loose power during that time. Before, when the Shelly lost power, the web interface IP address did not change and the Shelly Cloud app did not disconnect from Cloud. When I checked the data that Grafana had collected right before this issue occured, it had not overheated and the power was not close to its maximun power. So, the actual reason that caused this is unknown, but a power glitch is the most likely reason. 

Today, I also reviewed the pandas-to-influx.ipynb file. While going through it, I had to look up some of the methods to see what they do. I also tried to go through the Python code that is on the dca_modbus-tig GitHub site. Based off my previous knowledge of computer programming, I could understand that most of the code were functions. However, a I could not figure out what a lot of the methods did. Because the Eaton project may envolve doing similar stuff that these scripts do, I want to try to understand what is happening with each of the functions. As a result, I want to try to go through DataCamp's advanced Python and pandas course. I finished the Introduction to Python course today, and the advanced Python and pandas course are the next two courses on DataCamp's Python plan.  

## Friday, June 6, 2020

This morning, I reviewed the documents that are in the Documentation_Maintenance folder for the Solar Test Site. This was for preperation for the meeting on Monday.

Late morning and early afternoon, I researched information about the wavelengh and travel of radio waves. Specifically, I looked for information about radio waves that are at the frequency of 433 MHz. This is the frequency that the temperature and humidity sensors chirp to and that the RTL_SDR is set-up to pick up. Wavelength is calculated by dividing the speed of light by the frequency. The speed of light is about 3.0 x 10<sup>8</sup> meters per seconds. So, a frequency of 433 MHz has a wavelength of 69.28 centimeters (27.28 inches). The expected range for 433 MHz is about 100 to 300 feet outdoes and 30 to 100 feet indoors ([EDN, 2014](https://www.edn.com/using-433-mhz-for-wireless-connectivity-in-the-internet-of-things/)). This range does assume a helical antenna and a transmitter. Electromagnetic waves do not require a medium to travel through. As a result, they can travel though a vacuum, air, and through solid materials. ([NASA Science, 2010](http://science.nasa.gov/ems/02_anatomy)). AM and FM radio waves travel farther than the electromagnetic waves of 433 MHz. If this was not the case, car radios may have difficulty picking up the radio waves. AM radio waves are in the frequency range of 535 to 1605 kHz. FM radio waves are in the frequency of 88 to 108 MHz [Georgia State University](http://hyperphysics.phy-astr.gsu.edu/hbase/Audio/radio.html). As a result, it can be assumed that lower frequencies can travel farther. Thus, larger wavelengths can travel farther.

References
EDN. (2014, November 12). Using 433 MHz for wireless connectivity in the Internet of Things. Retrieved June 19, 2020, from [https://www.edn.com/using-433-mhz-for-wireless-connectivity-in-the-internet-of-things/](https://www.edn.com/using-433-mhz-for- wireless-connectivity-in-the-internet-of-things/) 

Georgia State University. (n.d.). AM and FM Radio Frequencies. Retrieved June 19, 2020, from [http://hyperphysics.phy-astr.gsu.edu/hbase/Audio/radio.html](http://hyperphysics.phy-astr.gsu.edu/hbase/Audio/radio.html)

National Aeronautics and Space Administration, Science Mission Directorate. (2010). Anatomy of an Electromagnetic Wave. Retrieved June 19, 2020, from [http://science.nasa.gov/ems/02_anatomy](http://science.nasa.gov/ems/02_anatomy))

During the afternoon, I worked on the Introduction to Shell DataCamp course.






