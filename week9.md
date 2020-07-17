# Week 9

## Monday, July 13, 2020

This morning, with Arsh's help, I got the Vodafone Mobile Broadand USB Stick working. 

I also set up the Raspberry Pi with the 7 inch touchscreen display. For the next two days, the Shelly 1PM meter will be measuring the power that is being used by the Raspberry Pi, silver RTL-SDR, and the 7 inch display. The data from the Shelly 1PM meter is being sent to the TIG-Playground. On the TIG-Playground, a seperate dashboard was set up for the 7 inch display. The dashboard for the 13.3 display was saved, so that the default time range was the time range that correspondes to the 13.3 inch display. The two dashboards were then set up as a Playlist, so that they could be compared easier.

This afternoon, I worked on the presentation for Friday and more on a DataCamp course about Pandas.

## Tuesday, July 14, 2020

This morning, I worked more on the presentation for Friday and more on learning about Pandas through DataCamp.

During the afternoon, I worked on figuring out how to calculate the battery backup size for the SSN project. The hard part about this is figuring out the formula for the Volt-Ampere (VA). As I find the formulas that contain the variables that I have, I have been creating a calculator in the [Raspberry Pi Power Measurements Spreadsheet](https://docs.google.com/spreadsheets/d/17GJ9YTvDMcEH1WpFeCocZOULSqIYiJgjLDqLi2Exdtg/edit?usp=sharing) that will calculate the battery backup size as values change. Tomorrow, I need to make a current measurement for the battery backup calculation. 


I started writing a document that shows how I completed the calculations for the battery backup.

## Wednesday, July 15, 2020

This morning, I worked more on the presentation for Friday.

I started writing a Jupyter Notebook Python script that will read in a csv file as a data frame and send the data to InfluxDB. I used the Jupyter Notebook scripts on the Research Workspace that did this task as examples. While doing this, it took me a while to figure out how to install InfluxDB to the notebook kernel. When I first tried running `!conda install --yes --prefix {sys.prefix} influxdb`, the output had an error. To fix this, I ran `conda install -c conda-forge influxdb` in the command terminal. After running that command, the code to install InfluxDB to the notebook kernel worked. Because I do not have the csv file with the proxy dataset, I was not able to finish the script. However, I have a basic outline done that contains the things that will likely need to be done. Some of things included in the outline are loading the csv file as a data frame, making sure that the data being imported are numeric values and not strings, converting the timestamp to a datetime object, setting the timestamp as the index, and pushing the data to InfluxDB.

This afternoon, I stopped collecting power data for the Raspberry Pi with the 7 inch display. I updated the timestamp on the TIG-Playground on the dashboard for the 7 inch display, so that it would default to the time range that the data was collected during. After this, I connected the 13.3 inch display and I measured the current that was being used. 

I updated the [Raspberry Pi Power Measurements Spreadsheet](https://docs.google.com/spreadsheets/d/17GJ9YTvDMcEH1WpFeCocZOULSqIYiJgjLDqLi2Exdtg/edit?usp=sharing) with the data that was collected from the TIG-Playground for the 7 inch display. I also added the current measurement for the 13.3 inch display to the Battery Backup Calculation section. Using the current, I finished cross-referencing the cells in that section to calculate the different values. I found two different formulas for Amp-hours. They both produce different values. I am not certain what value should be used.  

I also updated the Battery Backup Calculations document that I started yesterday. This mainly involved changing the format of the equations, so that they were formated nicer. 

## Thursday, July 16, 2020

Today, I mainly focused on preparing for the presentation tomorrow. I also worked more on a course through DataCamp about Python and Pandas.
