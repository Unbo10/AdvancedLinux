# Linux Terminal

## Useful syntax

### Wildcards

- ``*`` - Matches any string of characters.
- ``?`` - Matches any single character.
- ``[...]`` - Matches any one of the characters enclosed in the square brackets.
- ``[^...]`` - Matches any one of the characters not enclosed in the square brackets.
- ``[a-z]`` - Matches any one of the characters in the range from ``a`` to ``z``.

### Pipes
The pipe character or operator, ``|``, is used to pass the output of one command as the input of another command. That way you create a chain of commands that can be used to perform more complex operations.

### Redirection
- ``>`` - Redirects the output of a command to a file.
- ``>>`` - Appends the output of a command to a file.
- ``<`` - Redirects the input of a command from a file (reads what's in the file and prints it to the console as if it had been entered using a keyboard).

## Commands

### Searching

- find [path] -name "[filename]"
- grep [options] "[pattern]" [path]

#### [``find [path] -name "[filename]"``](https://www.geeksforgeeks.org/find-command-in-linux-with-examples/)

It is a search utility for files and directories in the Linux terminal. It returns a list of all the files and directories with the name ``[filename]`` located in ``[path]``. The most used option is ``-name`` which specifies the name of the file or directory to search for.

#### [``grep [options] "[pattern]" [path]``](https://www.geeksforgeeks.org/grep-command-in-unixlinux/)

It is a search utility for text in files incorporated in the Linux terminal. It returns a list of all the matches of ``[pattern]`` in the files located in ``[path]``. The most used option is ``-r`` which makes the search recursive, and the ``-i`` option which makes the search case-insensitive. In addition, a wildcard such as ``*`` can be used as the ``[pattern]``.

### Modifying file permissions

- chmod [options] [permissions] [file]

#### [``chmod [options] [permissions] [file]``](https://www.geeksforgeeks.org/chmod-command-in-linux-with-examples/)

It is an abbreviation of **change mode**. It modifies the permissions of a file or a folder for three types of users: the owner (u), the group (g), and others (o). There aren't many widely used options except for ``-R`` which makes the change recursive. However, the permissions can be set using two different notations: the octal notation (e.g. 777) and the symbolic notation (e.g. u=rwx,g=rw,o=r).

- The symbolic notation is the one that will be displayed when executing the command ``ls -l`` in the terminal. This will return in the console the permissions of the file or folder in the form of ``-rwxrwxrwx`` (a ``d`` could appear instead of the first dash, ``-``, meaning it is directory; otherwise it is a regular file). If there is a ``-`` in place of a letter, it means that permission is not granted to that specific user, starting from the left (owner, group, others).
  
  For example, an output of the command is ``-rw-rw-r-- 1 inbo10 inbo10 52 May 27 14:23 runcp.sh``. This means that the *owner* and the *group* can read and write the file, while *others* can only read it. The number after the description of the permissions is the number of hard links to the file (any references that exist to it, like it's done when configuring Blender for example). The next two fields are the owner and the group of the file (which are often the same). And finally, the date and time of the last modification of the file are shown.

  When changing the permissions of a file, symbolic notation has a set of symbols to represent the permissions:
  - ``u`` - The owner of the file.
  - ``g`` - The group of the file.
  - ``o`` - Others.
  - ``a`` - All users.
  - ``r`` - Read permission.
  - ``w`` - Write permission.
  - ``x`` - Execute permission.
  - ``+`` - Adds the permission.
  - ``-`` - Removes the permission.
  - ``=`` - Sets the permission.
  
  So, for example, if a reading permission were to be added to the user, the writing removed from the group, and only the execution granted to others, the command would be ``chmod u+r,g-w,o=x file``.

- The octal notation is a number that represents the permissions of the file or folder. It is a three-digit number where each digit represents the permissions of the owner, the group, and others, respectively. The permissions are represented by the sum of the values of the permissions:
  - 4 - Read permission.
  - 2 - Write permission.
  - 1 - Execute permission.
  - 0 - No permissions.
  
  So, for example, if the owner has read and write permissions, its value will be "6".
  
  When this notation is used to change permissions, it treats them absolutely, meaning there is no notion of current permissions. Therefore, the permissions of all users are set everytime the command is executed. If a number with less than three digits is passed, the missing digits are filled with zeros.

  For example, if wanting to set read and write permissions to the owner, read permissions to the group, and no permissions to others, the command would be ``chmod 640 file``.

