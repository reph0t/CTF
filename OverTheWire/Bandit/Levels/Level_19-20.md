# LEVEL 19 → 20

>[!Important]
> Username: `bandit19`
>
> Password: `cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8`

#### Level Goal
To gain access to the next level, you should use the setuid binary in the homedirectory. Execute it without arguments to find out how to use it. The password for this level can be found in the usual place (/etc/bandit_pass), after you have used the setuid binary.

### What is setuid?

`Setuid (short for Set User ID)` is a special permission bit in Unix and Linux file systems that allows users to execute a file with the permissions of the file's owner, rather than with the permissions of the user who runs it. This is often applied to executables owned by the root user, allowing regular users to execute certain commands with elevated privileges.

Key Points of Setuid:
1. Elevated Permissions: When a file with the setuid bit set is executed, it runs with the file owner’s privileges, which is typically root. For example, /bin/passwd (the command to change passwords) has the setuid bit set so that any user can change their password, even though the password file is only writable by root.

2. Security Implications: While setuid is useful, it also introduces security risks. If a setuid executable has vulnerabilities, it could potentially be exploited to gain unauthorized root access. For this reason, only trusted, essential programs typically have setuid enabled.

3. Setting and Viewing Setuid:

   - To set the setuid bit, the file owner or administrator can use chmod with the u+s option:
     `chmod u+s filename`
   - To check if a file has the setuid bit set, you can list files with the -l flag:
     `ls -l filename`

   - If the setuid bit is set, you’ll see an s in the owner’s permission section, like -rwsr-xr-x.

4. Example of Setuid Usage:

`/bin/passwd`: This command allows users to update their passwords. Since password changes need to write to /etc/shadow (owned by root), setuid enables users to change their password securely.

5. Risks and Precautions:
   - Misconfigured Setuid Binaries: Poorly configured or vulnerable setuid programs can be exploited by attackers to escalate privileges.
   - Limited Use: Setuid should only be applied when absolutely necessary, and files with setuid should be carefully audited.

>[!NOTE]
> Basically SUID is what gives permission or changes the mode of a restricted file/directory that allows the current user or group to act as another user. 

### WALKTHROUGH

In order to retieve the flag we must use the SUID executable, `bandit20-do` in our current directory that will elevate our access in order to retrieve the flag located in `/etc/bandit_pass/bandit20`. The executable will require a location to the file where gaining access to, so we use this command:

`./bandit20-do cat /etc/bandit_pass/bandit20`

![IMAGE](https://github.com/reph0t/CTF/blob/023a794de39ac740ec1aa0cfe9ab9136eacb1422/OverTheWire/Bandit/src/Level_19-1.png)



