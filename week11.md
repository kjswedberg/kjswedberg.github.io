# Week 11

## Monday, July 27, 2020

Today, I edited the final report.

I also worked more on the Jupyter Notebook script in the RCRE RW. I figured out how to take the variable that is associated with time1 and convert that into a Pandas DataFrame. I am going to try to do this for the rest of the time coordinates and then merge the 37 DataFrames into one DataFrame with a common Timestamp column as the index. Rob Cermak found a way to make a dictionary that contains the variables that are associated with each time coordinates. Rather than making the lists of variables manually, like I did with time1, I might try to do something similar. 

## Tuesday, July 28, 2020

Today, I worked more on the final report and the Jupyter Notebook script. I was able to get the Jupyter Notebook script to convert the dataset to a Pandas Dataframe. However, the DataFrame contains 1,268,365 rows. As a result, the script is not able to send the DataFrame to the TIG-Playground currently. The DataFrame may need to be broken up by using a for loop, or the editing that is done to the DataFrame may need to be completed inside the for loop that converts the dataset to a DataFrame. By doing the later option, the user will not be able to see the data to confirm that the editing did what was expected before the data is sent to the TIG-Playground.


