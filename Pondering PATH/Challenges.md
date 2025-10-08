# Challenges
1. The PATH variable
2. Setting PATH
3. Finding commands
4. Adding commands
5. Hijacking commands
   
   
# 1. The PATH variable
This challenge makes it so that if the program can't find the rm command it gives us the flag. 

## My solve
**Flag:** `pwn.college{cJN2__KOOkXeKU38nVt-B5hT-QD.QX3YjM1wSM5kjNzEzW}`

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
I learnt that there is a special shell variable called PATH that store a bunch of directory paths in which the shell will search for programs corresponding to commands. 

