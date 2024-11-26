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

After logging into `bandit25`, we notice a private SSH key in the current directory, suggesting we can log into `bandit26`. However, attempting to log in immediately disconnects the session. The challenge hints that we need to understand and exploit the shell used by `bandit26` to prevent disconnection and retrieve the flag.

##### Step 1: Investigate the Shell for Bandit26
To determine the shell used by bandit26, we inspect the /etc/passwd file, which contains user account information, including their assigned shell. We use the following command:

`cat /etc/passwd | grep "bandit26"`

![IMAGE](https://github.com/reph0t/CTF/blob/1743b5a82497a50f1b1de0a1dc97d7a968a4beca/OverTheWire/Bandit/src/Level_25-1.png)

The output reveals that `bandit26` uses a custom shell located at `/usr/bin/showtext`.

##### Step 2: Analyze the showtext Shell
Next, we examine the contents of the `showtext` shell script to understand its behavior:

`cat /usr/bin/showtext`

```
#!/bin/sh

export TERM=linux

exec more ~/text.txt
exit 0
```
**What is more?**
The `more` command is a text pager that displays large text files one screen at a time.

Script Breakdown:

**Script Breakdown:**
- `#!/bin/sh`: Specifies the script is a shell script.
- `export TERM=linux`: Sets the terminal type to Linux.
- `exec more ~/text.txt`: Executes the more command to display the text.txt file.
- `exit 0`: Exits the shell once the more command finishes.

The key insight is that the shell exits as soon as the `more` command completes. To prevent this, we must remain within the `more` command and use it to escape into an interactive shell.

##### Step 3: Exploit the showtext Shell

Shrink the Terminal Window
First, resize the terminal window to a smaller size. This causes more to pause as it tries to display the contents of text.txt.

Log Into Bandit26
Using the provided SSH key, log into bandit26:

`ssh -p 2220 -i bandit26.sshkey bandit26@localhost`

![IMAGE](https://github.com/reph0t/CTF/blob/d9f5a69130b6abd63bb90dbb6e6e08ffc51eca6e/OverTheWire/Bandit/src/Level_25-2.png)

Once logged in, the `showtext` shell starts and runs the `more` command to display `text.txt`. Because the terminal is small, `more` pauses, giving us an opportunity to interact.

![IMAGE](https://github.com/reph0t/CTF/blob/d9f5a69130b6abd63bb90dbb6e6e08ffc51eca6e/OverTheWire/Bandit/src/Level_25-3.png)

It is safe to maximize the terminal window now to make it easier for us to work on finding the flag. By entering `vi` we are now in editor mode: 


![IMAGE](https://github.com/reph0t/CTF/blob/d9f5a69130b6abd63bb90dbb6e6e08ffc51eca6e/OverTheWire/Bandit/src/Level_25-4.png)

##### Step 4: Escape Using vi Editor
While more is running, we can launch the vi editor to execute commands:

1. Type vi to open the editor.
2. Once inside vi, check the current shell using the command:

`: set shell?`

![IMAGE](https://github.com/reph0t/CTF/blob/d9f5a69130b6abd63bb90dbb6e6e08ffc51eca6e/OverTheWire/Bandit/src/Level_25-5.png)

The output confirms we are still in the `showtext` shell.

3. Change the shell to `/bin/bash` with:

`:set shell=/bin/bash`

4. Escape into the new shell by entering:
`:shell`

![IMAGE](https://github.com/reph0t/CTF/blob/d9f5a69130b6abd63bb90dbb6e6e08ffc51eca6e/OverTheWire/Bandit/src/Level_25-6.png)


Step 5: Retrieve the Flag
Now that we are in a bash shell, we can access the flag for `bandit26`:

`cat /etc/bandit_pass/bandit26`

![IMAGE](https://github.com/reph0t/CTF/blob/d9f5a69130b6abd63bb90dbb6e6e08ffc51eca6e/OverTheWire/Bandit/src/Level_25-7.png)
