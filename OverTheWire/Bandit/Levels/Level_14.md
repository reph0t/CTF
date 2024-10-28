# LEVEL 14

## Level Goal 
The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.

Commands you may need to solve this level
`ssh, telnet, nc, openssl, s_client, nmap`

### Walkthrough 

This level is straightforward. We simply need to connect to a specific port on the local server using the `telnet` command:

`telnet localhost 30000`

**Command Breakdown:**

- `telnet`: a client-server protocol that allows the users to access remote systems on local area networks.
- `localhost`: Specifies the server we are connecting to (in this case, the local server).
- `30000`: The port number to connect to on the server.

Once you enter the command, you will see a prompt indicating you’ve connected to the server’s IP address. Following the instructions, enter the current password used to log in to `bandit14`.

Upon entering the password, you’ll receive the flag for the next level.



