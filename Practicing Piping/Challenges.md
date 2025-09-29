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
In this challenge, you must use output redirection to write the word PWN into COLLEGE.

## My solve
**Flag:** `pwn.college{M8DyuELHvy35ijqdQnCqRs7X9AP.QX0YTN0wSM5kjNzEzW}`
```bash
hacker@piping~redirecting-output:~$ echo PWN > COLLEGE
Correct! You successfully redirected 'PWN' to the file 'COLLEGE'! Here is your 
flag:pwn.college{M8DyuELHvy35ijqdQnCqRs7X9AP.QX0YTN0wSM5kjNzEzW}
```

## What I learned 
I learnt how we can use the '>' operator to redirect a specific output to a single command. 
The data present on the left of the > operator is directed to its right.

# 2. Redirecting more output
In this challenge, you must use the output redirection to redirect the path of /challenge/run to get our flag.

## My solve
**Flag:** `pwn.college{03llq2KMm6sxqQTgoWKLhT6o6dS.QX1YTN0wSM5kjNzEzW}`
```bash
hacker@piping~redirecting-more-output:~$ /challenge/run > myflag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~redirecting-more-output:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{03llq2KMm6sxqQTgoWKLhT6o6dS.QX1YTN0wSM5kjNzEzW}
```

## What I learned 
I learnt how the '>' operator can also be used to redirect a path to a command.

# 3. Appending output
This challenge teaches us about the appending mode for output redirection.

## My solve
**Flag:** `pwn.college{wg0iBIFrHRC72aEFiCg4gBvH53a.QX3ATO0wSM5kjNzEzW}`

The challenge asks us to redirect to *stdout* to get the second half of the file but I wasn't sure on how exactly to do that. I first did /challenge/run >> stdout which gave me an error. Then upon re-reading I saw that stdout is a **channel**. Everytime I output a file linux gives the output through stdout. Then I used cat to get the flag.
```bash
hacker@piping~appending-output:~$ /challenge/run >> /home/hacker/the-flag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /home/hacker/the-flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] Good luck!

[TEST] You should have redirected my stdout to a file called /home/hacker/the-flag. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
I will write the flag in two parts to the file /home/hacker/the-flag! I'll do 
the first write directly to the file, and the second write, I'll do to stdout 
(if it's pointing at the file). If you redirect the output in append mode, the 
second write will append to (rather than overwrite) the first write, and you'll 
get the whole flag!
hacker@piping~appending-output:~$ cat /home/hacker/the-flag
 | 
\|/ This is the first half:
 v 
pwn.college{wg0iBIFrHRC72aEFiCg4gBvH53a.QX3ATO0wSM5kjNzEzW}
                              ^
     that is the second half /|\
                              |

If you only see the second half above, you redirected in *truncate* mode (>) 
rather than *append* mode (>>), and so the write of the second half to stdout 
overwrote the initial write of the first half directly to the file. Try append 
mode!
```

## What I learned 
> will create a new output file every time, deleting the old contents. A workaround to this is to use >> to redirect data.

# 4. Redirecting errors 
This challenge teaches us about file descriptors.

## My solve
**Flag:** `pwn.college{Ekqs_EXB7n1y5fMFjjQPUSaPKYq.QX3YTN0wSM5kjNzEzW}`
```bash
hacker@piping~redirecting-errors:~$ /challenge/run > myflag 2> instructions
hacker@piping~redirecting-errors:~$ cat instructions
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will check that error output is redirected to a specific file path : instructions
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!

[TEST] You should have redirected my stderr to instructions. Checking...

[PASS] The file at the other end of my stderr looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~redirecting-errors:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{Ekqs_EXB7n1y5fMFjjQPUSaPKYq.QX3YTN0wSM5kjNzEzW}
```

## What I leared
A File Descriptor (FD) is a number that describes a communication channel in Linux. 
FD 0: Standard Input
FD 1: Standard Output
FD 2: Standard Error
We use these numbers to redirect data to their specific channels before the > 

