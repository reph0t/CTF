# LEVEL 20 → Level 21

>[!Important]
> Username: `bandit20`
>
> Password: `0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO`


#### Level Goal

There is a setuid binary in the homedirectory that does the following: it makes a connection to localhost on the port you specify as a commandline argument. It then reads a line of text from the connection and compares it to the password in the previous level (bandit20). If the password is correct, it will transmit the password for the next level (bandit21).

NOTE: Try connecting to your own network daemon to see if it works as you think

Commands you may need to solve this level

`ssh, nc, cat, bash, screen, tmux, Unix ‘job control’ (bg, fg, jobs, &, CTRL-Z, …)`

#### WALKTHROUGH

In this level, we need to use a SUID binary to connect to a local host and retrieve the password for the next level. The hint suggests that the binary expects a connection from another source to provide the password, so we’ll set up a listener on one terminal and use the SUID binary to connect to it from another.

##### Step-by-Step Walkthrough

1. Set Up a Listener:
   - Open a terminal (right side) and set up a `netcat` listener to act as a server, listening on port `4444`:
   
     `nc -lvp 4444`

   ![IMAGE](https://github.com/reph0t/CTF/blob/4efd378b127e314dedd1bfff461e004edbac0442/OverTheWire/Bandit/src/Level_20-1.png)

   - This command starts `netcat` in listen mode (`-l`) on the specified port (`4444`), waiting for incoming connections.

1. Run the SUID Binary:

   - In another terminal (left side), execute the SUID binary, specifying the same port `4444` to connect to the listener:

     `./suconnect 4444`

     ![IMAGE](https://github.com/reph0t/CTF/blob/ddf6e036f5de0b7d7c6bb6b7a28f8222233f1c21/OverTheWire/Bandit/src/Level_20-1.png)
     
   - This command initiates a connection to the server on port `4444` that we set up in the first terminal.

2. Provide the Password:
   - With the connection established, the listener terminal prompts for input. Enter the password in this terminal, and it will be sent through the connection.

   - After entering the password, the SUID binary responds with the password for the next level, bandit21.

   ![IMAGE](https://github.com/reph0t/CTF/blob/4efd378b127e314dedd1bfff461e004edbac0442/OverTheWire/Bandit/src/Level_20-3.png)


By setting up this two-way communication, we’re able to simulate a client-server interaction, using netcat and the SUID binary to retrieve the flag.
