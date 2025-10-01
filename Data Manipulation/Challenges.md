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

