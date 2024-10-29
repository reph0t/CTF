# LEVEL 5 → 6

### Level Goal

The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:

  - human-readable
  - 1033 bytes in size
  - not executable

#### Commands you may need to solve this level

`ls , cd , cat , file , du , find`


## WALKTHROUGH

After logging into the Bandit5 server, our task is to find a file that meets specific criteria in the inhere directory. There are many subdirectories inside inhere, which makes searching manually inefficient. Instead, we’ll use the find command to locate the file based on its properties.
Step 1: Navigate to the inhere Directory

First, let's navigate to the inhere directory using the cd command:

```-bash
cd inhere
```
Once inside, we see that the directory contains multiple subdirectories:

![IMAGE](https://github.com/reph0t/CTF/blob/cd4802b5dc3c4f35f8524c5b1019218bb14c8ebd/OverTheWire/Bandit/src/Level_5-2.jpg)

Step 2: Use the find Command to Search for the File

Since manually checking each file in every subdirectory is inefficient, we can use the find command to search based on the specific properties provided:

- Human-readable
- Size: 1033 bytes
- Not executable

We can use the following find command to efficiently locate the file that meets these criteria:

```-bash
find ./* -readable -size 1033c \! -executable
```

Breakdown of the Command:

- `find`: Invokes the find command to search for files.
- `./*`: Specifies the current directory and all subdirectories.
- `-readable`: Searches for files that are human-readable.
- `-size 1033c`: Searches for files that are exactly 1033 bytes in size.
- `\!` -executable: Excludes any executable files (the \! is a NOT operator in find).

Step 3: Find the File and Display Its Contents

Running the above find command will locate the file that meets all the conditions. You can then use cat to display the contents of the file, which contains the password for the next level.

![IMAGE](https://github.com/reph0t/CTF/blob/49754b3c0f25ac95bc92d56865f494c72f3723bf/OverTheWire/Bandit/src/Level_5-5.jpg)

> [!TIP]
> If you need more information on how the find command works or any other command, you can always refer to the manual pages by typing:


Using this method, we efficiently located the human-readable file with the correct size, avoiding the need to manually inspect each file.
