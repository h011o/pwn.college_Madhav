# Challenges
1. Chaining with semicolons
2. Building on Success
3. Handling failure
4. Your first shell script
5. Redirecting script output
6. Executable shell scripts
7. Understanding shebangs
8. Scripting with arguments
9. Scripting with Conditionals
10. Scripting with Default cases
11. Scripting with multiple conditions
12. Reading shell scripts


# 1.Chaining with semicolons
> This challenge needs us to chain semicolons/challenge/pwn and then /challenge/college.

## My solve
**Flag:** `pwn.college{Qaapr8sgMn-xJU0xXDHR6wCXXZj.QX1UDO0wSM5kjNzEzW}`

```bash
hacker@chaining~chaining-with-semicolons:~$ /challenge/pwn; /challenge/college
Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:
pwn.college{Qaapr8sgMn-xJU0xXDHR6wCXXZj.QX1UDO0wSM5kjNzEzW}
```

## What I learned
> The semicolon basically tells the terminal to consider the following command to execute seperately.



# 2. Building on Success 
> In this challenge, you need to chain the programs /challenge/first-success and /challenge/second using the && operator.

## My solve
**Flag:** `pwn.college{864Dyai4nL-mCE4kzJHrmcl7DcT.0lM0MDOxwSM5kjNzEzW}`
 
```bash
hacker@chaining~building-on-success:~$ /challenge/first-success && /challenge/second
Nice chaining! Flag: pwn.college{864Dyai4nL-mCE4kzJHrmcl7DcT.0lM0MDOxwSM5kjNzEzW}
```

## What I learned
> The && operator works similarly in Linux like it does so in other programming languages.

# 3. Handling failure
> In this challenge, you need to chain /challenge/first-failure and /challenge/second using the || operator.

## My solve
**Flag:** `pwn.college{MXiVfvqxiMRVqsUzNYYEXGRJLG6.01M0MDOxwSM5kjNzEzW}`
 
```bash
hacker@chaining~handling-failure:~$ /challenge/first-failure || /challenge/second
Nice chaining! Flag: pwn.college{MXiVfvqxiMRVqsUzNYYEXGRJLG6.01M0MDOxwSM5kjNzEzW}
```

## What I learned
> The || operator works similarly in Linux like it does so in other programming languages. (like the 'OR' operator)

# 4. Your First Shell Script
> Same as last level, run /challenge/pwn and then /challenge/college, but this time in a shell script called x.sh, then run it with bash

## My solve
**Flag:** `pwn.college{wR6qmlAum_kheTYhm12wyjpxoZo.QXxcDO0wSM5kjNzEzW}`

Here I made the mistake of initially using > for both the programs. I then realized it and appended second program with >> and created the file with the first one. 
```bash
hacker@chaining~your-first-shell-script:~$ echo /challenge/pwn > x.sh
hacker@chaining~your-first-shell-script:~$ echo /challenge/college > x.sh
hacker@chaining~your-first-shell-script:~$ bash x.sh
You must first call the '/challenge/pwn' command, not '/challenge/college'!
hacker@chaining~your-first-shell-script:~$ echo /challenge/pwn > x.sh
hacker@chaining~your-first-shell-script:~$ echo /challenge/college >> x.sh
hacker@chaining~your-first-shell-script:~$ bash x.sh
Great job, you've written your first shell script! Here is the flag:
pwn.college{wR6qmlAum_kheTYhm12wyjpxoZo.QXxcDO0wSM5kjNzEzW}
```

## What I learned
> The shell script saves us time instead of having to run commands over and over.

# 5. Redirecting Script output 
> This challenge teaches us to send the output of several programs to one command.

## My solve
**Flag:** `pwn.college{wsEtEDuaKZLIuuFgq8OqAOxHmQu.QX4ETO0wSM5kjNzEzW}`

```bash
hacker@chaining~redirecting-script-output:~$ echo /challenge/pwn > script.sh
hacker@chaining~redirecting-script-output:~$ echo /challenge/college >> script.sh
hacker@chaining~redirecting-script-output:~$ bash script.sh | /challenge/solve
Correct! Here is your flag:
pwn.college{wsEtEDuaKZLIuuFgq8OqAOxHmQu.QX4ETO0wSM5kjNzEzW}
```

## What I learned
> In this challenge I learned how to combine shell scripts with piping.

# 5. Redirecting Script output 
> This challenge teaches us to send the output of several programs to one command.

## My solve
**Flag:** `pwn.college{wsEtEDuaKZLIuuFgq8OqAOxHmQu.QX4ETO0wSM5kjNzEzW}`

```bash
hacker@chaining~redirecting-script-output:~$ echo /challenge/pwn > script.sh
hacker@chaining~redirecting-script-output:~$ echo /challenge/college >> script.sh
hacker@chaining~redirecting-script-output:~$ bash script.sh | /challenge/solve
Correct! Here is your flag:
pwn.college{wsEtEDuaKZLIuuFgq8OqAOxHmQu.QX4ETO0wSM5kjNzEzW}
```

## What I learned
> The challenge teaches us to combine shell scripts with piping.

# 6. Executable Shell scripts 
> This challenge needs us to execute our shell script without explicitly calling bash.

## My solve
**Flag:** ``

```bash

```

## What I learned
>