# 5. Redirecting input
> This challenge needs us to direct input to programs.

## My solve
**Flag:** `pwn.college{4ZNrYkIZb7Ymx5clx5WbIH8Jfzg.QXwcTN0wSM5kjNzEzW}`

```bash
hacker@piping~redirecting-input:~$ /challenge/run > PWN
hacker@piping~redirecting-input:~$ /challenge/run < PWN
Reading from standard input...
Your PWN file must have the value 'COLLEGE', but I instead read: You have not 
redirected anything to my standard input. Please do so, using '<'.
hacker@piping~redirecting-input:~$ COLLEGE > PWN
bash: COLLEGE: command not found
hacker@piping~redirecting-input:~$ echo COLLEGE > PWN
hacker@piping~redirecting-input:~$ /challenge/run < PWN
Reading from standard input...
Correct! You have redirected the PWN file into my standard input, and I read 
the value 'COLLEGE' out of it!
Here is your flag:
pwn.college{4ZNrYkIZb7Ymx5clx5WbIH8Jfzg.QXwcTN0wSM5kjNzEzW}
```

## What I learned 
> I learned how using < we can read input that was redirected into the program.

# 6. Grepping stored results
> This challenge needs us to redirect the output of /challenge/run and grep to find our flag. 

## My solve
**Flag:** `pwn.college{8Ptq3NiCIqMdixfiGI36piAmAO-.QX4EDO0wSM5kjNzEzW}`

```bash
hacker@piping~grepping-stored-results:~$ /challenge/run > /tmp/data.txt
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /tmp/data.txt
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to a file called /tmp/data.txt. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~grepping-stored-results:~$ grep pwn.college /tmp/data.txt
pwn.college{8Ptq3NiCIqMdixfiGI36piAmAO-.QX4EDO0wSM5kjNzEzW}
```

## What I learned 
> I realized how practically useful output redirection can be. We can basically use this to redirect only specific data to a different file using grep.

# 7. Grepping live output
> This challenge introduces us to the pipe operator .

## My solve
**Flag:** `pwn.college{89KI9igYsuiHIt8_guojUkFhi0c.QX5EDO0wSM5kjNzEzW}`

They asked us to connect the standard output of the command from the left of the pipe to the right of the pipe. So I catted the /challenge/run program but it did not result in anything, then I realized we had to pipe the output of the *program* to the input grep.
```bash
hacker@piping~grepping-live-output:~$ cat /challenge/run | grep pwn.college
#!/opt/pwn.college/bash
hacker@piping~grepping-live-output:~$ /challenge/run | grep pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stdout : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/8b4vn1iyn6kqiisjvlmv67d1c0p3j6wj-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stdout!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{89KI9igYsuiHIt8_guojUkFhi0c.QX5EDO0wSM5kjNzEzW}
```

## What I learned
> Standard output from the command to the left of the pipe will be connected to the standard input of the command to the right of the pipe. Pipe can be used to reduce the lines required to complete a task.

# 8. Grepping errors 
This challenge introduces us to the concept of error grepping, similar to error redirection using file descriptor (2>)

## My solve
**Flag:** `pwn.college{YKT6fEtYXvd6c7BLoEjvIyOF9hj.QX1ATO0wSM5kjNzEzW}`
```bash
hacker@piping~grepping-errors:~$ ls
COLLEGE  COLLEGWE  PWN  f  instructions  myflag  stdout  the-flag
hacker@piping~grepping-errors:~$ /challenge/run 2>& 1
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stderr : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stderr to another process. Checking...

[FAIL] You did not satisfy all the execution requirements.
[FAIL] Specifically, you must fix the following issue:
[FAIL]   stderr of this process does not appear to be a pipe!
hacker@piping~grepping-errors:~$ /challenge/run 2>& 1 | grep pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stderr : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stderr to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/8b4vn1iyn6kqiisjvlmv67d1c0p3j6wj-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stderr!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{YKT6fEtYXvd6c7BLoEjvIyOF9hj.QX1ATO0wSM5kjNzEzW}
```

