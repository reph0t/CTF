# LEVEL 2

## Level Goal

The password for the next level is stored in a file called spaces in this filename located in the home directory

>[!NOTE]
> You will use the same command to login in to different bandit levels. 


**Commands you may need to solve this level**

`ls , cd , cat , file , du , find`

## WALKTHROUGH

In this level, the file name contains spaces: `spaces in this filename`. When working with files that have spaces in their names, you need to handle them carefully.

One of the easiest ways to handle spaces in filenames is by wrapping the filename in double quotes (`""`). This tells the shell to treat the entire string (including spaces) as a single entity.

**Solution**

`cat "spaces in this filename"`

**Why this works:**
- Double quotes are used in Bash to treat a group of characters (including spaces) as a single string.
- By wrapping the filename in double quotes, you're telling the cat command to treat spaces in this filename as one file,
  rather than interpreting each word separately.

Executing this command will output the contents of the file, which contains the password for the next level.

![image](https://github.com/user-attachments/assets/f8a94179-a0ad-4a29-94f5-7cdf626ad175)



