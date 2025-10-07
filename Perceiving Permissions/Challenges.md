# Challenges
1. Changing file ownership
2. Groups and Files
3. Fun with group names
4. Changing permissions
5. Executable files
6. Permission tweaking process
7. Permissions setting practice
8. The SUIT bit
   
# 1. Changing file ownership
> This challenge teaches us how to change the ownership of a file to help us read it.

## My solve
**Flag:** `pwn.college{wlWo7oNaq-Z2-9zU2Xi2hVNfFWh.QXxEjN0wSM5kjNzEzW}`
```bash
hacker@permissions~changing-file-ownership:~$ chown hacker /flag
hacker@permissions~changing-file-ownership:~$ cat /flag
pwn.college{wlWo7oNaq-Z2-9zU2Xi2hVNfFWh.QXxEjN0wSM5kjNzEzW}
```

## What I learned 
> I learnt how the chown command can be used to change the owner of the file and help us access it,
> Syntax: chown [username] [file]

# 2. Groups and Files
> This challenge requires us to change the group ownership of the flag file and read the flag. 

## My solve
**Flag:** ``
```bash

```

## What I learned 
> I learned how we can check what groups we are a part of using the 'id' command. 


