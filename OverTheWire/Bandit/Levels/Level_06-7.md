# LEVEL 6

>[!Important]
> Username: `bandit6`
>
> Password: `HWasnPhtq9AVKe0dmk45nxy20cvUa6EG`

### Level Goal 

The password for the next level is stored somewhere on the server and has all of the following properties:

- owned by user bandit7
- owned by group bandit6
- 33 bytes in size

#### Commands you may need to solve this level

`ls , cd , cat , file , du , find , grep`


# WALKTHROUGH

In this level, our goal is to find a file on the **Bandit6** server with very specific attributes. The file is owned by the user **bandit7**, the group **bandit6**, and it is exactly **33 bytes** in size. Given these details, the find command is the most efficient tool to search for the file across the system and directly print its contents.


We can use the find command to search the entire server based on the file’s ownership and size criteria. The command will locate the file and automatically display its contents using the cat command.

`find / -user bandit7 -group bandit6 -size 33c -exec cat {} \; 2>/dev/null`

**BREAKDOWN:**

- `find /`: Starts searching from the root directory (/) of the server.
- `-user bandit6` : Looks for a file owned by user named bandit6
- `grou bandit7`: Looks for a file owned by a group named bandit7
- `-size 33c`: Looks for a file that has a size of 33 bytes
- `-exec cat {} \;`: Executes the cat command on the file once it's found ({} is a placeholder for the found file). This prints the contents of the file directly.
- `2>/dev/null`: Suppresses permission errors or other irrelevant output (since some directories may be restricted).

After running the command, the contents of the file that matches the criteria will be printed directly in the terminal. This file will contain the password for the next level.


![IMAGE](https://github.com/reph0t/CTF/blob/591884d2c7f3832809a3b49c5624a311c83b9906/OverTheWire/Bandit/src/Level_6-1.jpg)


