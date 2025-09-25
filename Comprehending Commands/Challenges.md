# Challenges
1. cat: not the pet, but the command!
2. catting absolute paths
3. more catting practice
4. grepping for a needle in a haystack
5. comparing files
6. listing files
7. touching files
8. removing files
9. moving files
10. hidden files
11. An Epic Filesystem Quest
12. making directories
13. finding files
14. linking files
   
# 1.  cat: not the pet, but the command!
> This challenge asks us to read the 'flag' file from the home directory using the 'cat' command. 

## My solve
**Flag:** `pwn.college{YAzKp1uUD4l5iy02-oIdz69YxSL.QXxcTN0wSM5kjNzEzW}`
```bash

hacker@commands~cat-not-the-pet-but-the-command:~$ cat flag
pwn.college{YAzKp1uUD4l5iy02-oIdz69YxSL.QXxcTN0wSM5kjNzEzW}
```

## What I learned 
I learned about the linux command 'cat' which is primarily used for reading out files. It can con*cat*enate multiple files and I also noticed that if you dont provide an argument it functions like the echo command by reading the terminal input and outputting it. 

# 2.  catting absolute paths
> This challenge asks us to cat the absolute path of the flag.

## My solve
**Flag:** `pwn.college{c1ZrrJFTAMHZPb6hDtmTLCJcpUe.QX5ETO0wSM5kjNzEzW}`
```bash

hacker@commands~catting-absolute-paths:~$ cat /flag
pwn.college{c1ZrrJFTAMHZPb6hDtmTLCJcpUe.QX5ETO0wSM5kjNzEzW}
```

## What I learned 
I learnt how we can also provide paths as arguments for the cat command. This helps us view the content of files without having to use cd.

# 4. grepping for a needle in a haystack
> This challenge introduces us to the 'grep' command and asks us to use it to search for the flag among thousands of lines of text.

## My solve
**Flag:** `pwn.college{sebKlnAz6FgqeZYq2en6h45FP2i.QX3EDO0wSM5kjNzEzW}`

```bash
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ grep pwn.college /challenge/data.txt
pwn.college{sebKlnAz6FgqeZYq2en6h45FP2i.QX3EDO0wSM5kjNzEzW}

```
## What I learned
I learnt about the grep command and how it basically functions like a 'find' command for text only in the linux filesystem.
The syntax of the grep command is of the form:
> user@domain:~$ grep [item to be searched] path

# 5. comparing files
> This challenge introduces us to the 'diff' command and asks us to use it to search for the flag by comparision. 

## My solve
**Flag:** `pwn.college{Mu3ES8keBwGUK4eZWcjfDYSAmdi.01MwMDOxwSM5kjNzEzW}`

```bash
hacker@commands~comparing-files:~$ diff /challenge/decoys_only.txt /challenge/decoys_and_real.txt
63a64
> pwn.college{Mu3ES8keBwGUK4eZWcjfDYSAmdi.01MwMDOxwSM5kjNzEzW}

```
## What I learned
The diff command is used to differentiate between the contents of two files. The 63a64 in the output here means that after line 63 of file 1 add line 64 of file 2.
The syntax of the diff command is of the form:
> user@domain:~$ diff [file 1] [file 2]

# 6. listing files
> This challenge introduces us to the 'ls' command and asks us to use it to list the files in /challenge to find the flag.

## My solve
**Flag:** `pwn.college{sCH9jQjSJqIXXonWF0ljgtICfZY.QX4IDO0wSM5kjNzEzW}`

First, I used the ls command to view the contents of the /challenge directory. Then I made the mistake of using the cat command on 10870-renamed-run-18184 and I was confused on why it displayed an echo statement. Then I realized that cat only *reads* the content of the file and does not run it and the echo command I was seeing was to be executed when I ran the file.

```bash
hacker@commands~listing-files:~$ ls /challenge
10870-renamed-run-18184  DESCRIPTION.md
hacker@commands~listing-files:/challenge$ cat 10870-renamed-run-18184
#!/opt/pwn.college/bash

echo "Yahaha, you found me! Here is your flag:"
cat /flag
hacker@commands~listing-files:/challenge$ /10870-renamed-run-18184
hacker@commands~listing-files:/challenge$ cd
hacker@commands~listing-files:~$ /challenge/10870-renamed-run-18184
Yahaha, you found me! Here is your flag:
pwn.college{sCH9jQjSJqIXXonWF0ljgtICfZY.QX4IDO0wSM5kjNzEzW}

```
## What I learned
The 'ls' command is used to list files or directories inside a given directory.
The syntax of the ls command is of the form:
> user@domain:~$ ls [path]

# 7. touching files
> This challenge introduces us to the 'touch' command and asks us to create two files.

