# Garmin Connect - update script

I uploaded .gpx files from Runkeeper into Garmin Connect, only to find out that the activity type was not set. This scripts helps in setting the activity type.

## business logic

The script determines the activity type and name in the following way:
```python
    if activity.distance > 15 km: activity.type = 'cycling'
                                  activity.name = activity.location + ' Cycling" 
    elif activity.averageSpeed > 1.6667 m/s : activity.type = ' running' 
                                  activity.name = activity.location + ' Running" 
    elif activity.averageSpeed <= 1.6667 m/s : activity.type = 'hiking'
                                  activity.name = activity.location + ' Walking" 
```

You most likely need to tweek this to match your use case.

## running the script

Running the script:

```bash
$ python3 gc-export.py 
Welcome to the Garmin Connect Activity Type Tool (cycling version)!
  Currently this tool supports changing your activity type to either cycling, hiking or running

Username: john@doe.com
Password: 
Select Activities
  Up to 9999 activities can be processed at one time.
  Leave the start date blank to start at the beginning.
  Leave the end date blank to end at the latest activity.

  Start Date (e.g. "2018-09-30" or blank): 2020-05-01
  End Date (e.g. "2018-10-30" or blank): 2020-06-01

Logging in...
...
...
```

## authors

- Original author: Kyle Krafka (https://github.com/kjkjava/)
  Date: April 28, 2015
- Fork author: Michael P (https://github.com/moderation/)
  Date: February 15, 2018
- Fork author: Luc Gorissen (https://github.com/lgorissen/garmin-connect-update)
  Date: June 20, 2020