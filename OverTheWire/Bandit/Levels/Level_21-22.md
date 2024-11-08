# LEVEL 21 → 22

>[!Important]
> Username: `bandit21`
>
> Password: `EeoULMCra2q0dSkYj561DX7s1CpBuOBt`

#### Level Goal
A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

Commands you may need to solve this level

`cron, crontab, crontab(5) (use “man 5 crontab” to access this)`

#### WALKTHROUGH

A program is running automatically at regular intervals using cron, the time-based job scheduler in Linux. To find which command is being executed, we need to look in /etc/cron.d/ for the relevant configuration file.

**Understanding Cron Jobs**

Cron jobs are tasks scheduled to run automatically at specified intervals in Linux. There are multiple directories where cron jobs can be configured:

- `/etc/cron.d/`: General configuration files for specific cron jobs.
- `/etc/cron.daily/`, `/etc/cron.hourly/`, `/etc/cron.weekly/`, and `/etc/cron.monthly/`: Folders containing jobs set to run at daily, hourly, weekly, and monthly intervals, respectively.

Each cron job configuration file typically starts with five columns, indicating the scheduled time or interval for the task, followed by the command or program to execute.

**Step 1: Locate the Relevant Cron Job**

Following the task instructions, we navigate to the `/etc/cron.d/` directory to locate the configuration file. The file that stands out here is `cronjob_bandit22`, which appears to be related to our level.

**Step 2: Examine the Cron Job Script**

In the cron job configuration, we see that it points to a shell script at `/usr/bin/cronjob_bandit22.sh`. Viewing the contents of this script reveals its purpose:

`cat /usr/bin/cronjob_bandit22.sh`

The script shows that it creates a file in the `/tmp` directory with permissions that allow anyone to read it (indicated by the `chmod` command). Then, it copies the contents of the bandit22 password file into this temporary file, effectively exposing the password in a readable location.

By understanding how this cron job operates, we can retrieve the flag by reading the file it generates in `/tmp`. This level teaches us about the structure and purpose of cron jobs, as well as how automated tasks can be used to manipulate and access data in a Linux environment.