## What I learned 
> Errors are redirected using 2>, which I already knew. BUT | redirects only standard *output* therefore I need to redirect the standard error to standard output first and THEN I must again redirect to required input.

# 9. Filtering with grep -v
> This challenge teaches us about invert match using grp. 

## My solve
**Flag:** `pwn.college{8CcaoaMMyfYnAIDmLTHimtmK9nZ.0FOxEzNxwSM5kjNzEzW}`

what I did initally was /challenge/run | grep -v DECOY which resulted in multiple errors of the form: 
/challenge/run: line 14: echo: write error: Broken pipe
tr: write error: Broken pipe
/challenge/run: line 16: echo: write error: Broken pipe
This was because I forgot to quote "DECOY".
```bash
hacker@piping~filtering-with-grep-v:~$ /challenge/run | grep -v "DECOY"
pwn.college{8CcaoaMMyfYnAIDmLTHimtmK9nZ.0FOxEzNxwSM5kjNzEzW}
hacker@piping~filtering-with-grep-v:~$ 
```

## What I learned 
grep-v is used to remove specific content from the data of a file, so it works sort of like a filter for our pipe. 

# 10. Duplicated piped data with tee
> This challenge introduces us to the tee command and helps us understand why its useful. 

## My solve
**Flag:** `pwn.college{0IXu2vdmiMXq9B0HJeClsBXWudg.QXxITO0wSM5kjNzEzW}`

Here I created the flag spy to "intercept" the data piped from pwn to college. Then I output the tee file to read the required argument to run our pwn command.
```bash
hacker@piping~duplicating-piped-data-with-tee:~$ touch spy
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn | tee spy | /challenge/college
Processing...
WARNING: you are overwriting file spy with tee's output...
The input to 'college' does not contain the correct secret code! This code 
should be provided by the 'pwn' command. HINT: use 'tee' to intercept the 
output of 'pwn' and figure out what the code needs to be.
hacker@piping~duplicating-piped-data-with-tee:~$ cat tee
cat: tee: No such file or directory
hacker@piping~duplicating-piped-data-with-tee:~$ cat spy
Usage: /challenge/pwn --secret [SECRET_ARG]

SECRET_ARG should be "0IXu2vdm"
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn --secret [0IXu2vdm]
Processing...
You must pipe the output of /challenge/pwn into /challenge/college (or 'tee' 
for debugging).
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn --secret 0IXu2vdm | tee spy | /challenge/college
Processing...
WARNING: you are overwriting file spy with tee's output...
Correct! Passing secret value to /challenge/college...
Great job! Here is your flag:
```

## What I learned 
Tee is like the t-splitter in pipes, basically - this command duplicates data flowing through our pipes to any number of files provided. And helps us *see* the data as it flows through betwen commands  

# 11. Process substitution for input
> Here we learn about the elegant process substitution 

## My solve
**Flag:** `pwn.college{MCw-WbhzP4EHqqKvFtSmqfRQM9d.0lNwMDOxwSM5kjNzEzW}`

In this challenge I used process substitution to create temporary files to compare. First I directly compared the temporary files, this did not work because temporary files only exist for the duration the command runs, and resulted in a broken pipe.
```bash
hacker@piping~process-substitution-for-input:~$ echo <( echo /challenge/print_decoys) <(echo /challenge/print_decoys_and_flag)
/dev/fd/63 /dev/fd/62
bash: echo: write error: Broken pipe
hacker@piping~process-substitution-for-input:~$ diff /dev/fd/63 /dev/fd/62
diff: /dev/fd/63: No such file or directory
diff: /dev/fd/62: No such file or directory
hacker@piping~process-substitution-for-input:~$ diff <(/challenge/print_decoys) <(/challenge/print_decoys_and_flag)
80a81
> pwn.college{MCw-WbhzP4EHqqKvFtSmqfRQM9d.0lNwMDOxwSM5kjNzEzW}
```

## What I learned 
Process substitution in Linux is important because it allows commands to be treated as files, enabling more flexible and efficient operations without creating temporary files. 





