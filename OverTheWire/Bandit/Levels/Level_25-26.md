# Level 25 → Level 26

>[!Important]
> Username: `bandit25`
>
> Password: `iCi86ttT4KSNe1armKiwbQNmB3YJP3q4`

#### Level Goal

Logging in to bandit26 from bandit25 should be fairly easy… The shell for user bandit26 is not /bin/bash, but something else. Find out what it is, how it works and how to break out of it.

NOTE: if you’re a Windows user and typically use Powershell to ssh into bandit: Powershell is known to cause issues with the intended solution to this level. You should use command prompt instead.

Commands you may need to solve this level

`ssh, cat, more, vi, ls, id, pwd`

#### WALKTHROUGH

After we login into `bandit25` we need notice there is a private key in our current directory. It seems like we can easily log into `bandit26` with no issues. But if we were to attempt to login it would automcaitlly discconect the connection to the server. It it hinted that we must figure out how the shell for bandit26 is operating so we can break out of it and find the flag. 

In order to find the shell we must go to the `passwd` file and pinpoint what kind of shell is `bandit26` is using. So we use this command:

`cat /etc/passwd | grep "bandit26"`

![IMAGE]()

The result has shown that bandit26 is using a shell called `showtext` located in `/usr/bin/` directory. With this information we can print out the shell and find out how it works. 

`cat /usr/bin/showtext`

```
#!/bin/sh

export TERM=linux

exec more ~/text.txt
exit 0
```
**What is More?**
`More` is basically a buffer which  allows to display large texts files in the terminal. 

**Code Breakdown:**
- `#!/bin/sh`: uses a shell script
- `export TERM=linux`: establishes a Linux Terminal
- `exec more ~/text.txt`: executes the command `more` on the `text.txt` file
- `exit 0`: when the `more` command is finished executing terminal will exit

By understanding what this shell does, we need to find a way to prevent the shell from exiting. If the `more` command fininshes executing then the shell will quit. So the shell must reamin in the `more` command so we can find the flag. We can also set up an editor such as `v`/`vi` to run commands. Knowing this we can try it out. First we will need to shrink the terminal into a smaller window(it doesnt matter how small as long as we can get the shell to run the `more` command).

![IMAGE]()

After running the ssh command the shell is now running the `more` command. It will continue to run until we reach the end of the `text.txt` file, however this will allow us to run `vi` editor within the shell so we can run commands. 

![IMAGE]()

We can maximize the terminal window now to make it easier for us to work on finding the flag. By entering `vi` we are now in editor mode: 


![IMAGE]()

