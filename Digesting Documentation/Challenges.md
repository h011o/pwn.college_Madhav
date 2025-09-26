# Challenges
1. Learning from Documentation
2. Learning complex usage
3. Reading manuals
4. Searching manuals
5. Searching for manuals
6. Helpful programs
7. Help for Builtins



# 1. Learning from Documentation
> This challenge introduces us to documentation with an example.

## My solve
**Flag:** `pwn.college{s94s2Y2xMAcqZ_O8Vay0XajzBJH.QX0ITO0wSM5kjNzEzW}`

```bash
hacker@man~learning-from-documentation:~$ /challenge/challenge --giveflag
Correct argument! Here is your flag:
pwn.college{s94s2Y2xMAcqZ_O8Vay0XajzBJH.QX0ITO0wSM5kjNzEzW}
```

## What I learned
I learned that 'documentation' for linux is basically a how-to on how a certain command works, what arguments it can take etc

# 2. Learning complex usage
> This challenge introduces us to documentation with a different example.

## My solve
**Flag:** `pwn.college{UOE4Q5m1G5LJMACaHzk2L11hseK.QX1ITO0wSM5kjNzEzW}`

```bash
hacker@man~learning-complex-usage:~$ /challenge/challenge --printfile /flag
Correct argument! Here is the /flag file:
pwn.college{UOE4Q5m1G5LJMACaHzk2L11hseK.QX1ITO0wSM5kjNzEzW}
```
# 3. Reading Manuals 
> This challenge introduces us to the 'man' command and asks us to use it to find a secret option that prints the flag.

## My solve
**Flag:** ` pwn.college{UDaJMeb_sscAD6K-TR7NwzwWea1.QX0EDO0wSM5kjNzEzW}`

```bash
hacker@man~reading-manuals:~$ man challenge
hacker@man~reading-manuals:~$ /challenge/challenge --aebscc 671
Incorrect usage! Please read the challenge man page!
hacker@man~reading-manuals:~$ man challenge
hacker@man~reading-manuals:~$ /challenge/challenge --aebssc 671
Correct usage! Your flag: pwn.college{UDaJMeb_sscAD6K-TR7NwzwWea1.QX0EDO0wSM5kjNzEzW}
```

## What I learned
> The arguments for the man command arent file paths but names of entries themselves.
The syntax of the output from the 'man' command is of the form : 
* Name
* Synopsis
* Description
* See Also

# 4. Searching Manuals 
> This challenge teaches us on how to navigate manual pages. 

## My solve
**Flag:** `pwn.college{UQhVgjwjJEsYd1S97f1EC-mXNUK.QX1EDO0wSM5kjNzEzW}`

After opening the manual page, I use the / key to search for 'flag' which helped me find the command to aquire the flag.
```bash
hacker@man~searching-manuals:~$ /challenge/challenge --irqe
Initializing...
Correct usage! Your flag: pwn.college{UQhVgjwjJEsYd1S97f1EC-mXNUK.QX1EDO0wSM5kjNzEzW}
hacker@man~searching-manuals:~$ /challenge/challenge --irqe
Initializing...
Correct usage! Your flag: pwn.college{UQhVgjwjJEsYd1S97f1EC-mXNUK.QX1EDO0wSM5kjNzEzW}
```

## What I learned
> '/' to search inside manuals and 'n' = next result, 'N' = previous result.


# 5. Searching for manuals
> This challenge requires us to search for a specific manpage to find a hidden challenge man page.

HINT 1: man man teaches you advanced usage of the man command itself, and you must use this knowledge to figure out how to search for the hidden manpage that will tell you how to use /challenge/challenge

HINT 2: though the manpage is randomly named, you still actually use /challenge/challenge to get the flag!



## My solve
**Flag:** `pwn.college{UQhVgjwjJEsYd1S97f1EC-mXNUK.QX1EDO0wSM5kjNzEzW}`

After opening the manual page, I use the / key to search for 'search'
On reading a bit, I came upon this:     

``` bash
-K, --global-apropos
              Search for text in all manual pages.  This is a brute-force search, and is likely to take some time; if  you  can,  you  should
              specify a section to reduce the number of pages that need to be searched.  Search terms may be simple strings (the default), or
              regular expressions if the --regex option is used.

              Note that this searches the sources of the manual pages, not the rendered text, and so  may  include  false  positives  due  to
              things  like  comments  in  source  files, or false negatives due to things like hyphens being written as "\-" in source files.
              Searching the rendered text would be much slower.
```

```bash
hacker@man~searching-manuals:~$ /challenge/challenge --irqe
Initializing...
Correct usage! Your flag: pwn.college{UQhVgjwjJEsYd1S97f1EC-mXNUK.QX1EDO0wSM5kjNzEzW}
hacker@man~searching-manuals:~$ /challenge/challenge --irqe
Initializing...
Correct usage! Your flag: pwn.college{UQhVgjwjJEsYd1S97f1EC-mXNUK.QX1EDO0wSM5kjNzEzW}
```

## What I learned
> '/' to search inside manuals and 'n' = next result, 'N' = previous result.


