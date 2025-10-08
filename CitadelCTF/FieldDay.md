# Field Day

## Description
> This challenge required us to decode FIELDATA to get our flag. There was a sequence of 28 binary strings, each 12 bits long, representing holes on an 80-column punch
> card using the FIELDATA (UNIVAC) character encoding system. 

## My Solve

This is how the 12 bit string is indexed :
12 11 0 1 2 3 4 5 6 7 8 9

Each FIELDATA character (like A,B,1,2..) is represented by a combination of those bits.
Basically, every time the bit value is equal to 1, its bit position is considered.

So when you see: 010000010010, according to the indexing system, the 1 is in positions 11 and 5, according to the 80-punch card this means 11-5 which means N.

<img width="393" height="238" alt="image" src="https://github.com/user-attachments/assets/981fa061-850e-4276-9198-c53d58b90155" />

Similarly, on decoding all 28 binary strings following the same procedure we get our flag.

## Flag 
``citadel{r3b3ll10n$&BU1lt:0nH0p3}``

## References
> https://www.fourmilab.ch/documents/univac/fieldata.html
                                                                                    

 

