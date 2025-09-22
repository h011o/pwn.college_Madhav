# Challenges
1. Intro To Commands
2. Intro to Arguments
3. Command History
   
# 1. Intro to Commands
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

# 2. Intro to Arguments
This challenge requires you to use the hello command with an argument.
## My solve
**Flag:** `pwn.college{UUwUeA_68O6TltOKivTFhM1-4cV.QX4YjM1wSM5kjNzEzW}`
``` bash 
hacker@hello~intro-to-arguments:~$ echo Hello
Hello
hacker@hello~intro-to-arguments:~$ hello
It looks like you've invoked this command without an argument. Please invoke 
this with a single argument of 'hackers'!
hacker@hello~intro-to-arguments:~$ hello hackers
Success! Here is your flag:
pwn.college{UUwUeA_68O6TltOKivTFhM1-4cV.QX4YjM1wSM5kjNzEzW}
```

## What I learned 
I learnt about the echo command which functions similar to the print statement. It can take in multiple arguments and display them in the terminal.

# 3.  Command History
This challenge requires you to use the command history feautre to retrieve the flag from the memory of the terminal.

## My solve
**Flag:** `pwn.college{83_2T5ZDt_PtgxygGWBnp2dmb8n.0lNzEzNxwSM5kjNzEzW}`
``` bash
hacker@hello~command-history:~$ the flag is pwn.college{83_2T5ZDt_PtgxygGWBnp2dmb8n.0lNzEzNxwSM5kjNzEzW}
```

## What I learned
I learnt how using the arrow keys, we can easily get past commands used in the terminal, which makes it really useful in situations with repetitive commands.

## References 
None

