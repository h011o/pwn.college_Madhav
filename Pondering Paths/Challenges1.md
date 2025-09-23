# Challenges
1. The Root
2. Program and absolute paths
3. Position thy self
4. Position elsewhere
5. Position yet elsewhere
6. Implicit relative paths, from /
7. Explicit relative paths, from /
8. Implictive relative path
9. Home sweet home


# 1. The Root
This challenge asks us to invoke the pwn program using its absolute path.

## My solve
**Flag:** `pwn.college{UpHmnW3qBDDvS1AqhTOTVzmLbaw.QX4cTO0wSM5kjNzEzW}`

```bash
hacker@paths~the-root:~$ /pwn
BOOM!!!
Here is your flag:
pwn.college{UpHmnW3qBDDvS1AqhTOTVzmLbaw.QX4cTO0wSM5kjNzEzW}
```

## What I learned
I learned about the tree-like structure of the linux file system, which originates at the root (/), and how we can refer to any file in the linux filesystem by using its *path* that describes the exact location of the file.

## References 
None

# 2. Program and absoulte paths
This challenge asks us to invoke the run program inside the challenge directory

## My solve
**Flag:** `pwn.college{gGA-Ao15J4vKckwqHRgLhAZdJtH.QX1QTN0wSM5kjNzEzW}`

```bash
hacker@paths~program-and-absolute-paths:~$ /
bash: /: Is a directory
hacker@paths~program-and-absolute-paths:~$ /challenge/run
Correct!!!
/challenge/run is an absolute path! Here is your flag:
pwn.college{gGA-Ao15J4vKckwqHRgLhAZdJtH.QX1QTN0wSM5kjNzEzW}
```

## What I learned
I understood that the root (/) itself is a directory and the deeper into the "tree" the file lies, the longer its path becomes because the number of directories increase.

## References 
None

# 3. Position thy self
This challenge asks us to execute a certain program from a specific path.

## My solve
**Flag:** `pwn.college{AK2UsF7F5Z1PwiwlBeE9c2x8ntO.QX2QTN0wSM5kjNzEzW}`

first I located the position of the present directory using (~) after which I tried to run the program which gave me its directory. Then I attempted to change the directory and run the challenge program.

```bash
bash: /home/hacker: Is a directory
hacker@paths~position-thy-self:~$ cd /challenge/run
bash: cd: /challenge/run: Not a directory
hacker@paths~position-thy-self:~$ /challenge/run
Incorrect...
You are not currently in the /usr/share/zoneinfo/posix/Asia directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-thy-self:~$ cd /usr/share/zoneinfo/posix/Asia/challenge/run
bash: cd: /usr/share/zoneinfo/posix/Asia/challenge/run: No such file or directory
hacker@paths~position-thy-self:~$ cd /usr/share/zoneinfo/posix/Asia
hacker@paths~position-thy-self:/usr/share/zoneinfo/posix/Asia$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{AK2UsF7F5Z1PwiwlBeE9c2x8ntO.QX2QTN0wSM5kjNzEzW}
```

## What I learned
I realized that programs cannot be executed directly from their path before accessing its directory.

## References 
None

# 4. Position elsewhere
This challenge asks us to execute a certain program from a specific path.

## My solve
**Flag:** `pwn.college{g66T1dhFkpzstRbdTFbR-MzoOwD.QX3QTN0wSM5kjNzEzW}`
This flag was obtained following the same process as the previous one.
first I located the position of the present directory using (~) after which I attempted to change the directory and run the challenge program.

```bash
hacker@paths~position-elsewhere:~$ ~
bash: /home/hacker: Is a directory
hacker@paths~position-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /home directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-elsewhere:~$ cd /home
hacker@paths~position-elsewhere:/home$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{g66T1dhFkpzstRbdTFbR-MzoOwD.QX3QTN0wSM5kjNzEzW}
```

## References 
None

# 5. Position yet Elsewhere 
This challenge asks us to execute a certain program from a specific path.

## My solve
**Flag:** `
pwn.college{YTEOjchtbSPJn0jP0_2WWdqL24W.QX4QTN0wSM5kjNzEzW}`

This flag was obtained following the same process as the previous two.
first I located the position of the present directory using (~) after which I attempted to change the directory and run the challenge program.

