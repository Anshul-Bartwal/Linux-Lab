# Lab 4
## File text operators
[ -e $file1 ]

0: true

1: false

- #### -f
    Is regular?
- #### -r
    Readable?
- #### -w
    writable
- ####

- #### -nt
    Newer than
    syntax
    ```bash
    [$file1 -nt $file2]
    ```
- #### -ot
     Older than
- #### -et
    same file or not


## Command line Argument
bash file
``` bash
echo "Hello $1 $2"
```
in terminal
``` 
./greet.sh one two three
```
output
```
Hello one two
```

here 

space seperated inputs

these are positional arguments

$0: name of file


$1: first argument

.

.

.


after 9 $(10...)

$@ : all arguments

$# : number of agruments

here `$?` : last executed argument

``` 
./file.sh a b c d e f
```

file.sh
```bash
echo "$1" #! output : a
echo "$2" #  output : b 
echo "$@" #  output : a b c d e f
echo "$#" #  output : 6
``` 


## Arrays
- #### Indexed array
``` bash
# 1 
fruits=["these are space seperated" "element2" "element3"]
#2
fruits2[0]:"element 1"
fruits2[1]:"Eleement 2"

#3 to print we use 
echo ${(fruits[0])}
# print every elemnt
echo ${fruits[@]}
```

- #### Associated Array (Dictionary)
```bash
declare -A Capitals
Capitals["India"]="New Delhi"
Capitals["Abc"]="Def"

# print every elemnt
echo {Capital[@]}
# or
echo {Capital[*]}
# print every key

echo ${!Capitals[@]}
#or
echo ${!Capitals[*]}
```
- ##### Length of arrays
```bash
echo ${#fruits[@]}
echo ${!#Capitals[@]}
echo ${#Capitals[@]}
```
- #### adding 
```bash
fruits+="cherry" "strawberry"
#This updates the element at index 1
fruits[1]="Guava"
Capitals["Germany"]="Berlin"
```
- #### removing
```bash
unset fruits[0]
unset Capitals["Germany"]
```
## Array slicing
```bash
a=["a" "b" "c" "d" "e"]
#echo ${a[@]:Starting point:no of elements}
echo ${a[@]:0:3}
# output 
# a b c

echo ${a[@]::3}
# means starts from start and 3 elements

echo ${a[@]:2:}
# start from 2 till end
```
### conditional  statements
##### if elif else
```bash
if [ $x -gt 5]; then
        x=x+5
        echo "$x"
elif [ $x -lt 5 ]; then
        x=x-5
        echo "$x"
else
        echo "x is 5"
fi
```

##### case statement
```bash
day="Mon"
case $day in
        "mon") echo "monday";;
        "tue") echo "tuesdY";;
        "SAT"|"sun") echo "weekend";;
        *) echo "other day";;
```
###### shortcut
```bash
x=8
[ $x -gt 10 ] && echo "x is big" # if condition is true execute
[ $x -le 10 ] || echo " x is not big than 10"   # if condition is false execute
