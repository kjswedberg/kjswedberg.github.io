# Week 10

## Monday, July 20, 2020

This morning, I worked on a Jupyter Notebook that inputs a NetCDF (.nc) file from the Remote Community Renewable Energy Research Workspace project. So far, the Jupyter Notebook can open and read the file as a dataset by using the open_dataset function in the xarray library. When the to_dataframe() function is used to convert this dataset to a dataframe, the error `ValueError: iterator is too large` occurs. Other people who have had this problem have at least one dimension that is unlimited. 

During the Afternoon, I worked on the slides for the Vodcast. I am planning on using the OpenShot software to make the Vodcast. Today, I installed the software and started working on making slides. 

## Tuesday, July 21, 2020

Today, I worked more on the Jupyter Notebook on the Remote Community Renewable Energy Research Workspace Project. Today, I tried using a different file. By using a different file, the error that I kept recieving yesterday did not occur. I was able to turn the dataset into a dataframe. Originally, the timestamp was a index variable, but it was not listed after calling dtype on the dataframe. So, I added a timestamp column that was equal to that index variable. When running the Jupyter Notebook, there are no errors. Grafana was able to find the information about the data, but it did not find any data. 

I also worked more on the slides for the Vodcast. 


## Wednesday, July 22, 2020

Today, I focused on making a draft of the Vodcast. I also worked some on the final report.

I also pushed some data from the Remote Community Renewable Energy Research Workspace to the TIG-Playground. I removed the microsecond and nanosecond precision in the script, since Grafana does not use them by default. I think that the data was there on Tuesday. I think that Grafana had the timezone set to the time of my computer and that the data was UTC time.


## Thursday, July 23, 2020

Today, I edited the Vodcast.

I also tried using the Jupyter Notebook script with some other files on the RCRE RW. From what I can tell, the script works for the BusMeter.nc, Gen.nc, and Load2wo.nc files for the different tests. The majority of the other files cause the error saying that the iterator is too large. However, two from Test1.1 have the error  `maximum supported dimension for an ndarray is 32, found 37`. There are 37 time coordinates in the Load1elspec.nc file (time1 - time37). The data is associated with different, but only one, time coordinates. The differences between the times are on the microsecond range. One solution is to change the coordinates from time2 to time37 to time1. Then, the data would only be associated with time1 and time2 to time37 could be removed from the dataset. However, I have not found a way to do this. 

