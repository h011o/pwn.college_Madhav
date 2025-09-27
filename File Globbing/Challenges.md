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

# 6. Mixing globs
> This challenge requires us to use the globs from the previous challenges together.

## My solve
**Flag:** `pwn.college{YiOtBoznB0SNfxtU2h-96J-dmd7.QX1IDO0wSM5kjNzEzW}`

Here we are required to match the files "challenging", "educational", and "pwning" using 6 characters or less. 
First, I noticed 'in' was common among all the words and I tried running * [in] * , however, this resulted in a lot of extra words. Then I realized these were the only words starting with their respective letters in the directory which led me to my solution.
```bash
hacker@globbing~mixing-globs:~$ cd /challenge/files
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [cep]*
You got it! Here is your flag!
pwn.college{YiOtBoznB0SNfxtU2h-96J-dmd7.QX1IDO0wSM5kjNzEzW}
```
## What I learned
I learned how we can mix multiple file globs to find files under certain constraints. 

# 7. Exclusionary globbing
> This challenge introduces us to the concept of exclusionary globbing.

## My solve
**Flag:** `pwn.college{gx3sD1AXHz2KoLAVp-2QZjPn5lW.QX2IDO0wSM5kjNzEzW}`

```bash
hacker@globbing~exclusionary-globbing:~$ cd /challenge/files
hacker@globbing~exclusionary-globbing:/challenge/files$ ls
amazing    challenging  educational  great  incredible  kind      magical  optimistic  queenly  splendid   uplifting   wonderful  youthful
beautiful  delightful   fantastic    happy  jovial      laughing  nice     pwning      radiant  thrilling  victorious  xenial     zesty
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [^pwn]*
You got it! Here is your flag!
pwn.college{gx3sD1AXHz2KoLAVp-2QZjPn5lW.QX2IDO0wSM5kjNzEzW}
```

## What I learned
Exclusionary globbing logically works like the **NOT** operator. It can be used either with ! or ^(for newer shells). 

# 8. Tab completion
> This challenge teaches us about an actual autocomplete feautre in the linux filesystem - the 'tab'.

## My solve
**Flag:** `pwn.college{0V6gjt68IRfqnIfST22MVl4XBXw.0FN0EzNxwSM5kjNzEzW}`

```bash
hacker@dojo:~$ ls /challenge
DESCRIPTION.md  pwncollege
hacker@dojo:~$ cat /challenge/pwncollege
cat: /challenge/pwncollege: No such file or directory
hacker@dojo:~$ cat /challenge/pwn<TAB>
pwn.college{0V6gjt68IRfqnIfST22MVl4XBXw.0FN0EzNxwSM5kjNzEzW}
```

## What I learned
I learned that using * to shorten what must be typed on the command line can lead to mistakes, a safer alternative is pressing the tab key after typing part of the command.

# 9. Multiple options for tab completion
> This challenge is an extension of the previous challenge with multiple options for tab completion.

## My solve
**Flag:** `pwn.college{oABtZ0hjEI5Wytq0pyWhmrcfNg5.0lN0EzNxwSM5kjNzEzW}`

```bash
hacker@globbing~multiple-options-for-tab-completion:~$ /challenge/files/pwn
pwn                    pwn-the-planet         pwncollege-flamingo    pwncollege-hacking     
pwn-college            pwncollege-family      pwncollege-flyswatter  
hacker@globbing~multiple-options-for-tab-completion:~$ cd /challenge/files
hacker@globbing~multiple-options-for-tab-completion:/challenge/files$ ls
No ls for you in this level! Use tab-completion instead!
hacker@globbing~multiple-options-for-tab-completion:/challenge/files$ 
Display all 2339 possibilities? (y or n)
hacker@globbing~multiple-options-for-tab-completion:/challenge/files$ cat pwncollege-family 
No flag in this file!
hacker@globbing~multiple-options-for-tab-completion:/challenge/files$ cat pwncollege-flyswatter 
No flag in this file!
hacker@globbing~multiple-options-for-tab-completion:/challenge/files$ cat pwncollege-hacking 
No flag in this file!
hacker@globbing~multiple-options-for-tab-completion:/challenge/files$ cat pwn-college 
No flag in this file!
hacker@globbing~multiple-options-for-tab-completion:/challenge/files$ cat pwncollege-fla
pwncollege-flag      pwncollege-flamingo  
hacker@globbing~multiple-options-for-tab-completion:/challenge/files$ cat pwncollege-flamingo 
No flag in this file!
hacker@globbing~multiple-options-for-tab-completion:/challenge/files$ cat pwncollege-flag
pwn.college{oABtZ0hjEI5Wytq0pyWhmrcfNg5.0lN0EzNxwSM5kjNzEzW}
```

## What I learned
This challenge taught me how useful tabbing and the command history feautre are. I had to reuse commands multiple times to find the flag in this challenge.

# 10. Tab completion on commands 
> This level has a command that starts with pwncollege, and it'll give you the flag on auto-completing it.

## My solve
**Flag:** `pwn.college{Eq7zuADdZ6nSBxvLi6dgJ0feJoS.0VN0EzNxwSM5kjNzEzW}`

for some reason pwncollege wasnt auto-completing the first time I tried pressing tab, it simply listed some files. After I switched directories and came back to home, it worked like it was supposed to.

```bash
hacker@globbing~tab-completion-on-commands:~$ pwncollege 
.bash_history  .config/       .lesshst
hacker@globbing~tab-completion-on-commands:~$ cd /challenge
hacker@globbing~tab-completion-on-commands:/challenge$ pwncollege 
.bashrc         .init           DESCRIPTION.md  bin/
hacker@globbing~tab-completion-on-commands:/challenge$ cd
hacker@globbing~tab-completion-on-commands:~$ pwncollege-6597 
Correct! Here is your flag:
pwn.college{Eq7zuADdZ6nSBxvLi6dgJ0feJoS.0VN0EzNxwSM5kjNzEzW}

```

## What I learned
I learned how tab commands can be used for autocompleting programs aswell.

# Summary
*  ? is used to autocomplete single characters.
*  * is used to autocomplete multi characters.
*  [] is used to autocomplete a single character from a set of characters.
*  [^ ] is the inverse glob to discard specific single characters.
*  The tab key can be pressed to autocomplete both single and multi characters.



