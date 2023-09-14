# Shell Scripting Basics by [Rahul G](https://github.com/Rahulgj3)
---
## Creating a script file

In a shell script, the **`#`** symbol marks comments that the shell doesn't process. The special first line, **`#!/bin/bash`**, indicates the shell to use for running the script, even if you're using a different shell by default.

```bash
#!/bin/bash
```
<br><br>
# 1. Variables 

### 1.1 Environment Variables

**Environment variables** hold vital system information such as system name, logged-in user, user ID, default home directory, and program search path. You can see these variables with the **`set`** or **`env`** command.

### 1.2 User Variables

**User variables** in shell scripts are like custom containers to hold and work with data. Here's the essence:

- **Use:** They let you save and use data temporarily in a script, making it smarter.
- **Naming:** You can name them up to 20 letters, digits, or underscores, and they're case-sensitive (Var1 and var1 are different).
- **Personalization:** Create them for your script's unique needs.
- **Data Types:** They can store various data types, from text to numbers, depending on your task.
- **Versatility:** They make your scripts versatile, helping you handle complex tasks by managing data efficiently.

User variables are a core concept, empowering scriptwriters to build dynamic and tailored scripts.

**syntax :**

```bash
variable=string
varibale="string with many words"
```

note:

- **Assign Values:** Use **`=`** to assign values to user variables in shell scripts.
- **No Spaces:** Don't include spaces when assigning variables to avoid errors.
- **Common Mistake:** Missing the dollar sign ($) can turn the variable name into plain text, which is likely not what you want.

### 1.3 Command substitution

**Command Substitution** in shell scripting lets you store a command's output in a variable for later use. 

There are two ways to do it 

