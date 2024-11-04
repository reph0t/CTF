# LEVEL 4 → 5 

>[!Important]
> Username: `bandit4`
>
> Password: `2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ`


### Level Goal

The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.

#### Commands you may need to solve this level

`ls , cd , cat , file , du , find`

## WALKTHROUGH

Similar to previous levels, the task here is to find the password hidden in a file located in the `inhere` directory. Let’s walk through the steps to locate the human-readable file.

### Step 1: Locate and Navigate to the inhere Directory

Start by checking whether the inhere directory exists in your current location. Use the `ls` command to list the contents of your current directory.

`ls`

If `inhere` is present, change into that directory:

`cd inhere`


![IMAGE](https://github.com/reph0t/CTF/blob/17d8a3f5675ed177f9d02d858c0e2e676c1619e0/OverTheWire/Bandit/src/Level_4-1.jpg)

### Step 2: List the Files in inhere

Once inside the inhere directory, list the contents to see what files are there:

`ls`

![IMAGE](https://github.com/reph0t/CTF/blob/17d8a3f5675ed177f9d02d858c0e2e676c1619e0/OverTheWire/Bandit/src/Level_4-2.jpg)

You’ll notice there are 10 files. According to the instructions, the password is stored in the only human-readable file in this directory.

### Step 3: Identify the Human-Readable File

To determine which file is human-readable, we could print the contents of each file manually using cat, but that’s inefficient. In real-world scenarios, directories might contain hundreds or even thousands of files. Instead, we can use a command that helps us identify the type of each file more efficiently.

Here’s where the `file` command comes in handy. It tells us the type of each file. By running:

`file ./*`

![IMAGE](https://github.com/reph0t/CTF/blob/17d8a3f5675ed177f9d02d858c0e2e676c1619e0/OverTheWire/Bandit/src/Level_4-3.jpg)

This will return the type of each file in the inhere directory. You’ll notice that most of the files are not human-readable (e.g., binary files), but one of them should be identified as a text file, which is the one we’re looking for.

### Step 4: Find the Password

In this case, the `file` command output shows that `-file07` is the only human-readable file (a text file). Now, we can print the contents of -file07 to reveal the password:

`cat ./-file07`

This will display the password for the next level.

![IMAGE](https://github.com/reph0t/CTF/blob/17d8a3f5675ed177f9d02d858c0e2e676c1619e0/OverTheWire/Bandit/src/Level_4-4.jpg)

> [!TIP]
> If you're unsure about how a command works, you can always refer to the manual pages by typing:
> `man <command>`
> This will give you detailed information about the command and the various options you can use with it.

By using the `file` command, we efficiently identified the human-readable file and retrieved the password without needing to manually check each file.
This method is far more convenient and scalable when dealing with large directories, which is often the case in real-world scenarios
