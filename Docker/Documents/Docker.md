# Docker

## Docker Commands

* docker run ubuntu : This command is used to run the ubuntu image
* docker pull ubuntu : This command is used to pull the images from the docker hub
* docker run -it ubuntu : This command is used to run the image in the interactive mode
* docker ps : This command is used see all the processes running
* docker ps -a : This command is used to see all processes running and also with the stopped processes
* docker start -i 274: This command is used start a container or an image with help of image or container **Id**
* docker exec -it -u john 274 bash : This command is used to execute the running ubuntu image in the interactive mode with john as a user 

## Linux basics

* In linux operating system everything is considered as file even a directory is also considered as file
* Linux is a case sensitive the commands you are entering need to be in proper case
* apt - this is a package manager in the linux operating systems and used to install the packages from the package database
* pwd - This command is used to print working directory
* echo - This command is used to display the text on the terminal
* whami - This command is used to display the username of the current working user
* apt install nano - this command is used to install the packages
* apt remove nano - this command is used to remove the packages
* apt update - this command is used to update the package database
* nano - this is a linux based text editor used to edit the files in the interactive mode
* ls -1 : This command is used for listing all the directories and files in a vertical manner
* ls -l : This command is used for listing all the files and directories in a long listing manner
* cd ~ : This command is used for moving into the home directory
* mkdir : This command is used for creating a new directory
* touch : This command is used for creating files
* rm : This command is used for removing files or directory
* rm -r : This command is used for removing the files recursively
* rmdir : This  command is used for removing the directory
* mv : This command is used to rename or move files from one directory to another directory
* less : This command is used to view contents of the file in a interactive mode
* cat : This command is used to view contents of the file
* head : This command is used to view the first few lines of the file
* tail : This command is used to view the last few lines of the file
* **>** : This used for redirection from one place to another place
* grep : (grep is abrivated as global regular expression print) This command is used for searching a string in a file

```
root@de8326442519:~# grep -i hello file1.txt
root@de8326442519:~# grep -ir hello .
root@de8326442519:~# grep -i -r hello .
root@de8326442519:~# grep -i hello file1.txt file2.txt
root@de8326442519:~# grep -i hello file*
```
`   
 -i in the above sample commands indicate ignore case 
`
* find : the find command is used find the files or folders in the directory

```
root@de8326442519:~# find
root@de8326442519:~# find /etc
root@de8326442519:~# find -type d
root@de8326442519:~# find -type f
root@de8326442519:~# find -type f -name "f*"
root@de8326442519:~# find -type f -iname "F*"
root@de8326442519:~# find / -type f -name "*.py"
```

* chaining commands : we can chain multiple commands with the help of the semi coloun or with the help of the logical operators

* pipeing : pipeing concept is used to chain multiple commands with help of a pipe after executing the first command the output of the first command is considered as input to the second command
    - Example : `ls /bin | less` 
    - In the above example it lists all the files and directories of the bin folder and pass that data to the less and we can view that data in the interactive mode
* we can execute multiple commands in new seperate lines in the following mannner by adding \ at the end of the command
    - Example : 
    ```
        root@de8326442519:~# mkdir sample;\
        echo hello;\
    ```
* Environment Variables : environment variable is used to set the configuration settings for our application 
* printenv : This command is used for displaying all the env variables
* export DB_USER=MOSH : The export command is used to append the new varible to the existing env variables, But we cant access the variables once the terminal get's reloaded. To store the varible permanently we need to store the variable in the .bashrc file which is located in the home directory of the user
* echo DB_USER=MOSH >> .bashrc : We can append the data to the .bashrc file with the help of the `>>` Symbol

* ps : This command is used to see all the processes that are currently running 
* sleep 100 & : The ampersand sign is used to run the process in the background by allowing the user to access the terminal
* kill 38 : we can kill any process with help of the process Id
* echo $0 : This command is used to display the path for the bash terminal
* we can manage users and perform different kinds of operations like adding users, modifing users and deleting users 
* useradd -m john : This command is used for creating the user
* adduser : This command is also used creating the user with more details like name, password etc and it uses useradd underhood for creating the user
* usermod -s john /bin/bash/ : This command is used to modify the user details and set bash as a terminal to the user john
* /etc/passwd : The passwd directory consists of all the user details and thier id etc..
* /etc/shadow : The shadow directory consists of all the passwords of the user in the encrypted manner
* groups : the groups is mainly used to group the certain number of users and add some permisions to that group so that the users in that group can have common set of permissions for accessing the files 
* groupadd developers : This command is used create a group 
* usermod -G developers john : This command is used add jhon to the group developers, Their are two main group categories `Primary` and `Secondary`, The user would by default added to the primary group at the time creation 
* groups jhon : This command displays all groups that jhon has been added
* ./deploy.sh : This command is used to execute the shell file 
* chmod u+x : This command is used to change the permissions of the file, and in this command we are adding the execute permission to the file
* File Permisions : file permissions is used to add permissions to the file that who can access and modify the file in the different modes like read,write and execute 
```
root@de8326442519:/home# echo echo hello > deploy.sh
root@de8326442519:/home# ls -l
total 12
-rw-r--r-- 1 root root   11 Oct 11 14:40 deploy.sh
drwxr-x--- 2 john john 4096 Oct 11 13:40 john
drwxr-x--- 2 mosh mosh 4096 Oct 11 13:47 mosh
```
* In the above given sample executed command ouput you can see drwxr-x--- 
    + d - indicates its a directory, if it is a d then it is considered as directory or if it is `-`then it is considered as a file
    + The next 9 letters are divided into three groups `rwx` `r-x` `---` 
    +   
        `1) r - indicates that  the file has access to   read`

        `2) w - indicates that the file has access to write `

        `3) X - indicates that the file has access to execute`
    + The first group represents the permissions to the user who owns this group
    + The second group represents the permissions to the groups that can access the file
    + The third group represents the permissions to the other users
    + we update the permissions to the file with the help of chmod u+x command so that the users can execute the file, you replace the `u` in the command with `g - groups` or `o - others` and the `+` indicates adding the permission and the `-` indicates removing the permission
    ```
    root@de8326442519:/home# ./deploy.sh
    hello
    root@de8326442519:/home# chmod o+x deploy.sh
    root@de8326442519:/home# chmod g+x deploy.sh
    root@de8326442519:/home# chmod og+x+W-r *.sh
    ```

    ```
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


