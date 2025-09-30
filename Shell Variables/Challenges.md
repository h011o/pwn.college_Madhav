# Challenges
1. Printing Variables
2. Setting variables
3. Multi-word variables
4. Exporting variables
5. Printing exported variables
6. Storing command output
7. Reading Input
9. Reading Files 


# 1. Printing Variables
> This challenge tells us about printing variables. 

## My solve
**Flag:** `pwn.college{M1eKKtw61XZdYWKZ7RtDC9iryBC.QX3UTN0wSM5kjNzEzW}`


```bash
hacker@variables~printing-variables:~$ echo $FLAG
pwn.college{M1eKKtw61XZdYWKZ7RtDC9iryBC.QX3UTN0wSM5kjNzEzW}
```

## What I learned
> I already knew that the function of echo was to print our input to the terminal. Now we learned that echo can also display a variable if it has a $.

# 2. Setting variables 
> This challenge asks us to use the concept of setting variables to get our flag.

## My solve
**Flag:** `pwn.college{4DcfxCPQ_cTIQ_GBj8ya67B3jAK.QX5UTN0wSM5kjNzEzW}`


```bash
hacker@variables~setting-variables:~$ PWN=COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{4DcfxCPQ_cTIQ_GBj8ya67B3jAK.QX5UTN0wSM5kjNzEzW}

```

## What I learned
> There has to be no space between the variable and the (=). The $ symbol is used to *access* variables.

# 3. Multi-word variables 
> This challenge teaches us how to assign data with spaces to a variable.

## My solve
**Flag:** `pwn.college{8jEhABEY4BHHUIBB2Vgflt0pKWb.QXwYTN0wSM5kjNzEzW}`


```bash
hacker@variables~multi-word-variables:~$ PWN="COLLEGE YEAH"
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{8jEhABEY4BHHUIBB2Vgflt0pKWb.QXwYTN0wSM5kjNzEzW}

```

## What I learned
> The terminal reads the next word after the space as a command, to avoid this we use quotes around our required value while setting it to a variable.

# 4. Exporting variables 
> This challenge teaches us about how to export variables to a child shell. 

## My solve
**Flag:** `pwn.college{E5xh3EjURt0zVZyvcKwgRWsxGIw.QXyYTN0wSM5kjNzEzW}`


```bash
hacker@variables~exporting-variables:~$ export PWN=COLLEGE
You've set the PWN variable to the proper value!
hacker@variables~exporting-variables:~$ COLLEGE=PWN
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$ /challenge/run
CORRECT!
You have exported PWN=COLLEGE and set, but not exported, COLLEGE=PWN. Great 
job! Here is your flag:
pwn.college{E5xh3EjURt0zVZyvcKwgRWsxGIw.QXyYTN0wSM5kjNzEzW}
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
```

## What I learned
> By default, variables that you set in a shell session are local to that shell process. To allow exporting of these shell variables we use the export command.

# 5, Printing exported variables
> This challenge introduces us about other ways to access variables in linux. 

## My solve
**Flag:** `pwn.college{E5xh3EjURt0zVZyvcKwgRWsxGIw.QXyYTN0wSM5kjNzEzW}`


```bash
hacker@variables~printing-exported-variables:~$ env
SHELL=/run/dojo/bin/bash
HOSTNAME=variables~printing-exported-variables
PWD=/home/hacker
MANPATH=/run/dojo/share/man:
DOJO_AUTH_TOKEN=2bbdf02d096f5ccbbbaf643e05d4bcd0909fcece3eb580cc02340f6df4abde84
HOME=/home/hacker
LANG=C.UTF-8
FLAG=pwn.college{gHr8tEBHsdhg2VUvg4ua7lPkVtf.QX4UTN0wSM5kjNzEzW}
TERMINFO=/run/dojo/share/terminfo
TERM=xterm-256color
SHLVL=2
LC_CTYPE=C.UTF-8
SSL_CERT_FILE=/run/dojo/etc/ssl/certs/ca-bundle.crt
PATH=/run/challenge/bin:/run/dojo/bin:/root/.cargo/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
DEBIAN_FRONTEND=nonintera
```

## What I learned
> The env command prints out every exported variable set from our shell. 

# 6. Storing Command Output 
> This challenge introduces us to the concept of command substitution.

## My solve
**Flag:** `pwn.college{0zuMRsZFnGAjz-0EPlr1iL9FB-O.QX1cDN1wSM5kjNzEzW}`


```bash
hacker@variables~storing-command-output:~$ PWN=$(cat /challenge/run)
hacker@variables~storing-command-output:~$ echo $PWN
#!/opt/pwn.college/bash if [ -t 1 ] || [ ! -f /tmp/subshell ] then fold -s >&2 <<< "You are not running me via Command Substitution! Please make sure to run me with command substitution." exit 1 elif [ ! -f /tmp/dstvar ] then fold -s >&2 <<< 'You do not appear to be reading into a variable... Make sure to read me into a variable, e.g.:' echo ' VAR_NAME=$(/challenge/run)' >&2 exit 2 fi [ -f /tmp/dstvar ] && read DSTVAR < /tmp/dstvar if [ "$DSTVAR" != "PWN" ] then fold -s >&2 <<< "You are reading into the $DSTVAR variable, but you should read into the PWN variable. I am redacting the flag!" echo "pwn.college{REDACTED}" exit 3 fi fold -s >&2 <<< "Congratulations! You have read the flag into the PWN variable. Now print it out and submit it!" cat /flag
hacker@variables~storing-command-output:~$ PWN=$(/challenge/run)
Congratulations! You have read the flag into the PWN variable. Now print it out 
and submit it!
hacker@variables~storing-command-output:~$ echo $PWN
pwn.college{0zuMRsZFnGAjz-0EPlr1iL9FB-O.QX1cDN1wSM5kjNzEzW}
```

## What I learned
> Outputs to commands can be directly assigned to a variable using this concept. This is similar to process substituion which treats the output of a command as a temporary file.

# 7. Reading Input 
> This challenge teaches us how to accept values to a variable from the user itself. 

## My solve
**Flag:** `pwn.college{ECj3rockODUACUl58_rigKvgT7E.QX4cTN0wSM5kjNzEzW}`


```bash
hacker@variables~reading-input:~$ read PWN
COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{ECj3rockODUACUl58_rigKvgT7E.QX4cTN0wSM5kjNzEzW}
```

## What I learned
> The read command is used to accept data from the user. I also noticed how while using read we dont need the $, like we learned in a previosu challenge, the $ symbol is used the access variables and expand them. Here the data is inputed so variable expansion is not needed. 

# 8. Reading files
> This challenge needs us to read a file into an environment variable.  

## My solve
**Flag:** `pwn.college{wG30GXoH79QVwbBTnPnyC4SfZ9e.QXwIDO0wSM5kjNzEzW}`


```bash
hacker@variables~reading-files:~$ read PWN < /challenge/read_me
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{wG30GXoH79QVwbBTnPnyC4SfZ9e.QXwIDO0wSM5kjNzEzW}
```

## What I learned
> I learnt another way of inputing data into PWN using the concept of (<) input redirection. 

 
