---
layout: default
---
# Access Control Module Walkthrough *(Levels 1-7)* - PwnCollege 
Practicality of the module lies in building useful and practical examples of exploiting access control methods. 
## Level 1:
```
$ /challenge/run
$ cat /flag

Theory: The file's ownership was changed to be owned by the user and the user has sufficient permissions to simply read the flag by using the cat utility.
```
## Level 2:
```
$ /challenge/run
$ cat /flag

Theory: The file's ownership group was changed to our group and following same principles we can simply read the flag by using the cat utility.
```
## Level 3:
```
$ chmod u+r /flag             # // symbolic value by adding (+) 'r' (read) permissions to 'u' (user), while noting that 'g' stands for (group), and 'o' stands for(other) 
$ chmod 400 /flag             # // octal value representation with '4' representing read permissions and '00' for ---/--- (no permissions) for group/other
$ cat /flag

Theory: The file's ownership user was assigned to our user, but has no set permissions, we can solve this by
        modifying the flag's file permissions in two ways using chmod octal value or symoblic values.
```
## Level 4:
```
$ /challenge/run
$ cat /flag

Theory: The utility 'cat' was given a setuid permission which in fact gives the user the ability to invoke cat
        with the effective owner user ID which in this case is root, giving full power to the user to use it
        as they wish.
```
## Level 5:
```
$ /challenge/run
$ cp --no-preserve=mode,ownership /flag flag-copy.txt

Theory: The utility 'cp' was given a setuid permission, this makes the utility use the effective user ID which is root
        and with this set, we can look through the man pages of 'cp' to find an option '--no-preserve=mode,ownership'
        this creates a copy of the flag file with read permissions that we can use and obtain the flag value.
```
## Level 6:
```
$ /challenge/run
$ newgroup <"group_name">
$ cat /flag

Theory: The flag is now assigned ownership to a different group and has read permissions already set on,
        with the utility 'newgrp' we can use it to assign our user 'hacker' to that group and
        then use 'cat' utility to simply read the flag file.
```
## Level 7:
```
Method One:
$ /challenge/run
$ chmod u+r /flag        # // symbolic representation
$ chmod 400 /flag        # // octal representation
$ cat /flag

Method Two:
$ su "new_user"
$ cat /flag

Theory: The flag in this level can be solved in 2 ways, the normal intended way and a workaround using 'chmod',
        so after you initiate the run and the flag is set to be read by others and you're prompted a second user
        you can use 'su' to change user and read the flag using 'cat' or simply since now you own the flag, use
        '$ chmod u+r flag' or '$ chmod 400 /flag' to be able to read the flag while still signed in as 'hacker'.
```
