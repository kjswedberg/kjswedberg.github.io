## August 13, 2020

Today, I worked on the Jupyter Notebook script for the meter event file. The script now collects the starting timestamp and ending timestamp from the file and does not need to relay on those timestamps being inserted by the user manually. However, when the math is done to create the Timestamp column, the last calculated timestamp is different from the ending timestamp. I think that this is the result of rounding error, since the Rate variable is less precise as a datetime value than it was as a numeric value. 

