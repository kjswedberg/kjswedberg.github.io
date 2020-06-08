# Week 3

## Monday, June 1, 2020
This morning, I used the Shelly 1PM power meter on a blow dryer to get more data points. The actual current and the actual voltage were measured with a clamp-on meter that could read AC current and with a digital multimeter. [This Spreadsheet](https://docs.google.com/spreadsheets/d/1evgPBBHH2XYcFCAERA_7hmZKDgcDnaXJryOPfYvQiyg/edit?usp=sharing) shows the measured values, the actual power that was calculated from those measured values, and the power that the Shelly app said that the blow dryer. A coffee maker was also measured, while it was heating up water. The measured current and the measured voltage for the coffee maker was close enough to the measured current and the measured voltage of the blow dryer, while it was on its cool, high setting. This made the actual measured powers for those two loads close in value. However, the power that the Shelly app read for the two loads were not close in value, but were 68 W apart instead. The percent errors for the measurements that were made today are higher than 20 % and less than 35 %. The meter used to measure the current was rated to be accurate to plus/minus 2 %, while the digital multimeter was rated to be accurate to plus/minus 0.5 %. When some values were repeated, the Shelly app was not as precise as it was during the measurements that were done during Week 2. Figure 1 shows the power meter bar graph with the calculated power and the measured power results. In this case, the calculated power is the power that was calculated from the measured voltage and the measured current, while the measured power is the power that the Shelly 1PM power meter measured. Figure 2 shows a graph that compares the percent error between the measured power and the calculated power with the measured current. 

![Power Meter Graph](https://user-images.githubusercontent.com/65566903/83470841-a3fe6d80-a42f-11ea-9259-9cc4a6128369.png) <br>
**Figure 1: The power meter bar graph for the calculated and the measured powers.** <br>

![Percent Error vs  Measured Current ](https://user-images.githubusercontent.com/65566903/83470848-a791f480-a42f-11ea-8a53-088548495b07.png) <br>
**Figure 2: The percent error for the measured and calculated powers compared to the measured current.** <br>

Based off of the data that was collected today, this meter is currently not accurate and precise enough to use for important power measurements. However, there is an option to add a power correction coefficient, which may make the meter more accurate. The app also has a timer option and a schedule option. These options can allow for a user to schedule how long a device is on for. Those options also allow for a device to turn on at a certain and turn off at a certain time. So although this device is not able to make critical,  measurements with that are accurate, it does allow someone to control devices from a distance and it allows someone to have an idea about which devices using the most power.

During the afternoon, I installed Jupyter Notebooks and Anaconda on the Chromebook. I also started to think about how I would create a timeseries measurement with the Shelly 1PM power meter to use with Telegraf to create some graphs with Grafana. So far, the way that I can think of is to create a csv file with the data and see if Telegraf can read the data from that file. However, I need to find more information on how to create the data csv file, so that I can ensure that Telegraf can read the data file. I have enabled cloud on the Shelly app to see if the power used at set intervals will be stored in the app. I plugged a clock into the Shelly power meter to collect data from, so that I can see how the app will store the data.

## Tuesday, June 2, 2020
This morning and early afternoon, I worked more with the Shelly Cloud app to determine how data could be collected from the Shelly 1PM power meter. I started out collected some data manually, inserting that data in a csv file, and then editing a config file to allow Telegraf to read the data. While doing this, I was able to get Telegraf to find the csv file. However, Telegraf had an issue with finding the time column. To start working on automatic data collection, I found the IP address for the Shelly 1PM power meter from the Shelly Cloud app. The power meter is able to be controlled from the web interface. With some help, I was able to enable MQTT from the web interface. This allows data to be sent from the Shelly 1PM power meter to a server located at test.mosquitto.org:1883. After installing mosquitto-clients on a Chromebook, I was able to view data from the power meter from the command terminal. In addition to viewing data regarding the power, data regarding the internal temperature and the status of the device can also be viewed from the command terminal. A document that I am working on writing that shows how to set-up a Shelly 1PM power meter and how data can be collected from it can be found [here](https://docs.google.com/document/d/1-RYcvCb6G0ohw3NxV3vbHoEbNhK2FrxF3Uv9_O2ZMwI/edit?usp=sharing).   

This morning, I was also introduced to the Eaton project. This project has similarities to what I am currently working on with the Shelly 1PM power meter. In both cases, data is being collected by a meter. A way to access and analyze that data needs to be found. One of the main differences is that the Eaton project will contain more meters that will measure more than just power. The meters being used are different from the Shelly 1PM power meter and the software may also be different. However, I expect that there will be some similarites.

While being introduced to the Eaton project, I was given a quest to fnd out about deadband data triggered events. Deadband is described as the domain of imput values that result in the output being zero. Having a high deadband can create issues. Based off the Allied Valve Inc. link below, some issues that can result with having a high deadband include having higher possibilities of having oscillations in the control loop and errors from load disturbances. 

[https://alliedvalveinc.com/troubleshooting/common-control-valve-problems-watch/](https://alliedvalveinc.com/troubleshooting/common-control-valve-problems-watch/)

## Wednesday, June 3, 2020
This morning, I worked on proofreading the document that I started writing yesterday about how a Shelly 1PM power meter can be used to collect data. I added a section that summarizes some of the data that the Shelly 1PM collects and to show links where the user can find specifications and information about device. 

I have not yet determined how to access the time that is associated with each measurement that is outputed using the command terminal. There is a timestamp attribute. However, I have not been able to access that attribute yet. The site that shows that it exists is located [here](https://shelly-api-docs.shelly.cloud/#shelly1-1pm-status). Figure 3 is a screenshot of the part of that site that shows the description of the meters attribute and Figure 4 is a screenshot that shows the description of the timestamp attribute. Some of the commands that I have tried using to access the timestamp are shown in the list below. 

* mosquitto_sub -h test mosquitto.org -t 'shellies/ACEP/shelly/1pm-C44593/status/meters/timestamp'
* mosquitto_sub -h test mosquitto.org -t 'shellies/ACEP/shelly/1pm-C44593/status/meters/0/timestamp'
* mosquitto_sub -h test mosquitto.org -t 'shellies/ACEP/shelly/1pm-C44593/meters/timestamp'
* mosquitto_sub -h test mosquitto.org -t 'shellies/ACEP/shelly/1pm-C44593/meters/0/timestamp'
* mosquitto_sub -h test mosquitto.org -t 'shellies/ACEP/shelly/1pm-C44593/timestamp

> ![image](https://user-images.githubusercontent.com/65566903/83698524-1f862900-a5ae-11ea-8ad4-560d8080cbd9.png) <br>
> **Figure 3: The Shelly1/1PM: /status meters atributes screenshot** <br>

> ![image](https://user-images.githubusercontent.com/65566903/83698473-fbc2e300-a5ad-11ea-8896-f5673ca8e0b6.png) <br>
> **Figure 4: The screenshot of the meters attributes for the Shelly1PM.** <br>

While trying to access the timestamp attribe, I did some research to see if there was a solution online. However, the information that I could find regarding the timestamp was very limited. It may be necessary to write a script that can calculated the timestamp from the incrementing energy counter. This would require the script to input the energy counter value, the power, and the formula that is used to find the value for the energy counter.

Another possible way to get the time of each measurement is configuring a custom NTP server for the Shelly 1PM and then retriving the time from that. However, there may be different delay times for the Shelly to output the data and for the time to be retrieved from the server. This might make syncing the time with the data point difficult. As a result, it may be best to continue trying to access the timestamp attribute. 

## Thursday, June 4, 2020
Today, I worked on trying to use the data that was being from the Shelly 1PM power meter by using Telegraf and InfluxDB. I used [this site](https://gist.github.com/anoochit/5088b20dc51492b995b2da2841515052) as a reference to help me edit a Telegraf config file. After running the "Influx" and then "show databases", a database named mqtt-telegraf, which was the database specified in the Output Plugin section, did show up as a database. However, when I ran the command "telegraf --config $pwd Shelly_Data/mqtt-telegraf.conf" in the command terminal, an error message said "Error in plugin: must be an object or an array of objects." This error is shown in Figure 5. I think the error is in the Input section in the edited confg file. 

![2020-06-04-144025_1280x800_scrot](https://user-images.githubusercontent.com/65566903/83825620-47e15680-a686-11ea-9863-f1b829e09cc0.png) <br>
**Figure 5: The error that was recieved from the command terminal**

I also worked on writing up the ATW content that was asked for. 

## Friday, June 5, 2020
Today, I worked with Matt Perry on troubleshooting the config file for Telegraf. The main error was the URLs not pointing to the actual IP address of the Raspberry Pi being used. The data format needed to be changed to value and the data type needed to be changed to float. InfluxDB also needed to be changed to a newer version. It was version 1.6, but it needs to be version 1.8 for to work with Grafana. A user for InfluxDB was also created. After solving these issues, I was able to set up a data source on Grafana and then view the data on Grafana. The graphs on Grafana do have a timestamp that is assosiated with them. The timestamp that is associated with the data is from when InfluxDB reads the data that is sent from MQTT. As a result, there is not much that can be done to achieve a more accurate timestamp. After setting up the TIG stack, I updated the document about setting up the Shelly 1PM meter for data analysis by adding how I was able to set up the data with the TIG stack. Between Monday and Tuesday, I am planning on redoing this process on the Chromebook, so that I can try it a second time and understand the process better. 

