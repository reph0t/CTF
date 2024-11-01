# LEVEL 16 → 17

>[!Important]
> Username: `bandit16`
>
> Password: `kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx`

### Level Goal
The credentials for the next level can be retrieved by submitting the password of the current level to a port on localhost in the range 31000 to 32000. First find out which of these ports have a server listening on them. Then find out which of those speak SSL/TLS and which don’t. There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it.

Helpful note: Getting “DONE”, “RENEGOTIATING” or “KEYUPDATE”? Read the “CONNECTED COMMANDS” section in the manpage.

#### Commands you may need to solve this level: 

`ssh, telnet, nc, ncat, socat, openssl, s_client, nmap, netstat, ss`

### What is a Port Scanner?
A **Port Scanner ** is an application used to probe servers or hosts for open ports. It works by sending requests to a range of port addresses on a server to identify which ports are open and actively responding. 

While port scanning can sometimes be used in malicious contexts, it is primarily a legitimate tool used by network administrators and security professionals to discover services available on a remote machine.

### WALKTHROUGH

In this level, our task is to find the flag by connecting to a localhost server with an open SSL port. The open port will allow us to access the server, where we’ll receive credentials to proceed to the next level.

Since we need to identify the SSL port within a specific range, we’ll use nmap to scan these ports:

`nmap -sV -p 31000-32000 localhost`

IMAGE HERE!

This command scans the specified range (`31000-32000`) on `localhost` and checks for services running on each open port.

After a few moments, nmap provides a list of open ports and their associated protocols. Among the results, we find that port 31790 is associated with SSL. We can now use this information to connect to the server using the openssl s_client command:


`openssl s_client -connect -quiet localhost:31790`

IMAGE HERE!


Upon connecting, the server prompts us to enter input. Here, it’s waiting for the current password we used to access bandit16. Entering this password allows us to proceed and retrieve a new certificate, which contains a private key.

IMAGE HERE!

The server provides a certificate that we’ll use as a private key. This process is similar to the one we used in bandit13-14 for SSH key-based authentication. Follow these steps to set up and secure the key:

  1. Save the Private Key: Copy the certificate output and save it as a file (e.g., private.key) in the `/tmp` directory.

  2. Set Permissions: To secure the private key, use `chmod 400` to restrict its permissions. This makes the key readable only by the file owner, which is required for secure SSH connections.

`chmod 400 private.key`

> [!NOTE]
> Setting up permissions to `400` ensures that the private key isn't writable or executable. keeping it secure. 

With the private key saved and permissions set, use the `ssh` command to log in to `bandit17`:


`ssh -p 2220 -i private.key bandit17@localhost`

IMAGE HERE!

Once connected to `bandit17`, we can retrieve the flag by viewing the contents of the password file:

`cat /etc/bandit_pass/bandit17`

IMAGE HERE!
