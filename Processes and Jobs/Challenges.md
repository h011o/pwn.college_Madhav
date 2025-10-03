# Challenges
1. Listing processes
2. Killing processes
3. Interrupting Processes
4. Killing misbheaving processes
5. Suspending processes
6. Resuming processes
7. Backgrounding processes
8. Foregrounding processes
9. Starting background processes
10. Process Exit codes
   
# 1. Listing processes
> This challenge tells us all about listing processes 

## My solve
**Flag:** `pwn.college{Q_c-42rCi9REdyqYnKZl0cq9eYk.QX4MDO0wSM5kjNzEzW} `
```bash
hacker@processes~listing-processes:~$ ps aux
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.0  0.0   1056   640 ?        Ss   18:16   0:00 /sbin/docker-init -- /nix/var/nix/profiles/dojo-workspace/bin/dojo-init /run/d
root           7  0.0  0.0 231708  2560 ?        S    18:16   0:00 /run/dojo/bin/sleep 6h
root         132  0.0  0.0   4132  2560 ?        S    18:16   0:00 /challenge/32232-run-4860
root         135  0.0  0.0   2744  1600 ?        S    18:16   0:00 sleep 6h
hacker       146  0.0  0.0  36972 21760 ?        Sl   18:16   0:00 /nix/store/g0q8n7xfjp7znj41hcgrq893a9m0i474-ttyd-1.7.7/bin/ttyd --port 7681 --
hacker       160  0.0  0.0 231940  4160 pts/0    Ss   18:18   0:00 /run/dojo/bin/bash --login
hacker       172  0.0  0.0 233600  3840 pts/0    R+   18:23   0:00 ps aux
hacker@processes~listing-processes:~$ ^C
hacker@processes~listing-processes:~$ cat /challenge/32232-run-4860
#!/opt/pwn.college/bash

if [ -z "$DOIT" ]
then
        export DOIT=yes
        exec -a $0 bash < $0
fi

echo "Yahaha, you found me! Here is your flag:"
cat /flag
echo "Now I will sleep for a while (so that you could find me with 'ps')."
sleep 6h
hacker@processes~listing-processes:~$ /challenge/32232-run-4860
Yahaha, you found me! Here is your flag:
pwn.college{Q_c-42rCi9REdyqYnKZl0cq9eYk.QX4MDO0wSM5kjNzEzW}
Now I will sleep for a while (so that you could find me with
```

## What I learned 
> ps is used to identify every process in the linux environment.
> -ef argument can be used to list every process in full format output. (standard syntax)
> ps -ef differes from ps - aux in the way that it outputs the parent process id while ps-aux outputs stuff such as total system CPU and memory.

# 2. Killing processes
> This challenge tells us about the process termination command  'kill'

## My solve
**Flag:** `pwn.college{ohzwnbJZ9UOtnErfH2JdUV4Ko7G.QXyQDO0wSM5kjNzEzW}`
```bash
hacker@processes~killing-processes:~$ ps -aux
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.6  0.0   1056   640 ?        Ss   18:31   0:00 /sbin/docker-init -- /nix/var/nix/profiles/dojo-workspace/bin/dojo-init /run/d
root           7  0.4  0.0 231708  2560 ?        S    18:31   0:00 /run/dojo/bin/sleep 6h
root         135  0.0  0.0   5204  3520 ?        S    18:31   0:00 su -c /challenge/.launcher hacker
hacker       136  0.0  0.0 231576  3520 ?        Ss   18:31   0:00 /challenge/dont_run
hacker       137  0.0  0.0 231708  2560 ?        S    18:31   0:00 sleep 6h
hacker       148  0.4  0.0  36972 21760 ?        Sl   18:31   0:00 /nix/store/g0q8n7xfjp7znj41hcgrq893a9m0i474-ttyd-1.7.7/bin/ttyd --port 7681 --
hacker       152  0.0  0.0 231940  4160 pts/0    Ss   18:31   0:00 /run/dojo/bin/bash --login
hacker       162  0.0  0.0 233600  3840 pts/0    R+   18:31   0:00 ps -aux
hacker@processes~killing-processes:~$ kill 136
hacker@processes~killing-processes:~$ /challenge/run
Great job! Here is your payment:
pwn.college{ohzwnbJZ9UOtnErfH2JdUV4Ko7G.QXyQDO0wSM5kjNzEzW}
```

