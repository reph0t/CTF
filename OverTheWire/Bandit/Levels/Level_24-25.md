# LEVEL 24 → 25

>[!Important]
> Username: `bandit24`
>
> Password: `gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8`


#### Level Goal

A `daemon` is listening on port `30002` and will give you the password for bandit25 if given the `password for bandit24` and a secret `numeric 4-digit pincode`. There is no way to retrieve the pincode except by going through all of the 10000 combinations, called brute-forcing.
You do not need to create new connections each time

#### What is a Daemon? 

A `daemon` is a computer program that runs in the background, typically without direct user interaction. Daemons often handle specific tasks or services, such as listening for incoming connections or performing scheduled jobs.

#### Walkthrough 

In this level, we are informed that a daemon is listening on port 30002, and our task is to enter both the current password and a 4-digit PIN code ranging from 0000 to 9999. Since the PIN code is not provided, we will need to brute-force it until we find the correct one.

##### What is Brute Force? 

`Brute force` is a technique often used in cybersecurity where every possible combination of a password or PIN is systematically tested until the correct one is found. While this method guarantees success, it can be time-consuming depending on the complexity of the password or PIN.

We’ll navigate to the tmp directory created in the previous levels and write a script to automate the brute-forcing process. This script will connect to the daemon, submit the current password along with each possible 4-digit PIN, and continue until the correct PIN is identified.

Below is the script:

```
#!/bin/bash
passwd24=gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8
for i in {0000..9999}; do
            echo "$passwd24 $i"
done | nc localhost 30002
```

Steps:
1. Create the Script: Save the above code in a file (e.g., script.sh) in the tmp directory.

2. Change Permissions: Make the script executable by running:

`chmod +x script.sh`

3. Run the Script: Execute the script:

`./bruteforce.sh`

4. Observe Output: The script will iterate through all possible PINs, sending them to the daemon. Once the correct PIN is found, the daemon will provide a success message.

![IMAGE](https://github.com/reph0t/CTF/blob/854982c3327de3c2502f65cd844080537a86705b/OverTheWire/Bandit/src/Level_24-1.png)


