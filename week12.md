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

- [ ] Work on creating Pandas DataFrames from the Eaton sample dataset files 

## Wednesday, August 5, 2020

- [ ] Visualize DataFrames from the Eaton sample dataset files

- [ ] Update sections on final repot about jupyter notebook scripts?
	- [ ] Methodology: Check last paragraph
	- [ ] Results 
	- [ ] Conclusion: Last few lines


## Thursday, August 6, 2020

- [ ] Proofread and submit final report and vodcast

## Friday, August 7, 2020

- [ ] Make sure that Final Report and Vodcast are submited
