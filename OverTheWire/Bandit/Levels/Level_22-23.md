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

Similar to the previous level, we are tasked with examining cron jobs to retrieve the flag. Our first step is to look into the cron job configuration for `bandit23`.

1. **Inspect the Cron Job Configuration**

Start by checking the cron job file, `cronjob_bandit23`, to locate the associated script:

![IMAGE](https://github.com/reph0t/CTF/blob/a34bc163afc4c0603e12458a1af51c75acba0692/OverTheWire/Bandit/src/Level_22-1.png)

2. **Review the Script** in `/usr/bin/cronjob_bandit23.sh`

The cron job points to a script located in `/usr/bin/cronjob_bandit23.sh`. Let’s examine the script to understand what it does:

`cat /usr/bin/cronjob_bandit23.sh`

The contents of the script are as follows:

```
#!/bin/bash

myname=$(whoami)
mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)

echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"

cat /etc/bandit_pass/$myname > /tmp/$mytarget
```
**Explanation of the Script**
- `#!/bin/bash`: Specifies that this is a Bash script.
  
- `myname=$(whoami)`: Sets the myname variable to the current username. This allows the script to dynamically adapt to different users.

- `mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)`:
  - Generates a unique filename by creating an MD5 hash of the phrase `I am user $myname`.
  - `md5sum` generates the hash, and `cut` isolates the hash value.
  - This hash serves as a unique identifier for a temporary file in /tmp.
- `echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"`:
  - Prints a message indicating that the password file for the current user is being copied to /tmp with a unique filename.
- `cat /etc/bandit_pass/$myname > /tmp/$mytarget`:
  - Copies the content of /etc/bandit_pass/$myname (the password file) into /tmp/$mytarget, making it accessible.

**Understanding the Purpose of the Script**

The script automatically copies the password file of the current user (in this case, `bandit23`) to a temporary file in `/tmp` with a unique name based on an MD5 hash. By understanding this, we can deduce that the flag will be stored in this temporary file and can be retrieved if we know the file name.

**Step 3: Generate the Filename for the Password File**
To locate the exact file where the password is stored, we can simulate the steps in the script by manually setting the `myname` variable to `bandit23` and running the hash command.

1. Set the `myname` variable to `bandit23`:

`myname=bandit23`

2. Generate the MD5 hash to find the temporary filename:
   
`echo I am user $myname | md5sum | cut -d ' ' -f 1`

This command outputs the filename, which should look something like `8ca319486bfbbc3663ea0fbe81326349`.

![IMAGE](https://github.com/reph0t/CTF/blob/a34bc163afc4c0603e12458a1af51c75acba0692/OverTheWire/Bandit/src/Level_22-2.png)

Use the output to locate and read the file in `/tmp`:

`cat /tmp/8ca319486bfbbc3663ea0fbe81326349`

![IMAGE](https://github.com/reph0t/CTF/blob/a34bc163afc4c0603e12458a1af51c75acba0692/OverTheWire/Bandit/src/Level_22-3.png)

**Conclusion**
By understanding the cron job and script, we determined how to locate the password file created by the automated process. This file contains the flag needed to proceed to the next level. This level teaches you how to interpret and utilize scheduled scripts that dynamically generate file names based on user-specific variables.




