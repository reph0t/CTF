# LEVEL 2 → 3
>[!Important]
> Username: `bandit2`
> Password: `263JGJPfgU6LtdEvgfWU1XP5yac29mFx`

### Level Goal

The password for the next level is stored in a file called spaces in this filename located in the home directory

#### **Commands you may need to solve this level**

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

![image](https://github.com/reph0t/CTF/blob/e0387123ca4bacd8ae5f4584b431dfd336429ba4/OverTheWire/Bandit/src/Level_2-1.jpg)



