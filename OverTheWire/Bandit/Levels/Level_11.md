# LEVEL 11

**Level Goal**

The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions

Commands you may need to solve this level

`grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd`

## **What is ROT13?**

ROT13 (short for "Rotate by 13 places") is a simple letter substitution cipher where each letter is replaced by the letter that is 13 positions later in the alphabet. It is a special case of the Caesar cipher, which dates back to ancient Rome. In ROT13:

  - Letters `A-M` are replaced by `N-Z` (and vice versa for uppercase letters).
  - Letters `a-m` are replaced by `n-z` (and vice versa for lowercase letters).

Since there are 26 letters in the alphabet, applying ROT13 twice brings the original text back, making it a reversible and symmetric cipher.

## **WALKTHROUGH**

In this level, the password is hidden in the file `data.txt`, but it has been encoded using ROT13. If we print the contents of the file, it will look like a scrambled, unreadable message. To decode it, we need to apply the ROT13 transformation using the tr (translate) command.

![IMAGE](https://github.com/reph0t/CTF/blob/3561ee7e09e09ebe67689def47cc0d8f26260442/OverTheWire/Bandit/src/Level_11-2.png)


To decode the ROT13 cipher and retrieve the password, run the following command:

`cat data.txt | tr ['A-Za-z'] ['N-ZA-Mn-za-m']`

Command Breakdown:

- `cat data.txt`: This command prints the contents of data.txt, which is currently encoded using ROT13.
- `| (Pipe)`: The pipe (|) sends the output from cat as input to the tr command.
- [`tr 'A-Za-z'] ['N-ZA-Mn-za-m']`:
   - The `tr` command translates characters.
   - `'A-Za-z'` specifies the range of uppercase (`A-Z`) and lowercase (`a-z`) letters.
   - `'N-ZA-Mn-za-m'` specifies the corresponding ROT13-translated letters, where each letter is shifted by 13 positions.

Once you run the above command, it will output the decoded text, revealing the password for the next level.

![IMAGE](https://github.com/reph0t/CTF/blob/030cc21ccc653808be96f537d19c911e30522862/OverTheWire/Bandit/src/Level_11-1.png)



