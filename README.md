Sleep Tracker

A hand-collected dataset of my sleep and how my day goes. Every morning I read last night's sleep off my Fitbit app and type it into the CSV myself, then finish the rest of the row later the same day. Recording started on 31 October 2026.

Question:
How does sleep and work affect my mood, and how do my behaviours affect my sleep?

Data

The data is in data/my_data.csv. Each row is one day: last night's sleep plus what happens on the day I wake up. Every row is recorded on that same day, never later.

Data dictionary
Column	Type	Units / format	How I measure it
date	date	YYYY-MM-DD	The day I woke up and recorded the row. Last night's sleep is recorded under this date
bedtime	time	HH:MM (24h)	Time my Fitbit app shows I fell asleep, read from the app in the morning
wake_time	time	HH:MM (24h)	Time my Fitbit app shows I woke up, read from the app in the morning
hours_slept	decimal	hours, 1 d.p.	Total time asleep shown in the Fitbit app (excluding time awake), converted to decimal hours (e.g. 7 h 30 min = 7.5, 3 h 23 min = 3.4)
mood	integer	1-5	My own rating at midday: 1 = very low, 2 = low, 3 = okay, 4 = good, 5 = great
worked	categorical	y / n	Whether I work a shift on the date of the row
caffeine_after_noon	categorical	y / n	Whether I have any caffeine after 12:00 on the date of the row

Collection rules

These are fixed from day one and do not change:

One row per day, recorded on the day I wake up. I fill in the sleep values in the morning, mood at midday, and worked and caffeine_after_noon once the day's events are known (in the evening at the latest).
I read the sleep values off the Fitbit app by hand and type them in. I never export, download or use the Fitbit API to get data.
No backfilling. If I forget a day, that row is left out rather than filled in later.
Times use 24-hour format with leading zeros (02:37, 07:15). Dates use ISO format (2026-10-31).
hours_slept is always written to 1 decimal place.
Mood is always rated at midday, using the same 1-5 scale.
No spaces after commas in the CSV.
If I fall asleep after midnight, bedtime is still the time I fell asleep (e.g. 02:37), and date is still the day I woke up.

Example row:
date,bedtime,wake_time,hours_slept,mood,worked,caffeine_after_noon
2026-11-01,23:40,07:20,7.0,4,y,n

How I collected the data

Each morning I open the Fitbit app, read the sleep start time, wake time and time asleep, and write them in my CSV straight away. At midday I rate my mood. In the evening I add whether I worked and whether I had caffeine after noon, then commit and push the finished row the same day.
