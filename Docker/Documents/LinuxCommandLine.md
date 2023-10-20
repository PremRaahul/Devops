# Linux Command Line

* In the Linux operating system, everything is considered as a file, including directories.
* Linux is case-sensitive; commands need to be entered in the proper case.
* `apt`: This is a package manager in Linux operating systems used to install packages from the package database.
* `pwd`: This command is used to print the working directory.
* `echo`: This command is used to display text on the terminal.
* `whoami`: This command is used to display the username of the current user.
* `apt install nano`: This command is used to install packages.
* `apt remove nano`: This command is used to remove packages.
* `apt update`: This command is used to update the package database.
* `nano`: This is a Linux-based text editor used to edit files in interactive mode.
* `ls -1`: This command is used to list all directories and files in a vertical manner.
* `ls -l`: This command is used to list all files and directories in a long listing format.
* `cd ~`: This command is used for moving into the home directory.
* `mkdir`: This command is used for creating a new directory.
* `touch`: This command is used for creating files.
* `rm`: This command is used for removing files or directories.
* `rm -r`: This command is used for removing files recursively.
* `rmdir`: This command is used for removing directories.
* `mv`: This command is used to rename or move files from one directory to another.
* `less`: This command is used to view the contents of a file in an interactive mode.
* `cat`: This command is used to view the contents of a file.
* `head`: This command is used to view the first few lines of a file.
* `tail`: This command is used to view the last few lines of a file.
* `>`: This is used for redirection from one place to another.
* `grep` (abbr. for global regular expression print): This command is used for searching a string in a file.
   - Examples:
     ```
     grep -i hello file1.txt
     grep -ir hello .
     grep -i -r hello .
     grep -i hello file1.txt file2.txt
     grep -i hello file*
     ```
   `-i` in the above sample commands indicates case insensitivity.

* `find`: The `find` command is used to find files or folders in a directory.
   - Examples:
     ```
     find
     find /etc
     find -type d
     find -type f
     find -type f -name "f*"
     find -type f -iname "F*"
     find / -type f -name "*.py"
     ```

* Chaining Commands: You can chain multiple commands using a semicolon or logical operators.

* Piping: Piping is used to chain multiple commands by using a pipe symbol. The output of the first command serves as the input for the second command.
   - Example: `ls /bin | less`

* Environment Variables: Environment variables are used to set configuration settings for applications.

* `printenv`: This command displays all the environment variables.

* `export DB_USER=MOSH`: The `export` command is used to add a new variable to the existing environment variables. However, variables added this way are not accessible after the terminal is reloaded. To store variables permanently, they need to be added to the `.bashrc` file located in the user's home directory.

* `echo DB_USER=MOSH >> .bashrc`: You can append data to the `.bashrc` file using the `>>` symbol.

* `ps`: This command is used to see all the processes currently running.

* `sleep 100 &`: The ampersand sign is used to run a process in the background while allowing the user to access the terminal.

* `kill 38`: You can kill a process using its process ID.

* `echo $0`: This command is used to display the path for the Bash terminal.

## Managing Users:
   You can perform various operations related to users, such as adding, modifying, and deleting users.
   - `useradd -m john`: This command is used to create a user.
   - `adduser`: This command is also used to create a user with additional details like name and password, using `useradd` underneath.
   - `usermod -s john /bin/bash/`: This command is used to modify user details and set Bash as the user's shell.
   - `/etc/passwd`: The `/etc/passwd` file contains user details and IDs.
   - `/etc/shadow`: The `/etc/shadow` file contains user passwords in an encrypted form.
   - `groups`: The `groups` command is used to manage user groups.
   - `groupadd developers`: This command is used to create a group.
   - `usermod -G developers john`: This command is used to add "john" to the "developers" group.
   - `groups john`: This command displays all the groups "john" belongs to.

* Executing Multiple Commands:
  You can execute multiple commands in new lines by using a backslash at the end of each command. For example:
  ```
  mkdir sample;\
  echo hello;\
  ```
## File Permissions

File permissions in Unix are used to control who can access and modify files. These permissions are represented by three groups: owner, group, and others. You can change permissions using the `chmod` command. For example:

- `chmod u+x deploy.sh`: This command is used to add execute permission for the owner of the file.

In the following example, you can see the output of the executed command, where the permissions of the file are displayed:

```shell
john@de8326442519:/home$ cat deploy.sh
cat: deploy.sh: Permission denied
john@de8326442519:/home$ cat deploy.sh
echo hello
john@de8326442519:/home$ ls -l
total 12
-rwx-wxrwx 1 root root   11 Oct 11 14:40 deploy.sh
drwxr-x--- 2 john john 4096 Oct 11 13:40 john
drwxr-x--- 2 mosh mosh 4096 Oct 11 13:47 mosh
john@de8326442519:/home$ ./deploy.sh
hello
```

In this output, you can see the file permissions represented by `-rwx-wxrwx`. Here's the breakdown of the permissions:

- The `d` indicates that it's a directory (if it were `-`, it would be considered a file).
- The next 9 letters are divided into three groups: `rwx`, `r-x`, `---`.
  - `r` indicates read permission.
  - `w` indicates write permission.
  - `x` indicates execute permission.
- The first group represents the permissions for the owner of the file.
- The second group represents the permissions for the groups that can access the file.
- The third group represents the permissions for other users.

You can update permissions using the `chmod` command, such as `chmod u+x deploy.sh`, where `u` indicates the user's permissions, and `+x` adds execute permission.
