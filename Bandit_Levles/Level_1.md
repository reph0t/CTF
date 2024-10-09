# LEVEL 1

## **Level Goal**
The password for the next level is stored in a file called `-` located in the home directory

**Commands you may need to solve this level**

`ls , cd , cat , file , du , find`

### **Dashed Files (-)**
When listing the files of the current directory, there is a file with a `-`. We can't really use the `cat` command
because the `cat` command doesn't know if you're referring to a file or directly from the user's input(stdin).

This is due to the fact that the `-` symbol in many UNIX commands, is a shorthand for "read from standard input" as stated before it means, it is expecting some kind of input in order for the command to execute it. 

In order to execute the command properly there will have to be a different approach. So `cat -` won't work in this case. We must execute a command that tells the `cat` command to interpret the dash as a file. 

## **WALKTHROUGH**

**STEP 1**

 We enter this command: 

 ```cat ./-```

