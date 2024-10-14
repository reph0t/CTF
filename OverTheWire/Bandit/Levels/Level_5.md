# LEVEL 5

# Level Goal

The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:

  - human-readable
  - 1033 bytes in size
  - not executable

Commands you may need to solve this level

`ls , cd , cat , file , du , find`


## WALKTHROUGH

After logging into the Bandit5 server we are tasked to find a file somwhere in `inhere` directory. By going into the directory we notcied there are many directories that may have the flag. 

![IMAGE](https://github.com/reph0t/CTF/blob/cd4802b5dc3c4f35f8524c5b1019218bb14c8ebd/OverTheWire/Bandit/src/Level_5-2.jpg)

To be more effiecint in finding the flag I am going to use `find` to search each directory. Specifically a file that is: human-readable, and has size of 1033 byes, adn is not executable. With these specifications I created this command:

`find ./* -readable -size 1033c \! -executable`

**Breakdown:**
 - `find` - using the find command
 - `./*` - present directory
 - `-size 1033` - specifies the size of the file which is 1033 bytes
 - `\!` - NOT boolean expression
 - `-executable` - file is executable

> [!NOTE]
> For more information read the man pages.

By entering the command we are able to locate the file.

![IMAGE](https://github.com/reph0t/CTF/blob/49754b3c0f25ac95bc92d56865f494c72f3723bf/OverTheWire/Bandit/src/Level_5-5.jpg)

