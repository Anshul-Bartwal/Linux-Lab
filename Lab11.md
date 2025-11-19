# Process Synchronization
## Data Race
```bash
#!/bin/bash
LOGFILE="shared.log"
LOCKFILE="shared.lock"

echo "Process with pid $$ writing at $(date)">>"$LOGFILE"
sleep 5
echo "Process with pid $$ ended writing ar $(date)">>"$LOGFILE"
```
```bash
./sync.sh&
[1] 4789
./sync.sh&
[2] 4799
./sync.sh&
[3] 4803

[1]   Done                    ./sync.sh
[2]-  Done                    ./sync.sh
[3]+  Done                    ./sync.sh

cat shared.log
Process with pid 4789 writing at Wed Nov 19 12:31:44 PM IST 2025
Process with pid 4799 writing at Wed Nov 19 12:31:45 PM IST 2025
Process with pid 4803 writing at Wed Nov 19 12:31:45 PM IST 2025
Process with pid 4789 ended writing ar Wed Nov 19 12:31:49 PM IST 2025
Process with pid 4799 ended writing ar Wed Nov 19 12:31:50 PM IST 2025
Process with pid 4803 ended writing ar Wed Nov 19 12:31:51 PM IST 2025

```
here data is written in this shared but instead of waiting for one write to finish other write starts with it

- With Locking
```bash
#!/bin/bash
LOGFILE="shared.log"
LOCKFILE="shared.lock"
(
        flock -x 200
        echo "Process with pid $$ writing at $(date)">>"$LOGFILE"
        sleep 5
        echo "Process with pid $$ ended writing ar $(date)">>"$LOGFILE"
) 200>"$LOCKFILE"
```
after running these 3 times
```bash
Process with pid 4871 writing at Wed Nov 19 12:40:10 PM IST 2025
Process with pid 4871 ended writing ar Wed Nov 19 12:40:16 PM IST 2025
Process with pid 4877 writing at Wed Nov 19 12:40:16 PM IST 2025
Process with pid 4877 ended writing ar Wed Nov 19 12:40:21 PM IST 2025
Process with pid 4885 writing at Wed Nov 19 12:40:21 PM IST 2025
Process with pid 4885 ended writing ar Wed Nov 19 12:40:26 PM IST 2025
Process with pid 4889 writing at Wed Nov 19 12:40:26 PM IST 2025
Process with pid 4889 ended writing ar Wed Nov 19 12:40:32 PM IST 2025
```


`flock -x 200`
- -x : execution mode
    - if we have p1 p2 and o3 sharing a resource 
    - now using -x will make sure that once p1 has locked it other cannot do anyting in this
- 200: file descriptor
    - pointer to file 
    - we use 200 conventionally to synchronization

- -n : non blocking mode
    - instead of blocking like -x it doesnt block it goes like
    - can you write 
        - YES : then write
        - NO : dont write lol

## Deadlock
- when two process are waiting indefintely for resource
## load avg

run `uptime`
we will get like **uptime details** then 
 - load average: 5,7,8 # or something
    - these are 1/5/15

    - it means 
        - first value is avg for last 1 min
        - 2nd value is avg for last 5 min
        - 3rd value is avg for last 15 min