## My solve
**Flag:** `pwn.college{ogdgn7CkOgVas8AFdJyNIrGBXYz.QXwMDO0wSM5kjNzEzW}`

```bash
hacker@commands~touching-files:~$ touch /tmp/pwn
hacker@commands~touching-files:~$ touch /tmp/college
hacker@commands~touching-files:~$ /challenge/run
Success! Here is your flag:
pwn.college{ogdgn7CkOgVas8AFdJyNIrGBXYz.QXwMDO0wSM5kjNzEzW}
```
## What I learned
The 'touch' command is used to create new files in a given directory.
The syntax of the touch command is of the form:
> user@domain:~$ touch [file name]

# 8. removing files
> This challenge introduces us to the 'rm' command and asks us to delete a file from the home directory.

## My solve
**Flag:** `pwn.college{onAaRMgJC91xx2vBvKUk8GcailS.QX2kDM1wSM5kjNzEzW}`

```bash
hacker@commands~removing-files:~$ rm delete_me
hacker@commands~removing-files:~$ /challenge/check
Excellent removal. Here is your reward:
pwn.college{onAaRMgJC91xx2vBvKUk8GcailS.QX2kDM1wSM5kjNzEzW}
```
## What I learned
The 'rm' command is used to delete files in a given directory.
The syntax of the rm command is of the form:
> user@domain:~$ rm [file to be removed]
 
# 9. moving files
>This challenge introduces us to the 'mv' command and asks us to move a file into a specific path

## My solve
**Flag:** `pwn.college{8O4Ymt9osErntDw1sEwSQnpLtDV.0VOxEzNxwSM5kjNzEzW}`

```bash
hacker@commands~moving-files:~$ ls
f
hacker@commands~moving-files:~$ mv /flag /tmp/hack-the-planet
Correct! Performing 'mv /flag /tmp/hack-the-planet'.
hacker@commands~moving-files:~$ /challenge/check
Congrats! You successfully moved the flag to /tmp/hack-the-planet! Here it is:
pwn.college{8O4Ymt9osErntDw1sEwSQnpLtDV.0VOxEzNxwSM5kjNzEzW}
```
## What I learned
The 'mv' command is used to transport files in a given directory.
The syntax of the mv command is of the form:
> user@domain:~$ mv [file to be transferred] [path to be transferred to]

# 10. hidden files
>This challenge introduces us to concept of hidden files and asks us to look for a flag inside a hidden file.

## My solve
**Flag:** `pwn.college{ED3qewXTFxVCrCXbWUc9ogWvrLo.QXwUDO0wSM5kjNzEzW}`

```bash
hacker@commands~hidden-files:~$ cd /
hacker@commands~hidden-files:/$ ls -a
.   .dockerenv             bin   challenge  etc   lib    lib64   media  nix  proc  run   srv  tmp  var
..  .flag-311512805813923  boot  dev        home  lib32  libx32  mnt    opt  root  sbin  sys  usr
hacker@commands~hidden-files:/$ cat flag-311512805813923
cat: flag-311512805813923: No such file or directory
hacker@commands~hidden-files:/$ cat .flag-311512805813923
pwn.college{ED3qewXTFxVCrCXbWUc9ogWvrLo.QXwUDO0wSM5kjNzEzW}
```
## What I learned
The 'ls -a' command is used to view "hidden" files that start with a '.' which the linux filesystem hides by default.

# 11. An Epic Filesystem Quest
> This challenge requires us to use the 'cat, ls, la-a, and cd' commands multiple times across different directories to find the flag.

## My solve
**Flag:** `pwn.college{gZY1y3ZQAZllFkut6ftXyM4Q0-F.QX5IDO0wSM5kjNzEzW}`

