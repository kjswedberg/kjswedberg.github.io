## September 7, 2020

Today, I worked more on the Event-to-influx code. Since the reason for the calculated ending timestamp being different than the trigger_timestamp is due to rounding error, I looked into different ways to round floats. I looked into ceil to see if there was a way to use it would work to round floats to 6 decimal places. I also looked at [this resource](https://www.tutorialspoint.com/How-do-you-round-up-a-float-number-in-Python), which suggests to add 0.5 to a float to always round the float up. As a result, I decided to try adding a constant to each timestamp and then rounding the timestamp to 6 decimal places.


Adding a constant to the timestamp did work to create a timestamp list, where the calculated ending timestamp was equal to the trigger_timestamp. The same constant works to achieve this for the Event0 and the Event1 files. After adding the constant to each timestamp, each timestamp was rounded to 6 decimal places and converted into a datetime timestamp format. If larger Event files are recieved, this constant may need to be adjusted. Figure 1 demonstrates the code that was used to create the timestamp.  

![image](https://user-images.githubusercontent.com/65566903/92414479-d5f33000-f100-11ea-88dc-5a3ba100fd06.png)
**Figure 1: The code used to create the timestamp column**

