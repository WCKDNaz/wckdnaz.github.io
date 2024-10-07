---
layout: default
---
# Access Control Module Walkthrough *(Levels 1-7)* - PwnCollege 
Practicality of the module lies in building useful and practical examples of exploiting access control methods.
The requirement of each level is to run a binary in the challenge directory `/challenge/run`, then the environment of the flag file changes in a specific manner, 
the goal is to find a way to read the content of the `flag` file, hence exploiting available resources. The flag value will be hidden in these walkthroughs, as the end goal of my writing is to share insights and methodologies rather than answers.
## Level 1:
```
$ /challenge/run 
===== Welcome to Access Control! =====
In this series of challenges, you will be working with various access control systems.
Break the system to get the flag.


In this challenge you will work with different UNIX permissions on the flag.

The flag file will be owned by you and have 400 permissions.


Before:
-r-------- 1 root root 58 Oct  7 10:07 /flag
After:
-r-------- 1 hacker root 58 Oct  7 10:07 /flag

$ cat /flag
<flag_value>

Theory: The file's ownership was changed to be owned by the user and the user has sufficient permissions to simply read the flag by using the cat utility.
```
## Level 2:
```
$ /challenge/run 
===== Welcome to Access Control! =====
In this series of challenges, you will be working with various access control systems.
Break the system to get the flag.


In this challenge you will work with different UNIX permissions on the flag.

The flag file will be owned by root, group as you, and have 040 permissions.


Before:
-r-------- 1 root root 58 Oct  7 10:11 /flag
After:
----r----- 1 root hacker 58 Oct  7 10:11 /flag

$ cat /flag
<flag_value>

Theory: The file's ownership group was changed to our group and following same principles we can simply read the flag by using the cat utility.
```
## Level 3:
```
$ /challenge/run 
===== Welcome to Access Control! =====
In this series of challenges, you will be working with various access control systems.
Break the system to get the flag.


In this challenge you will work with different UNIX permissions on the flag.

The flag file will be owned by you and have 000 permissions.


Before:
-r-------- 1 root root 58 Oct  7 10:12 /flag
After:
---------- 1 hacker root 58 Oct  7 10:12 /flag

$ chmod u+r /flag             # // symbolic value by adding (+) 'r' (read) permissions to 'u' (user), while noting that 'g' stands for (group), and 'o' stands for(other) 
$ chmod 400 /flag             # // numeric value representation with '4' representing read permissions and '00' for ---/--- (no permissions) for group/other

$ cat /flag
<flag_value>

Theory: The file's ownership user was assigned to our user, but has no set permissions, we can solve this by
        modifying the flag's file permissions in two ways using chmod numeric values or symbolic values representations.
```
## Level 4:
```
$ /challenge/run 
===== Welcome to Access Control! =====
In this series of challenges, you will be working with various access control systems.
Break the system to get the flag.


In this challenge you will work understand how the SETUID bit for UNIX permissions works.

What if /bin/cat had the SETUID bit set?


Before:
-rwxr-xr-x 1 root root 43416 Sep  5  2019 /bin/cat
After:
-rwsr-xr-x 1 root root 43416 Sep  5  2019 /bin/cat

$ cat /flag
<flag_value>
Theory: The utility 'cat' was given a setuid permission which in fact gives the user the ability to invoke cat
        with the effective owner user ID which in this case is root, giving full power to the user to use it
        as they wish.
```
## Level 5:
```
$ /challenge/run 
===== Welcome to Access Control! =====
In this series of challenges, you will be working with various access control systems.
Break the system to get the flag.


In this challenge you will work understand how the SETUID bit for UNIX permissions works.

What if /bin/cp had the SETUID bit set?

Hint: Look into how cp will deal with different permissions.

Another Hint: check the man page for cp, any options in there that might help?


Before:
-rwxr-xr-x 1 root root 153976 Sep  5  2019 /bin/cp
After:
-rwsr-xr-x 1 root root 153976 Sep  5  2019 /bin/cp

$ cp --no-preserve=mode,ownership /flag flag-copy.txt
$ cat flag-copy.txt
<flag_value>

Theory: The utility 'cp' was given a setuid permission, this makes the utility use the effective user ID which is root
        and with this set, we can look through the man pages of 'cp' to find an option '--no-preserve=mode,ownership'
        this creates a copy of the flag file with read permissions that we can use and obtain the flag value.
```
## Level 6:
```
$ /challenge/run 
===== Welcome to Access Control! =====
In this series of challenges, you will be working with various access control systems.
Break the system to get the flag.


In this challenge you will work with different UNIX permissions on the flag.

The flag file is owned by root and a new group.

Hint: Search for how to join a group with a password.


Before:
-r-------- 1 root root 58 Oct  7 10:17 /flag
After:
----r----- 1 root group_cziehuds 58 Oct  7 10:17 /flag
The password for group_cziehuds is: xvqovuvh

$ newgrp <"group_name">
Password: xvqovuvh          // Prompt
$ cat /flag
<flag_value>

Theory: The flag is now assigned ownership to a different group and has read permissions already set on,
        with the utility 'newgrp' we can use it to assign our user 'hacker' to that group and
        then use 'cat' utility to simply read the flag file.
```
## Level 7:
```
$ /challenge/run 
===== Welcome to Access Control! =====
In this series of challenges, you will be working with various access control systems.
Break the system to get the flag.


In this challenge you will work understand how UNIX permissions works with multiple users.

You'll also be given access to various user accounts, use su to switch between them.


Before:
-r-------- 1 root root 58 Oct  7 10:19 /flag
Created user user_wjourxos with password hksgyvfi
After:
-------r-- 1 hacker root 58 Oct  7 10:19 /flag

Method One:
$ chmod u+r /flag        # // symbolic representation
$ chmod 400 /flag        # // numeric representation
$ cat /flag
<flag_value>

Method Two:
$ su "new_user"
$ cat /flag
<flag_value>


Theory: The flag in this level can be solved in 2 ways, the normal intended way and a workaround using 'chmod',
        so after you initiate the run and the flag is set to be read by others and you're prompted a second user
        you can use 'su' to change user and read the flag using 'cat' or simply since now you own the flag, use
        '$ chmod u+r flag' or '$ chmod 400 /flag' to be able to read the flag while still signed in as 'hacker'.
```