## What I learned 
> The 'kill' command is sort of like the 'end task' button in windows task manager. Every process has a 'PID' which is the process identifier used to kill the process.

# 3. Interrupting processes
> This challenge tells us how to get rid of processes that clog up the terminal

## My solve
**Flag:** `pwn.college{ohzwnbJZ9UOtnErfH2JdUV4Ko7G.QXyQDO0wSM5kjNzEzW}`
```bash
hacker@processes~interrupting-processes:~$ /challenge/run
I could give you the flag... but I won't, until this process exits. Remember, 
you can force me to exit with Ctrl-C. Try it now!
^C
Good job! You have used Ctrl-C to interrupt this process! Here is your flag:
pwn.college{UOg82hjnReoMXHPIVJvNbRq3b3I.QXzQDO0wSM5kjNzEzW}
```

## What I learned 
> Its very interesting that the hotkey to interrupt process in terminal is the same as the copy shortcut. That explains why I've failed all the times I've tried to paste commands instead of using command history.

# 4. Killing misbehaving processes 
> This challenge tells us how to get rid of processes that dont behave accordingly. 

## My solve
**Flag:** `pwn.college{ohzwnbJZ9UOtnErfH2JdUV4Ko7G.QXyQDO0wSM5kjNzEzW}`

What happened here is basically, the decoy challenge was constantly writing fake flags to /tmp/flag_fifo, which stayed in the buffer despite being killed. What I think happens is after the decoy is gone and we run it again the flag is outputted. 
```bash
hacker@processes~killing-misbehaving-processes:~$ ps -aux
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.3  0.0   1056   640 ?        Ss   18:38   0:00 /sbin/docker-init -- /nix/var/nix/profiles/dojo-workspace/bin/dojo-init /run/d
root           7  0.3  0.0 231708  2560 ?        S    18:38   0:00 /run/dojo/bin/sleep 6h
root         137  0.0  0.0   4132  1280 ?        S    18:38   0:00 /bin/bash /challenge/.init
root         138  0.0  0.0   4132  1280 ?        S    18:38   0:00 /bin/bash /challenge/.init
root         139  0.0  0.0   5204  3520 ?        S    18:38   0:00 su -c exec /challenge/decoy > /tmp/flag_fifo hacker
root         140  0.0  0.0   2744  1600 ?        S    18:38   0:00 sleep 6h
root         141  0.0  0.0   2744  1600 ?        S    18:38   0:00 sleep 6h
hacker       142  0.4  0.0  13516  9280 ?        Ss   18:38   0:00 /usr/bin/python /challenge/decoy
hacker       153  0.3  0.0  36972 21760 ?        Sl   18:38   0:00 /nix/store/g0q8n7xfjp7znj41hcgrq893a9m0i474-ttyd-1.7.7/bin/ttyd --port 7681 --
hacker       157  0.0  0.0 231972  4160 pts/0    Ss   18:38   0:00 /run/dojo/bin/bash --login
hacker       167  0.0  0.0 233600  3840 pts/0    R+   18:38   0:00 ps -aux
hacker@processes~killing-misbehaving-processes:~$ kill 142
hacker@processes~killing-misbehaving-processes:~$ kill 139
bash: kill: (139) - No such process
hacker@processes~killing-misbehaving-processes:~$ /challenge/run
Sending the flag to /tmp/flag_fifo!
^C
hacker@processes~killing-misbehaving-processes:~$ cat /tmp/flag_fifo
pwn.college{vp7mXK.souoxaCzoQtQkSSLjNJb8jsWMSEBKWgOOsr6zBY4}
pwn.college{XiYlzft31C1ovGZJhSu3RBsTTxzjo5P9VaD6I1zdFl.qF2.}
pwn.college{-JwrgMZh3xVmKFX067OAIuHupntTGCk1VuB.WKE3i78Oy2J}
pwn.college{PmD00SWb05ouwgnwPsParABxkVrn8U4emrwXd4rbwW0-1Qq}
pwn.college{xZ5TZ1ThClCQNCS0ZiCrOMcnfS6ULDtfk7ViVEaPDvbglwA}
pwn.college{wvQpiBewE4uTR.OZW4VeY4cnqWXSPtHg6zdgCtYpO0n3von}
pwn.college{F98tBcD2pID3JhdCY-0eLvj1j-LQDnqF07iCdkYOnmqhRAQ}
pwn.college{B69sW3UONqkNOZrY9zznTHR470fPURmiDur6isGgc.7DNpx}
pwn.college{62P5IJqjDgz91FwvAAB6ukuxeF5fLXf9MM8uzIe5pWzcHdV}
pwn.college{O89bs9hnrjzXnFMn0uoU6-eVRIcobQIIWsz46CxsmjVJZQp}
pwn.college{2WFfLxDX.b4NMG8Mi3dBl510prbHf96oP0xEW48NFaNsttd}
pwn.college{rMeBqyy8dfUl0cAu6BwaiM0Gx-E1x3aKB0j5w56tbVbHu0G}
pwn.college{fitxcBRujMJ5xjTwE8gdiSa9J-2SCTO5nue3977IYq8PKdO}
pwn.college{0A7Sf-20B77J3XVZmkbVt61rBMh8XrNZ607I35UN7Q-6kxt}
pwn.college{40sLMzDRkG7HXhu3pYn292ROGmkx1D60Fu9DeA41MpppsJB}
pwn.college{8S5qtsl5.GD8MLsDXk-soEG1LN33HqdPEN8ckr9qv8.AJXT}
pwn.college{knyhubN3uAVW-5G3ZavtVEI93aGoVkh1AXjwdmc--XxeUZA}
pwn.college{hIhTXPF1kxJyocz1HpsQSuyYGXMigfVPGU1DtfL3jcxE3mY}
pwn.college{C4VE0vyS8onutgwD1-u42YijguKSPZU6IoXBIxAXUh4OcI.}
pwn.college{3haIRmthX7ciNUhHr6l7-PWsDxqKjjoqiu0R3bCiZBPX53g}
pwn.college{IHYbHLmaRE04TiqUn0FJkrqAU1hyFhWZzf2i6JTBEvJMqiF}
pwn.college{B4tRfzWEfYlxCfklaAhJShxMUZbZwVDnhwceBCkDh8lGyIo}
pwn.college{ivyJyuTE8A-PR1ZcGuGcWKoValQ2Jpwoo2iqSQrvj-iJ8wY}
pwn.college{cgo2Dx68OrAxUgLLz6dO.XZ7qlRFh6gHUCXqgQA4HmVa.k9}
pwn.college{LMdpXVkUhvb1pFN.2l732SIJFv0AcNAH.0Mp4FSnXStyzwv}
pwn.college{T5lpB8fgRr6eiQSAQlzH3V-EqgBdKIPEwfV2H-GB7LTjW3V}
pwn.college{YgtoHy4NEV8fNvvPqabJ-4zbbt3i5ho1Nj4EnXWCXgPkHbw}
pwn.college{40QrGD56oyED8gmQ7f1CEihw5Sr8OzmTdXfh2SKqUCVGRlm}
pwn.college{1BfbGr9lzo-uRRzV5TpBhlpWomPdbR5mkFzlFmOP4rNEZ2D}
pwn.college{-Vvv64sAmGTFZT3YWCPxdD9WEbXj1U09snF7WN8VoqlFjqk}
pwn.college{DJd1m4C016dtC3Vu.Pjnjtjmxv3RIx11bMpKOgf5Aih7EBO}
pwn.college{.0g4u9N0dY6Ro-11dJi3thF35lrvCUyFTBuDgZihe5fFmrm}
pwn.college{zATLy3nseeiMsOrVU4VYy3PcXrF4bLbEMCNABqRQBhodWet}
pwn.college{9tVFOdxsCI8GCxeoqZ699UJyBZGVAFHW.dtim-eegY.8P2d}
pwn.college{y3F1q-kDAlqKwuRca-EI871k2Gw2ZJ2jNbZ8gl.Aump93hb}
pwn.college{1rDVkJW-3aIPHLDFuul2YPNxQnQ8Me0.qZ9JHWafx8haFeW}
pwn.college{zAG1O35aPkIUXdFdv6v9AsV785YpZ3bRf.DuOzHjnaGIYnS}
pwn.college{y76aWozb7BQh98y.PzyZ0cM2GtxkciXwKo0XT6bGsJeNb3E}
pwn.college{yhDVcH-XqN1z0YecJXu1zZpGaJ-UkkDf-.u90nVaEsgssDW}
pwn.college{8Py0EVlHmelxxpEC3VsRJozJobcLSPcLmzWNeOZe6r1m1rf}
pwn.college{Qo1Fl62dky1GabSbTAPIkWnYLE3kBTpvm0ni8yJYBTIPyuv}
pwn.college{Vm8tiydUs6iIbMCKieQBFd-y-aYiDV3gshV9IsxcD.8UNjd}
pwn.college{8TE9.mod-Xr0ZUs2CcGdfepRlrrBqDwqH5AiUnTfOBdkwML}
pwn.college{w8QFhV.dfJ1ztwCy-TUBEn-JUzA81XfTII4bbcsepT.24l7}
pwn.college{Erzu3vQ8HHUxtzUZ3CqiTr5RAISRA.ILIXqR0ek7Qyn-9B7}
pwn.college{4ZjeovhTjrdaEw5uZvhDKJ6s1zVeV7sMAO675xWIaOXhAxc}
pwn.college{wxyzXWuR1DtB44P91z7NJNDwqVJnyBZBP4NRC9BmE0L807i}
pwn.college{jBTXH82PxgOBgHlpk58rZIMMIKxjAFoTLZQbj.JL2EAnGUC}
pwn.college{6x4wjeIFqhMlvv02ihoZIIcTFL.pvKHaVrVPsZdCEQRfB8i}
pwn.college{N-wgYypNzTHTu9zQ.1lACoWhQs1pkUUVfnW1s-zJy7xVkXz}
pwn.college{hiViQZ53EQmtpimuQXzGaPu2-hdHh.d9pgdOOVul1NofUlC}
pwn.college{N3rlMCp9n6MhbjANHDg.i-yeqVzwdm1t.JZybb7kRJq5yAA}
pwn.college{gUXdm7A9wQjQioJCJA-yXOzyTjYu42saQw6pjnCggURc2he}
pwn.college{Miohx65iMhXt2av7bT6DcTDVCZJo6JbXbsKl.gDKxbryCKr}
pwn.college{efPUSaW4rtU7qjMwjJ8h.jhsdArKkUgjKcfRUQn5aNDnIdI}
pwn.college{5.TAZ9bbqwIDTxvrcE4d1iAy8kghBWY-FL8L.ChnTglBBQM}
pwn.college{peNjlDrb00ySm-9NyUxbozX9PVrbi7Me3xhZN3zEImiHdBA}
pwn.college{3SIrcNL1oZpkyehJsIMVsNKKsLZDQdL21JiqTO0K6yQ7prM}
pwn.college{mGJ0QYcA6PvfmStP-0NBtOBriHxvmuR0bwUFu3MrkpOnGYl}
pwn.college{qcnw3WK8WWRVTcSDcqXetoqRN3UuLZ-kEbfbHKKsgY4ZS6-}
pwn.college{RjNx2-2mCs3cl-waMcyKlNFt6RM622o0Bn3EEKF4Erdc.F.}
pwn.college{hDUZD.aXiLel2p6APZ3rF66VYzoccbVMUKKXYwaF-84fQky}
pwn.college{yZJ5qrZsTMm0yREkbiGeFHYrmXb6P3BkDz3Omvp9UUOU3sX}
pwn.college{6n7YkN8sXqLC2uW7VQ7VFXiUz1.-r1eNbvz38ayW.TDxkoI}
pwn.college{P-seZnKiv8JMif-oONY8sCmYfboF2tBHpzZ09BV7sj5vBAn}
pwn.college{FcZC8Qm0xOOxXzEoyztQAdkSrdVvAt5qMNmMgH0sD4iD6G1}
pwn.college{jXdl0.2b5..C1ukbNgGOCL-wqgTgZv0m-qChPIh2fU9QFaC}
pwn.college{oYrFhUhJ8Bpp037vt1KhDa2fOeY22XMyh2mhiXnSoqIhaJP}
pwn.college{3h2A5NbRDPQdEamLXFVuo5l3wbtSWtP6bjkF8qEfHb11IFp}
pwn.college{cV.md0g00vaV2485paDPJzc.jcIakUNZ6whARQ7qXTBRqh5}
pwn.college{32zvhIP4e8wNmpuZiExN7spcCt695oQ8QbfrmW4fsqaXfrI}
pwn.college{ur9h0.EHCzytBeG27GF46tFUfOeeLOUaRIzyCAJ5-1yay6M}
pwn.college{POSI7XV6RT63vtNFPVLEowXNlT5mgjsM8pl0beu1iXDjhkD}
pwn.college{YPX2bSnZGzDj47kvZomBoTyY9AG3kNMiaJknSRzWIZosrA8}
pwn.college{Md8Ch6kjA.KGz1ekP7I9jfXRPsM4GERe0iAaGoJUVXXNPzU}
pwn.college{ACgE9BlAIdkCY13ifkSrnCrLu1MbBqMMNxX1JD4nr3UAlTk}
pwn.college{GrWIW-QG8KTNlyEEvDz7fB6Mq24a8PxJPwqJ1kgov1xQoYQ}
pwn.college{xbqbQFD2LqO2d.VAF6rd.IIZT91aUQzHIXDywFcQA8nRCeW}
pwn.college{kN7A.Z2FD.twVeKiKqpKfVKJ2.2cv7pOoXVXZ1Y3uwCRH3c}
pwn.college{4yER2FAFHGDx6gAHjFNrr2amwZhc6H8V0eeafi8ADvJHrLX}
pwn.college{facMuk7F6hBEf4-cpLg98-0l38yGHmWYkmJn65WAn5UOzk6}
pwn.college{gNmR-YNWRLtzbhuhJ4XfDqghNYuosBrQ0-n-F-NGPvd-uoV}
pwn.college{aZzkz6hWKAjkJ8qkFSvZjaSr6YrcK5lz18Z56OMCVHQ04kX}
pwn.college{Js4fY739U3CKtYl1i7lOPbcK8NXLbgjLLrnVOklVhwuZbIN}
pwn.college{iUt1jT66UZfyRhsep9CPvQRauLUV8IaeDlh26YS3iewOePf}
pwn.college{w7S9W.Q5ENGhxWCLBP8fwBIWfhfCbXzZQICIsrp.vXytuwZ}
pwn.college{UqzQxRUaV3aWTrsJ37XaK0kigwfynnjy7pgRgB59Skn0gUT}
pwn.college{sfVmjwcdKx7ZQYERXgPN8oWM3OO5J.xmp3CQbELmc7jsUlO}
pwn.college{LZa8gzx4LWi5AeXMGy22iOgxMgTEsGeh3MbBKz55NtRLqyy}
pwn.college{w.3jgsl9YWPOoWXZhZ1.UsHkDaEaxt0TqdTYruKbeYx0rct}
pwn.college{TxWhYpLEy.t9l8qo9AfgAP78us2k3knPUViJAsV2yzLIUt2}
pwn.college{kC-8rOc-Lj7NFUAs3U6Pb9bqU6jzOnfYlsuVnt9gx2UpVlI}
pwn.college{-xpx9Mnw2izxZUWdnIPxWZvKfJN7ff2YNGYY5bbErfQJqfg}
pwn.college{nKu4Sq8z1IrYDoyB6In9aVjXUNMRZcH5-Wpl9LKJA8LxV9u}
pwn.college{XjbWgLlZQAfHwEJYuMFMeAhSEh-gOXHksLy.IhsFD17iRR7}
pwn.college{8jAtjX6i8CYQCeQ9EmQoghGlLYV.aSIgdOdCU..bJzB9AOk}
pwn.college{RxNiqsO-48Z.8RwQPbsn695R0shnZ.N7Tc60PYXtqGk8g3B}
pwn.college{sH8iZAmF4J7EiEYFW6pbyy53hWQtwgmvBuoa3aNTiVTD.8b}
pwn.college{PcJirBVkWFP6vlcraOGL9-HitkdR.DWeQJkYHNGva3pHt5Z}
pwn.college{Y6e.fiO5w15AK4rFbinG1FNuSzYZSDfvr5VuXI1nPEmNloj}
pwn.college{Wb3MUaTqc1-asuTxTXKRqt88Rml6ZYBox7WxBmnFUvUM54q}
pwn.college{3vyevOjhO4XLRziQcsOwstHfkYYEc25DcnBs0LxKw0HAfBq}
pwn.college{jY7ttbGmGdaOEHe-86zE4J2RGEePwzZ0k9t4SP9mBPTcDqo}
pwn.college{p2amcm.yCvttYSJVBZ4zaJsi86uMEPFgYetMVyaFwm94gNi}
pwn.college{5cVRnu4EGsOB4zjadUVObv5P.pxiHkxwPzctVzQWqQWsKAV}
pwn.college{XDGD8eLD.AXsqF4r7g6UGaBJ4a0mTOMmGXuOx9jmRPGh1hy}
pwn.college{265JKA8iuobwNfrdyWahkMiXjnf-XIAQxTOo3.LLNP0lPey}
pwn.college{gwc79auGkq0sSz5PvCt73gTFO2r46S-O3kXD4IZpla54Iwa}
pwn.college{aeMxK349QAwXN0iRW5lxNhQRgeObcwIigT1gG0b.pKoXXU-}
pwn.college{WvtR.COxHorNhEh2iOyE2w4PYhFtyA8tGwc9E64sn3qJadT}
pwn.college{LP3cO1OfgijW7md65P4wBqGAh57Q3iIR2itcbdlpywpN1V0}
pwn.college{YiLR3aGHpVAcjVlUMPMBBUghsMoEaOSzyEL0VGEfZLZtqDI}
pwn.college{cxz2pVX96mS0SwN97BanFnXS5C.MNDmaDJHGywcoj3eq.1s}
pwn.college{ez8aM0wMM6xtUOES-bM9Am6nRLVq9iHZpTaCm9KkG838wJX}
pwn.college{8fbbXs.fD.d19IYAGzvM8NvvZL4CJMVbyKhZrJqv636.vzA}
pwn.college{ptwEUR2S62CY0MJwfz7MNTt4oTMcytjpPdGPZLNMsfdm45.}
pwn.college{mU5wKQ20gDXdLNR-GXQx4ROMZ9qwgMpGDFSYuOmPE6BY2U4}
pwn.college{RDp6k1j31DQmAqSl-d0ksW.AXiJCryKn5RgKu0UFPzBRPMX}
pwn.college{ypYNFvh37N9znWLKodqIq6vdKn9zVEq4fjLqtnvadQ47iMS}
pwn.college{4Jom1EwRkrIHc9M7.-8zBgm8bG5XtkmvxC-VXYjV3mNug2N}
pwn.college{1HR1i6aj..DNjndivW-vg6BgPEoBylVRVPTRHAPDO6nRIXy}
pwn.college{aZuBHlN6ZvzkDc7DPsO3JuhDK6xULHVQ43WDHIgNCAIkhkD}
pwn.college{tk7x-4P4z6nnavXRXTVZpawtSzT-1aobGl-Kg98i5RKZY1.}
pwn.college{fmqLrlWIM6z69D-AmrtSCVqY2inNAjwgRrgURxbua87ESzZ}
pwn.college{6fZCFTpSf4aGMwR79mj7C915W1Mx7fTlCUO3tQmU0JkH7d3}
pwn.college{Y8us64mwMdIb9WX7UCf3ypr0vGtLBgMQmTz4YdTiU1i.WfQ}
pwn.college{hVAFn5vcLQZcN1wDDrth2SpOLXg-bwQCGlFvWNjCUE8Yqfi}
pwn.college{o.iphenbBSIXxy.DuOxZzt-vpaBY.0w6z7OmjrKdhg-DgHL}
pwn.college{O9YCvp12KaP-SWecC21XCv-qxJAhHlvAnSAxVufCWHKyJhs}
pwn.college{tzeEiSDMqef.ydHot5nQDhAHDGLeD9.CjUSAqi4dc9LJuwR}
pwn.college{LERGUWvzWG69LHJp0zrNysH2ZgEXa0.eRbPfwBxjV4nGINK}
pwn.college{QvfKbtVUQy8.04CFwdJ.nScVXYcpRErWPeNFG8TVlod2kPS}
pwn.college{menXnSU6s6QMvHnA52DgQQQxo6RtbzecktFZeSacHBGpS6p}
pwn.college{Pdw2sIKStWQvCQU6WqcGMKMm3i3Rj7m6hGvfEHFygho8LFv}
^C
hacker@processes~killing-misbehaving-processes:~$ ^C
hacker@processes~killing-misbehaving-processes:~$ /challenge/run
Sending the flag to /tmp/flag_fifo!
hacker@processes~killing-misbehaving-processes:~$ cat /tmp/flag_fifo
pwn.college{8lwFeWE6oX1g7eLbjbEm1GXDFlK.0FNzMDOxwSM5kjNzEzW}

```

