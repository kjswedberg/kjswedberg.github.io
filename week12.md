# Week 12


## Monday, August 3, 2020

Today, I worked on two Jupyter Notebook scripts for the Eaton sample datasets. 

The first Jupyter Notebook script inputs the sample dataset from the Foreseer csv file as a DataFrame. It then makes sure that all values are numeric and that the timestamp column is a datetime object. The timestamp was then set as an index. 

The second Jupyter Notebook script that was worked on is more complex. This one is for the Visual T&D sample dataset. It also inputs the sample dataset from a csv file as a DataFrame. The columns of the DataFrame were Name, Value, Quality, Date, and Time. These column titles represented the name of the measurement, the measurement's value, the Quality of the measurement (OK or ERROR), the date of the measurement, and the time that the measurement was made. Since the name of the measurement is usually the columns name, this DataFrame was re-arranged. After inputing the csv file as a DataFrame, a list, ColNames, was made from the names of the measurements. Any duplicates in that list were droped. The Name, Date, Time, and Quality columns were set as index columns, so that the values would stay with the correct name, date, time, and quality as the DataFrame was re-arranged. A for loop was used to loop through ColNames. For each ColNames, the values that were associated with each Name in the list were added to a dictionary. That dictionary was then converted into a DataFrame. The Date and Time columns were combined to create a timestamp column. All the values, except for the Quality and Timestamp columns were converted into floats. The timestamp column was converted into a datetime, and the Quality column was converted into a object with the possible values of OK or ERROR. The Date and Time columns were removed from the DataFrame, and the Timestamp was set as the Index. The final DataFrame has the Quality columns and the values with the measurement names as the column names. 


The following documents were put into a folder and put in my ACEP Internship Student Folder.
- [X] Shelly 1PM Meter Documentation
- [X] Battery Back-Up Calculations Document
- [X] Telegraf Config Files
- [X] Eaton Project Statement of Work

I also worked more a DataCamp course.




## Tuesday, August 4, 2020

Today, I tried to convert the meter event files into a DataFrame. Each event has three files. For each event, there are .cfg, .dat, and .hdr files. This makes it seem to be a [COMTRADE](https://en.wikipedia.org/wiki/Comtrade#) file format. I was able to find a python module that worked to import the Comtrade files into the Jupyter Notebook script. The resource that I used to do this on the github site that is located [here](https://github.com/dparrini/python-comtrade). From this site, I figured out how to get the id's, which will be used as column names. The method that I used to create a dictionary is shown in Figure 1. However, the dictionary seems to be too large to print. After converting the dictionary to a DataFrame, I was able to print the head and tail of the DataFrame. When doing this, the DataFrame did not include a column with times. 

![image](https://user-images.githubusercontent.com/65566903/89350457-8b434b80-d65c-11ea-981b-80fcacb1ebf4.png) <br>
**Figure 1: The current method of creating the dictionary using a Jupyter Notebook script in the Research Workspace** <br>

In the .cfg files, there are two timestamps. Assuming that one is the start timestamp and the other was the end timestamp, I was able to create a timestamp list. This was found using the physics equation t<sub>end<sub> = V * X + t<sub>start<sub>. For creating the timestamp list, t<sub>start<sub> is the starting timestamp, X is the row number, V is the rate, and t<sub>end<sub> is the timestamp at row X. Only the second, millisecond, and nanosecond part of the timestamp was used in this equation. The rate was caluclated with the equation (t<sub>end<sub> - t<sub>start<sub>) / X. Currently, the list is made up of strings. 



## Wednesday, August 5, 2020

Today, I finished the timestamp list on the Jupyter Notebook script for the Meter Event files. I added the second, millisecond, and nanosecond timestamp list that was created yesturday and added the date, hour, and minute section to it. The equation that creates the timestamp list was changed, however the process that the list is created follows the same concepts. I then inserted the timestamp list into the DataFrame as a column and converted it from a string into a datetime object. It is important to remember that this timestamp column is based off of the assumptions that the timestamps in the .cfg file are the starting and ending timestamps and that the data is collected over a set interval. As a result, the timestamp column is currently only an assumption.


I sent the Foreseer and the Visual T&D DataFrames to the TIG-Playground to be visualized. I also updated the final report with the results from the visualization. Because the Meter Events timestamp column is based off of an assumption, that DataFrame has not been visualized.


I also worked on a DataCamp course.








## Thursday, August 6, 2020

- [ ] Proofread and submit final report and vodcast

## Friday, August 7, 2020

- [ ] Make sure that Final Report and Vodcast are submited
