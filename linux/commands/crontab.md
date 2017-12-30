# Cron jobs

```bash
$ crontab -l # See active cron jobs
$ crontab -e # Edit crontab file
```

###### Structure

```
* * * * *  command-to-execute
│ │ │ │ │
│ │ │ │ └─── day of week (0 - 6) (0 is Sunday, 7 is Sunday)
│ │ │ └──────── month (1 - 12)
│ │ └───────────── day of month (1 - 31)
│ └────────────────── hour (0 - 23)
└─────────────────────── min (0 - 59)
```

###### Examples

```bash
# Everyday day at 9:40pm
40 21 * * * ~/script.sh


# Everyday hour at --:05
5 * * * * ~/script.sh


# Everyday minute
* * * * * ~/script.sh


# Execute on workdays 1AM
0 1 * * 1-5 ~/script.sh


# Execute every 10 minutes
*/10 * * * * ~/script.sh
```