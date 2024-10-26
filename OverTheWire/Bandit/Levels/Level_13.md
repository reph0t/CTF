# LEVEL 13

### Level Goal
The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. Note: localhost is a hostname that refers to the machine you are working on

Commands you may need to solve this level
`ssh, telnet, nc, openssl, s_client, nmap`



### Walkthrough 

In this level the flag is located in another server, so in order to gain access to it, we must use a private ssh key using `ssh`. THe private key is located withing our current working directory. 


We will use this private file to gain access to the bandit14 server. We will use this command: 

ssh -i sshkey.private -p 2220 bandit14@localhost

**Command Breakdown**

- `ssh`: establish a secure connection on a remote machine
- `-i sshkey.private`: selects the private key file
- `-p 2220`: specifies port 2220
- `bandit14@localhost`: establishing the username to login into `localhost`


Now that we managed to login into the server it has been indicated that the file is located in `/etc/bandit_pass/bandit14`. By entering this command we managed to retirieve the flag for the next level. 

`cat /etc/bandit_pass/bandit14`


