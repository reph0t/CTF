# LEVEL 18 → 19 

>[!Important]
> Username: `bandit18`
>
> Password: `x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO`

#### Level Goal
The password for the next level is stored in a file readme in the homedirectory. Unfortunately, someone has modified .bashrc to log you out when you log in with SSH.

Commands you may need to solve this level

`ssh, ls, cat`

### WALKTHROUGH

When trying to log in to bandit18, you may notice that the connection is immediately terminated upon login.

![IMAGE](https://github.com/reph0t/CTF/blob/83e8aa6c491f7edb2f8fb922851e6fa369c10c1a/OverTheWire/Bandit/src/Level_18-1.png)

This is due to a modification in the `.bashrc` file, which has been altered to prevent any interactive login to the server. You may wonder, "How can we retrieve the flag if we can't use `ssh` to log in normally?" The answer is that we can still use `ssh` to execute a single command remotely without opening an interactive shell.

We know that there is a `readme` file in the home directory of `bandit18` that contains the flag. By combining the `ssh` command with `cat` in a single line, we can bypass the need for an interactive session and directly retrieve the contents of `readme` without fully logging in.

Here’s the command:

`ssh -p 2220 bandit18@bandit.labs.overthewire.org cat readme`

![IMAGE]()


This command connects to `bandit18` and immediately runs `cat readme`, printing the contents of the file (the flag) to our terminal before the connection is closed.

> [!Note]
> To make this process more efficient, you can set up environment variables for frequently used parameters, such as the server name and port, which saves time and reduces the need to retype
> commands.




