## Linux Distributions

Ubuntu

```
docker run ubuntu

docker ps
<!-- show the latest running process(container) -->

docker ps -a
<!-- for all -->

docker run -it ubuntu
<!-- start a container in interactive mode -->

echo

whoami
<!-- show the current -->

echo $0
<!-- location of the shell program -->

history
<!-- show the history of the command used lately -->
!3
<!-- use the the third command used in history -->
```

## **Managing Packages**

**package manager:**
npm
yarn
pip
.....

In ubuntu use `apt`

```
Most used commands:
  list - list packages based on package names
  search - search in package descriptions
  show - show package details
  install - install packages
  reinstall - reinstall packages
  remove - remove packages
  autoremove - Remove automatically all unused packages
  update - update list of available packages
  upgrade - upgrade the system by installing/upgrading packages
  full-upgrade - upgrade the system by removing/installing/upgrading packages
  edit-sources - edit the source information file
  satisfy - satisfy dependency strings
```

use `apt update` and then `apt install`
using `ctrl + L` to clean the window

## Linux File System

`root` folder on top of the hierarchy:
    `bin`,  `lib`,  `dev`, `home`(div for devices)....

In linux, everything is a file

**Navigating**

```
pwd
ls

cd ~
<!-- back to root directory -->
mv
<!-- rename files or folders or move them somewhere else -->
touch
<!-- create new file (can create multiple files in one go)-->

ctrl+W
<!-- delete in one go -->

rm
<!-- remove files -->

rm -r
<!-- remove directories -->

cat
<!-- show the content -->
more
<!-- show part of the content -->
less
<!-- press up and down arrows and press q to quite -->
head -n 5
<!-- show the first five lines -->
tail -n 5
<!-- show the last five lines -->

cat file1.txt > file2.txt
<!-- redirect the file -->
cat file1.txt file2.txt >combined.txt
echo hello > hello.txt
```

**Search for text**

```
grep hello file1.txt
grep -i hello file1.txt
<!-- -i means case insensitive -->
grep -i root /etc/passwd
grep -i hello file*
grep -i -r hello .
<!-- r:search this directury and all its sub directory recursively -->
grep -ir hello .
<!-- combine the instructions -->

find
?finding files in directory
find -type d
<!-- search all the directory inside the current directory -->
find -type f
<!-- search all the files inside the current directory -->
find -type f -name "*f"
find -type f -iname "F"
find / -type f -name "*.py"
```

**Chaining Commands**

```
mkdir test;cd test;echo done
mkdir test&&cd test&&echo done
<!-- if one command fails, the other commands wont be executed -->
mkdir test||cd test||echo done
ls /bin | less
<!-- build a pipe -->
root@a63cfb76d68f:~# mkdir hello;\
> cd hello;\
> echo done

```

**Environment Variables**

```
printenv
printenv PATH
echo $PATH

exit
<!-- to endexit the container -->
docker start -i (container id)
<!-- to restart a container -->
```

use `.bashrc` file to write permanent environment variables
`echo DB_USER=XXX >>.bashrc`
`source` to reload the file

**Managing processes**

```
ps
<!-- to show all the running processes -->
sleep
kill

```

**Managing Users**
