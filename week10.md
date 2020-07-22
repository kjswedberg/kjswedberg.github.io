# Week 10

## Monday, July 20, 2020

This morning, I worked on a Jupyter Notebook that inputs a NetCDF (.nc) file from the Remote Community Renewable Energy Research Workspace project. So far, the Jupyter Notebook can open and read the file as a dataset by using the open_dataset function in the xarray library. When the to_dataframe() function is used to convert this dataset to a dataframe, the error `ValueError: iterator is too large` occurs. Other people who have had this problem have at least one dimension that is unlimited. 

During the Afternoon, I worked on the slides for the Vodcast. I am planning on using the OpenShot software to make the Vodcast. Today, I installed the software and started working on making slides. 

## Tuesday, July 21, 2020

Today, I worked more on the Jupyter Notebook on the Remote Community Renewable Energy Research Workspace Project. Today, I tried using a different file. By using a different file, the error that I kept recieving yesterday did not occur. I was able to turn the dataset into a dataframe. Originally, the timestamp was a index variable, but it was not listed after calling dtype on the dataframe. So, I added a timestamp column that was equal to that index variable. When running the Jupyter Notebook, there are no errors. Grafana was able to find the information about the data, but it did not find any data. 

I also worked more on the slides for the Vodcast. 



