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

# 3. Cracking passwords 
> This challenge needs us to use  John the Ripper,

## My solve
**Flag:** `pwn.college{g2jHTfoARIkRhbs7Nb_r7zPnAB6.QX2UDN1wSM5kjNzEzW}`

This challenge needs us to crack a leak of /etc/shadow (where passwords are stored). We use the ripper to 
```bash
hacker@users~cracking-passwords:~$ john /challenge/shadow-leak
Loaded 1 password hash (crypt, generic crypt(3) [?/64])
Press 'q' or Ctrl-C to abort, almost any other key for status
0g 0:00:00:09 93% 1/3 0g/s 282.0p/s 282.0c/s 282.0C/s zardus999992002..zardus1963
0g 0:00:00:12 0% 2/3 0g/s 283.3p/s 283.3c/s 283.3C/s brenda..keith
0g 0:00:00:14 0% 2/3 0g/s 283.8p/s 283.8c/s 283.8C/s serena..88888888
aardvark         (zardus)
1g 0:00:00:20 100% 2/3 0.04878g/s 284.0p/s 284.0c/s 284.0C/s Johnson..buzz
Use the "--show" option to display all of the cracked passwords reliably
Session completed
hacker@users~cracking-passwords:~$ john --show /challenge/shadow-leak
hacker:NO PASSWORD:20357:0:99999:7:::
zardus:aardvark:20367:0:99999:7:::

2 password hashes cracked, 0 left
hacker@users~cracking-passwords:~$ su zardus
Password: 
zardus@users~cracking-passwords:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{AwFqLAA7n1cou7PCZ-Z5kKOZpvf.QX3UDN1wSM5kjNzEzW}
```

## What I learned 
> If a hacker gets their hands on a leaked /etc/shadow, they can start cracking passwords and wreaking havoc. 



   

