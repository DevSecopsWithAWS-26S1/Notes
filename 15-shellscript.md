# Scripting:
* coding is developing the application
* scripting is automating the daily / repetetive activities. 

* Native linux - shell scripting 
* python for scripting 


* nodejs - .js 
* pyhton - .py
* java - .java 
* html - .html
* shell - .sh 

* In simple words , shell scripting in listing your linux commands in a file of extension .sh and run it .

* touch test.sh

* #! - shebang and helps your script to tell which interpreter you are using 
* /bin/sh  
* /bin/bash 

* 1-helloworld.sh 

```
#! /bin/bash
echo "Helloworld"
```
* run the script 
```
./1-helloworld.sh
/bin/bash 1-helloworld.sh
```

* 2-discussion.sh :

```
#! /bin/bash
echo "Krishna : Hi Teja , How are you ?"
echo "Teja : Hi Krishna , I'm good . How about you ? "
echo "Krishna : Thanks for aksing . I'm good too."
```

* 3-variables.sh

```
#! /bin/bash
person1=krishna
person2=Teja
echo "$person1 : Hi $person2 , How are you ?"
echo "$person2 : Hi $person1 , I'm good . How about you ? "
echo "$person1 : Thanks for aksing . I'm good too."


# DRY - Do not repeat yourself 
# variable 
# syntax : variabalename=variablevalue
# call : $variablename
```


* 4-arguments.sh

```
#! /bin/bash
person1=$1
person2=$2
echo "$person1 : Hi $person2 , How are you ?"
echo "$person2 : Hi $person1 , I'm good . How about you ? "
echo "$person1 : Thanks for aksing . I'm good too."


# DRY - Do not repeat yourself 
# arguments  
# syntax : person1=$1 , person2=$2
# Pass the value to the argument while running script : ./4-arguments.sh Elonmusk trumph 
```

* Adding two numbers :

    * Algorithm:
    ```
    number1=10
    number2=20
    sum=number1+number2
    ```
    * scripting: 5-add.sh

    ```
    number1=10 
    number2=20
    sum=$(($number1 + $number2))
    echo " The sum of $number1 * $number2 is : $sum "
    ```
* 5-add.sh
```
#! /bin/bash 
number1=10
number2=20
sum=$(($number1 + $number2))
echo "The sum of $number1 &  $number2 is : $sum "
```

* 6-read.sh
```
#! /bin/bash 
echo "This script will add two numbers. Please provide the value below "
echo "Please enter Number1 value:"
read -s Number1
echo "Please enter Number2 value:"
read -s Number2
sum=$(($Number1 + $Number2))
echo "The sum of $Number1 &  $Number2 is : $sum"

# Hide user input : read -s 
```

* 7-userauth.sh

```
#! /bin/bash 
echo "Username: "
read Username
echo "Password: "
read -s Password 
echo "User input values are $Username & $Password"
```

## Data types :
1.String 
```
person1=krishna
```
2.Integer
```
number1=10
```
3.Array
```
fruits=("banana","apple","mango")
```
4.Boolean
```
True/False
```

* In shell scripting no need to defins the data data 
```
int var=4
string name=teja 
array fruits = 
```

# Bash Data Types

| Data type | What it stores | Example |
|---|---|---|
| String | Text | `name="Sam"` |
| Integer | A whole number | `age=20` |
| Array | A list of values | `colors=("red" "blue")` |
| Boolean | True or false, usually stored as text | `is_ready=true` |

## Using the Values

```bash
echo "$name"
echo "$age"
echo "${colors[0]}"
echo "$is_ready"
```