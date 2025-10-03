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