## What I learned 
> Linux pipes are buffered, they have a sort of length through which data flows. If the data already entered the pipe, it flows through the end (till my cat) despite being killed.

# 5. Suspending processes
> This challenge is similar to interrupting processes, it tells us how to suspend processes.

## My solve
**Flag:** `pwn.college{cH2OE8mggfkKUCDxlqwuCYNEnnU.QX1QDO0wSM5kjNzEzW}`
```bash
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in 
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         146     136  0 18:50 pts/0    00:00:00 bash /challenge/run
root         148     146  0 18:50 pts/0    00:00:00 ps -f

I don't see a second me!

To pass this level, you need to suspend me and launch me again! You can 
background me with Ctrl-Z or, if you're not ready to do that for whatever 
reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in 
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         146     136  0 18:50 pts/0    00:00:00 bash /challenge/run
root         153     136  0 18:50 pts/0    00:00:00 bash /challenge/run
root         155     153  0 18:50 pts/0    00:00:00 ps -f

Yay, I found another version of me! Here is the flag:
pwn.college{cH2OE8mggfkKUCDxlqwuCYNEnnU.QX1QDO0wSM5kjNzEzW}
```

## What I learned 
> Ctrl + Z can be used to suspend process. A copy of a suspended process can be ran at the same time in the same terminal.

# 6. Resuming Processes
> This challenge tells us how to resume suspending processes.

## My solve
**Flag:** `pwn.college{AeQDB39G9W2Th54fi1OI2MsgOz-.QX2QDO0wSM5kjNzEzW}`
```bash
hacker@processes~resuming-processes:~$ /challenge/run
Let's practice resuming processes! Suspend me with Ctrl-Z, then resume me with 
the 'fg' command! Or just press Enter to quit me!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~resuming-processes:~$ fg
/challenge/run
I'm back! Here's your flag:
pwn.college{AeQDB39G9W2Th54fi1OI2MsgOz-.QX2QDO0wSM5kjNzEzW}
Don't forget to press Enter to quit me!
```

## What I learned 
> The 'fg' command is used to resume suspended processes. I experimented a bit and I found out that if there are multiple copies of a suspended proess, fg resumes the one that was suspended first.

# 7. Backgrounding Processes
> This challenge tells us 

## My solve
**Flag:** ``
```bash

```

## What I learned 
> The 

  
