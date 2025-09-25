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

## References 
None

# 2.  catting absolute paths
> This challenge asks us to read the absolute path of the flag using the 'cat' command. 

## My solve
**Flag:** `pwn.college{c1ZrrJFTAMHZPb6hDtmTLCJcpUe.QX5ETO0wSM5kjNzEzW}`
```bash

hacker@commands~catting-absolute-paths:~$ cat /flag
pwn.college{c1ZrrJFTAMHZPb6hDtmTLCJcpUe.QX5ETO0wSM5kjNzEzW}
```

## What I learned 
I learnt how we can also use paths as arguments in the cat command.

## References
None




