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
I realized that programs cannot be executed directly from their path before accessing its directory. I also understood how useful the 'cd' command is in navigating the linux filesystem.

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

## What I learned
I noticed how the output said /challenge/run is an absolute path.

## References 
None

# 5. Position elsewhere
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

## What I learned
I noticed how the output said /challenge/run is an absolute path.

## References 
None

