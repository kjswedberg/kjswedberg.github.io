# Week 11

## Monday, July 27, 2020

Today, I edited the final report.

I also worked more on the Jupyter Notebook script in the RCRE RW. I figured out how to take the variable that is associated with time1 and convert that into a Pandas DataFrame. I am going to try to do this for the rest of the time coordinates and then merge the 37 DataFrames into one DataFrame with a common Timestamp column as the index. Rob Cermak found a way to make a dictionary that contains the variables that are associated with each time coordinates. Rather than making the lists of variables manually, like I did with time1, I might try to do something similar. 

## Tuesday, July 28, 2020

Today, I worked more on the final report and the Jupyter Notebook script. I was able to get the Jupyter Notebook script to convert the dataset to a Pandas Dataframe. However, the DataFrame contains 1,268,365 rows. As a result, the script is not able to send the DataFrame to the TIG-Playground currently. The DataFrame may need to be broken up by using a for loop, or the editing that is done to the DataFrame may need to be completed inside the for loop that converts the dataset to a DataFrame. By doing the later option, the user will not be able to see the data to confirm that the editing did what was expected before the data is sent to the TIG-Playground.


## Wednesday, July 29, 2020

This morning, I set up Visual Studio with Python on my computer and looked into setting it up with C++. This was so that I could start becoming familar with the program. I also looked some at the GitHub guides that were posted to the Discord hacking-chat.

I also finished the Jupyter Notebook script today. Because of the large DataFrames that sometimes occur with the script, the user has to specify which rows to send. This way, the data can be sent in smaller groups. After finishing the script, I sent the Test 1.1 Load1elspec data to the TIG-Playground. I set up the script to send about 100,000 rows of data at a time to the TIG-Playground. 

After finishing the Jupyter Notebook script, I edited and proofread the final report.

## Thursday, July 30, 2020

This morning, I worked on the Grafana Dashboards for the BusMeter and Load1elspec data on the TIG-Playground. I organized the panels by variable name. So, all the variables starting with Ia are together and all the variables starting with Va are together.

I tested the Jupyter Notebook script with other datasets on the RCRE RW from Test 1.1. The script works to convert all the datasets from Test 1.1 into a DataFrame and then edit the DataFrame into a form that can be send to the TIG-Playground. As with the Load1elspec data, the script will require that the user specifies a range of rows to send. The DataFrame may need to be send in several smaller groups, since it may be too large to send all the data at once. From my current knowledge, the datasets from the other tests are a similar format. As a result, this script will most likely work with the datasets from the other tests. When testing the script with the datasets from Test 1.1, the two lines that send the data to the TIG-Playground were not run.

When reviewing the Jupyter Notebook script, I found a mistake in it. The mistake caused only the variables that were associated with the last time coordinate to be sent to the TIG-Playground. So I fixed that today and resent the Load1elspec data to the TIG-Playground.

During the afternoon, I finished the DataCamp course on merging DataFrames that I started a while ago.

## Friday, July 31, 2020

Today, I gathered the documentation files and other documents that I have written for this internship into one folder on Google Drive. 

I looked at the Jupyter Notebook script on the RCRE RW that Matt Perry has been working on. 

I also proofread the final report. I added a section to the final report that contained images of some of the visualized data from Grafana.

I also worked some on a DataCamp course.
