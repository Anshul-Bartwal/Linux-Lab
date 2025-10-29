# Process
 We need to identify process
## Identifiers
- PID: Process Id
- PPID: Parent PID
- UID: User ID (unique for every user)


Process thingy 
- Resources 
    - CPU time, memory
        

- States 
    - Running, sleeping, stopped, waiting, zombie, k*lled


- Priority/NICE value 
    - range [-20,+19]

    - high number means low prioirty
    
    inverse relation



Another Process thngy
```bash
echo "Hello"
sleep 60&
echo "World"
```

Killing process
`kill PID`

SIGKILL : KILLS WITHOUT SAVING

`kill -9 PID`



