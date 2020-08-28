## August 13, 2020

Today, I worked on the Jupyter Notebook script for the meter event file. The script now collects the starting timestamp and ending timestamp from the file and does not need to relay on those timestamps being inserted by the user manually. However, when the math is done to create the Timestamp column, the last calculated timestamp is different from the ending timestamp. I think that this is the result of rounding error, since the Rate variable is less precise as a datetime value than it was as a numeric value. 

## August 18, 2020

I worked more on the meter event Jupyter Notebook script today. I was able to minimize some of the rounding error, but not all of it. I did this by making the Rate variable a float value. This did involve converting some of the timestamps to floats temporarily

## August 20, 2020

I worked on the Grafana dashboard that contains both the Visual T&D data and Foreseer data. This was done to allow the data from the two meter to be compared easier.

## August 27, 2020

Today, I experemented with the meter event Jupyter Notebook script. I tried to decrease some of the rounding error, but was not able to decrease it further. Since a time precision parameter was added to the command that sends the data to the TIG-Playground, I set up a new dashboard and a new measurement to visualize the data. With the parameter, some of the datapoints still seem to be missing. As a result, the current and voltage data are not smooth sinusoidal signals on the Grafana dashboard.
