# **LEVEL 3 → 4**

>[!Important]
> Username: `bandit3`
>
> Password: `MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx`


### Level Goal

The password for the next level is stored in a hidden file in the inhere directory.

#### Commands you may need to solve this level

`ls , cd , cat , file , du , find`

## **WALKTHROUGH**

With the goal in mind, we know that the password is hidden in the inhere directory. To start, we need to locate and navigate to this directory using the `ls` and `cd` commands.

**Step 1: Listing the Contents of the Current Directory**

![IMAGE](https://github.com/reph0t/CTF/blob/f7d85e3cb51c4f97836d204101cd4d23e58945d2/OverTheWire/Bandit/src/Level_3-1.jpg)

We can see the inhere directory. Now, we will navigate into it using the `cd` command.

**Step 2: Changing to the inhere Directory**

To change into the `inhere` directory, we use:

![IMAGE](https://github.com/reph0t/CTF/blob/f7d85e3cb51c4f97836d204101cd4d23e58945d2/OverTheWire/Bandit/src/Level_3-2.jpg)

> [!TIP]
> You can confirm that you have successfully changed directories by using the `pwd` ("print working directory") command,
> which displays your current location.

![IMAGE](https://github.com/reph0t/CTF/blob/e1c83422d19519929057dfa5b93c81c4e328ead7/OverTheWire/Bandit/src/Level_3-5.jpg)

**Step 3: Locating Hidden Files**

Once inside the `inhere` directory, running `ls` will not show any files because the target file is hidden. To reveal hidden files, we need to use the `ls -a` command, which lists all files, including hidden ones.

![IMAGE](https://github.com/reph0t/CTF/blob/e1c83422d19519929057dfa5b93c81c4e328ead7/OverTheWire/Bandit/src/Level_3-3.jpg)

After running the command, you’ll see a file named `...Hiding-From-You`. This is the hidden file that contains the password.

![IMAGE](https://github.com/reph0t/CTF/blob/e1c83422d19519929057dfa5b93c81c4e328ead7/OverTheWire/Bandit/src/Level_3-4.jpg)

Congratulations! You’ve successfully found the password and completed this level. 👍



