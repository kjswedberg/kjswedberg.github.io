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

## Tuesday, June 9, 2020
Yesterday evening, the internet router got rebooted. While trying to troubleshoot why Telegraf was not liking the IP address in the config file, I rebooted the Raspberry Pi and the Shelly. Since that did not fix the issue, I looked up the IP address of the Raspberry Pi, and found that it had changed. I updated the config file and the Grafana data source with the new IP address and it started working again. Because the Shelly was restarted, the incrementing energy counter reset to start at zero. As a result, the incremening energy counter plot changed, but the other plots did not change significantly. This morning, I checked the IP for the Chromebook and that IP address did not change.

I looked into seeing if it was possible to change the Raspberry Pi's address from a dynamic IP address to a static IP address. This can be done by editing the dhcpcd.conf file. I would also probally have to stop collecting data, while I am editing the config. Since it is not very often that the internet router gets rebooted, I decided leave the IP address as a dynamic IP address. If the IP address changes for other reasons, then it will need to be changed to a static IP. I do not want to risk messing up the settings of the Raspberry Pi by trying to change an IP address from dynamic to static, when a dynamic IP address is currently working to collect the data.

For the majority of the work day, I focused on finishing the draft of the statement of work for the Eaton Project. I researched examples and templates, and I tried to include the information that the majority of the examples suggested included. The majority of the templates and examples use introduction/background, objective, and scope of work for categories. They suggest having one section that describes different phases and then a seperate section to describe the tasks involved with each phase. I decided to use the categories introduction/background, objective, scope of work, and tasks descriptions. I then organized what I had written yesterday into those categories. Tomorrow, I will proofread the document one more time and then share it.

In the afternoon, I started finding the user manuals for the different components of the network metering system. After proofreading the statement of work document tomorrow morning, I am planning on looking through those user manuals tomorrow morning. I was able to find the user manual for the Power Epert Meter 2000 Series on the Discord site. I was able to find pdfs for the user manual for the Power Xpert Meter 2000 Series and the Foreseer 7.2.210 Server Guide by doing a google search for them. I also found a guide for Eaton's Yukon Visual T&D HMI/SCADA by doing a google search. The list below contains links to the manuals. I am not certain if the guides that I found for the Foreseer and the Visual T&D are the for the correct models. If I have time, I may look through them anyway.

* [Power Xpert Meter 2000 Series](http://m.eaton.com/ecm/groups/public/@pub/@electrical/documents/content/im02601001e.pdf) <br>
* [Power Xpert PXM 4000/6000/8000](https://www.eaton.com/ecm/groups/public/@pub/@electrical/documents/content/im02601004e.pdf) <br>
* [Foreseer 7.2.210 Server Guide](https://www.eaton.com/content/dam/eaton/services/eess/eess-documents/foreseer-7-2/eaton-foreseer-72210-server-guide-mn152049en.pdf) <br>
* [Yukon Visual T&D HMI/SCADA](https://www.eaton.com/content/dam/eaton/products/utility-and-grid-solutions/grid-automation-systems/hmi-scada/yukon-visual-td-hmi-scada-br914001en.pdf) <br>

Throughout the day, I checked Grafana to make sure that it was collecting data. So far, it has been able to run about 22 hours without having any problems. While on Grafana, I created more panels. In addition to the original panel with all the data fields on it, each data field now has its own dedicated panel. 

## Wednesday, June 10, 2020
This morning, I looked through the user guides for the two Power Xpert Meters that will be used for the Eaton Project. 

During the afternoon, I worked on gaining experiece using Python. I worked through writing a copy of the dca-ORCA modbus.ipynb in Jupyter Notebooks on the Chromebook. This is a file that Henry shared with me on GitHub earlier. After running that and confirming that I did not have errors in my script, I worked on writing a simple game in the Jupyter Notebooks. This was to gain experience and test my understanding using Python. The game generated a random number from 1 to 10 and gave the user three tries to guess what the number was. The user was notified if their guess was correct. If the user did not guess the correct number after three tries, the user was told what the number was. Then, the user could decide whether to keep playing or to quit.

Also during the afternoon, I learned more about Grafana and I learned some about using the TIG playground that. With the knowledge that I learned from this, I changed the settings on the panels, displaying the data from the Shelly 1PM meter, to show the maximum, minimum, average, and current values in a table format.
