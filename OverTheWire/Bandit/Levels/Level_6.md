# LEVEL 6

# Level Goal 

The password for the next level is stored somewhere on the server and has all of the following properties:

- owned by user bandit7
- owned by group bandit6
- 33 bytes in size

Commands you may need to solve this level

`ls , cd , cat , file , du , find , grep`


# WALKTHROUGH

Similar to the previous level we are tasked to find a file within the bandit6 server. This should be straight forward since we are given specific details of the kind of file we need to search for. Same as the previous level we are going to use the `find` command to search throughout the server and printing it:

`find / -name bandit6 -group bandit7 -exec cat {} \; 2>/dev/null`

**BREAKDOWN:**

- `find /`: Starts searching from the root directory (/) of the server.
- `-user bandit6` : Looks for a file owned by user named bandit6
- `grou bandit7`: Looks for a file owned by a group named bandit7
- `-exec cat {} \;`: Executes the cat command on the file once it's found ({} is a placeholder for the found file). This prints the contents of the file directly.
- `2>/dev/null`: Suppresses permission errors or other irrelevant output (since some directories may be restricted).





