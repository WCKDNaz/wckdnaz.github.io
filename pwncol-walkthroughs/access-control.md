---
layout: default
---
# Access Control Module Walkthrough *(Levels 1-3)* - PwnCollege 
Practicality of the module lies in building useful and practical knowledge application of read, write, or execute file permissions. 
## Level 1:
```
$ /challenge/run
$ cat /flag

Theory: Since the file was changed to be owned by the user and the user has sufficient permissions to simply read the flag by using the cat utility.
```
## Level 2:
```
$ /challenge/run
$ cat /flag

Theory: The file's ownership group was changed to our group and following same principles we can simply read the flag by using the cat utility.
```
## Level 3:
```
$ chmod u+r /flag             # // symbolic value by adding (+) r (read) permission to u (user), g for (group), and o (other) 
$ chmod 400 /flag             # // octal value with 4 representing read permission and 00 for ---/--- for group/other

Theory: The file's ownership user was assigned to our user, but has no set permissions, we can solve this by
        modifying the flag's file permissions in two ways using chmod octal value or symoblic values.
```
