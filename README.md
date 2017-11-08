# Call Bing Maps routing API to get travel times along segment of road

This .py file contains parameters and functions to call and run the Bing Maps API
to get the travel time and the traffic-estimated travel time from A-->B. The functions create
a url path to call the Bing Maps API using a key generated by the user at https://www.bingmapsportal.com/.

A-->B information entered in the following format, where [lat,lng] are floating point and
'TIP' is a descriptive string:
	```python
	corridors = [
		{	
		'TIP': 			'Route 1',		# The Name of the Corridor (A-->B) (string)
		'start_coord': 		[lat,lng],		# Coordinates of start point (A)
		'end_coord': 		[lat,lng]		# Coordinates of end point (B)
		}
	]
	```
	
Data is saved to a text file as a json object that has the following format:
	```python
	bing_result = [
		{
			'route': 					'Route 1', 			# The Name of the Corridor (A-->B) (string)
			'dow': 						'Wednesday', 		# Day of the week (string),
			'date':						'11/08/2017', 		# Date (mm/dd/yyyy) (string),
			'callTime': 				'17:35:16',			# Time (24-Hour Clock) (string)
			'travelDistance': 			0.9534,				# Travel Distance (miles) (float)
			'travelDuration': 			170,				# Travel Duration, no Traffic (seconds) (integer)
			'travelDurationTraffic': 	305, 				# Travel Duration with Traffic (seconds) (integer)
			'trafficCongestion': 		'Heavy'				# The Level of Traffic Congestion	(string)
		}
	]
	```
	
For more information on the Bing Maps API, see:
	https://www.bingmapsportal.com/Application
	https://msdn.microsoft.com/en-us/library/ff701717.aspx
	
This script uses the schedule library to query Bing Maps every n minutes. The documentation
for the schedule library can be found here:
	https://schedule.readthedocs.io/en/stable/
