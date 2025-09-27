# Challenges
1. Matching with *
2. Matching with ?
3. Matching with []
4. Matching paths with []
5. Multiple globs
6. Mixing globs
7. Exclusionary globbing
8. Tab completion
9. Multiple options for tab completion
10. Tab completion on commands 


# 1. Matching with *
> This challenge asks us to use the concept of globbing to change directories under a 4 character limit.

## My solve
**Flag:** `pwn.college{c5IDwk0qKsF2c5FYaiJFhrYRjy2.QXxIDO0wSM5kjNzEzW}  `


```bash
hacker@globbing~matching-with-:~$ cd /challenge
You specified the path to 'cd' to in more than 4 characters. Disallowed!
This challenge resets your working directory to /home/hacker unless you change 
directory properly...
This challenge resets your working directory to /home/hacker unless you change 
directory properly...
hacker@globbing~matching-with-:~$ cd /ch*
hacker@globbing~matching-with-:/challenge$ /run
bash: /run: Is a directory
hacker@globbing~matching-with-:/challenge$ run
bash: run: command not found
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{c5IDwk0qKsF2c5FYaiJFhrYRjy2.QXxIDO0wSM5kjNzEzW}
hacker@globbing~matching-with-:/challenge$ ^C
```

## What I learned
'globbing' means using wildcard patterns to match filenames. The glob works sort of like an 'autocomplete' feautre that matches the incomplete filename with existing ones.

# 2. Matching with ?
> This challenge introduces us to globbing patterns using '?' 

## My solve
**Flag:** `pwn.college{wFbj0yDrZo_0S2uyB0VK_5AAScJ.QXyIDO0wSM5kjNzEzW}`
 
```bash
This challenge resets your working directory to /home/hacker unless you change 
directory properly...
This challenge resets your working directory to /home/hacker unless you change 
directory properly...
hacker@globbing~matching-with-:~$ cd /challenge
You used either the 'c', 'l', or '*' characters. Disallowed!
This challenge resets your working directory to /home/hacker unless you change 
directory properly...
This challenge resets your working directory to /home/hacker unless you change 
directory properly...
hacker@globbing~matching-with-:~$ cd /?ha*
You used either the 'c', 'l', or '*' characters. Disallowed!
This challenge resets your working directory to /home/hacker unless you change 
directory properly...
This challenge resets your working directory to /home/hacker unless you change 
directory properly...
hacker@globbing~matching-with-:~$ cd /?h???enge
hacker@globbing~matching-with-:/challenge$ /?h???enge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{wFbj0yDrZo_0S2uyB0VK_5AAScJ.QXyIDO0wSM5kjNzEzW}
```
## What I learned
> '?' works like '*' but only 'autocompletes' one character. 

# 3. Matching with []
> This challenge teaches us about globbing patterns using [].

## My solve
**Flag:** `pwn.college{k8otPrcHJecK67Bjn4mAHYmTxl4.QXzIDO0wSM5kjNzEzW}`

```bash
hacker@globbing~matching-with-:~$ cd /challenge/files
hacker@globbing~matching-with-:/challenge/files$ /challenge/run
Error: you did not use a square bracket glob...
hacker@globbing~matching-with-:/challenge/files$ ls /challenge/run
/challenge/run
hacker@globbing~matching-with-:/challenge/files$ /challenge/run file_[bash]
You got it! Here is your flag!
pwn.college{k8otPrcHJecK67Bjn4mAHYmTxl4.QXzIDO0wSM5kjNzEzW}
```

## What I learned
[] is a wildcard for a subset of potential characters to fill in for ? . So its like an autocomplete for characters that exist only within the given subset. The required characters are specified inside the [] without commas or spaces.

# 4. Matching paths with []
> This challenge requires us to use the previous concept to match paths and aquire the flag.

## My solve
**Flag:** `pwn.college{8d-yIYGtZ6rfg_B4n3tE55V5JkN.QX0IDO0wSM5kjNzEzW}`

