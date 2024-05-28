# Linux Terminal

## Useful syntax

### Wildcards

- `*` - Matches any string of characters.
- `?` - Matches any single character.
- `[...]` - Matches any one of the characters enclosed in the square brackets.
- `[^...]` - Matches any one of the characters not enclosed in the square brackets.
- `[a-z]` - Matches any one of the characters in the range from `a` to `z`.

### Pipes
The pipe character or operator, `|`, is used to pass the output of one command as the input of another command. That way you create a chain of commands that can be used to perform more complex operations.

### Redirection
- `>` - Redirects the output of a command to a file.
- `>>` - Appends the output of a command to a file.
- `<` - Redirects the input of a command from a file (reads what's in the file and prints it to the console as if it had been entered using a keyboard).

## Utilities

### Information

#### [`man [command]`](https://www.geeksforgeeks.org/man-command-in-linux-with-examples/)

It stands for **manual**. It is the most useful and detailed tool to get information about a command. It displays the manual page of the specified command. To navigate in it, use the arrow keys to navigate each line, the `space` key to go forward one page, the `b` key to go back one page, the `q` key to quit the manual, and the `/` key to search for a specific word.

### Input/Output

- echo [options] [string]
- cat [options] [file]
- touch [file]

#### [`echo [options] [string]`](https://www.geeksforgeeks.org/echo-command-in-linux-with-examples/)

This is a command pretty much equivalent to a print in Python or a cout in C++. It prints a message to the console. The options are not widely used, but the `-e` one can be used to interpret backslash escapes in the string.

#### [`cat [options] [file]`](https://www.geeksforgeeks.org/cat-command-in-linux-with-examples/)

Although it is short for **concatenate**, it does more than that: it displays the content of a file in the console, concatanates (join or append) files, and creates new ones. 
It is used alongside the redirection operator `>` to create a new file with the content of another one.

### Directory navigation

- pwd [options]
- cd [path]
- ls [options] [path]

#### [`pwd [options]`](https://www.geeksforgeeks.org/pwd-command-in-linux-with-examples/)

It stands for **print working directory**. It prints the full path of the current directory in the console. The `-P` option is used to print the physical path without any symbolic links, whilst the `-L` option prints the logical path (the most commonly used).

#### [`cd [path]`](https://www.geeksforgeeks.org/cd-command-in-linux-with-examples/)

It stands for **change directory**. It is used to navigate through the file system. The path can be either absolute or relative. If no path or a single dot is given, `.`, it will take you to the home directory. The `..` notation is used to go up one directory.

#### [`ls [options] [path]`](https://www.geeksforgeeks.org/ls-command-in-linux/)

It stands for **list**. It is used to list the contents of a directory. There are four main options:

- `-a` - Lists all files, including hidden ones.
- `-l` - Lists the files in a long format, showing permissions, number of hard links, owner, group, size, date, and time of last modification, and the name of the file.
- `-h` - Makes the output human-readable, showing the size of the files in a more understandable format.
- `-d` - Lists the directory itself, not its contents.

### Management of files and directories

- mkdir [options] [directory]
- rmdir [options] [directory]
- touch [file]
- cp [options] [source] [destination]
- mv [options] [source] [destination]
- rm [options] [file]

#### [`mkdir [options] [directory]`](https://www.geeksforgeeks.org/mkdir-command-in-linux-with-examples/)

It stands for **make directory**. It is used to create a new directory. A useful option that contains the same functionality as the `chmod` command is `-m`, which sets the permissions of the directory when it is created (the permission settings must follow the option).

#### [`rmdir [options] [directory]`](https://www.geeksforgeeks.org/rmdir-command-in-linux-with-examples/)

It stands for **remove directory**. It is used to delete a directory. The `-p` option is used to remove the directory and its parent directories if they are empty, and the `-v` option is used to display the name of the directory(s) being removed.

#### [`touch [file]`](https://www.hostinger.com/tutorials/linux-cat-command-tutorial-and-examples/#:~:text=the%20cat%20command.-,How%20Does%20the%20cat%20Command%20Work%3F,to%20view%20a%20file's%20content.)

This command is used to create a file without the need to open an editor or file explorer. It modifies the update and access time of a file if it already exists, and creates a new one if it doesn't.

#### [`cp [options] [source] [destination]`](https://www.geeksforgeeks.org/cp-command-linux-examples/)

It stands for **copy**. It is used to copy files and directories. The destination file or directory will be created if it doesn't exist and overriden without any warning if no option is used. For that purpose -avoiding unwanted overwriting-, the `-i` option can be used to prompt the user (ask it to confirm the operation) before replacing files or directories, and the `-b` option can be used to create a backup of the file or directory before replacing it.

#### [`mv [options] [source] [destination]`](https://www.ibm.com/docs/es/aix/7.2?topic=m-mv-command)

It stands for **move**. It is used to move the content of files and directories to a different location (renaming them in the process if that's the case). The `-i` option can be used to prompt the user before moving files or directories to an existing location.

#### [`rm [options] [file]`](https://www.ibm.com/docs/en/aix/7.3?topic=r-rm-command)

It stands for **remove**. Contrary to common knowledge, it doesn't directly delete files, it removes the entry of the specified file. Only if that entry is the last one, it will delete the file. The `-i` option promps the user and the `-e` option displays a message after a file is deleted (can be used in conjunction with `-r`).

Note: The `-r` option means **recursive**, and it is used to execute a command in the current directory and any subdirectories it could have. Also, the `-f` option, which stands for **force**, has to be used with caution, as it will force an operation no matter the warnings or permissions.

### Searching

- find [path] -name "[filename]"
- grep [options] "[pattern]" [path]

#### [`find [path] -name "[filename]"`](https://www.geeksforgeeks.org/find-command-in-linux-with-examples/)

It is a search utility for files and directories in the Linux terminal. It returns a list of all the files and directories with the name `[filename]` located in `[path]`. The most used option is `-name` which specifies the name of the file or directory to search for.

#### [`grep [options] "[pattern]" [path]`](https://www.geeksforgeeks.org/grep-command-in-unixlinux/)

It is a search utility for text in files incorporated in the Linux terminal. It returns a list of all the matches of `[pattern]` in the files located in `[path]`. The most used option is `-r` which makes the search recursive, the `-i` option which makes the search case-insensitive, and the `-n` flag used for returning the line at which the pattern was found inside a file. In addition, a wildcard such as `*` can be used as the `[pattern]`.

### Modifying file permissions

- chmod [options] [permissions] [file]

#### [`chmod [options] [permissions] [file]`](https://www.geeksforgeeks.org/chmod-command-in-linux-with-examples/)

It is an abbreviation of **change mode**. It modifies the permissions of a file or a folder for three types of users: the owner (u), the group (g), and others (o). There aren't many widely used options except for `-R` which makes the change recursive. However, the permissions can be set using two different notations: the octal notation (e.g. 777) and the symbolic notation (e.g. u=rwx,g=rw,o=r).

- The symbolic notation is the one that will be displayed when executing the command `ls -l` in the terminal. This will return in the console the permissions of the file or folder in the form of `-rwxrwxrwx` (a `d` could appear instead of the first hyphen, `-`, meaning it is directory; otherwise it is a regular file). If there is a `-` in place of a letter, it means that permission is not granted to that specific user, starting from the left (owner, group, others).
  
  For example, an output of the command is `-rw-rw-r-- 1 inbo10 inbo10 52 May 27 14:23 runcp.sh`. This means that the *owner* and the *group* can read and write the file, while *others* can only read it. The number after the description of the permissions is the number of hard links to the file (any references that exist to it, like it's done when configuring Blender for example). The next two fields are the owner and the group of the file (which are often the same). And finally, the date and time of the last modification of the file are shown.

  When changing the permissions of a file, symbolic notation has a set of symbols to represent the permissions:
  - `u` - The owner of the file.
  - `g` - The group of the file.
  - `o` - Others.
  - `a` - All users.
  - `r` - Read permission.
  - `w` - Write permission.
  - `x` - Execute permission.
  - `+` - Adds the permission.
  - `-` - Removes the permission.
  - `=` - Sets the permission.
  
  So, for example, if a reading permission were to be added to the user, the writing removed from the group, and only the execution granted to others, the command would be `chmod u+r,g-w,o=x file`.

- The octal notation is a number that represents the permissions of the file or folder. It is a three-digit number where each digit represents the permissions of the owner, the group, and others, respectively. The permissions are represented by the sum of the values of the permissions:
  - 4 - Read permission.
  - 2 - Write permission.
  - 1 - Execute permission.
  - 0 - No permissions.
  
  So, for example, if the owner has read and write permissions, its value will be "6".
  
  When this notation is used to change permissions, it treats them absolutely, meaning there is no notion of current permissions. Therefore, the permissions of all users are set everytime the command is executed. If a number with less than three digits is passed, the missing digits are filled with zeros.

  For example, if wanting to set read and write permissions to the owner, read permissions to the group, and no permissions to others, the command would be `chmod 640 file`.

