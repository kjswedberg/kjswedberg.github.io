## October 5, 2020

Today, I worked on the meter event script that is on the Research Workspace. I created a copy of the script, so that I could experiement without messing up the script that currently works. I tried to simplify the way the timestamp column was generated. Currently, the method that works to generate the timestamp column does so by converting datetime objects to floats and then back to a datetime object. Today, I started working on finding a way to generate that column without having to convert the datetime objects into floats. However, by not converting the datetime objects into floats first, rounding error seems to be introduced into the timestamp column. 

I think that the way to solve this is to add a constant to the datetime object and then round the timestamp to the desired precision. This is what worked to generate the timestamp column that did not produce a large amount of rounding error and that involved converting datetime objects to floats. However, python did not allow for floats to be added to datetime objects. As a result, I researched ways to create a datetime object that can be added to another datetime object and for a way to round datetime objects.


## October 12, 2020

Today, I worked more on the Eielson-Eaton-DataCollection_Diagrams.


## October 19, 2020

Today, I worked on the Meter Event Jupyter Notebook script. I found a way to use linspace to simplifiy generating the timestamp column with minimal rounding error.

## October 26, 2020

I installed Python on my Windows 10 laptop by downloaded a exe file from python.org. The windows exe file installs an "IDLE" application to run python commands. When Python is installed using this method, it needs to be added to PATH. Otherwise, the command prompt cannot see that it has been install. The documentation that I wrote on how to install Python can be found [here](https://docs.google.com/document/d/12sHhiw5txSesbleHt-_Q4KMpa-jSpMhNcIE7BVjdjco/edit?usp=sharing). 
