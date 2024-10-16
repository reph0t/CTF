# LEVEL 8

**Level Goal**

The password for the next level is stored in the file data.txt and is the only line of text that occurs only once

**Commands you may need to solve this level**

`grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd`

## **WALKTHROUGH**

In this level, we are introduced to new Linux commands that will help us locate the flag. Similar to previous levels, our goal is to find the password within the contents of data.txt, which is located in the current working directory. The key difference here is that the password is on the only line of text that appears once in the file.

To achieve this, we’ll use a technique called piping, where the output of one command is used as the input for the next. We will use the sort command to organize the data and then pass it to the uniq command to identify the unique line.

**Understanding Piping (|)**

The pipe symbol `|` is an operator that allows you to take the output from the command on the left and use it as input for the command on the right.
Example:


```ls -l | head -3```

In this example, the `ls -l` command lists all the contents of the current directory in a detailed format. The output is then passed through the pipe (|) to the head -3 command, which displays only the first 3 lines of the output:

```
foo1
foo2
foo3
```

This technique is useful when you want to chain commands together to process data more efficiently.
Applying Piping to Solve This Level

To find the password, we need to identify the line in data.txt that appears only once. We can achieve this using the following command:

`sort data.txt | uniq -u`

**Command Breakdown:**

- `sort data.txt`: This command sorts the lines in data.txt, arranging identical lines next to each other. This makes it easier for uniq to identify duplicates.
- `| (Pipe)`: The pipe takes the sorted output and feeds it as input to the next command.
- `uniq -u`: This command filters out all the lines that appear more than once, leaving only the unique lines.

**Result:**

![IMAGE](https://github.com/reph0t/CTF/blob/addc6da22ec9c8eba31e33adb84bfd5dce753cc1/OverTheWire/Bandit/src/Level_8-1.png)


By running the command, you will see the output of the line that occurs only once, which contains the password for the next level.

