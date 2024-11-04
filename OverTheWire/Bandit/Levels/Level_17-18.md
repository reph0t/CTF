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

Here we have two files within our directory: `passwords.old` and `passwords.new`. So we will need to use `diff` to comapre between the two files and use piping and the grep commands:

`diff passwords.old passwords.new | grep -f passwords.new`

![IMAGE]()
