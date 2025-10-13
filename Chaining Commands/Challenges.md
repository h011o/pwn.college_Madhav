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


# 6. Executable Shell scripts 
> This challenge needs us to execute our shell script without explicitly calling bash.

## My solve
**Flag:** `pwn.college{MMvqK5wGUOBvYqD5PyWa4mZo8Xw.QX0cjM1wSM5kjNzEzW}`

```bash
hacker@chaining~executable-shell-scripts:~$ echo /challenge/solve > script.sh
hacker@chaining~executable-shell-scripts:~$ chmod +x script.sh
hacker@chaining~executable-shell-scripts:~$ ./script.sh
Congratulations on your shell script execution! Your flag:
pwn.college{MMvqK5wGUOBvYqD5PyWa4mZo8Xw.QX0cjM1wSM5kjNzEzW}

```
## What I learned
> we can make a shell script directly executeable by using the +chmod x command.

# 7. Understand shebangs 
> This challenge introduces us to shebangs.

## My solve
**Flag:** `pwn.college{kIROo5ajgnCqpNQANRobd_L8bW8.0VOzMDOxwSM5kjNzEzW}`

```bash
hacker@chaining~understanding-shebangs:~$ echo #!/bin/bash > /home/hacker/solve.sh
hacker@chaining~understanding-shebangs:~$ echo  'echo "hack the planet"' >> /home/hacker/solve.sh
hacker@chaining~understanding-shebangs:~$ chmod a+x /home/hacker/solve.sh
hacker@chaining~understanding-shebangs:~$ /challenge/run
Testing your script...
Perfect! Your flag:
Flag: pwn.college{kIROo5ajgnCqpNQANRobd_L8bW8.0VOzMDOxwSM5kjNzEzW}

```
## What I learned
> What shebang basically does is tell the terminal inststructions on how how to run the script.
> #!/bin/bash means use bash to run this script

# 8. Scripting with arguments
> This challenge teaches us how to accept arguments

## My solve
**Flag:** `pwn.college{kIROo5ajgnCqpNQANRobd_L8bW8.0VOzMDOxwSM5kjNzEzW}`

```bash
hacker@chaining~scripting-with-arguments:~$ echo #!/bin/bash > /home/hacker/solve.sh
hacker@chaining~scripting-with-arguments:~$ echo echo "$2 $1" >> /home/hacker/solve.sh
hacker@chaining~scripting-with-arguments:~$ chmod a+x /home/hacker/solve.sh
hacker@chaining~scripting-with-arguments:~$ /challenge/run
Correct! Your script properly reversed the arguments.
Here's your flag:
pwn.college{Q19PlaNSQXemM4EQOvA1k4ouHl0.0VNzMDOxwSM5kjNzEzW}

```
## What I learned
> I learned how we can integrate arguments with scripts alongside shebang


# 9. Scripting with conditionals

## My solve
**Flag:** `pwn.college{EgAhCEEe-w_Nk2-sTPwL_6cYefe.0lNzMDOxwSM5kjNzEzW}`

```bash
hacker@chaining~scripting-with-conditionals:~$ echo '#!/bin/bash' > /home/hacker/solve.sh
hacker@chaining~scripting-with-conditionals:~$ echo 'if [ "$1" == "pwn" ]' >> /home/hacker/solve.sh
hacker@chaining~scripting-with-conditionals:~$ echo 'then' >> /home/hacker/solve.sh
hacker@chaining~scripting-with-conditionals:~$ echo '  echo "college"' >> /home/hacker/solve.sh
hacker@chaining~scripting-with-conditionals:~$ echo 'fi' >> /home/hacker/solve.sh
hacker@chaining~scripting-with-conditionals:~$ chmod a+x /home/hacker/solve.sh
hacker@chaining~scripting-with-conditionals:~$ /challenge/run
Correct! Your script properly handles all the conditions.
Here's your flag:
pwn.college{EgAhCEEe-w_Nk2-sTPwL_6cYefe.0lNzMDOxwSM5kjNzEzW}

```
## What I learned
> I learned how we can use conditional logic in our arguments.
> I also learned to use the following syntax while using conditonals in linux:
> There has to be a space after if, after '[' and before ']'.
> if then and fi must all be in different lines 

