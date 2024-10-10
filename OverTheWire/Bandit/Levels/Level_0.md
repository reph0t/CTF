# **LEVEL 0**

## Part 1 - Logging In

### **Level Goal**
The goal of this level is for you to log into the game using SSH. The host to which you need to connect is bandit.labs.overthewire.org, on port 2220. 

The username is bandit0 and the password is bandit0. Once logged in, go to the Level 1 page to find out how to beat Level 1.

**Commands you may need to solve**

- `ssh`

Before we can move on to Level 1, we need to access Level 0. The Level Goal instructs us to log into the game using a Linux tool called `ssh` (Secure Shell Protocol).

### **What is SSH?**
**SSH** is a network protocol used to connect to other hosts/servers 💻 --- 💻 in a unsecured network through a **secure connection**. 

**SSH** connects and logs specified _destination_, which may be specified as either [user@]hostname or URI of the form ssh://[user@]hostname[:port] 

The user must prove thier identity to the remote machine using one of the several methods. 

## **WALKTHROUGH**

On the Level Goal we are already give the creadentials needed to connect to the server. Which are:

- Username: **bandit0**
- Password: **bandit0**
- Host: **bandit.labs.overthewire.org**
- Port: **2220**

Its all of a matter putting everything together as a command.

We are going to use method, `-p` to enter the specific port we want to connect to the server. 

COMMAND:
```ssh -p 2220 bandit0@bandit.labs.overthewire.org```

- `ssh`: This initiate the secure connection
- `-p 2220`: This specifies port 2220, which is the port used by the Bandit game server
- `bandit0@bandit.labs.overthewire.org`: This is the username(`bandit0`) and the
  host (`badnti.labs.overthewire.org`) to which we want to connect

When prompted, enter the password `bandit0` as shown below:

![image](https://github.com/reph0t/CTF/blob/6049c08bd25a6f44a2455e165f65faa257d1a08c/OverTheWire/Bandit/src/Level_0-1.jpg)


After entering the correct password, you will be logged into the Bandit server, where you'll 
see a welcome message and some rules regarding this level:

![image](https://github.com/reph0t/CTF/blob/136b3497db3ad60540a702e1830a6d45f44e853d/OverTheWire/Bandit/src/Level_0-2.jpg)


> [!TIP] **Login Confrimation**
> To confirm that we have logged in succesfully we can use commands `whoami` and `hostname`
> to verify our current username and hostname we are connected to:
>USERNAME
> ![image](https://github.com/reph0t/CTF/blob/5b0e2d3225de18184af8ac43a293683d71028daa/OverTheWire/Bandit/src/Level_0-3.jpg)
>HOSTNAME
> ![image](https://github.com/reph0t/CTF/blob/5b0e2d3225de18184af8ac43a293683d71028daa/OverTheWire/Bandit/src/Level_0-4.jpg)


This is a confirmation that we have succeded and connecting the bandit host. 

## Part 2 - Cat - (Level 0 --> Level 1)

Now that we have successfully logged in to Bandit0, we need to progress to the next level.

### **Level Goal**
The password for the next level is stored in a file called readme located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.

**Commands you may need to solve this level**

`ls , cd , cat , file , du , find`

## **Understanding the File System**

Before we proceed, it’s helpful to understand the file system we’re navigating. If you've used your system’s terminal before, you’ll recognize that the server has a file hierarchy system (which can vary slightly based on the operating system).

When you run a command like ls (which lists files and directories), you’ll see important files and directories that are part of the system's structure. These files allow the system to run various applications and boot correctly.

> [!CAUTION]
> For beginner users, it’s important **NOT** to modify or delete these native files unless you fully understand what you’re doing, as they can be crucial for system operation. Every technology relies on a file system as a reference to execute commands and manage operations.


## **WALKTHROUGH**

Now that we’ve briefly covered the file system, let's focus on the task at hand. According to the Level Goal, there is a file called readme in the home directory that contains the password for the next level.

You’re given several commands to help find and retrieve this password:

- `ls` - Lists all the contents in the current directory.
- `cd` - Changes directories, allowing you to navigate through the file system.
- `cat` - Concatenates and prints the content of a file to the terminal.
- `file` -  Determines the type of a file (e.g., text, binary, etc.).
- `du` - Displays disk usage information for files and directories.
- `find` - Searches for files in a directory hierarchy.

With these commands available, let’s choose the best ones to help us retrieve the password.

### **Step 1: List the Directory Contents**

Use the `ls` command to see what’s inside the current directory (your home directory).

This will list all the files and directories in your current location.

![image](https://github.com/reph0t/CTF/blob/136b3497db3ad60540a702e1830a6d45f44e853d/OverTheWire/Bandit/src/Level_0-5.jpg)

As you can see, there is indeed a file named `readme`.

### **Step 2: Display the File Contents**

Now that we've confirmed the `readme` file is present, we can use the `cat` command to display its contents and reveal the password.

```cat readme```

This will output the content of the file, including the password for the next level.

![image](https://github.com/reph0t/CTF/blob/136b3497db3ad60540a702e1830a6d45f44e853d/OverTheWire/Bandit/src/Level_0-6.jpg)

Congratulations! You now have the password for **Bandit1**.

> [!NOTE] 
> The passwords you find for each level will not be saved automatically. It’s strongly recommended that you
>  save them in a document for future reference. If you lose track of a password, you’ll have to start over from
> Bandit0, so make sure to document your progress!


