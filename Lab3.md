# LAB - 3
## Shell Scripting
User is communicating with kernel of os
### Shell 
- Acts as bridge b/w user and kernel
- command line interpreter
- ### Bash (Bourne again shell)
    - it combines features of sh csh and ksh
    - use ```ps``` to find which shell you have
- ### How to start
    - Open filename.sh in vior nano
    - ``` #!/bin/bash``` : comment
    - ``` echo "Hello World"```
    - Check the permission to execute
    - ```./hello.sh``` to run the file
- ### Variable
- ##### Rules
    - (A-z)and(0-9)and _
    - cant start as digit
    - ``` n = 5``` is not vaild
        -  ```n=5``` is  valid as no redundant space is present
    - cant be a keyword
    - to access variable 
        - ``` echo "$n" ```
- readonly : makes variable readonly so we cant change its value
    - ``` readonly n=5```
### Input
- ```read```
- And ``` read -p "print something" num```

### Operators
- ``` echo "$((a+b))"```
- For floats:
    - For floating point operations, use the `bc` command:
        - ```echo "scale=2; a/b" | bc```
        - `scale=2` sets the number of decimal places.
        - `bc` means basic calculator used for float calculations.
        - Example:
            - ```echo "scale=2; 5/2" | bc``` outputs `2.50`
- "++ and --"
    it has pre and post
    - ```a++``` means Post increment
        
        - Put value of a in place of a++ and then change the value of a to a+1
    - ```++a``` means pre increment
        - first add 1 to a then put the new value in place of ++a
- #### SAME FOR DECREMENT
- ### Relational operators
- Old method  Working with []
    - here 0:True , 1: False
    ```bash
    [ $a -eq $b ]
    echo "a==b : $?"
    ```
    - `-eq` : equal
    - `-ne` : not equal
    - `-gt` : greater than
    - `-lt` : less than
    - `-ge` : greater than or equal to
    - `-le` : less than or equal to
    - #### Wont work on float works on just int
- New Methods working with(())
    - here 0: False 1: True
    ```bash
    echo "a==b $((a==b))"
    ```
    for floats:
    ```bash
    echo "a==b $(echo "($a==$b)"|bc)"
    ```
- ### Logical Operators
```bash
# 0:True 1:False
[ $a -eq $b] && [ $a < 1 ]
echo "Logical AND $?"
[ $a -eq $b] || [ $a < 1 ]
echo "lOGICAL OR $?"
! [ $a -eq $b]
echo "Logical NOR
```
- ### Bitwise Operators
Works with integers
``` bash
a=3
b=5
echo "BITWISE AND: $((a&b))"
echo "BITWISE OR: $((a|b))"
echo "BITWISE NOT: $((~a))"
echo "BITWISE XOR: $((a^b))"


11111101 in 8 bit 
```
### trick 😏
- `~(x)` x is number
    - ~(x) =-x-1




