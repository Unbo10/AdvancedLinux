# Shell scripting

- It is a way to automate tasks by writing a script that contains a sequence of commands that are then executed by the shell interpreter just by calling the script..
- Usually a script will be contained in a `.sh` file (`sh` is the default shell interpreter in Linux).
- One of its main advantages is the implementation of programming logic as it would be done in any other language's script.

## File syntax

The first line of any script should contain the so called *sheebang*, a special character sequence that tells the shell which interpreter to use to execute the script. It is written as `#!` followed by the path to the interpreter. For example, the sheebang for the `bash` interpreter is `#!/bin/bash`.

This is what makes possible the implementation of conditionals, for instance, since the shell interpreter will know how to interpret them.

## Variables

Variables in shell scripts are defined by assigning a value to a name. The syntax is `name=value`. 

To access the value assigned with a name the `$` character must be used. For example:

```bash
name="John"
echo $name
```

will print `John` in the console.

## Arguments

The programming logic in these scripts is propelled by passing information to the script through arguments. These arguments are passed when calling or executing the script, so they are actually part of the command that calls the script. They are accessed using the `$` character, which has multiple functionalities:

- `$0` - The name of the script.
- `$1-9` - Arguments from 1 to 9 passed to the script.
- `$@` - All arguments passed to the script.
- `$#` - The number of arguments passed to the script.
- `$?` - The exit status of the last command executed.

Note: The exit status of the last command executed is a number between 0 and 255. 0 means the command was successful, while any other number means there was an error.

To pass arguments to the script, you simply type them after the call to the script separating each of them with a space:

````bash
./script.sh arg1 arg2 arg3
````

## Conditionals

In conjunction with arguments and the sheebang, conditionals can be implemented in shell scripts. The syntax is:

````bash
if [ condition ]; then
    # code
fi
````

The `condition` can be any expression that returns a boolean value. For example, to check if a file exists:

````bash
if [ -f file.txt ]; then
    echo "File exists"
    return 0
else
    echo "File does not exist"
    return 1
fi
````

Note that there is an `fi` keyword at the end of the conditional block. This is how the shell interpreter knows where the conditional ends.

Similar sintax needs to be used for ending loops, functions, and other blocks of code.

Another example is an implementation of conditionals with arguments:

````bash
if [ -f "$1" ]; then
    echo "File exists"
    return 0
else
    echo "File does not exist"
    return 1
fi
````

This block checks if a file exists in the current directory. The `$1` is the first argument passed to the script, and should be added after the script is called in the terminal:

````bash
./script.sh file.txt
````

## Example

An example of how useful and simple is scripting in Linux is the following script, `runcp.sh`:

````bash
#!/bin/bash
file_name=$1
g++ -O2 -Wall $file_name.cpp -o t
echo "Compiled"
./t.exe
````

this script compiles a C++ file using the `g++` compiler, optimizes the file (using the `-O2` level of optimization, which improves the machine code of the file to run faster), prints any relevant warnings, and then runs the compiled file. The script is called with the name of the file to be compiled as an argument (without the `.cpp` extension). In addition, it also prints a message to the console to let the user know the file was compiled.

This is extremely convenient because two commands are runt at once, the user doesn't have to remember the exact syntax to compile the file, and it tells the user when is the file ready to receive input.