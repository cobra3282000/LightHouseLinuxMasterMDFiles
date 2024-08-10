# Loops in Bash

Loops are fundamental constructs in programming that allow you to execute a set of commands repeatedly. In Bash scripting, loops are essential for automating repetitive tasks, processing multiple files, and working with data structures. This tutorial will cover the three main types of loops in Bash: for loops, while loops, and until loops.

## 1. For Loops

The 'for' loop is used to iterate over a list of items or a range of values.

Syntax:
```bash
for variable in list
do
    commands
done
```

Examples:

- Iterating over a list of items:
```bash
for fruit in apple banana orange
do
    echo "I like $fruit"
done
```

- Iterating over a range of numbers:
```bash
for i in {1..5}
do
    echo "Number: $i"
done
```

- C-style for loop:
```bash
for ((i=0; i<5; i++))
do
    echo "Count: $i"
done
```

- Iterating over files in a directory:
```bash
for file in *.txt
do
    echo "Processing $file"
    # Add commands to process each file
done
```

## 2. While Loops

The 'while' loop executes a set of commands as long as a given condition is true.

Syntax:
```bash
while condition
do
    commands
done
```

Examples:

- Basic while loop:
```bash
count=1
while [ $count -le 5 ]
do
    echo "Count: $count"
    ((count++))
done
```

- Reading input until a condition is met:
```bash
while read -p "Enter a number (0 to exit): " num
do
    if [ "$num" -eq 0 ]; then
        echo "Exiting..."
        break
    fi
    echo "You entered: $num"
done
```

## 3. Until Loops

The 'until' loop is similar to the while loop, but it executes commands until a condition becomes true.

Syntax:
```bash
until condition
do
    commands
done
```

Example:

```bash
count=1
until [ $count -gt 5 ]
do
    echo "Count: $count"
    ((count++))
done
```

## 4. Loop Control Statements

Bash provides two main loop control statements:

- break: Exits the loop immediately
- continue: Skips the rest of the current iteration and moves to the next one

Example using both:
```bash
for i in {1..10}
do
    if [ $i -eq 5 ]; then
        continue
    fi
    if [ $i -eq 8 ]; then
        break
    fi
    echo "Number: $i"
done
```

## 5. Advanced Loop Techniques

- Nested loops:
```bash
for i in {1..3}
do
    for j in {1..3}
    do
        echo "i=$i, j=$j"
    done
done
```

- Looping through arrays:
```bash
declare -a fruits=("apple" "banana" "orange" "grape")
for fruit in "${fruits[@]}"
do
    echo "I like $fruit"
done
```

- Infinite loops (use with caution):
```bash
while true
do
    echo "This will run forever unless interrupted"
    sleep 1
done
```

- Looping with command substitution:
```bash
for line in $(cat file.txt)
do
    echo "Line: $line"
done
```

- Parallel execution of loops:
```bash
for job in job1 job2 job3
do
    (
        echo "Starting $job"
        sleep 2
        echo "Finished $job"
    ) &
done
wait
echo "All jobs completed"
```
