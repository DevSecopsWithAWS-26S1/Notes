# Shell scripting

Shell scripting stores Linux commands in a `.sh` file and runs them in sequence.

| Tool | Extension |
|---|---|
| Shell | `.sh` |
| Python | `.py` |
| JavaScript | `.js` |
| Java | `.java` |

## Hello world

Create `hello.sh`:

```bash
#!/bin/bash
echo "Hello world"
```

Run it:

```bash
chmod +x hello.sh
./hello.sh

# Or run it without executable permissions
bash hello.sh
```

`#!` is the shebang. It tells the operating system which interpreter to use.

## Variables

```bash
#!/bin/bash
person1="Krishna"
person2="Teja"

echo "$person1: Hi $person2"
echo "$person2: Hi $person1"
```

Syntax:

```bash
variable_name="value"
echo "$variable_name"
```

## Command arguments

Arguments passed when a script runs are available as `$1`, `$2`, and so on.

```bash
#!/bin/bash
person1=$1
person2=$2

echo "$person1: Hi $person2"
echo "$person2: Hi $person1"
```

```bash
./arguments.sh Krishna Teja
```

## Arithmetic

```bash
#!/bin/bash
number1=10
number2=20
sum=$((number1 + number2))

echo "The sum of $number1 and $number2 is $sum"
```

## Read user input

```bash
#!/bin/bash
echo "Enter Number 1:"
read number1

echo "Enter Number 2:"
read number2

sum=$((number1 + number2))
echo "The sum is $sum"
```

Use `read -s` to hide input, for example when reading a password.

```bash
echo "Password:"
read -s password
```

## Bash data types

Bash variables do not require explicit type declarations.

| Data type | Example |
|---|---|
| String | `name="Sam"` |
| Integer | `age=20` |
| Array | `colors=("red" "blue")` |
| Boolean-style value | `is_ready=true` |

Access values:

```bash
echo "$name"
echo "$age"
echo "${colors[0]}"
echo "$is_ready"
```
