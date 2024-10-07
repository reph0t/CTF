# **LEVEL 0**
## **Level Goal**

The goal of this level is for you to log into the game using SSH. The host to which you need to connect is bandit.labs.overthewire.org, on port 2220. 
The username is bandit0 and the password is bandit0. Once logged in, go to the Level 1 page to find out how to beat Level 1.

### **Commands you may need to solve**

- ssh

# **WALKTHROUGH**
So, before we get to level 1, we need to get to level 0. In the Level Goal section we need to log into the game using the Linux tool called, `ssh` or **Secure Shell Protocol**.
**SSH** is a network protocol used to connect to other hosts/servers 💻 --- 💻 in a unsecured network through a **secure connection**. 

> **What is SSH?**
> **SSH** connects and logs specified _destination_, which may be specified as either [user@]hostname or URI of the form ssh://[user@]hostname[:port] 
> The user must prove thier identity to the remote machine using one of the several methods. 

On the Level Goal we are already give the creadentials needed to connect to the server. Which are:

Username: **bandit0**
Password: **bandit0**
Host: **bandit.labs.overthewire.org**
Port: **2220**

Its all of a matter putting everything together as a command

we are going to user method, `-p` to enter the specific port we want to connect to the server. 

COMMAND: `ssh -p 2220 bandit0@bandit.labs.overthewire.org`

![image](https://github.com/user-attachments/assets/0bed7279-64b1-4fcb-9460-c75d48cc33ca)

Enter --> **Password: Bandit0**

![image](https://github.com/user-attachments/assets/558fd9bb-fb4d-40ea-a00a-7c0f93c149ad)

Once we enter the correct password, we will recieve a prompt about the rules on this level, and our user name and 
the host name will change. 

![image](https://github.com/user-attachments/assets/b629292e-b423-41eb-9be0-2c9a579fb70b)


![image](https://github.com/user-attachments/assets/1f376907-10d4-4331-802a-d5003034a1bd)


This is a confirmation that we have succeded and connecting the bandit host. 
