# LEVEL 9

**Level Goal**

The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.

Commands you may need to solve this level

`grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd`

**WALKTHROUGH**

In this level, our task is to find the password hidden in `data.txt`. The password is located within a human-readable string and is preceded by a series of = characters. We can use the strings command to extract all printable (human-readable) text from the file and then filter the results using grep.

Run the following command:

`strings data.txt | grep "="`

**Breakdown**:

- `strings data.txt`: This command scans data.txt and extracts all sequences of printable characters. It helps filter out binary data, leaving only human-readable text.
- `| (Pipe)`: The pipe sends the output from strings as input to the next command.
- `grep "="`: This searches the output for any lines containing = characters, helping us locate the specific line where the password is hidden.

**Result**:

By running this command, you will be able to identify the string containing the password, as it will be preceded by = characters.


