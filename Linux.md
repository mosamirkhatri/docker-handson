# Linux Commands (Ubuntu)

***apt*** is used as package manager for ubuntu linux.

For listing(installed/not installed both) the packages in package database `apt list`

For updating the package database, use `apt update` cmd.

For installing any package, user `apt install <package-name>`.

For removing any package, user `apt remove <package-name>`.

Print Working Directory `pwd`

listing files and dirs `ls`

For vertical layout `ls -1`

For vertical long list `ls -l`

For listing all files (including hidden) `ls -a`

For changing current dir `cd <relative or abs path>`

For changing current dir to user home dir `cd ~`

moving or rename `mv <old> <new>`

Adding new files `touch <filename>`

removing files `rm <filename>`

removing dir recursively `rm -r <filename>`

`CTRL + W` for removing entire word in one go.

view contents of the file `cat <filename>`(small file), `more <filename>`(scroll downwards), `less <filename>`(scroll both ways) 

first n lines of file `head -n <number-of-lines> <filename>`

Last n lines of file `tail -n <number-of-lines> <filename>`

redirection of output `>` for redirecting stdout

### Example `cat <filecontents> > <newfile>`

for redirection of stdin `<` is used

Searching for text `grep` command. Stands for `Global Reg Exp Print`. `-i` is used in case insensative search. `-r` search in directory recursively (applies to folders).

`grep -i -r <pattern> <file or pattern or multiple files>`

For finding files `find` cmd is used. using just `find` will output all files rescursively.

For outputing only directories `find -type d`.`find -type f` for files.

For finding file with name pattern `find -type f -name filepattern`. Example `find -type f -name "f*"`. Use `-iname` for case insensative search.

## chaining cmd

- use `;` for chaining. Example `mkdir test ; cd test ; echo done`. This cmd will run next cmd in case of error in previous cmd.

- For next cmd not to execute on error in previous cmd, use `&&` operator. Example `mkdir test && cd test && echo done`

- For a next cmd to execute only if previous fails, `||` is used. If a cmd is successfully executed, then next cmd won't get executed. Example `mkdir test || echo "directory exists"`

- To use the output of a cmd as input of next cmd use `|` operator. Example `ls /bin | less`.

- break up a long chaining cmd into multiple lines using `\` backslash.

## Env Variables

- `printenv` outputs all env variables. `printenv <variablename>` will output value of a variable.

- For outputting value of env variable, `echo` can also be used with `$` prefixed to variable name. `echo $<variablename>`.

- setting a variable `export <Var-Name>=<Var-Value>`. Example: `export DB_USER=sam`. But only exists for that particular session of terminal.

- For permanent env variables, we need to write them in `.bashrc` file. `echo DB_USER=sam >> .bashrc`. Here `>>` is used for appending the file as `>` will over-write it.

- To reload `.bashrc` file, use `source .bashrc` from HOME directory. 

## Processes

- to see all running processes `ps` cmd is used. `PID` is process id. `TTY` is teletype, `pts` is short for pseudo terminal. `TIME` is amount of CPU time which is consumed. 

- Create a process and put it in background. `sleep <seconds>` command. To put `sleep` cmd in background, append with &. `sleep 3 &`.

- To kill any process `kill <pid>`.

## Managing Users

- `useradd` to add user. Example: `useradd -m john`. For list of user account info. `cat /etc/passwd`. For user passwords `cat /etc/shadow`, here passwords are stored in encrypted format.

- users can also be added with `adduser` cmd which is new and more interactive.

- `usermod` to add user. Example: `usermod -s /bin/bash john` to change default shell of user john to `/bin/bash`. Add user to grp, `usermod -G developers john`.

- `userdel` to add user.

- To login as user john, `docker exec -it -u john <containerid> bash`


## Managing Groups

- `groupadd`. `groupadd <name>`. `cat /etc/group`. `groups john` to view groups of john

- `groupmod`

- `groupdel`

## File Permissions

- To view files with its permissions `ls -l`.

- Example: `drwxr-xr-x`, `-rw-r--r--`.

- The first letter represents directory `d` or file `-`.

- The permission has 9 letters divided in 3 groups of 3.

- `First group` represents `user` who owns this file.

- `Second group` represents `group` who owns this file.

- `Third group` represents permissions for `everyone else`.

- `First letter` in each group is `r` which stands for `read` or `-` if no read permission.

- `Second letter` in each group is `w` which stands for `write` or `-` if no write permission.

- `Third letter` in each group is `x` which stands for `execute` or `-` if no execute permission.

- By default, all directories have `x` permission as we can go into it using `cd` cmd.

- chmod cmd `chmod <u|g|o><+|-><r|w|x> <filenames or patterns>`. Example: To add execute permission for user for file `deploy.sh`, `chmod u+x deploy.sh` is used.