# Strings
### Concatination
```bash
a="hello"
b="world"
echo "$a $b"
```
- Prints `hello world`

###
- strings is just array

### slicing
```bash
# substring

${a[@]:0:3}
```
- will give `hel`
### replace
```bash
str="I Love Linux"
echo ${str/Linux/C}
#array/word to be replaced / word to replace with

```

### compare
```bash
a="hello"
b="Hello"
```
#### Equal
```bash
if [ $a = $b ];then
    echo "Equal"
fi
```

- it is case sensitive

#### Less than/greater than
```bash
if [$a > $b]; then
    echo "$a"
else
    echo "$b"
fi
```
- it compares ascii values
- since smaller chars have higher ascii therefore output `hello`

### tr 
- it means translate

``` bash
echo "hello world"|tr 'a-z' 'A-Z'
##################|tr 'what to translate' 'to what to translate'

```
Output: `HELLO WORLD`

### rev
```bash
echo "Hello World"| rev
#reversed
```
Output : `dlrow olleH`


### redirection
```bash
a=$(echo "Hello")
echo "$a"
```
### empty ad not emptys
```bash
str=""
if [ -z $str ];then
    echo "Empty"
fi
```
---

- not empty
```bash
if [ -n $str ]; then
    echo "Not Empty"
fi
```