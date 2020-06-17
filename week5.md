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







