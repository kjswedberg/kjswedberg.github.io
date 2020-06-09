# Week 4

## Monday, June 7, 2020

This morning, I finished the ATW content and sent it in. I also started writing a draft of the statement of work for the Eaton project. 

This afternoon, I set up the TIG stack on the Chromebook with the data from the Shelly 1PM meter. I did this to gain more practice setting up the TIG stack to collect data from a MQTT source. While doing this on the Chromebook, I had to install the nano command. This is the command that I used to edit the Telegraf config files on the Raspberry Pie and on the Chromebook. The only difficulty with setting up the TIG stack on the Chromebook was finding the IP address. On the Raspberry Pi, I could find the IP address with the ifconfig command. However, the command terminal on the Chromebook did not recognize this command. I found several commands online to find the IP address, and the command that worked and that outputed an IP address that worked is `hostname -I | awk ‘{print $1}’`. 

In the telegraf config files on the Raspberry Pi computer and on the Chromebook, I changed the topic fields to suscribe to the power, energy, internal temperatures, and overtemperature topics separately. Previously, the topic that was suscribed to was `"shellies/ACEP/1pm-C44593/#"`. This caused an error, since telegraf was trying to treat the string "on", which was recieved from the status topic, as a float. By suscribing to the topics seperately, this error did not appear, since I was able to choose not to suscribe to the status topic. 

I also finishd setting up the Raspberry Pi computer to collect data today. I turned the screensaver to a black screen. I turned on the Raspberry Pi one of the first things this afternoon, so that I could confirm that no settings needed to be adjusted to ensure that data would continue to be collected. After starting the command terminal and running the command `telegraf`, I minimized the command terminal. I also unplugged the mouse and keyboard from the Raspberry Pi, so that they won't accidentally mess up the data collection progress if a button is pressed on one of them. The plots from Grafana that show three hours of data are shown in Figure 1, Figure 2, Figure 3, Figure 4, and Figure 5. Figure 5 should always have an output of 0, since an output of 1 means that the device is overheating.

![image](https://user-images.githubusercontent.com/65566903/84094315-0ebc2580-a9a9-11ea-84e6-2f6eca942ffe.png) <br>
**Figure 1: The power plot overtime from Grafana** <br>
![image](https://user-images.githubusercontent.com/65566903/84094337-15e33380-a9a9-11ea-9a41-0d51f89543ec.png) <br>
**Figure 2: The incrementing energy counter plot overtime from Grafana** <br>
![image](https://user-images.githubusercontent.com/65566903/84094359-1f6c9b80-a9a9-11ea-9216-2a7f85768eeb.png) <br>
**Figure 3: The internal temperature plot overtime from Grafana** <br>
![image](https://user-images.githubusercontent.com/65566903/84094370-27c4d680-a9a9-11ea-94bf-7eb52b96dd90.png) <br>
**Figure 4: The internal temperature plot overtime from Grafana** <br>
![image](https://user-images.githubusercontent.com/65566903/84094390-2eebe480-a9a9-11ea-8dec-a3b7b407643c.png) <br>
**Figure 5: The overtemperature plot overtime from Grafana** <br>
