# LEVEL 22 → 23

>[!Important]
> Username: `bandit22`
>
> Password: `tRae0UfB9v0UzbCdn9cY0gQnds9GF58Q`


### Level Goal
A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

NOTE: Looking at shell scripts written by other people is a very useful skill. The script for this level is intentionally made easy to read. If you are having problems understanding what it does, try executing it to see the debug information it prints.

Commands you may need to solve this level

`cron, crontab, crontab(5) (use “man 5 crontab” to access this)`


#### WALKTHROUGH

A program is automatically running at regular intervals using cron, the time-based job scheduler in Linux. To find out what command is being executed, we need to examine the configuration files in /etc/cron.d/.

> ![Note]
> Reading and understanding shell scripts written by others is a valuable skill. The script for this level is intentionally written in a simple, readable way. If you’re unsure about its functionality, try executing the script to see any debug information it outputs.
