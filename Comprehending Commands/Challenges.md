# Challenges
1. cat: not the pet, but the command!
2. catting absolute paths
3. more catting practice
4. grepping for a needle in a haystack
5. comparing files
6. lising files
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
I learnt how we can also use paths as arguments in the cat command.

# 4. grepping for a needle in a haystack
> This challenge introduces us to the 'grep' command and asks us to use it to search for the flag among thousands of lines of text.

## My solve
**Flag:** `pwn.college{sebKlnAz6FgqeZYq2en6h45FP2i.QX3EDO0wSM5kjNzEzW}`

```bash
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ grep pwn.college /challenge/data.txt
pwn.college{sebKlnAz6FgqeZYq2en6h45FP2i.QX3EDO0wSM5kjNzEzW}

```
## What I learned
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



