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
> I learnt that we can set our PATH to whatever path we wish it to be, basically telling our shell to look for look in the given path while resolving plain command names.


# 4. Adding commands
>  

## My solve
>**Flag:** ``

```bash

```

## What I learned 
>

# 5. Hijacking commands 
>  

## My solve
>**Flag:** ``

```bash

```

## What I learned 
>


