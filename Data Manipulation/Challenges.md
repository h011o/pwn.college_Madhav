# Challenges
1. Translating characters
2. Deleting characters
3. Deleting newlines
4. Extracting the first lines with head
5. Extracting specific sections of text
6. Sorting data
   
# 1. Translating characters
> This challenge requires us to use the tr command to change the case of our flag.

## My solve
**Flag:**  `pwn.college{swjJe4U1YpAu91ieDLl-xda5vfU.01MxEzNxwSM5kjNzEzW} `
In this challenge we also used the file globbing concept of [] to store alphabets.
```bash
hacker@data~translating-characters:~$ cat /challenge/run
#!/opt/pwn.college/bash

echo "Your case-swapped flag:"
cat /flag | tr '[A-Z][a-z]' '[a-z][A-Z]'
echo
hacker@data~translating-characters:~$ /challenge/run | tr '[A-Z][a-z]' '[a-z][A-Z]'
yOUR CASE-SWAPPED FLAG:
pwn.college{swjJe4U1YpAu91ieDLl-xda5vfU.01MxEzNxwSM5kjNzEzW}

```

## What I learned 
>The translate command (tr) is used in pipes when we have to swap or modify characters.
> Syntax: tr (character to be replaced) (new character) 

# 2. Deleting characters
> This challenge requires us to use the tr command to delete characters.

## My solve
**Flag:**  `pwn.college{Ixj_687Ng1ctGA2cKxGArYGOf6k.0FNxEzNxwSM5kjNzEzW}`

```bash
hacker@data~deleting-characters:~$ echo /challenge/run | tr -d '[^%]'
/challenge/run
hacker@data~deleting-characters:~$ /challenge/run | tr -d -d '[^%]'
Your character-stuffed flag:
pwn.college{Ixj_687Ng1ctGA2cKxGArYGOf6k.0FNxEzNxwSM5kjNzEzW}

```

## What I learned 
>The translate command (tr) can also be used to delete chartacters
> Syntax: tr -d 'character(s) to be deleted'

# 3. Deleting newline
> This challenge introduces us to the use of escape sequences in the linux filesystem.

## My solve
**Flag:**  `pwn.college{IGE6VwBfYcQrpErwjPW7jFk64FA.0VNxEzNxwSM5kjNzEzW}`

```bash
hacker@data~deleting-newlines:~$ /challenge/run | tr -d "\n"
Your line-split flag: pwn.college{IGE6VwBfYcQrpErwjPW7jFk64FA.0VNxEzNxwSM5kjNzEzW}hacker@data~deleting-newlines:~$ 

```

## What I learned 
> I learned how escape characters can be also used in the linux filesystem and how to seperate or delete new lines.

# 3. Deleting newline
> This challenge introduces us to the use of escape sequences in the linux filesystem.

## My solve
**Flag:**  `pwn.college{IGE6VwBfYcQrpErwjPW7jFk64FA.0VNxEzNxwSM5kjNzEzW}`

```bash
hacker@data~deleting-newlines:~$ /challenge/run | tr -d "\n"
Your line-split flag: pwn.college{IGE6VwBfYcQrpErwjPW7jFk64FA.0VNxEzNxwSM5kjNzEzW}hacker@data~deleting-newlines:~$ 

```

## What I learned 
> I learned how escape characters can be also used in the linux filesystem to seperate or delete new lines.

# 4. Extracting the first lines with head 
> This challenge introduces us to head command and asks us to use it to aquire our flag,

## My solve
**Flag:**  `pwn.college{w6cVle-CwEmXYg3mlFCDEeUUFjs.0lNxEzNxwSM5kjNzEzW}`



```bash
hacker@data~extracting-the-first-lines-with-head:~$ /challenge/pwn | head -n 7 | /challenge/college
Congratulations, you piped the right codes!
pwn.college{w6cVle-CwEmXYg3mlFCDEeUUFjs.0lNxEzNxwSM5kjNzEzW}

```

## What I learned 
> I learned how the head command can be used with -n to output the very first input for a set number of files.

# 5. Extracting specific sections of text 
> This challenge teaches us about how to extract specific sections of text using the cut command. 

## My solve
**Flag:**  `pwn.college{w6cVle-CwEmXYg3mlFCDEeUUFjs.0lNxEzNxwSM5kjNzEzW}`



```bash
hacker@data~extracting-the-first-lines-with-head:~$ /challenge/pwn | head -n 7 | /challenge/college
Congratulations, you piped the right codes!
pwn.college{w6cVle-CwEmXYg3mlFCDEeUUFjs.0lNxEzNxwSM5kjNzEzW}

```

## What I learned 
> I learned how the head command can be used with -n to output the very first input for a set number of files.






