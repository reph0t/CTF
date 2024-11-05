# LEVEL 7 → 8 

>[!Important]
> Username: `bandit7`
>
> Password: `morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj`

### Level Goal

The password for the next level is stored in the file data.txt next to the word millionth


#### Commands you may need to solve this level:

`man, grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd`

## **WALKTHROUGH**

Let's examine the file `data.txt` that is in our current directory. By outputing the contents of the file we have noticed that there's a list of words associated with a string of characters: 


![IMAGE](https://github.com/reph0t/CTF/blob/91a8631d4f3f3ee22c8e4b6a9a6208aba3f550d9/OverTheWire/Bandit/src/Level_7-1.png)

To find the word `millionth` we are going to use the command `grep` to search for any words or patterns that contain the word "millionth". We will use:

`grep "millionth" data.txt`

![IMAGE](https://github.com/reph0t/CTF/blob/91a8631d4f3f3ee22c8e4b6a9a6208aba3f550d9/OverTheWire/Bandit/src/Leve_7-2.png)

By using the command we are able to find the flag to proceed to the next level. 