```bash
hacker@commands~an-epic-filesystem-quest:~$ cd /
hacker@commands~an-epic-filesystem-quest:/$ ls
EVIDENCE  boot       dev  flag  lib    lib64   media  nix  proc  run   srv  tmp  var
bin       challenge  etc  home  lib32  libx32  mnt    opt  root  sbin  sys  usr
hacker@commands~an-epic-filesystem-quest:/$ cat EVIDENCE
Great sleuthing!
The next clue is in: /opt/linux/linux-5.4/security/tomoyo/policy

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/$ cd /opt/linux/linux-5.4/security/tomoyo/policy
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/security/tomoyo/policy$ ls
TRACE  exception_policy.conf.default
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/security/tomoyo/policy$ cat TRACE
Tubular find!
The next clue is in: /usr/local/lib/python3.8/dist-packages/IPython/sphinxext/__pycache__
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/security/tomoyo/policy$ cd /usr/local/lib/python3.8/dist-packages/IPython/sphinxext/__pycache__
hacker@commands~an-epic-filesystem-quest:/usr/local/lib/python3.8/dist-packages/IPython/sphinxext/__pycache__$ ls
BLUEPRINT  __init__.cpython-38.pyc  custom_doctests.cpython-38.pyc  ipython_console_highlighting.cpython-38.pyc  ipython_directive.cpython-38.pyc
hacker@commands~an-epic-filesystem-quest:/usr/local/lib/python3.8/dist-packages/IPython/sphinxext/__pycache__$ cat BLUEPRINT
Congratulations, you found the clue!
The next clue is in: /opt/linux/linux-5.4/include/config/balloon

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/usr/local/lib/python3.8/dist-packages/IPython/sphinxext/__pycache__$ ls /opt/linux/linux-5.4/include/config/balloon
ALERT-TRAPPED  compaction.h
hacker@commands~an-epic-filesystem-quest:/usr/local/lib/python3.8/dist-packages/IPython/sphinxext/__pycache__$ cat /opt/linux/linux-5.4/include/config/balloon/ALERT-TRAPPED
Lucky listing!
The next clue is in: /opt/linux/linux-5.4/tools/testing/selftests/rcutorture/configs/lock

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/usr/local/lib/python3.8/dist-packages/IPython/sphinxext/__pycache__$ ls /opt/linux/linux-5.4/tools/testing/selftests/rcutorture/configs/lock
BUSTED       CFLIST    LOCK01  LOCK02.boot  LOCK03.boot  LOCK04.boot  LOCK05.boot  LOCK06.boot  LOCK07.boot      ver_functions.sh
BUSTED.boot  CFcommon  LOCK02  LOCK03       LOCK04       LOCK05       LOCK06       LOCK07       MESSAGE-TRAPPED
hacker@commands~an-epic-filesystem-quest:/usr/local/lib/python3.8/dist-packages/IPython/sphinxext/__pycache__$ cat /opt/linux/linux-5.4/tools/testing/selftests/rcutorture/configs/lock/MESSAGE-TRAPPED
Lucky listing!
The next clue is in: /opt/linux/linux-5.4/arch/microblaze/lib

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/usr/local/lib/python3.8/dist-packages/IPython/sphinxext/__pycache__$ ls -a /opt/linux/linux-5.4/arch/microblaze/lib
.   .WHISPER  ashldi3.c  cmpdi2.c  fastcopy.S  lshrdi3.c  memmove.c  modsi3.S  mulsi3.S       ucmpdi2.c  umodsi3.S
..  Makefile  ashrdi3.c  divsi3.S  libgcc.h    memcpy.c   memset.c   muldi3.c  uaccess_old.S  udivsi3.S
hacker@commands~an-epic-filesystem-quest:/usr/local/lib/python3.8/dist-packages/IPython/sphinxext/__pycache__$ cd /opt/linux/linux-5.4/arch/microblaze/lib
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/arch/microblaze/lib$ cat .WHISPER
Congratulations, you found the clue!
```
## What I learned
This challenge uses concepts learned from the previous challenges multiple times, the command history feautre helped a lot.

# 12. making directories
> This challenge introduces us to the 'mkdir' command and asks us to create a directory into which files can be stuck.

## My solve
**Flag:** `pwn.college{cevDqCFZZYWfHdLHpeU_6Fs1YnO.QXxMDO0wSM5kjNzEzW}`

```bash
hacker@commands~making-directories:~$ mkdir /tmp/pwn
hacker@commands~making-directories:~$ cd /tmp/pwn
hacker@commands~making-directories:/tmp/pwn$ touch college
hacker@commands~making-directories:/tmp/pwn$ cd
hacker@commands~making-directories:~$ /challenge/run
Success! Here is your flag:
pwn.college{cevDqCFZZYWfHdLHpeU_6Fs1YnO.QXxMDO0wSM5kjNzEzW}
```
## What I learned
The 'mkdir' command is used to create directories.
The syntax of the mkdir command is of the form:
> user@domain:~$ mkdir [name of directory]

# 13. finding files
> This challenge introduces us to the 'find' command and asks us to use it to find the flag.

## My solve
**Flag:** ``

First I changed the directory to / and simply used find on it, this started generating an endless list of files and directories. Then I used find / -name flag 
```bash

```
## What I learned
The 'file' command is used to search for files and directories. It can take arguments and also look in specific search locations. It's different from grep because grep searches for text inside the file whereas find searches for the file itself.
I also noticed that find can be used to list (find .) files similar to 'ls-a' but in an unorganized manner.

The syntax of the find command is of the form:
> user@domain:~$ find [directory] -name [file to be searched] 












