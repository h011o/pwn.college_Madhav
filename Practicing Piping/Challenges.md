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
I learnt how we can use the '>' operator to redirect a specific output to a single command. This is done using the echo command.

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
In this challenge, you must use the output redirection to write the word PWN.

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



