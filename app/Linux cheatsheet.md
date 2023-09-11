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

```

1useradd
Options:
      --badnames                do not check for bad names
  -b, --base-dir BASE_DIR       base directory for the home directory of the
                                new account
      --btrfs-subvolume-home    use BTRFS subvolume for home directory
  -c, --comment COMMENT         GECOS field of the new account
  -d, --home-dir HOME_DIR       home directory of the new account
  -D, --defaults                print or change default useradd configuration
  -e, --expiredate EXPIRE_DATE  expiration date of the new account
  -f, --inactive INACTIVE       password inactivity period of the new account
  -g, --gid GROUP               name or ID of the primary group of the new
                                account
  -G, --groups GROUPS           list of supplementary groups of the new
                                account
  -h, --help                    display this help message and exit
  -k, --skel SKEL_DIR           use this alternative skeleton directory
  -K, --key KEY=VALUE           override /etc/login.defs defaults
  -l, --no-log-init             do not add the user to the lastlog and
                                faillog databases
  -m, --create-home             create the user's home directory
  -M, --no-create-home          do not create the user's home directory
  -N, --no-user-group           do not create a group with the same name as
                                the user
  -o, --non-unique              allow to create users with duplicate
                                (non-unique) UID
  -p, --password PASSWORD       encrypted password of the new account
  -r, --system                  create a system account
  -R, --root CHROOT_DIR         directory to chroot into
  -P, --prefix PREFIX_DIR       prefix directory where are located the /etc/* files
  -s, --shell SHELL             login shell of the new account
  -u, --uid UID                 user ID of the new account
  -U, --user-group              create a group with the same name as the user
  -Z, --selinux-user SEUSER     use a specific SEUSER for the SELinux user mapping
      --extrausers              Use the extra users database
```

```
user -m john
cat /etc/passwd
usermod -s /bin/bash john
cat /etc/shadow
<!-- show the password(only accessiable to the root user) -->
docker exec -it -u john (container ID) bash
<!-- login as john -->

adduser
<!-- more interactive than useradd -->
```

**Managing groups**

```
groupadd
  -f, --force                   exit successfully if the group already exists,
                                and cancel -g if the GID is already used
  -g, --gid GID                 use GID for the new group
  -h, --help                    display this help message and exit
  -K, --key KEY=VALUE           override /etc/login.defs defaults
  -o, --non-unique              allow to create groups with duplicate
                                (non-unique) GID
  -p, --password PASSWORD       use this encrypted password for the new group
  -r, --system                  create a system account
  -R, --root CHROOT_DIR         directory to chroot into
  -P, --prefix PREFIX_DIR       directory prefix
      --extrausers              Use the extra users database
<!-- all user in the same group has the same permission -->
cat /etc/group

```

Every LInux user has one primary group and zero ore more secondary groups

```
usermod -G developers john
grep john /etc/passwd
groups john
<!-- see the groups of the user -->

```

**File permissions**

```
-rw-r--r-- 1 root root   11 Sep 10 22:27 deploy.sh
drwxr-x--- 2 john john 4096 Sep 10 22:07 john
<!-- d for directory, - for file -->
<!-- 9 letters means 3 groups. the first group is the permission of the user who own the file,the second is the permisson for the group who own this file, the third group means the permission of everyone else -->
chmod
chmod u+x deploy.sh
<!-- change mode -->

```
