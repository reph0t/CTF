# LEVEL 18 → 19 

>[!Important]
> Username: `bandit18`
>
> Password: `x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO`

#### Level Goal
The password for the next level is stored in a file readme in the homedirectory. Unfortunately, someone has modified .bashrc to log you out when you log in with SSH.

Commands you may need to solve this level

`ssh, ls, cat`

### What is Non-Interactive SSH?

The main goal of this level is to teach you how to execute `non-interactive SSH` commands and retrieve information from a restricted environment. Here’s why these skills are useful:

`Non-Interactive SSH Session`: Normally, SSH is used to open an interactive session on a remote server. However, in cases where login is restricted, as in this level, SSH can still be used to run single commands remotely. This lets you retrieve information even without full login access.

`Bypassing Login Restrictions`: The `.bashrc` file on this level’s server is modified to immediately close connections, simulating environments where interactive access is restricted. By using SSH to run commands directly, you can work around these restrictions.

`Efficient Remote Command Execution`: Running a command remotely without an interactive session is a common technique for retrieving logs, checking statuses, and automating tasks on remote servers. This approach can save time and reduce the need for full access in automation or systems management.


### WALKTHROUGH

When trying to log in to bandit18, you may notice that the connection is immediately terminated upon login.

![IMAGE](https://github.com/reph0t/CTF/blob/83e8aa6c491f7edb2f8fb922851e6fa369c10c1a/OverTheWire/Bandit/src/Level_18-1.png)

This is due to a modification in the `.bashrc` file, which has been altered to prevent any interactive login to the server. You may wonder, "How can we retrieve the flag if we can't use `ssh` to log in normally?" The answer is that we can still use `ssh` to execute a single command remotely without opening an interactive shell.

We know that there is a `readme` file in the home directory of `bandit18` that contains the flag. By combining the `ssh` command with `cat` in a single line, we can bypass the need for an interactive session and directly retrieve the contents of `readme` without fully logging in.

Here’s the command:

`ssh -p 2220 bandit18@bandit.labs.overthewire.org cat readme`

![IMAGE](https://github.com/reph0t/CTF/blob/f8e79bf24c2ea2e1475633db8a8fc34bb7ef5117/OverTheWire/Bandit/src/Level_18-2.png)

This command connects to `bandit18` and immediately runs `cat readme`, printing the contents of the file (the flag) to our terminal before the connection is closed.

> [!Note]
> To make this process more efficient, you can set up environment variables for frequently used parameters, such as the server name and port, which saves time and reduces the need to retype
> commands.




