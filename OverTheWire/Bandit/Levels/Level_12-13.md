# LEVEL 12 → 13

>[!Important]
> Username: `bandit12`
>
> Password: `7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4`

### Level Goal

The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work. Use mkdir with a hard to guess directory name. Or better, use the command “mktemp -d”. Then copy the datafile using cp, and rename it using mv (read the manpages!)

#### Commands you may need to solve this level

`grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd, mkdir, cp, mv, file`

## **What is Hex Dump?**

A **hex dump** is a textual representation of binary data, typically displayed as hexadecimal values. It’s used for debugging, reverse engineering, and digital forensics. A hex dump allows you to inspect data from files or memory that is otherwise not readable in its binary form. By reversing the hex dump (turning it back into binary), we can recover the original data.

## **WALKTHROUGH**

As outlined in the level goal, we need to create a directory in /tmp and work from there. Let’s break it down step by step:

### **Step 1: Create a Temporary Working Directory**

We first create a directory under `/tmp` where we’ll work with the file. You can do this with the mkdir command or use `mkdir -d` to create a temporary directory with a random name:

`mkdir ./usr0`

![IMAGE](https://github.com/reph0t/CTF/blob/b8efb1e3d34f8e3010c3454f1cd3b97454c468cf/OverTheWire/Bandit/src/Level_12-1.png)


> [!NOTE]
> It doesnt matter the name of your directory as long as you have a directory to work with in this level.

**Alternative approach:**

`mktemp -d`

> [!NOTE]
> This will create a directory with a randomly generated name for security purposes.


### **Step 2: Copy the File to Your Temporary Directory**

Next, we need to copy `data.txt` from the current working directory into the newly created temporary directory:

`cp data.txt /tmp/usr0/`

![IMAGE](https://github.com/reph0t/CTF/blob/b8efb1e3d34f8e3010c3454f1cd3b97454c468cf/OverTheWire/Bandit/src/Level_12-2.png)


![IMAGE](https://github.com/reph0t/CTF/blob/b8efb1e3d34f8e3010c3454f1cd3b97454c468cf/OverTheWire/Bandit/src/Level_12-3.png)


> [!NOTE]
> This command copies the file data.txt into the /tmp/usr0/ directory.

### **Step 3: Reverse the Hex Dump**

Now that we’ve copied the file, change into the directory and start by reversing the hex dump back into binary data:

`cat data.txt | xxd -r > data`

![IMAGE](https://github.com/reph0t/CTF/blob/b8efb1e3d34f8e3010c3454f1cd3b97454c468cf/OverTheWire/Bandit/src/Level_12-4.png)

**Command Breakdown:**

- `cat data.txt`: Prints the contents of data.txt
- `| (Pipe)`: Sends the output from cat as input to the next command.
- `xxd -r`: Reverts the hex dump back into its original binary form.
- `> data`: Saves the output to a new file called data.

### **Step 4: Inspect the File**

Use the file command to determine the file type of the newly created binary file:

`file data`

![IMAGE](https://github.com/reph0t/CTF/blob/b8efb1e3d34f8e3010c3454f1cd3b97454c468cf/OverTheWire/Bandit/src/Level_11-5.png)

> [!NOTE]
> This will likely reveal that the file is compressed, such as a **gzip** file.

### **Step 5: Decompress the File**

The `file` command will indicate which compression format was used (e.g., gzip, bzip2). First, rename the file to match its original format and then decompress it.

If the file is identified as gzip compressed, rename it and decompress:

`mv data data2.gz`

![IMAGE](https://github.com/reph0t/CTF/blob/d17a7d7e6cddbbb8073ebfa3fa50edf30914811a/OverTheWire/Bandit/src/Level_12-6.png)


`gzip -d data2.gz`

This will decompress the file into `data2`.

We then use the `file` command: 

`file data2`

![IMAGE](https://github.com/reph0t/CTF/blob/d17a7d7e6cddbbb8073ebfa3fa50edf30914811a/OverTheWire/Bandit/src/Level_12-7.png)

>[!NOTE]
>This will verify the format of the file. 

### **Step 6: Repeat the Process for Other Compressions**

At this point, you may notice that the file is still compressed in a different format (e.g., bzip2). Continue checking the file type using `file` and decompress accordingly. Rename the file each time to reflect its proper format:

`mv data2 data3.bz2
bzip2 -d data3.bz2`

Repeat this process of renaming, decompressing, and verifying with file until you reach the final uncompressed file.

![IMAGE](https://github.com/reph0t/CTF/blob/d17a7d7e6cddbbb8073ebfa3fa50edf30914811a/OverTheWire/Bandit/src/Level_12-8.png)

We continue to rename the file `data2` ▶️ `data3.bz` after it will decompress the file using the correct command format, and we do the same process to verify if the file is readable. There is a pattern to this level, so it is easy to figure out what to do next after this point.  

![IMAGE](https://github.com/reph0t/CTF/blob/d17a7d7e6cddbbb8073ebfa3fa50edf30914811a/OverTheWire/Bandit/src/Level_12-9.png)

### **Step 7: Retrieve the Flag**

Once all the compression layers have been removed and the file is in a readable format, you’ll be able to open the file and retrieve the password for the next level:

`cat data9`

![IMAGE](https://github.com/reph0t/CTF/blob/d17a7d7e6cddbbb8073ebfa3fa50edf30914811a/OverTheWire/Bandit/src/Level_12-10.png)

This will display the password, allowing you to proceed to the next level.

By following these steps, we successfully decoded and decompressed the file to find the password for Bandit13.

