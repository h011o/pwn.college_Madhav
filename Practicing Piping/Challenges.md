# Challenges
1. Redirecting output
2. Redirecting more output
3. Appending output
4. Redirecting errors
5. Redirecting input
6. Grepping stored results
7. Grepping live output
8. Grepping errors
9. Filtering with grep -v
10. Duplicating piped data with tee
11. Process substitution for input
12. Writing to multiple programs
13. Split-piping stderr and stdout
14. Named pipes 
   
# 1. Redirecting output
This challenge asks you to invoke the hello command to get the flag.

## My solve
**Flag:** `pwn.college{cJN2__KOOkXeKU38nVt-B5hT-QD.QX3YjM1wSM5kjNzEzW}`
```bash
hacker@hello~intro-to-commands:~$ whoami
hacker
hacker@hello~intro-to-commands:~$ Hello
bash: Hello: command not found
hacker@hello~intro-to-commands:~$ hello
Success! Here is your flag:
pwn.college{cJN2__KOOkXeKU38nVt-B5hT-QD.QX3YjM1wSM5kjNzEzW}
```

## What I learned 
I learnt how the promt for the linux terminal is written as **username@hostname:~$**, where the $ symbol means that the user does not have administrative privileges whereas the # symbol means the user is an administrator. I also learnt how linux is case sensitive which means Hello does not provide the same output as hello does.

## References 
None
