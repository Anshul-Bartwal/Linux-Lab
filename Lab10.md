# Process scheduling
- Way to allocate diff. time /timespan by the machine to different processes
- two types of processes: nomral and realtime
```bash
ps -eo pid,comm,cls,pri,ni,rtprio```
```

```
     PID COMMAND        CLS PRI  NI RTPRIO
      1 systemd          TS  19   0      -
      .
      .
      .
     21 migration/0      FF 139   -     99
     .
     .
     .
   3488 tracker-miner-f IDL   0   -      0
```
- cls: class of scheduling algroithm :TS,FF,RR,IDLE

    - TS: CFS(Completely Fair Scheduler) 
        - normal process have TS these have nice value but no RTPRIO
    - FF: First In first Out
        - realtime process can have FF 
    - RR: Round Robin
        - realtime process can have RR
    - IDLE

- pri: kernel level priority (user can interfere)

- ni: nice value(range: [-20,+19])

- RTPRIO : Real time priority
    - for real time  process
    - range[+1,+99]
    - RTPRIO directly proportional to priority

---
Process Scheduling

|-> Fair Distribution

|-> Minimize the CPU idle time

|-> Priority

|-> Maximum Throughput( completed tasks/sec )

|-> Scalability

## algos
- CFS (Completely Fair Scheduler)
    - for normal processes

    - At any instance of time CPU time is given to the function with least vruntime adjusted by their priority
    - lower nice -> higher priority --- vruntime increases slower
    - E D C B A -> pick anything randomly 
        - Lets say A got 10 sec to run at first
        - vruntime of A = 10

    at cpu 10 sec we got 
    - vruntime
        - A:10
        - B C D E : 0
    - now send back A to queue
        - now lets say that B got 5 secs now

    at cpu 15 sec we got
    - vruntime
        - A:10
        - B:5
        - C D E:0
    - and it goes lol

    at cpu 90 sec we got
    - vruntime
        - A: 18
        - B: 15
        - C: 20
        - D: 17
        - E: 20

    - NOW it see that B have the lowest vruntime so B gets chance to run  
    - and it runs like this when there is a tie its picks randomly like we did in first two examples

    if cpu cycle is 120 so it should be Fairly distributed i.e each process get nearly same time

- FF : First in First Out 
    - IF Process starts then it ends then the next will get chance

- Round Robin :  
    - it sorts with priority
    - process gets a time slice 
        - eg C has highest priority
        - C works for 12 sec and then goes back to queueu
        - 2nd highest prioirty process runs and all



```bash
sudo chrt -r -p 70 $PID
```

- 70 means Priority of it 
- -r means round robin
so here we are chanign ot to RR wit h prioirty 70 -> rtprio:70

if we dont give 70 value then the process isnt changed so we need to give it its important
- -f means FF


## Process Signals
- SIGTERM: by default generated when kill is used without telling any signal
    - it requests to terminate the process
    - not an ultimatum
    - graceful Termination

- SIGKILL
 ```bash
kill -9 1234
```
maaaro maaro maaro 
- SIGINT
    - `-2`
    - signal to interrupt the process
    - ^C

- SIGTSTP
    - `-20`
    - ^Z
    - Stops the process for some time
    - it can be reinitated

- SIGHUP - signal hang up
    - we canstop process and start from that checkpoint
- SIGCHLD
    - for killing the child of parent
    - it sends the info to parent process

## Handling prcess Signal
```bash
#!/bin/bash
trap 'echo "Ctrl+C is received";sleep 11' SIGINT # it traps SIGINT SO we cant stop this with ^C or SIGINT 
while true;do
        echo "Running"
        sleep 2
done
```

- SIGTSTP
    - we can continue the process after pressing CTRL+Z by using 
        - `bg` : send it to background : it cant be stopped using CTRL Z
        - `fg` : send it to foreground: it can be stopped using CTRL Z 
    
## Process Monitoring and Resource Usage
`top` : taskmanger

`htop`: better colourfull and scrollable task manager

`vmstat 5`: virtual memory stat after every 5 sec stop
- `procs -----------memory---------- ---swap-- -----io---- -system-- -------cpu-------`

- `r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa st gu`


`vmstat 2 10` : virtual memory stat after every 2 sec but 10 times only

`iostat 2 10` : io stat after every 2 sec gap 10 times 
- `Device             tps    kB_read/s    kB_wrtn/s    kB_dscd/s    kB_read    kB_wrtn    kB_dscd`

## Jobs :(

- all the processes a shell runs 
```bash
#!/bin/bash
sleep 60&
PID1=$!
jobs
echo "HEllo Linux"
PID2=$!
jobs
```

## Inter Process Communication
reader:

```bash
VirtualBox:~/Desktop/test$ mkfifo mypipe
VirtualBox:~/Desktop/test$ cat mypipe
VirtualBox:~/Desktop/test$ cat mypipe
Hello Linux
VirtualBox:~/Desktop/test$
```
writer:

```bash
VirtualBox:~/Desktop/test$ echo "Hello Linux" > mypipe
```

`mkfifo` : creates pipe b/w reader and writer 