- backticks (`)
- the **`$()`** format

It's like capturing data from a command and putting it in a box (a variable) for your script to use. It's a fundamental and powerful skill in shell scripting.

syntax :

```bash
variable=$(command) or
variable=`command`
```
<br><br>

# 2. Redirecting Input and Output

**Redirection** in shell scripting lets you control where the output of a command goes:

- **Output Redirection:** Instead of displaying the command's output on the screen, you can save it to a file.
- **Input Redirection:** You can also send the contents of a file as input to a command.

Redirection helps manage data flow in your scripts, saving or supplying data from/to files as needed

### 2.1 **Output redirection**

**Output redirection** in the bash shell involves sending a command's output to a file using the greater-than symbol (**>**). 

```bash
command > filename
```

This overwrites the file's contents if it already exists.

For appending output to an existing file, use the double greater-than symbol (**>>**). It's useful for tasks like updating log files with additional data.

```bash
command >> filename
```

### 2.2 **Input Redirection**

**Input redirection** in shell scripting involves taking the content of a file and sending it as input to a command using the less-than symbol (**<**). The command comes first in the line, and the symbol indicates data flowing from the file to the command.

```bash
command < file
```

For inline input redirection, where data is provided directly in the command line instead of a file, you use the double less-than symbol (**<<**). You specify a text marker to indicate the start and end of the input data, and the shell prompts for data until you enter the marker.

```bash
command << marker
>data
>marker
```

This is useful for commands like **`wc`** that count lines, words, and bytes in provided data.
<br><br>
# 3. Pipes

**Piping** in shell scripts uses the **|** symbol to pass the output of one command as input to another command. It's like a real-time data conveyor that allows you to chain multiple commands together for efficient processing.

```bash
command 1 | command 2 | command 3
```
<br><br>
# 4. Performing Math

In shell scripts, you can perform mathematical operations in two different ways.

### 4.1 The expr Command

The **`expr`** command in shell scripting allows mathematical and string operations, but it's somewhat clunky. It supports various operators like **`+`**, **`-`**, **`*`**, **`/`**, **`%`**, and comparison operators (**`<`**, **`<=`**, **`=`**, **`!=`**, **`>=`**, **`>`**), among others.

However, it can be challenging to use these operators directly in scripts due to potential conflicts with shell special characters. To address this, you may need to escape characters using the backslash (**`\`**) to avoid misinterpretation by the shell.

```bash
expr EXPRESSION
```

You provide your mathematical or string expression in place of **`EXPRESSION`**. For example, to add two numbers:

```bash
result=$(expr 5 + 3)
echo $result
```

It can handle arithmetic, string length, pattern matching, and more.

Fortunately, the bash shell offers a more streamlined approach for mathematical operations, as we'll see in the next section.

### 4.2 Using brackets

In bash, you can perform mathematical operations more easily by enclosing equations in square brackets with a dollar sign, like this: **`$[ operation ]`**. This method is simpler and avoids issues with character misinterpretation by the shell.

```bash
$[ operation ]
```

However, it's essential to note that bash's mathematical operators support only integer arithmetic, which can be limiting for complex real-world mathematical calculations.

### 4.3 A floating-point solution

A floating-point solution You can use several solutions for overcoming the bash integer limitation. The most popular solution uses the built-in bash calculator, called bc.

### 4.3.1 **The basics of bc**

The bash calculator (bc) is a programming language for floating-point math. It can handle:

- Numbers (integers and floating-point).
- Variables (simple and arrays).
- Comments (lines starting with # or /* */).
- Expressions.
- Programming statements (like if-then).
- Functions.

To use it, run **`bc`** from the command line, enter expressions, and it calculates and shows results. Set the decimal places using the "scale" variable. Default is 0; set it to 4 for 4 decimal places. Use **`-q`** to skip the welcome message. Variables are usable once defined, and the "print" statement displays numbers and variables.

### 4.3.2 Using bc in scripts

You can use the bash calculator (**`bc`**) in your shell scripts for floating-point math. Here's how:

1. **Basic Format:** You can assign the output of a **`bc`** command to a variable using command substitution like this:
    
    ```bash
    variable=$(echo "options; expression" | bc)
    ```
    
2. **Using Variables:** Variables defined in your script can be used in the **`bc`** expression by prefixing them with a dollar sign.
3. **Multiple Calculations:** After assigning a value to a variable, you can use that variable in further calculations.
4. **Inline Input Redirection:** For more complex calculations, use inline input redirection like this:
    
    ```bash
    variable=$(bc << EOF
    options
    statements
    expressions
    EOF
    )
    ```
    
    The **`EOF`** text marks the beginning and end of the input to **`bc`**.
    
5. **Clean Formatting:** Place each option, statement, and expression on separate lines for better script readability.

Remember that variables created within the **`bc`** calculator are only valid within **`bc`** and cannot be used in the shell script.
<br><br>
# 5. Exiting the Script

Commands in the shell use an exit status, an integer between 0 and 255, to indicate completion. You can capture and use this exit status in your scripts for a more controlled and elegant termination.

### 5.1 Checking the exit status

Linux uses the special variable **`$?`** to store the exit status of the last executed command. You should check it immediately after the command you want to assess. Typically, a successful command has an exit status of 0, while errors result in positive integers. However, specific error exit status codes vary and lack a standard convention in Linux.

```bash
echo $?
```

Here is a table of exit status codes and their descriptions:

| Code | Description |
| --- | --- |
| 0 | Successful completion of the command |
| 1 | General unknown error |
| 2 | Misuse of shell command |
| 126 | The command can’t execute |
| 127 | Command not found |
| 128 | Invalid exit argument |
| 128+x | Fatal error with Linux signal x |
| 130 | Command terminated with Ctrl+C |
| 255 | Exit status out of range "in table" |

### 5.2 The exit command

The **`exit`** command lets you specify the exit status code for your shell script. When you check the script's exit status, you'll get the value you set with **`exit`**. Be cautious, though, as exit status codes can only range from 0 to 255, with values exceeding 255 wrapping back around using modulo arithmetic. This feature is handy for checking command success or failure using if-then statements.

```bash
exit [exit_status]
```

- **`exit_status`**: This is an optional parameter that specifies the exit status code you want to assign to your script. It should be an integer between 0 and 255.
- The **`exit`** command is typically placed at the end of your script to define the exit status code when the script completes.