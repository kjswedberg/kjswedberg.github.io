# Week 5

## Monday, June 15, 2020
The main reason that MQTT would not connect on Friday is because another package of mosquitto needed to be installed. Before, only mosquitto-clients package was installed. This morning, I installed the mosquitto package to try to fix this issue. 

At first, the command that was used to publish the data was `rtl_433 -F "mqtt://localhost:1883, events=sensors"`. The main error that was found was that the timestamp that was being sent to MQTT was not being recognized as a valid time stamp. As a result, the command to publish the data was changed to `rtl_433 -F "mqtt://localhost:1883, events=sensors" -M time:unix`. After hours of troubleshooting to see why Grafana was still not seeing the data, this command was changed again to `rtl_433 -F "mqtt://test.mosquitto.org:1883, events=acep/sensors" -M time:unix`. 

The majority of the day was spent editing and troubleshooting the config file for Telegraf. The config file had to be set up for the json data format. The same config file was edited that was used for the Shelly 1PM meter. The edits that worked included changing the server to `["tcp://test.mosquitto.org:1883"]`, the subscribed topics to `sensors`, and the data format to `"json"`. In addition the following lines were added: `json_time_key = "time"`, `json_time_format = "unix"`, json_time_format = "unix"`, json_string_fields = ["model", "channel", "mic", "id"], and `tag_keys = "id"`. After making these edits, `influx` was ran and mqtt_consumer was refreshed. After doing this, the data started to show up on Grafana.

Sometimes, there would be a connection error with MQTT. as an attempt to fix this, the command to publish the data was changed back to `rtl_433 -F "mqtt://localhost:1883, events=sensors" -M time:unix`. After making this edit, the data was stil being posted to Grafana. So far, this edit has resolved that issue.

I moved the Shelly 1PM meter from a clock radio to a refrigerator. I am not certain if the power fluxuation that is occuring is normal with the Shelly 1PM meter or if it has something to do with the clock itself. By moving it to the refrigerator, I should be able to determine this. 
