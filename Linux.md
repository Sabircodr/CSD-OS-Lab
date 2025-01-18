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

---

### Shell Script to Print Name, Working Directory, Date, and Calendar

**Question**: Write a shell script to print your name, present working directory, date, and calendar.

#### Shell Script to Print Name, Working Directory, Date, and Calendar
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

**Output**:
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

#### Shell Script for Addition, Subtraction, Multiplication, and Division of Two Numbers
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

**Output**:
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
