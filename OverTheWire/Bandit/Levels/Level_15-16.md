# Level 15 → Level 16

### Level Goal
The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL/TLS encryption.

Helpful note: Getting `“DONE”`, `“RENEGOTIATING”` or `“KEYUPDATE”`? Read the `“CONNECTED COMMANDS”` section in the manpage.

#### Commands you may need to solve this level
`ssh, telnet, nc, ncat, socat, openssl, s_client, nmap, netstat, ss`


## What is TLS/SSL?
`TLS (Transport Layer Security) and SSL (Secure Sockets Layer)` are cryptographic protocols designed to secure communication over a network, such as the internet. They provide confidentiality, integrity, and authentication for data transmitted between clients (like web browsers) and servers (like websites), ensuring sensitive information—such as passwords, credit card numbers, and personal data—remains private and protected from interception.

**Key Components of TLS/SSL:**
1. Encryption: TLS/SSL encrypts the data transmitted between a client and a server, ensuring that anyone intercepting the data cannot read or alter it. This encryption helps protect against eavesdropping and tampering.

2. Authentication: TLS/SSL verifies the identity of the parties in the communication. Typically, the server’s identity is confirmed by a certificate issued by a trusted Certificate Authority (CA), which confirms that the server is legitimate.

3. Data Integrity: TLS/SSL ensures that the data has not been altered in transit. Through message authentication codes (MACs), it checks that no part of the data has been tampered with or corrupted.

**How TLS/SSL Works:**
1. Handshake: When a client connects to a server (e.g., a browser connecting to a website), a TLS/SSL handshake takes place. During this process, the client and server agree on encryption methods, and the server provides its digital certificate to verify its identity.

2. Session Keys: Once the handshake is complete, both parties generate session keys used to encrypt and decrypt the data transmitted for the duration of the session.

3. Data Transfer: The encrypted data is securely transferred between the client and the server.

4. Session Termination: When the session is finished, the session keys are discarded.

**SSL vs. TLS**
- SSL was the original protocol introduced in the 1990s, but it had significant vulnerabilities.
- TLS is the improved, more secure version of SSL. TLS 1.0 was introduced as SSL’s successor, and TLS has since become the standard with updated versions (1.1, 1.2, and 1.3) that offer enhanced security.

**Why TLS/SSL is Important:**
TLS/SSL is essential for protecting sensitive data and maintaining trust in online transactions. Websites using TLS/SSL are identified by https:// in their URL and often display a padlock icon in the browser, indicating that the connection is secure.

## Walkthrough

It’s hinted that to retrieve the flag for the next level, we need to use SSL/TLS encryption to connect securely to the local server on port `30001`. Let’s use the following command to establish this connection:
`openssl s_client -connect localhost:30001`

![IMAGE](https://github.com/reph0t/CTF/blob/f2732dde7accc71330791e6f5bdb267c09d6b71f/OverTheWire/Bandit/src/Level_15-1.png)


**Command Breakdown:**

- `openssl`: The OpenSSL command-line tool, which provised various crpytopgraphic functions.
- `s_client`: A tool within OpenSSL that initiates SSL/TLS connections to servers, useful for testing and troubleshooting
- `-connect` Specifies the target server and port to connect to.
- `localhost:30001`: Specifies the server (`localhost`) and the SSL-enabled port (`30001`) to connect to


After running the command, we’re connected to the local server over SSL/TLS. The server responds with an encrypted certificate, indicating it’s ready for secure communication and is awaiting user input.

![IMAGE](https://github.com/reph0t/CTF/blob/f2732dde7accc71330791e6f5bdb267c09d6b71f/OverTheWire/Bandit/src/Level_15-2.png)

Once connected, enter the current flag (password) to authenticate and retrieve the new flag for the next level.

![IMAGE](https://github.com/reph0t/CTF/blob/f2732dde7accc71330791e6f5bdb267c09d6b71f/OverTheWire/Bandit/src/Level_15-3.png)

This will display the new flag, allowing you to proceed to the next level.