After a lot of trial and error, I figured out 
```bash
hacker@globbing~matching-paths-with-:~$ /challenge/files
bash: /challenge/files: Is a directory
hacker@globbing~matching-paths-with-:/challenge/files$ /challenge/run/file_[bash]
bash: /challenge/run/file_[bash]: Not a directory
hacker@globbing~matching-paths-with-:/challenge/files$ ls
file_a  file_c  file_e  file_g  file_i  file_k  file_m  file_o  file_q  file_s  file_u  file_w  file_y
file_b  file_d  file_f  file_h  file_j  file_l  file_n  file_p  file_r  file_t  file_v  file_x  file_z
hacker@globbing~matching-paths-with-:/challenge/files$ cd
hacker@globbing~matching-paths-with-:~$ ~/challenge/run/file_[bash]
bash: /home/hacker/challenge/run/file_[bash]: No such file or directory
hacker@globbing~matching-paths-with-:~$ /challenge/run
Error: you did not use a square bracket glob...
hacker@globbing~matching-paths-with-:~$ /challenge/run file_[bash]
Error: you will need to specify the path to the files as part of your glob 
argument, since they are in a different directory than your current working 
directory!
hacker@globbing~matching-paths-with-:~$ cd /challenge/run
bash: cd: /challenge/run: Not a directory
hacker@globbing~matching-paths-with-:~$ ch*/files/ch*/run/file_[bash]
bash: ch*/files/ch*/run/file_[bash]: No such file or directory
hacker@globbing~matching-paths-with-:~$ /ch*/files/ch*/run/file_[bash]
bash: /ch*/files/ch*/run/file_[bash]: No such file or directory
hacker@globbing~matching-paths-with-:~$ /challenge/files
bash: /challenge/files: Is a directory
hacker@globbing~matching-paths-with-:~$ challenge/run
bash: challenge/run: No such file or directory
hacker@globbing~matching-paths-with-:~$ /challenge/run /challenge/files/file_[bash]
You got it! Here is your flag!
pwn.college{8d-yIYGtZ6rfg_B4n3tE55V5JkN.QX0IDO0wSM5kjNzEzW}`
```

## What I learned
I learned how we can use [] directly inside the path name. 

# 5. Multiple globs
> Here we learn about the multi-globbing feautre of * and explore it to find our flag.

## My solve
**Flag:** `pwn.college{AvWXU7Ou8XrYXPkyLFsuAkQmC6I.0lM3kjNxwSM5kjNzEzW}`

```bash
hacker@globbing~multiple-globs:~$  cd /challenge/files
hacker@globbing~multiple-globs:/challenge/files$ /challenge/run p**
Your expansion did not expand to the requested files (happy optimistic pwning 
splendid uplifting).
Instead, it expanded to:
pwning
hacker@globbing~multiple-globs:/challenge/files$ ls
amazing    challenging  educational  great  incredible  kind      magical  optimistic  queenly  splendid   uplifting   wonderful  youthful
beautiful  delightful   fantastic    happy  jovial      laughing  nice     pwning      radiant  thrilling  victorious  xenial     zesty
hacker@globbing~multiple-globs:/challenge/files$ /challenge/run *p*
You got it! Here is your flag!
pwn.college{AvWXU7Ou8XrYXPkyLFsuAkQmC6I.0lM3kjNxwSM5kjNzEzW}
hacker@globbing~multiple-globs:/challenge/files$ 
```

## What I learned
I learned how linux searches for every possible combination in the directory to autocomplete for every * used in an argument. So if we ran the challenge with *, it would just list every file under the directory since it autocompletes without any constraints. For example if we ran 'p *' then it would search for every file starting with p. 

6. Mixing globs
This challenge requires us to use the globs from the previous challenges together.

## My solve
**Flag:** `pwn.college{helloworld}`

Here we are required to match the files "challenging", "educational", and "pwning" using 6 characters or less. 
```bash
example triple ticks for bash
pwn.college{helloworld}
```

## What I learned
explain what you learned

# 7. Exclusionary globbing
type what the challenge asks

## My solve
**Flag:** `pwn.college{helloworld}`

type in your solve and your thought process behind solving the challenge. Include as much as info as possible. Use triple ticks for bash.
```bash
example triple ticks for bash
pwn.college{helloworld}
```

## What I learned
explain what you learned

# 8. Tab completion
type what the challenge asks

## My solve
**Flag:** `pwn.college{helloworld}`

type in your solve and your thought process behind solving the challenge. Include as much as info as possible. Use triple ticks for bash.
```bash
example triple ticks for bash
pwn.college{helloworld}
```

## What I learned
explain what you learned

# 9. Multiple options for tab completion
type what the challenge asks

## My solve
**Flag:** `pwn.college{helloworld}`

type in your solve and your thought process behind solving the challenge. Include as much as info as possible. Use triple ticks for bash.
```bash
example triple ticks for bash
pwn.college{helloworld}
```

## What I learned
explain what you learned

# 10. Tab completion on commands 
type what the challenge asks

## My solve
**Flag:** `pwn.college{helloworld}`

type in your solve and your thought process behind solving the challenge. Include as much as info as possible. Use triple ticks for bash.
```bash
example triple ticks for bash
pwn.college{helloworld}
```

## What I learned
explain what you learned



