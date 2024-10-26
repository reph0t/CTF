# LEVEL 13

### Level Goal
The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. Note: localhost is a hostname that refers to the machine you are working on

Commands you may need to solve this level
`ssh, telnet, nc, openssl, s_client, nmap`



### Walkthrough 

In this level, the flag is located on a different server, and we’ll need to use a private SSH key to gain access. The private key file is located in the current working directory.

![IMAGE](https://github.com/reph0t/CTF/blob/e7035ff0959861323d0f2cb5a978f3f91092daa3/OverTheWire/Bandit/src/Level_13-2.png)


We’ll use this private key to log in to the bandit14 server with the following command:

`ssh -i sshkey.private -p 2220 bandit14@localhost`

![IMAGE](https://github.com/reph0t/CTF/blob/e7035ff0959861323d0f2cb5a978f3f91092daa3/OverTheWire/Bandit/src/Level_13-3.png)

**Command Breakdown:**

- `ssh`: Initiates a secure connection to a remote server.
- `-i sshkey.private`: Specifies the private key file to use for authentication.
- `-p 2220`: Connects through port 2220, as specified for this level.
- `bandit14@localhost`: Logs in as the `bandit14` user on the `localhost` server.


Once logged in, we can locate the flag in the file `/etc/bandit_pass/bandit14`, as directed. Use the following command to display the contents of the file:

`cat /etc/bandit_pass/bandit14`

![IMAGE](https://github.com/reph0t/CTF/blob/e7035ff0959861323d0f2cb5a978f3f91092daa3/OverTheWire/Bandit/src/Level_13-1.png)

This will reveal the password for the next level, allowing you to proceed.
