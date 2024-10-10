# LEVEL 1

# Logging into Bandit1

Similar to logging into bandit0 with the credentials provided, we will login into bandit1 as the username and with the password we have retrieved from the previous level. 

- username: **bandit1**
- host: **bandit.labs.overthewire.org**
- port: 2220
  
  ![image](https://github.com/reph0t/CTF/blob/d3e3adf343bb9ad2c64c9fd5cbc03692b14352a4/OverTheWire/Bandit/src/Level_1-1.jpg)


>[!NOTE]
> You will use the same command to login in to different bandit levels; the only difference is to change the username that corresponds to the current level.
> (e.g., Level 1: bandit1, Level 2, bandit2, etc.)

## **Level Goal**
The password for the next level is stored in a file called `-` located in the home directory

**Commands you may need to solve this level**

`ls , cd , cat , file , du , find`

### **Dashed Files (`-`)**
In this level, when you list the files in the current directory, you'll notice a file named `-`. The challenge here is that you can’t directly use the `cat` command as usual because `cat` doesn’t know whether you're referring to a file or expecting input from the user (known as stdin).

The `-` symbol is commonly used in many UNIX commands to signify **standard input (stdin)**. This means that when you run `cat -`, the system interprets `-` as "read from stdin" and waits for you to type input rather than treating `-` as a filename.

Therefore, a different approach is needed to explicitly tell `cat` to interpret the dash (`-`) as the name of a file, not stdin. This is why simply running `cat -` will not work.

## **WALKTHROUGH**

**STEP 1**

To view the contents of the `-` file, run the following command:

 ```cat ./-```

Here’s why this works:

- The `./` refers to the current directory. By prepending `./` to the dash (`-`), you are telling `cat` that `-` is the name of a file in the current directory, not a special option for standard input.

Executing this command will reveal the password for the next level.

![image](https://github.com/reph0t/CTF/blob/d3e3adf343bb9ad2c64c9fd5cbc03692b14352a4/OverTheWire/Bandit/src/Level_1-2.jpg)

**Another Approach**

There is also another way to handle dashed files. You can use **input redirection**:

```cat < -```

This method uses the `<` symbol, which is called **input redirection** in Bash. The `<` symbol tells Bash to take input from a file and pass it to the command.

Here’s what happens:

- cat < - is telling cat to read input from the file named - via input redirection.
- However, this approach is less common and potentially confusing because cat already reads from stdin by default when no file is specified. Additionally, in more complex cases, input redirection with a file named - can lead to confusion since the dash is often interpreted as stdin.

![image](https://github.com/reph0t/CTF/blob/d3e3adf343bb9ad2c64c9fd5cbc03692b14352a4/OverTheWire/Bandit/src/Level_1-3.jpg)


**TL;DR**
- The command cat ./- is the cleaner and more reliable method to read the contents of the file named -.
- While cat < - works by using input redirection, it's not as clear or commonly used since cat reads from stdin by default when no file is specified.
- Both methods will display the contents of the file, but the first method (cat ./-) is simpler and clearer for this situation.


