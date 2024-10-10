# **LEVEL 3**

## Level Goal

The password for the next level is stored in a hidden file in the inhere directory.

Commands you may need to solve this level

`ls , cd , cat , file , du , find`

## **WALKTHROUGH**

With the information given we are hinted that there is a hidden file in a directory called, `inhere`. 
By finding the directory we will usee the `ls` command. 

![IMAGE](https://github.com/reph0t/CTF/blob/f7d85e3cb51c4f97836d204101cd4d23e58945d2/OverTheWire/Bandit/src/Level_3-1.jpg)

Now that we have located the directory, we will use the `cd` command to change directory to `inhere`.

![IMAGE](https://github.com/reph0t/CTF/blob/f7d85e3cb51c4f97836d204101cd4d23e58945d2/OverTheWire/Bandit/src/Level_3-2.jpg)

> [!TIP]
> You can confirm that you have succesfully changed the directory by using `pwd`("print working directory")
> this will print your current location.
> ![IMAGE](https://github.com/reph0t/CTF/blob/e1c83422d19519929057dfa5b93c81c4e328ead7/OverTheWire/Bandit/src/Level_3-5.jpg)

In the direcroty you will notice that at first glance there is no file. We must remember that the file is "invisible"
or at least hidden from the user. So we must a command that allows to list all the hidden files within our current directory. The command we will use is `ls` but with an option, `-a` this will list all the files including the hidden ones. 

![IMAGE](https://github.com/reph0t/CTF/blob/e1c83422d19519929057dfa5b93c81c4e328ead7/OverTheWire/Bandit/src/Level_3-3.jpg)

After running the command there is a file called, `...Hiding-From-You` that has been displayed before us. 
We now have the filename and next is simply concatenating the contents of the file using the `cat` 🐱 command followed by the filename.

![IMAGE](https://github.com/reph0t/CTF/blob/e1c83422d19519929057dfa5b93c81c4e328ead7/OverTheWire/Bandit/src/Level_3-4.jpg)

We have succedded in finding the flag to the next level! 👍