# 10. Scripting with Default cases 

## My solve
**Flag:** `pwn.college{Q19PlaNSQXemM4EQOvA1k4ouHl0.0VNzMDOxwSM5kjNzEzW}`

```bash
hacker@chaining~scripting-with-default-cases:~$ echo #!/bin/bash > /home/hacker/solve.sh
hacker@chaining~scripting-with-default-cases:~$ echo if [ "$1" = "pwn" ] >> /home/hacker/solve.sh
hacker@chaining~scripting-with-default-cases:~$ echo then >> /home/hacker/solve.sh
hacker@chaining~scripting-with-default-cases:~$ echo echo "college" >> /home/hacker/solve.sh
hacker@chaining~scripting-with-default-cases:~$ echo else >> /home/hacker/solve.sh
hacker@chaining~scripting-with-default-cases:~$ echo echo "nope" >> /home/hacker/solve.sh
hacker@chaining~scripting-with-default-cases:~$ echo fi >> /home/hacker/solve.sh
hacker@chaining~scripting-with-default-cases:~$ chmod +x /home/hacker/solve.sh
hacker@chaining~scripting-with-default-cases:~$ /challenge/run
Correct! Your script properly handles the if/else conditions.
Here's your flag:
pwn.college{wQlkjQ7cmiV6yGItMzVVqGRmzqn.01NzMDOxwSM5kjNzEzW}

```
## What I learned
> I learned how we can use the else statement along with the if in linux.

# 11. Scripting with Multiple Condtions

## My solve
**Flag:** `pwn.college{Q19PlaNSQXemM4EQOvA1k4ouHl0.0VNzMDOxwSM5kjNzEzW}`

```bash
hacker@chaining~scripting-with-multiple-conditions:~$ echo #!/bin/bash > /home/hacker/solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ echo if [ "$1" = "hack" ] >> /home/hacker/solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ echo then >> /home/hacker/solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ echo echo "the planet" >> /home/hacker/solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ echo elif [ "$1" = "pwn" ] >> /home/hacker/solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ echo then >> /home/hacker/solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ echo echo "college" >> /home/hacker/solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ echo elif [ "$1" = "learn" ] >> /home/hacker/solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ echo then >> /home/hacker/solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ echo  echo "linux" >> /home/hacker/solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ echo else >> /home/hacker/solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ echo echo "unknown" >> /home/hacker/solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ echo fi >> /home/hacker/solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ chmod +x /home/hacker/solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ /challenge/run
Correct! Your script properly handles all the conditions with elif.
Here's your flag:
pwn.college{wseNDwsCR-XSJP1wx1ZZmSXpkea.0FOzMDOxwSM5kjNzEzW}

```
## What I learned
> I learned how we can use elif for multiple conditions in linux.


# 12. Reading Shell scripts 

## My solve
**Flag:** `pwn.college{cwXwmwPQQAxWDmHPjBEb1htMy0u.0lMwgDOxwSM5kjNzEzW}`

```bash
hacker@chaining~reading-shell-scripts:~$ cat /challenge/run
#!/opt/pwn.college/bash

read GUESS
if [ "$GUESS" == "hack the PLANET" ]
then
        echo "CORRECT! Your flag:"
        cat /flag
else
        echo "Read the /challenge/run file to figure out the correct password!"
fi
hacker@chaining~reading-shell-scripts:~$ echo "hack the PLANET" | /challenge/run
CORRECT! Your flag:
pwn.college{cwXwmwPQQAxWDmHPjBEb1htMy0u.0lMwgDOxwSM5kjNzEzW}
```
## What I learned
> I learned how to read shell scripts(/challenge/run in this challenge).











