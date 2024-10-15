# LEVEL 7

**Level Goal** 

The password for the next level is stored in the file data.txt next to the word millionth


**Commands you may need to solve this level:
**
`man, grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd`

## **WALKTHROUGH**

Let's examine the file `data.txt` that is in our current directory. By outputing the contents of the file we have noticed that there's a list of words associated with a string of characters: 


IMAGE HERE

To find the word `millionth` we are going to use the command `grep` to search for any words or patterns that contain the word "millionth". We will use:

`grep "millionth" data.txt`

IMAGE HERE

By using the command we are able to find the flag to proceed to the next level. 

