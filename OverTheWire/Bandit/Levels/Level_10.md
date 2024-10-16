# LEVEL 10

**Level Goal**

The password for the next level is stored in the file data.txt, which contains base64 encoded data

Commands you may need to solve this level

`grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd`

## **What is Base64?**

Base64 is a binary-to-text encoding scheme that converts binary data into a sequence of printable characters, using a set of 64 unique characters. It takes the source binary data 6 bits at a time and maps each group of 6 bits to one of the 64 characters. This encoding is often used to transmit binary data over text-based protocols (like email or HTTP) that may not support binary formats.

**WALKTHROUGH**

In this level, the password is hidden in `data.txt`, and we are informed that the file is encoded in Base64. To retrieve the password, we need to decode this file. We can accomplish this using the `base64` command with the decode option.


Use the following command to decode the contents of `data.txt` and display it on standard output:

`base64 -d data.txt`

**Command Breakdown:**
- `base64 -d data.txt`:
    - The `base64` command handles encoding and decoding of Base64 data.
    - The `-d` (or `--decode`) option tells it to decode the Base64 data back into its original form.
    - `data.txt` is the input file that contains the encoded data.

**Result:**

After running the command, the decoded output will be displayed, revealing the password for the next level.

![IMAGE](https://github.com/reph0t/CTF/blob/27741e4d846b12fda6e7117d11b7d19910abb4a6/OverTheWire/Bandit/src/Level_10-1.png)

