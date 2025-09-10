# Lab 5
## Loops
Three types
- While
- Until 
- For 


### **While**
- works while condition is true
- works untill condition is false
```bash
i=0
while [$i -le 4]
do 
    echo "$i"
    i=$((i+1))
done

```
### **Until**
- works while condition is false
- works untill condition is true
```bash
i=0
until [ $i -gt 4 ] # jb tk i is not gt 4 tb tk 
do
    echo "$i"
    i=$((i+1))
done
```

### **For**
```bash
for i in 1 2 3 4
do 
    echo "$i"
done
```
```bash
#fruits ={"Apple" : 3,
#          "Mango" : 5,
#          "Cherry" : 15}

for i in {fruits[@]}
do 
    echo "$i"
done
```
Output
```
3 
15 
5 
```
because in *associated array* values are stored in *alphabetical order* of keys.

```bash
for ((i=0,i>=10,i++))
do 
    echo "$i"
done
```

### Control Statement
- break
- continue

same as C i guess
- exit
    - takes out of program not just loop
    - exit 0 : success
    - exit 1 : failure
    eg
```bash
for i in {1..10}
do
    if [ $i -eq 5 ]
    then 
        exit 
    fi
    echo "$i"
done
```
## Functions

### Defination

```bash
greeting()
{
    echo "Hello World"
}
```

### Calling

```bash
greeting
```
### Function with arguments
```bash
greeting()
{
    echo "Hello $1"
}
```
Calling
```bash
greeting "User"
```
### return
```bash
add()
{
    sum=$(($1+$2))
    return $sum
}
```
Calling
```bash
#
add 3 5
echo "Sum is $?" 
# here $? will give return value of last executed command
``` 
#### to catch in a variable
```bash
add()
{
    sum=$(($1+$2))
    echo "$sum"
}
```
Calling
```bash

sumis=$(add 3 5)
echo "Sum is $sumis"
```

