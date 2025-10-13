SSH Information: ``@bandit.labs.overthewire.org -p 2220``


# Level 2

> We need to get our password from a file named --spaces in the filename--

```bash
bandit2@bandit:~$ cat ./
cat: ./: Is a directory
bandit2@bandit:~$ cat ./*
MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
```

# Level 3 

> Password is in a hidden file in the inhere directory

```bash
bandit3@bandit:~/inhere$ ls -a
.  ..  ...Hiding-From-You
bandit3@bandit:~/inhere$ cat HI*
cat: 'HI*': No such file or directory
bandit3@bandit:~/inhere$ cat Hi*
cat: 'Hi*': No such file or directory
bandit3@bandit:~/inhere$ cat ...H*
2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
```

# Level 4

> Password is in a specific file in the inhere directory.

```bash
bandit4@bandit:~/inhere$ file ./*
./-file00: data
./-file01: data
./-file02: data
./-file03: data
./-file04: data
./-file05: data
./-file06: data
./-file07: ASCII text
./-file08: data
./-file09: data
bandit4@bandit:~/inhere$ cat ./-f*07
4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
```

# Level 5

> The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties: 
```bash 
 human-readable
 1033 bytes in size
 not executable
```

```bash
bandit5@bandit:~$ ls
inhere
bandit5@bandit:~$ cd inhere
bandit5@bandit:~/inhere$ ls
maybehere00  maybehere02  maybehere04  maybehere06  maybehere08  maybehere10  maybehere12  maybehere14  maybehere16  maybehere18
maybehere01  maybehere03  maybehere05  maybehere07  maybehere09  maybehere11  maybehere13  maybehere15  maybehere17  maybehere19
bandit5@bandit:~/inhere$ file ./
./: directory
bandit5@bandit:~/inhere$ file ./*
./maybehere00: directory
./maybehere01: directory
./maybehere02: directory
./maybehere03: directory
./maybehere04: directory
./maybehere05: directory
./maybehere06: directory
./maybehere07: directory
./maybehere08: directory
./maybehere09: directory
./maybehere10: directory
./maybehere11: directory
./maybehere12: directory
./maybehere13: directory
./maybehere14: directory
./maybehere15: directory
./maybehere16: directory
./maybehere17: directory
./maybehere18: directory
./maybehere19: directory
bandit5@bandit:~/inhere$ find . -type f -size 1033c
./maybehere07/.file2
bandit5@bandit:~/inhere$ cat ./maybehere07/.file2
HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
```


# Level

>

```bash

```


