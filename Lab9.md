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



## processes
- current process
```bash
PID=$$
```

- previous process
```bash
$!
```
- parent process
```bash
$PPID
```

- ### user runnung the process
```bash
$USER
```
---
- top 5 cpu process
```bash
ps -eo pid,comm,%cpu,%mem --sort=-%cpu | head -n 6
```
- this means
    - ps: process status
    - `-e` to select all processes even outisde terminal
    - `-o` to select what we need to show columns
    - pid: process id , comm: command(what is running)
    - `--sort` to sort
    - `--sort=-%cpu` sort according to %cpu but `-` means descending 
    - `| head -n 6`: take the output and printf 6 lines (5 process and 1 header)

- ### monitoring processes
```bash
    #making dummy process
    sleep 500&
    dummyPID=$!
    #monitoring it
    ps -p dummyPI -o pid,comm,%cpu,%mem,etime

```
- this means
    - `-p`: it is used to search process by PID

- ### killing process
kills by PID
```bash
kill $PID
```
kills by NAME/PATTERNS
```bash
pkill $NAME
```



