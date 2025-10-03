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

# 5. Extracting specific sections of text 
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
> This challenge teaches us about the cut command, which is used to grab specific columns of data.

## My solve
**Flag:**  `pwn.college{QrrL8LDclDNwwnmGQ0HSmgYbYd1.01NxEzNxwSM5kjNzEzW`

```bash
hacker@data~extracting-specific-sections-of-text:~$ /challenge/run | cut -d " " -f2 | tr -d "\n"
pwn.college{QrrL8LDclDNwwnmGQ0HSmgYbYd1.01NxEzNxwSM5kjNzEzW
```

## What I learned 
> I learned how the cut command can be combined with the -d command to show only specific colums of data and how all of these can work in union to perform operations.
> Syntax of cut: cut -d " "(column delimiter = how the columns are separated) -f (field number = which column to extract) [name of file]

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

# 6. Sorting data
> In this challenge it was specified that the flag was at the end of a 100 sorted flags so I sorted them in reverse and took the first flag. 

## My solve
**Flag:**  `pwn.college{o7nXqHF2TQFwMlo49VL0_YnekDs.0FM0MDOxwSM5kjNzEzW}`

```bash
hacker@data~sorting-data:~$ sort -r /challenge/flags.txt
pwn.college{o7nXqHF2TQFwMlo49VL0_YnekDs.0FM0MDOxwSM5kjNzEzW}
pwn.college{o7nXqHF2TQFwMlo49VL0_YnekDs.0EM0MCOxvSM5kjNzEzW}
pwn.college{o7nXqHF2TQFwMlo49VL0_YnekDr.0FM0MDOxwSM5kjNzEzW}
pwn.college{o7nXqHF2TQFwMlo49VL0_YnekDr.0FL0MDOxwSM5kjNzEzW}
pwn.college{o7nXqHF2TQFwMlo49VL0_XnekCs.0FM0MDOxwSM5kjMzEzW}
pwn.college{o7nXqHF2TQFwMlo49VL0_XnejDr.0FL0MDOxwSM5kjNzEzW}
pwn.college{o7nXqHF2TQFvMlo49VL0_YnekDs.0EM0MDOxwSM5kjNzEzW}
pwn.college{o7nXqGF2TQFwMlo49VL0_XnekDs.0FM0LDOxwSM5kjNzEzW}
pwn.college{o7nXqGE2TQFwLko49UL0_YnekDr.0EM0MDNxwSL5kiNyEzW}
pwn.college{o7nXpHF2TQFwMlo49VL0_YmekDs.0FM0MDOxwSM5kjNzEzW}
pwn.college{o7nXpHF2TQFwLlo49VK0_YnekDr.0FM0MDOxwSM5kjNzEyW}
pwn.college{o7nXpHF2SQFwMlo38VL0_XnekDs.0FM0MDOxwSL5kjNzEzW}
pwn.college{o7mXqHF2TPFwMlo38VL0_YmekDr.0FM0MCOxwSM5kjNzEzW}
pwn.college{o7mXqHE2TQFwMko49VL0_XnekDr.0FM0LDNxwSM5kiNzEzW}
pwn.college{o7mXqGF2TQFwMlo49VL0_YnekDs.0FM0MDOxwSM5kjNzEzW}
pwn.college{o6nXqHF2TPEwMlo49VL0_YnekDr.0FM0MCOxwSM4kjNzEzW}
pwn.college{o6nXqHF2SPFwMlo49VL0_YnejDs.0EL0LDOxvSL4kjNzEzV}
pwn.college{n7nWqHF2TQFwLlo49VL0_YnekDs.0FL0MDOxwSM5kjNzEyW}
pwn.college{n7mWqHF2TQFwMko49VL0_YnekDs.0EL0LDOxwSM5kjNzEzW}
pwn.collegd{o7nXqHF2TQFwMlo49VL0_YnekDs.0FM0MDOxwSM5kjNzDzW}
pwn.collegd{o7nXqHF2TQFwMko49VL0_YnekDs.0EM0MDOwwSM4kjNzEzW}
pwn.colldge{o7nXqHF2TQFwLlo49VL0_YnekDs.0FM0MDOxwSM5kjNzEzW}
pwn.colldge{o7nXqGF1TQFwMlo49VL0_YnejDs.0FM0MDOxwRM4jjNzEzV}
pwn.colldge{o6nXpHF2TQFwLko49VL0_YndkDr.0FL0LDNxwSM5kjNzDzW}
pwn.colldfe{o7mXqHE2TQEwMkn48VL0_YnejCs.0FM0MDOxwSM4kiMyEzW}
pwn.colldfe{o6nXqHF1TQFwLln48VK0_YndjCs.0EM0MCOxwSM5kjNyDyW}
pwn.colkege{n7nXqHF2TQFwLlo49VL0_YnejCs.0FM0MDOxwSM4kjNzEzW}
pwn.colkegd{n7nXpHF2SQEwMko49UL0_YndkDs.0EM0MDOwvSM4kjMzEyV}
pwn.colkefd{o7nXqGE2TQEwMkn49VL0_YnekDs.0FM0MCOxwRM4kiNyEzW}
pwn.coklege{o7nXqGF2SPEvLkn49VL0_XnejCs.0EM0MDNxwSM5kiMzEzW}
pwn.coklege{o6mXqHF1TPEwLlo48VL0_YmekCs.0FM0LDOxwSM4kjNzEzW}
pwn.coklegd{o7nXqHF1TQFwMlo48UK0_YndjCs.0FL0MDOxwSM4jjMzEzW}
pwn.cokldge{o6mWqHE2SPEwMlo48VL0_YnekCs.0EM0MDOxwRL5jjNzEyV}
pwn.cokkege{o7mXpGF2TQFwMlo49VK0_YmdkCs.0FM0MCOwvSM5jiNzEyW}
pwn.cokkegd{o7nWqHF2SQFwMko49UL0_YndkCs.0FL0MDOxwSM4kjMyEzW}
pwn.cokkefe{n7mXqGF1TQEwMlo48VL0_YndkDs.0FL0MDOwvRM5kiNyEyW}
pwn.cokkefd{o6nXqHE2TPFwMkn49UK0_YnekCs.0FL0MCOxwSM4kjNzEyV}
pwn.cnllegd{n7nXqHF2TPFwMln48VL0_XmejDs.0FM0MCOxwRM4kiMzEyW}
pwn.cnlldge{o7nXqHF2TPFvMlo48VL0_YnejCs.0EM0LDOxwSM5kjNzEzW}
pwn.cnklefd{o7mXqHF2TQEwLlo49VL0_YndkCs.0EM0MCOxwSM5kiNyEyW}
pwn.cnkldge{o6nXqHE2SQFwMln48VL0_XnejDs.0FM0LCOxwSL5kiNzDyV}
pwn.bollege{o7nXpHF2TPFwMlo49VL0_YndkDs.0FM0MDOxwSM5kjNzEyV}
pwn.bollegd{o6nXpHF2TQEwLlo49UL0_XmekCr.0FM0LCNxvSM4kjMzEzW}
pwn.bollegd{n7nXqHF2SQFvMko39VL0_YnekDs.0FM0MDOxwSM5jjNzDzW}
pwn.bolldge{o7nXpHE1TPFwMlo48VK0_YnekDr.0FM0MDOwwSL5jiMzDzV}
pwn.bolkegd{o6nXqHF2SQFwLko38VL0_YnekCs.0EL0LDOwwSL5kiMzDzV}
pwn.bolkdge{o6nXqHF2TQFwMko48VL0_YndkCs.0FM0MCOxwSM4jiMzEzV}
pwn.boklefe{o6nXqGF2TQFvMlo49VL0_XnekDs.0FL0LCOxvSL5jiNyDyW}
pwn.boklefe{n7mXqHF1TQFvMlo49VK0_YnejDs.0FM0MDOxwSM5kjNzEzW}
pwn.bokldgd{o7nWpHF1TQFvMlo48UK0_XndjDs.0EL0MCOxwRM5jiNyEyW}
pwn.bnllege{o7nXqHF1TQFvMko49VL0_YnejDr.0FM0MDOxwSM5kjMzEzW}
pwn.bnllege{o6nXqGF2TQEwMln39UL0_XmdjDs.0FM0MCOxwRM5kjNzEzW}
pwn.bnklege{o7mWqGF2SQEvLlo49VL0_YnejCr.0FM0MCNxwSL4kjNzEzW}
pwm.college{n7nXqHF2SQFwMkn49VL0_YnekDs.0FL0LDOxwSM5kjMzEzV}
pwm.collegd{n7mXpGE2TQFwMln49UK0_YnekDr.0FM0MCOwwSL5jjMyEyV}
pwm.colkege{o6mXpHF2SQFvMko38VL0_YnejDr.0FL0LDOxvSL5kjNyEyW}
pwm.coklege{o7nXqHF2TQFwMlo49VK0_YnekDs.0FM0MDOxwSM5kjNzEyW}
pwm.cokldfd{o7mXqHF1SPFwLlo39UL0_XmejDs.0FL0LDOxwSL5kiNzEzW}
pwm.cnllege{o6nXpHE2TQFwMlo49VL0_YndkDs.0FM0MCOxwSM4kjNzEzV}
pwm.cnllegd{o7mXpGF1TQEwMko48VL0_XnejCr.0EL0MDNxvSM4kjNzEzV}
pwm.cnlkege{o7nXqGE2SQFvMlo39UL0_YnekDr.0FM0MDOxwSM5jjNzEzV}
pwm.cnkkegd{o6mWqGE1TPFvLlo49VL0_YmdjCs.0FM0MCNxvSM5kiNzDzW}
pwm.bokkegd{o7nXpHE2SQFwMko49UL0_YnejDs.0FL0MDNxwRL5jjNyEyV}
pwm.bnllege{o7nXpHF2TQFwMlo49VL0_XmdkDs.0EL0MDOwwRM5jjNzEzW}
pwm.bnlkdge{o7mXqHE2SQFwMko48VK0_XndjDr.0FM0LDNwwSM5jjNyEzW}
pvn.college{o7nXqHF2TQFwMlo49VL0_YnekDs.0FM0MDOxwSM5kjNzEyW}
pvn.collegd{n6nXqHF2TQFwMlo49VL0_YmdkDs.0FM0MDOxvSM5kjNzEzW}
pvn.colkefe{n7mXqHF2TPEwMko48VK0_YnejDs.0EM0LCOxwSL5jiMzEzW}
pvn.cokldge{n7mXqHF2TPFvLko39VL0_XndjCs.0EM0MDOxwSM5jjNzEyV}
pvn.cokldgd{o7nXpHF2SQFwLkn49VK0_XmejCs.0EM0MDOxwSM5kiMzDyW}
pvn.cokkdge{o6nWpHF2TQEwLko49UL0_YnekCr.0FM0MDOwwSM5kjNyDzW}
pvn.cnllege{o7nXqHF1TQFwMln49VL0_YnekDs.0FM0MDOxvRM5kjNyEyW}
pvn.cnlkege{n7nWqHF2TQEvLln38VK0_XndkDs.0FL0MDOxvRM5kiNyEzW}
pvn.bollege{o7nXqGF2SPFwMlo38VL0_XnekCs.0FL0MCOwwSM5kjMzEzW}
pvn.boklefe{o6nXqHE2TQFvLlo39VK0_YmejDr.0EM0LDNxvSM4kiNzEzW}
pvn.bnllege{o7nWpGF2TQEvLko49VL0_YnekCs.0FL0MCOwvSM5kjNzEyW}
pvn.bnlldgd{o7mWqGE2SPFwMln48VL0_XnekDs.0EM0LCOxvSL4kjNzDyV}
pvm.bokldfd{n7mWqGF2SQEwLln49UK0_YnekDs.0EM0LCOwwSM5kjNzDzW}
```

## What I learned 
> The sort command can be very useful in practical applications. It's arguments can take:
> -r (reverse) , -n (numeric) , -u (unique) , -r (random)