```bash
hacker@paths~position-yet-elsewhere:~$ ~
bash: /home/hacker: Is a directory
hacker@paths~position-yet-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /proc/138/fd directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-yet-elsewhere:~$ cd /proc/138/fd
hacker@paths~position-yet-elsewhere:/proc/138/fd$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{YTEOjchtbSPJn0jP0_2WWdqL24W.QX4QTN0wSM5kjNzEzW}
```

## What I learned
I understood the concept of the 'cd' command in navigating the linux filesystem.

## References 
None

# 6. Implicit relative paths, from /
This challenge asks us to execute a certain program using a relative path.  

## My solve
**Flag:** `
pwn.college{sA_F56BVy74uMxPUlSWHq6QyY0e.QX5QTN0wSM5kjNzEzW}`


```bash
hacker@paths~implicit-relative-paths-from-:~$ ~
bash: /home/hacker: Is a directory
hacker@paths~implicit-relative-paths-from-:~$ cd /
hacker@paths~implicit-relative-paths-from-:/$ challenge/run
Correct!!!
challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{sA_F56BVy74uMxPUlSWHq6QyY0e.QX5QTN0wSM5kjNzEzW}
```

## What I learned
I understood the concept of a relative path which refers to the relative position of a file with respect to the directory it is under. Relative paths are used to navigate directories based on your current location in the file system whereas an absolute path is used to navigate directly to a specific directory from the root, regardless of your current location.

## References 
https://www.geeksforgeeks.org/linux-unix/absolute-relative-pathnames-unix/



# 7. Explicit relative paths, from /
This challenge requires us to use the . operator inside the / directory to get our flag.


## My solve
**Flag:** `
pwn.college{sA_F56BVy74uMxPUlSWHq6QyY0e.QX5QTN0wSM5kjNzEzW}  `


```bash
hacker@paths~explicit-relative-paths-from-:~$ ~
bash: /home/hacker: Is a directory
hacker@paths~explicit-relative-paths-from-:~$ cd /
hacker@paths~explicit-relative-paths-from-:/$ ./challenge/./run
Correct!!!
./challenge/./run is a relative path, invoked from the right directory!
Here is your flag:
```

## What I learned
I noticed how the explicit relative path is a more precise way of looking for programs inside a directory.

## References 
None

# 8. Implictive relative path
This challenge asks us to use . operator inside the /challenge directory to get our flag.

## My solve
**Flag:** `pwn.college{4UUZA06Vfd65dJaa-2r1NkpvzL8.QXxUTN0wSM5kjNzEzW}`

```bash
hacker@paths~implicit-relative-path:~$ ~
bash: /home/hacker: Is a directory
hacker@paths~implicit-relative-path:~$ cd /challenge
hacker@paths~implicit-relative-path:/challenge$ /run
bash: /run: Is a directory
hacker@paths~implicit-relative-path:/challenge$ ./run
Correct!!!
./run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{4UUZA06Vfd65dJaa-2r1NkpvzL8.QXxUTN0wSM5kjNzEzW}
```

## What I learned
I learnt how the linux filesystem automatically avoids looking in the current directory when a naked path is provided to prevent accidental execution of programs. This is where the importance of explicit path lies, it *explicitly* tells the Linux filesystem to execute the program in the current directory

## References 
None

# 9. Home sweet home
This challenge requires us to copy the flag to /home/hacker under a set of three constraints.

## My solve
**Flag:** `pwn.college{AdlOEI47qeSdsoecuITXvu7CGkT.QXzMDO0wSM5kjNzEzW} `

Firstly, the path had to be absolute. So I started the file path with (/) which was already one character. Then, I used the (~) which represented the home directory for the challenge path to write a copy of the flag to the file named 'm'.

```bash
hacker@paths~home-sweet-home:/$ challenge/run
You must provide an argument to /challenge/run when you invoke it!
hacker@paths~home-sweet-home:/$ challenge/run ~/m
Writing the file to /home/hacker/m!
... and reading it back to you:
pwn.college{AdlOEI47qeSdsoecuITXvu7CGkT.QXzMDO0wSM5kjNzEzW}

```

## What I learned.
I learnt that files can be transferred from a different directory to the home directory using the (~) operator

## References 
None







