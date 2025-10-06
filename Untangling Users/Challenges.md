# Challenges
1. Becoming root with su
2. Other users with su
3. Cracking passwords
4. Using sudo
   
# 1. Becoming root with su
> This challenge teaches us how to become root using the su (substitute user) command. 

## My solve
**Flag:** ``
```bash

```

## What I learned 
> I learned how older systems used to have root passwords which were used to access the root upon using the su command.

# 2. Other users with su 
> This challenge needs to become user zaradus to get our flag.

## My solve
**Flag:** `pwn.college{g2jHTfoARIkRhbs7Nb_r7zPnAB6.QX2UDN1wSM5kjNzEzW}`

```bash
hacker@users~other-users-with-su:~$ su zardus
Password: 
zardus@users~other-users-with-su:/home/hacker$ /challengr/un
bash: /challengr/un: No such file or directory
zardus@users~other-users-with-su:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{g2jHTfoARIkRhbs7Nb_r7zPnAB6.QX2UDN1wSM5kjNzEzW}
```

## What I learned 
> I learned how we can switch to other users in the terminal using the su command. 



   

