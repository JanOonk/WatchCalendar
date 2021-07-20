# WatchCalendar
A multi-platform program which watches an iCal calendar for changes (added, changed and deleted appointments) and send push notifications using Pushover API. This can be handy when you share a calendar with a friend and you want to be instantly notified when something changes.

## Requirements
It requires an Pushover (paid) account (only $5 per platform one-time, see https://pushover.net/pricing).

## Installation

Step 0. Pick a release for your platform or build the (Visual Studio 2019 .NET Core 5) source from scratch. Unpack into a new directory.

Step 1. Review the `settings.ini` and at least update the `[Pushover]` and `[Calendar]` sections:

### \[Pushover\] section
* Login on Pushover https://pushover.net/ or create account.
* After logging in you will find `userkey`, add this to the `userkey=` line.
* Create a new application (only name is mandatory). After creating you will see the `application key`, add this to the `apikey` line.
* Add a device where you want to receive Calendar change notifications on. Add the device name(s) comma separated on `devices=` line.

### \[Calendar\] section
* On `url=` line add an (preferable private) url which points to a .ics file. For example for Google Calendar it looks something like https://calendar.google.com/calendar/ical/[...]/basic.ics


Step 2. (Optional) Review the other settings  
Step 3. Make a cronjob or use task scheduler to periodically call the program.  
Step 4. You can optionally run it by hand:  
Linux: `./WatchCalendar`  
Windows: `WatchCalendar.exe`

## Current limitations
* doesn't see instance deletion(s) in a repeating event  
When an instance from a repeating event (RRULE is set) is deleted an EXDATE is created  
 `RRULE:FREQ=DAILY
 EXDATE;TZID=Europe/Amsterdam:20190419T161500`

