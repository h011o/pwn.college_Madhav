# Challenges
1. Launching Screen
2. Detaching and Attaching
3. Finding sessions
4. Switching Windows
5. Detaching and attaching (tux)
6. Switching windows (tmux)
   
# 1. Launching screen

## My solve
**Flag:** `pwn.college{sck2KQX3VZt4a0Gx83ikA0R__Z8.0VN4IDOxwSM5kjNzEzW}`
```bash
Congratulations! You're inside a screen session!
Here's your flag:
pwn.college{sck2KQX3VZt4a0Gx83ikA0R__Z8.0VN4IDOxwSM5kjNzEzW}
```

## What I learned 
> screen is a program that creates virtual terminals inside your terminal. It's somewhat like having multiple browser tabs, but for your command line.

# 2. Detaching and Attaching

## My solve
**Flag:** `pwn.college{U2Z9euRtzFinPiE8W2Jocn4aOir.0lN4IDOxwSM5kjNzEzW}`
```bash
hacker@terminal-multiplexing~detaching-and-attaching:~$ echo Yes! Flag is: pwn.college{U2Z9euRtzFinPiE8W2Jocn4aOir.0lN4IDOxwSM5kjNzEzW}
Yes! Flag is: pwn.college{U2Z9euRtzFinPiE8W2Jocn4aOir.0lN4IDOxwSM5kjNzEzW}
```

## What I learned 
> I learned how we can attach and deattach screens on the linux terminal.

# 3. Finding sessions

## My solve
**Flag:** `pwn.college{U2Z9euRtzFinPiE8W2Jocn4aOir.0lN4IDOxwSM5kjNzEzW}`

The flag was in PID 150.

```bash
hacker@terminal-multiplexing~finding-sessions:~$  echo 'Congratulations! You found the right session!'
Congratulations! You found the right session!
hacker@terminal-multiplexing~finding-sessions:~$  echo pwn.college{87b7k_3ZRIJlJsXUOhP9vx4aUOo.01N4IDOxwSM5kjNzEzW}
pwn.college{87b7k_3ZRIJlJsXUOhP9vx4aUOo.01N4IDOxwSM5kjNzEzW}
```

## What I learned 
> I learned how we can find screens using the ls command and attach to specific ones using their PID.

# 4. Switching Windows

## My solve
**Flag:** `pwn.college{U2Z9euRtzFinPiE8W2Jocn4aOir.0lN4IDOxwSM5kjNzEzW}`

The flag was in PID 150.

```bash
hacker@terminal-multiplexing~switching-windows:~$  cat <<MSG
> Excellent work! You found window 0!
> Here is your flag: pwn.college{w5VvBtyPWyVqjcQ_errRh2PsXIn.0FO4IDOxwSM5kjNzEzW}
> MSG
Excellent work! You found window 0!
Here is your flag: pwn.college{w5VvBtyPWyVqjcQ_errRh2PsXIn.0FO4IDOxwSM5kjNzEzW}
hacker@terminal-multiplexing~switching-windows:~$ 
```

## What I learned 
> Inside a single screen session, you can have multiple windows, like your browser has multiple tabs. We use Ctrl+A followed by c/n/p/0 to navigate through the screens.

# 5. Detaching and Attaching (tmux)
> This challenge asks you to attach and detach from tmux to get our flag. 

## My solve
**Flag:** `pwn.college{I1957zNO8vq4OHEepb8svlW0P1-.0VO4IDOxwSM5kjNzEzW}`


```bash
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$  echo Congratulations, here is your flag: pwn.college{I1957zNO8vq4OHEepb8svlW0P1-.0VO4IDOxwSM5kjNzEzW}
Congratulations, here is your flag: pwn.college{I1957zNO8vq4OHEepb8svlW0P1-.0VO4IDOxwSM5kjNzEzW}
```

## What I learned 
> I learned how tmux is basically the modern version of screen for the linux terminal. And how to attach and detach using Ctrl + B.

# 6. Switching Windows (tmux) 

## My solve
**Flag:** `pwn.college{48WJXAAkkAmOrgDhGPK3OLjZbmy.0FM5IDOxwSM5kjNzEzW}`


```bash
hacker@terminal-multiplexing~switching-windows-tmux:~$  cat <<MSG
> Excellent work! You found window 0!
> Here is your flag: pwn.college{48WJXAAkkAmOrgDhGPK3OLjZbmy.0FM5IDOxwSM5kjNzEzW}
> MSG
Excellent work! You found window 0!
Here is your flag: pwn.college{48WJXAAkkAmOrgDhGPK3OLjZbmy.0FM5IDOxwSM5kjNzEzW}
```

## What I learned 
> I learned how to navigate through tmux screens in the linux terminal







