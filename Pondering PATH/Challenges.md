   # Challenges
1. The PATH variable
2. Setting PATH
3. Finding commands
4. Adding commands
5. Hijacking commands
   
   
# 1. The PATH variable
>This challenge makes it so that if the program can't find the rm command it gives us the flag. 

## My solve
>**Flag:** `pwn.college{cJN2__KOOkXeKU38nVt-B5hT-QD.QX3YjM1wSM5kjNzEzW}`

Without a PATH, bash cannot find the rm command. So I replaced the shell's path with a useless value.
```bash
hacker@path~the-path-variable:~$ PATH=" "
hacker@path~the-path-variable:~$ rm /challenge/run
bash: rm: command not found
hacker@path~the-path-variable:~$ /challenge/run
Trying to remove /flag...
/challenge/run: line 4: rm: command not found
The flag is still there! I might as well give it to you!
pwn.college{wlnGJm_zygIqylP-z5qtPkb7N1q.QX2cDM1wSM5kjNzEzW}
```

## What I learned 
>I learnt that there is a special shell variable called PATH that store a bunch of directory paths in which the shell will search for programs corresponding to commands. 

# 2. Setting PATH
>This challenge is an extension of the previous one where we do something useful with the PATH. 

## My solve
>**Flag:** `pwn.college{MlunExyU9zoATTANsKTItHJbdba.QX1cjM1wSM5kjNzEzW}`

```bash
hacker@path~setting-path:~$ PATH=/challenge/more_commands/
hacker@path~setting-path:~$ /challenge/run
Invoking 'win'....
Congratulations! You properly set the flag and 'win' has launched!
pwn.college{MlunExyU9zoATTANsKTItHJbdba.QX1cjM1wSM5kjNzEzW}
```

## What I learned 
>I learnt that we can set our PATH to whatever path we wish it to be, basically telling our shell to look for look in the given path while resolving plain command names.

# 3. Finding Commands 
>This challenge introduces us to the 'which' command to locate the directories of commands. 

## My solve
>**Flag:** `pwn.college{cdjrRzXIv69zlHPsbIJhmXl-uNd.01NzEzNxwSM5kjNzEzW}`

```bash
hacker@path~finding-commands:~$ which win
/challenge/paths/27930/win
hacker@path~finding-commands:~$ cat /challenge/paths/27930/win
#!/bin/bash

/bin/fold -s <<< "Search for the flag in the same directory in which I am located!"
hacker@path~finding-commands:~$ cat /challenge/paths/27930/flag
pwn.college{cdjrRzXIv69zlHPsbIJhmXl-uNd.01NzEzNxwSM5kjNzEzW}
```

## What I learned 
> I learnt that using which to find which directory our flag is located.


# 4. Adding commands

## My solve
> **Flag:** `pwn.college{A1NIsYzw_RrTWAOoqmctVLKSLTL.QX2cjM1wSM5kjNzEzW}`

```bash
hacker@path~adding-commands:~$ echo '#!/bin/bash' > win
hacker@path~adding-commands:~$ which cat
/run/dojo/bin/cat
hacker@path~adding-commands:~$ echo '/run/dojo/bin/cat /flag' >> win
hacker@path~adding-commands:~$ chmod +x win      
hacker@path~adding-commands:~$ PATH=/home/hacker 
hacker@path~adding-commands:~$ /challenge/run  
Invoking 'win'....
pwn.college{A1NIsYzw_RrTWAOoqmctVLKSLTL.QX2cjM1wSM5kjNzEzW}
hacker@path~adding-commands:~$ ^C

```

## What I learned 
> I learned how to create my own shell scripts and add them to PATH so they can be executed as commands from anywhere.

# 5. Hijacking commands 

## My solve
> **Flag:** `pwn.college{MfJFqx4mLoFVpnnJkxl7kZrLoeU.QX3cjM1wSM5kjNzEzW}`

```bash
hacker@path~hijacking-commands:~$ echo #!/bin/bash > /tmp/rm
hacker@path~hijacking-commands:~$ echo /bin/cat /flag>> /tmp/rm
hacker@path~hijacking-commands:~$ chmod +x /tmp/rm
hacker@path~hijacking-commands:~$ PATH=/tmp
hacker@path~hijacking-commands:~$ /challenge/run
Trying to remove /flag...
pwn.college{MfJFqx4mLoFVpnnJkxl7kZrLoeU.QX3cjM1wSM5kjNzEzW}
```

## What I learned 
> I learned that by creating a fake version of a command (like rm) and placing it in a directory thats earlier in the PATH, I can substitute the actual command


