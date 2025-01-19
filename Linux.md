# Linux (Ubuntu)

## Index
1. [Common Linux Commands](#common-linux-commands)
2. [Shell Scripting Basics](#shell-scripting-basics)
3. [Programs](#programs)

---

## Common Linux Commands
| **Command**        | **Purpose / Use**                                                                                          | **Example**                                 |
|---------------------|----------------------------------------------------------------------------------------------------------|---------------------------------------------|
| `pwd`              | Displays the current working directory.                                                                   | `pwd`                                       |
| `date`             | Displays the current date.                                                                                | `date`                                      |
| `man`              | Displays the manual for a specified command.                                                              | `man ls`                                    |
| `cal`              | Displays the calendar.                                                                                    | `cal`                                       |
| `mkdir`            | Creates a new directory.                                                                                  | `mkdir new_folder`                          |
| `ls`               | Shows the list of all files in a directory.                                                               | `ls -l`                                     |
| `clear`            | Clears the terminal.                                                                                      | `clear`                                     |
| `cd <name>`        | Changes the current working directory to the specified one.                                               | `cd Documents`                              |
| `cd ..`            | Navigates to the parent working directory.                                                                | `cd ..`                                     |
| `cat`              | A multifunctional command used to display, write, concatenate, and copy files or change the content of a file. | `cat file.txt`                             |
| `cat <filename>`    | Displays the contents of a file.                                                                          | `cat myfile.txt`                           |
| `cat > filename`   | Creates a new file and allows content to be written to it.                                                 | `cat > newfile.txt`                        |
| `cat >> filename`  | Adds content to an existing file.                                                                         | `cat >> existingfile.txt`                  |
| `rm`               | Removes a file.                                                                                            | `rm unwantedfile.txt`                      |
| `rmdir`            | Removes a directory.                                                                                      | `rmdir foldername`                         |
| `cp`               | Copies a file or a directory.                                                                             | `cp source.txt destination.txt`            |
| `mv`               | Moves a file to a different directory. Also used to rename files.                                          | `mv oldname.txt newname.txt`               |

---

## Shell Scripting Basics
- **`echo`**: Display a message or output to the terminal. Example: `echo "Hello, World!"`
- **`read`**: Read user input from the terminal. Example: `read name`
- **`exit`**: Exit from the script or terminal. Example: `exit`

---

## Programs

### List of Programs

1. **[Shell Script to Print Name, Working Directory, Date, and Calendar](#shell-script-to-print-name-working-directory-date-and-calendar)**
2. **[Shell Script for Addition, Subtraction, Multiplication, and Division of Two Numbers](#shell-script-for-addition-subtraction-multiplication-and-division-of-two-numbers)**
3. **[Shell Script to Check Which of the Two Numbers is Greater, or If They are Equal](#shell-script-to-check-which-of-the-two-numbers-is-greater-or-if-they-are-equal)**
4. **[Shell Script to Check If a Number is Positive, Negative or Zero](#shell-script-to-check-if-a-number-is-positive-negative-or-zero)**
5. **[Shell Script to Print 1 to n](#shell-script-to-print-numbers-from-1-to-n)**
6. **[Shell Script to Check If a Number is Even or Odd](#shell-script-to-check-if-a-number-is-even-or-odd)**
7. **[Shell Script to Print a Pattern of Stars](#shell-script-to-print-a-pattern-of-stars)**
8. **[Shell Script to Reverse a Number](#shell-script-to-reverse-a-number)**
9. **[Shell Script to Check if a Number is Prime or Not](#shell-script-to-check-if-a-number-is-prime-or-not)**
10. **[Shell Script to Perform Binary Search](#shell-script-to-perform-binary-search)**


---

### Shell Script to Print Name, Working Directory, Date, and Calendar

**Question**: Write a shell script to print your name, present working directory, date, and calendar.

#### Code
```bash
cat > display.sh
#!/bin/bash

# Print Name
$echo "Name: Sabir Mallick"

# Print Present Working Directory
$echo "Current Working Directory: $(pwd)"

# Print Date
$echo "Current Date: $(date)"

# Print Calendar
$echo "Calendar:"
$cal
```

To Run the Script:
```bash
sh display.sh
```

#### Output:
```bash
Name: Sabir Mallick
Current Working Directory: /home/ubuntu/Documents
Current Date: Fri Jan 18 15:42:31 UTC 2025
Calendar:
     January 2025
Su Mo Tu We Th Fr Sa
                   1
 2  3  4  5  6  7  8
 9 10 11 12 13 14 15
16 17 18 19 20 21 22
23 24 25 26 27 28 29
30 31
```

---

### Shell Script for Addition, Subtraction, Multiplication, and Division of Two Numbers

**Question**: Write a shell script to perform addition, subtraction, multiplication, and division on two numbers.

#### Code
```bash
#!/bin/bash

# Input two numbers
echo "Enter first number: "
read a
echo "Enter second number: "
read b

# Perform addition
sum=$((a + b))
echo "Addition: $sum"

# Perform subtraction
sub=`expr $a - $b`
echo "Subtraction: $sub"

# Perform multiplication
mul=`expr $a \* $b`
echo "Multiplication: $mul"

# Perform division
div=$((a / b))
echo "Division: $div"
```

To Run the Script:
```bash
sh calc.sh
```

#### Output:
```bash
Enter first number: 
10
Enter second number: 
5
Addition: 15
Subtraction: 5
Multiplication: 50
Division: 2
```

---

### Shell Script to Check Which of the Two Numbers is Greater, or If They are Equal

**Question**: Write a shell script to check which of the two numbers is greater, or if they are equal.

To create and edit the shell script, use the following command:
```bash
nano compare.sh
```

#### Code
```bash
# Input two numbers
echo "Enter first number: "
read a
echo "Enter second number: "
read b

# Check which number is greater or if they are equal
if [ $a -gt $b ]; then
  echo "$a is greater than $b"
elif [ $a -lt $b ]; then
  echo "$a is smaller than $b"
else
  echo "$a is equal to $b"
fi
```

To save the file, press `Ctrl + O`, then press `Enter`.  
To exit, press `Ctrl + X`.

To Run the Script:
```bash
sh compare.sh
```

#### Output:
```bash
Enter first number: 
8
Enter second number: 
5
8 is greater than 5
```

---

### Shell Script to Check if a Number is Positive, Negative, or Zero

**Question**: Write a shell script to check if a number is positive, negative, or zero.

To create and edit the shell script, use the following command:
```bash
nano check_number.sh
```

#### Code
```bash
# Input a number
echo "Enter a number: "
read num

# Check if the number is positive, negative, or zero
if [ $num -gt 0 ]; then
  echo "$num is positive"
elif [ $num -lt 0 ]; then
  echo "$num is negative"
else
  echo "$num is zero"
fi
```

To save the file, press `Ctrl + O`, then press `Enter`.  
To exit, press `Ctrl + X`.

To Run the Script:
```bash
sh check_number.sh
```

#### Output:
```bash
Enter a number: 
5
5 is positive
```

---

### Shell Script to Print Numbers from 1 to N

**Question**: Write a shell script to print numbers from 1 to N using `while` loop.

To create and edit the shell script, use the following command:
```bash
nano print_numbers.sh
```

#### Code
```bash
# Input the value of N
echo "Enter a number: "
read n

# Initialize counter
i=1

# Print numbers from 1 to N using while loop
while [[ $i -le $n ]]
do
  echo $i
  ((i++))
done
```

To save the file, press `Ctrl + O`, then press `Enter`.  
To exit, press `Ctrl + X`.

To Run the Script:
```bash
sh print_numbers.sh
```

#### Output:
```bash
Enter a number: 
5
1
2
3
4
5
```

---

### Shell Script to Check if a Number is Even or Odd

**Question**: Write a shell script to check if a number is even or odd.

To create and edit the shell script, use the following command:
```bash
nano even_odd.sh
```

#### Code
```bash
# Input a number
echo "Enter a number: "
read num

# Check if the number is even or odd
if [[ $((num % 2)) -eq 0 ]]; then
  echo "$num is even."
else
  echo "$num is odd."
fi
```

To save the file, press `Ctrl + O`, then press `Enter`.  
To exit, press `Ctrl + X`.

To Run the Script:
```bash
sh even_odd.sh
```

#### Output:
```bash
Enter a number: 
4
4 is even.
```

---

### Shell Script to Print a Pattern of Stars

**Question**: Write a shell script to print the following pattern:
```
      *
    * * *
  * * * * *
* * * * * * *
```

To create and edit the shell script, use the following command:
```bash
nano pattern.sh
```

#### Code
```bash
#!/bin/bash

# Number of rows
n=4
i=1

# Loop for each row
while [[ $i -le $n ]]
do
  # Print spaces
  j=$i
  while [[ $j -lt $n ]]
  do
    echo -n " "
    ((j++))
  done

  # Print stars
  k=1
  while [[ $k -le $((2*i-1)) ]]
  do
    echo -n "* "
    ((k++))
  done

  # Move to the next line
  echo
  ((i++))
done
```

To save the file, press `Ctrl + O`, then press `Enter`.  
To exit, press `Ctrl + X`.

To Run the Script:
```bash
sh pattern.sh
```

#### Output:
```bash
      * 
    * * * 
  * * * * * 
* * * * * * *
```

---

### Shell Script to Reverse a Number

**Question**: Write a shell script to reverse a number.

To create and edit the shell script, use the following command:
```bash
nano reverse_number.sh
```

#### Code
```bash
# Input number
echo "Enter a number:"
read num

# Reverse the number
reverse=0
while [ $num -gt 0 ]
do
    remainder=$(( num % 10 ))
    reverse=$(( reverse * 10 + remainder ))
    num=$(( num / 10 ))
done

# Display reversed number
echo "Reversed number: $reverse"
```

To save the file, press `Ctrl + O`, then press `Enter`.  
To exit, press `Ctrl + X`.

To Run the Script:
```bash
sh reverse_number.sh
```

#### Output:
```bash
Enter a number:
12345
Reversed number: 54321
```

---

### Shell Script to Check if a Number is Prime or Not

**Question**: Write a shell script to check if a number is prime or not.

To create and edit the shell script, use the following command:
```bash
nano prime_check.sh
```

#### Code
```bash
# Input number
echo "Enter a number:"
read num

# Check if number is prime
if [ $num -le 1 ]; then
    echo "$num is not a prime number"
else
    flag=0
    i=2
    while [ $i -le $(( num / 2 )) ]
    do
        if [ $(( num % i )) -eq 0 ]; then
            flag=1
            break
        fi
        i=$(( i + 1 ))
    done

    if [ $flag -eq 0 ]; then
        echo "$num is a prime number"
    else
        echo "$num is not a prime number"
    fi
fi
```

To save the file, press `Ctrl + O`, then press `Enter`.  
To exit, press `Ctrl + X`.

To Run the Script:
```bash
sh prime_check.sh
```

#### Output:
```bash
Enter a number:
7
7 is a prime number
```

---

### Shell Script to Perform Binary Search

**Question**: Write a shell script to perform binary search.

To create and edit the shell script, use the following command:
```bash
nano binary_search.sh
```

#### Code
```bash
# Input number of elements
echo "Enter the number of elements:"
read n

# Input elements in sorted order
echo "Enter the elements in sorted order:"
i=0
while [ $i -lt $n ]
do
    read arr[i]
    i=$(( i + 1 ))
done

# Input element to search
echo "Enter the element to search:"
read key

# Binary search logic
low=0
high=$(( n - 1 ))
found=0

while [ $low -le $high ]
do
    mid=$(( (low + high) / 2 ))
    
    if [ ${arr[mid]} -eq $key ]; then
        found=1
        break
    elif [ ${arr[mid]} -lt $key ]; then
        low=$(( mid + 1 ))
    else
        high=$(( mid - 1 ))
    fi
done

# Display result
if [ $found -eq 1 ]; then
    echo "Element $key found at position $(( mid + 1 ))"
else
    echo "Element $key not found"
fi
```

To save the file, press `Ctrl + O`, then press `Enter`.  
To exit, press `Ctrl + X`.

To Run the Script:
```bash
sh binary_search.sh
```

#### Output:
```bash
Enter the number of elements:
5
Enter the elements in sorted order:
1 3 5 7 9
Enter the element to search:
7
Element 7 found at position 4
```

---

