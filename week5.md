# Week 5

## Monday, June 15, 2020
The main reason that MQTT would not connect on Friday is because another package of mosquitto needed to be installed. Before, only mosquitto-clients package was installed. This morning, I installed the mosquitto package to try to fix this issue. 

At first, the command that was used to publish the data was `rtl_433 -F "mqtt://localhost:1883, events=sensors"`. The main error that was found was that the timestamp that was being sent to MQTT was not being recognized as a valid time stamp. As a result, the command to publish the data was changed to `rtl_433 -F "mqtt://localhost:1883, events=sensors" -M time:unix`. After hours of troubleshooting to see why Grafana was still not seeing the data, this command was changed again to `rtl_433 -F "mqtt://test.mosquitto.org:1883, events=acep/sensors" -M time:unix`. 

The majority of the day was spent editing and troubleshooting the config file for Telegraf. The config file had to be set up for the json data format. The same config file was edited that was used for the Shelly 1PM meter. The edits that worked included changing the server to `["tcp://test.mosquitto.org:1883"]`, the subscribed topics to `"sensors"`, and the data format to `"json"`. In addition the following lines were added: `json_time_key = "time"`, `json_time_format = "unix"`, `json_time_format = "unix"`, `json_string_fields = ["model", "channel", "mic", "id"]`, and `tag_keys = "id"`. 

Sometimes, there would be a connection error with MQTT. as an attempt to fix this, the command to publish the data was changed back to `rtl_433 -F "mqtt://localhost:1883, events=sensors" -M time:unix`. After making this edit, the data was stil being posted to Grafana. So far, this edit has resolved that issue.

I moved the Shelly 1PM meter from a clock radio to the Raspberry Pi. I am not certain if the power fluxuation that is occuring is normal with the Shelly 1PM meter or if it has something to do with the clock itself. By moving it to another object, I should be able to determine this. 

## Tuesday, June 16, 2020
This morning, I attended the ACEP-USARC Virtual Alaska Electric Vehicle (EV) Workshop. 

I also worked more on editing config files for Telegraf. When I edited that file yesterday, I committed out the lines that were associated with the data from the Shelly 1PM meter and I added the lines that were associated with data from the temperature and humidity sensors. I decided that I wanted to try to collect data from the Shelly 1PM meter and the sensors at the same time. So, I made two copies of the current config file. One copy is set up for the data being collected by the sensors and the other is set up for the data being collected by the Shelly 1PM meter. The two config files have been uploaded to the Research Workspace for reference.

The config file that is set up for the temperature and humidity sensors is named sensorstelegraf.conf. It sends data to InfluxDB with the mqtt database that is set up with Influx. In the "Service Input Plugins" section, the server is set to `["tcp://192.168.1.118:1883"]`. The data format is set to json. To start Telegraf with this file, the command `telegraf --config sensorstelegraf.conf` is used. As with before, the data is sent to the MQTT server with the command `rtl_433 -F "mqtt://localhost:1883, events=sensors" -M time:unix`.

The config file that is set up for the Shelly 1PM meter is named shellytelegraf.conf. It also sends data to InfluxDB with the mqtt database. In the "Service Input Plugins" section, the server is set to `["tcp://test.mosquitto.org:1883"]`. The data format is set to value of type float. To start this Telegraf with this file, the command `telegraf --config shellytelegraf.conf` is used. The data from the Shelly meter is sent to the MQTT server. from the web interface. So, no additional command needs to be ran to sent the data to the MQTT server.

All that needed to be done to have Telegraf send InfluxDB the data from both the sensors and the Shelly meter was run `telegraf --config shellytelegraf.conf` in one command terminal window and run `telegraf --config sensorstelegraf.conf` in a different command terminal window. A third command terminal window is needed to run `rtl_433 -F "mqtt://localhost:1883, events=sensors" -M time:unix`, so that Telegraf can recieve the data with the sensorstelegraf.conf file. After I had completed these steps, Grafana was able to collect the data from the sensors and from the Shelly meter at the same time. Grafana is set up to collect the data using two Dashboards. Tomorrow, I will post screenshots of the panels in the two Dashboards. I am waiting till tomorrow, so that 24 hours of uninterrupted data will be available for the screenshots for both the sensors and the Shelly meter. 

This afternoon, I started working through DataCamp's Introduction to Python course.

## Wednesday, June 17, 2020
This morning,  I collected screenshots of the data from the temperature and humitiy sensors and the Shelly 1PM meter from Grafana to include in this post. Figures 1 and 2 contain the data from the sensor in my bedroom. Figures 3 and 4 contain the data from the sensor in the living room. Figures 5 and 6 contain the data from the sensor that is outside. Figures 7 through 11 contain the data from the Shelly 1PM meter, when it is plugged into the Raspberry Pi. In Figure 7, power decreases at 10:38:40, spikes at 16:11:20, increases at about 19:00, and increases at 7:00:00. There is still a small amount of flucuation in the power, however the amount of flucuations varies thoughout the day. As a result, I think that the flucuation is associated with the Shelly 1PM meter and with the load that it is taking measurements from. 

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



