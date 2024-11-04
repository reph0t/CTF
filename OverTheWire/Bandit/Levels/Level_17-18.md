# LEVEL 17 → 18

>[!Important]
> Username: `bandit17`
>
> Password: `EReVavePLFHtFlFsjn3hyzMlvSuSAcRD`

### Level Goal
There are 2 files in the homedirectory: passwords.old and passwords.new. The password for the next level is in passwords.new and is the only line that has been changed between passwords.old and passwords.new

NOTE: if you have solved this level and see ‘Byebye!’ when trying to log into bandit18, this is related to the next level, bandit19

**Commands you may need to solve this level**

`cat, grep, ls, diff`

#### WALKTHROUGH

In this task, we have two files in our directory: `passwords.old` and `passwords.new`. To identify differences between these files, we’ll use the diff command to compare them, along with grep to filter the output.

The command we’ll use is:

`diff passwords.old passwords.new | grep -f passwords.new`

**Command Breakdown**
- `diff passwords.old passwords.new`: Compares passwords.old and passwords.new, highlighting any differences.
- `| (Pipe)`: Passes the output of diff as input to the next command.
`grep -f passwords.new`: Filters the diff output to show lines that match entries in passwords.new.

![IMAGE](https://github.com/reph0t/CTF/blob/816d99c0746963c7a0b06566b644e6f81679bbe9/OverTheWire/Bandit/src/Level_17-1.png)
