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
In this challenge, you must use the output redirection to write the word PWN.

## My solve
**Flag:** `pwn.college{M8DyuELHvy35ijqdQnCqRs7X9AP.QX0YTN0wSM5kjNzEzW}`
```bash
hacker@piping~redirecting-output:~$ echo PWN > COLLEGE
Correct! You successfully redirected 'PWN' to the file 'COLLEGE'! Here is your 
flag:pwn.college{M8DyuELHvy35ijqdQnCqRs7X9AP.QX0YTN0wSM5kjNzEzW}
```

## What I learned 
I learnt how we can use the '>' operator to redirect a specific output to a single command. This is done using the echo command.
