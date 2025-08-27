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
- "++ and --"
    it has pre and post
    - ```a++``` means Post increment
        
        - Put value of a in place of a++ and then change the value of a to a+1
    - ```++a``` means pre increment
        - first add 1 to a then put the new value in place of ++a
- #### SAME FOR DECREMENT






