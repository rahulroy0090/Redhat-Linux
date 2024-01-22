

Lession: 1

# Understanding RHEL Installation.

# Red Hat Enterprise Linux can be installed or deployed in different ways

1) On physical hardware
2) In virtual machines
3) As container
4) AS an instance in cloud

We're installing in a virtual machine.

1). Use RHEL8(download from redhat.com) 


# Understanding Server Requrements.

1) Physical, cloud or virtual?

2) With or without GUI?

3) What are you going to do with the server.

For Installation of a virtual machine.

1) 2Gib of RAM.

2) 20 GiB of Disk space

3) Wired Network connection.






# Logging in to the server.

1). For security, don't log in as root by default.
2). Use su - to open a root shell when required 
3). Or use sudo to run tasks as root




# Check the location.
pwd

# Loging as root.

su - 
password: xxx


# Exit from root.
exit



## Lession 1 Lab: Installing Red Hat Enterprise Linux.

## Install a RHEL Server that meets tha following requremetns.

1). Make sure a graphical user interface is installed.
2). Configure a 10 GiB root patition.
3). Use a 1GiB Swap partition.
4). Makre sure that at least 4GiB of disk space remains as unused.
5). Create a user "Student" with the password "password".
6). Configure the network interface to contact a DHCP Server.









========================================================================================

Lession : 2

======================================================================================
## 2.1 Getting Started with Linux Commands.


CLI: Using the CLI is essential for a linux Administrator.



# Check the Persent working dirctory.
pwd

# Check the Username.
whoami

# Check the list of direcoty and files.
ls

# Check the long list of direcoty and files.
ls -l


# Check the IP Address.
ip addr show


# Check the memory.
free

# Check the memory in MB.
free -m


# Check the disk size.
df

# Check the disk size in human readble.
df -h


# Check the hosts files data.
cat /etc/hosts


# Check the mounted location on your system.
findmnt



---------------------------------------------------------------
## 2.2 Working with the Bash Shell.


Bash is the default shell and provides serveral features.
1). Tab command completion.

2). history: Check the history of commands which one used and you can use privious commands using.

!12 (here run command line number 12)
!f
!h (long time used command list).

3). piping: 
ps aux | less

ps aux | wc

4). redirection: 

whoami > lsfiles
!ca

ls >> lsfiles
!ca




-----------------------------------------------------------------
## 2.4 Using I_O Redirection and Piping.

Redirection uses STDIN, STDERR and STDOUT to work with command input and output in a flexible way.

1) >
2) >>
3) 2> /dev/null
4) <


In piping, the STDOUT of the first commmand is used as STDIN of the second command.

# Save the file with commands data.
ls > file.txt
cat file.txt

# Save the file with commands data without overwrite.
ls Download >> file.txt
cat file.txt


# Find the user from etc file.
grep -R user /etc/


# Find the user from etc file without any error of permission denied
grep -R user /etc/ 2>/dev/null 


# Check the number of files in Download directory.
ls -l Downloads |wc

# Find the file using grep commands.
ls -l Downloads | grep .png


------------------------------------------------------------------------
## 2.5 Understanding the Linux File System Hierarchy.

1). Directory usage on linux is highly standardized
2). Standard directories are defined in the FHS, which is maintained by Linux Foundation.
3). The starting point is the root directory.
4). Different devices may be intergrated in the FHS by using mounts.



--------------------------------------------------------------------------
## 2.6 Using man.

man is the best source to get externsive usage information.

1). Section define command types.
2). Many man pages have examples.
3). Search for text using /

man vim
man ls 



-----------------------------------------------------------------------------
## 2.7 Finding the right man page.

1). All man pages are indexed in the mandb.
2). Use man -k or apropos to search the mandb based on a keybord.
3). A lot of results can show, use grep to filter the results.
4). The mandb is built automatically through a cron scheduled task.
5). Manually trigger a rebuild using mandb.


man mandb
mandb



-----------------------------------------------------------------------------

## 2.8 Understanding vim

1). Vim is the default editor, and is used as embedded editor by many commands.
2). vim is an enhanced version of vi.
3). To work with vim, you need to manage command mode and input mode.



----------------------------------------------------------------------------

## 2.9 Using vim.

Vim Command Overview-1

1). Esc
2). i, a
3). o
4). :wq
5). :q!
6). dd
7). yy
8). p
9). v
10). u
11). ctrl -r
12). gg
13). G
14). /text
15). ?text
16). ^
17). $
18). :%s/old/new/g




----------------------------------------------------------------------------------
## 2.10 Using Globbing and Wildcards.


# Globbing Examples

1). ls host*
2). ls ?ost
3). ls [hm]ost
4). ls [!hm]ost
5). ls script[0-9][0-9]


----------------------------------------------------------------------------------
## 2.11 Using Cockpit

systemctl enable --now cockpit.socket

systemctl enable --now cockpit.socket


localhost:9090


-----------------------------------------------------------------------------

## Lesson 2 Lab - Using Essential Tools



1). Locate the man page that shows how to set a password.
2). Use the man page for useradd and as root, create a user with the name anna.
3). Set the password for user anna to "password".
4). Use cd/etc to make /etc your current dicrectory.
5). Use globbing and ls to show all file in /etc that have a number in thier name.
6). Still from /etc, use the commands ls-l. Use a pipe to display the results page by page. Next type cd without any arguments.
7). Use vim to create a file with the name users, and make sure that it contains the names ales, alexander, linda and belinda on separate lines.


------------------------------------------------------------------------------

## Lesson 2 Lab Solution - Using Essential Tools.

man useradd

useradd rahul

passwd rahul




------------------------------------------------------------------------

3.1 Essential File Management Tasks


1). ls

2). mkdir

3). cp
cp /etc/hosts .s

4). mv

5). rmdir

6). rm


 
 
 ----------------------------------------------------------------
## 3.2 Finding Files.


1). ls is used to list files, not to find files.

2). which looks for binaries in $PATH

3). locate uses a database, built by updatedb to find files in a database.

4). find is the most flexible tool that allows you to find files based on many criteria.


which useradd

echo $PATH



-----------------------------------------------------------------
## 3.3 Understanding Mounts

To access a device, it must be connected to a directory.

This is known as mounting the device

The Linux filesystem typecally uses multiple mounts.

Different types of data typically are on different devices for multiple reasons

1). Security.
2). Manageability.
3). Specific mount options.


-----------------------------------------------------------------
### 3.4 Understanding Links

1). Links are pointers to file in a different location.

2). Compare to shortcuts on other operating systems.

3). Links can be useful to make the same file abailable on multiple location.

4). Linux used hard links and sysbolic links.

5). Create hard links with In and symbolic links with In -s




-------------------------------------------------------------------

##  3.5 Working with Links. 


ls  -il /etc/hosts




-------------------------------------------------------------------------------
## 3.6 Working with tar

Tar is the Tape Archive and was created a long time ago.

By default, it doesn't comparess data

Basic use is to compress, extract, or list

tar -cvf my_archive.tar /home/etc

tar -tvf will show conents of an archive

tar -xvf my_archive extracts to the current dirctory.

 Use -C to swithc the output path
 
 To add compression, use -z, -j or -j
 
 
 
 
 ------------------------------------------------------------
 
 ## 3.7 Working with Compressed Files.
 
A wide range of compression solution is availbale for linux.

	gzip is still the most common compression utility.
	bzip2 is an alternative utility.
	zip is also abailable and has windowns-compatible syntax
	xz is showing up more often as well
	



# Create the zip file.
gzip filename

# Create the zip file without dealte file.

gzip -k filename


# Extracat the file
gunzip filename



----------------------------------------------------------------
Session 3: Essential File Management Tools.


Create a directory structure /tmp/files/pictures, /tmp/files/photos amd /tmp/files/video

Copy all file that have a name starting with an a ,b, or c from /etc/ to /tmp/files

From /tmp/files, move all files that have a name starting with an a or b to /tmp/files/photos, and files with a name starting  with a c to /tmp/files/videos

Find all files in /etc/ that have a size smaller than 1000 bytes and copy those to /tmp/files


In /tmp/files, create a symbolic link to /var

Create a compressed archive file of the /home directory.

Extract this compressed archive filen names in /tmp/archive




==================================================================================
## 4.1 Using Common Text Tools

More was the original file pager.

less was developered to offer some more advantaced features.

As a reaction to that, more was developed a bit more.

But still, to do more, use less



less /etc/passwd



## Using head and tail.

Use head to show the 10 first lines of a text file.
Use tail to show the 10 last lines.
Use -n nn to specify another of lines.




## Displaying File Contents with cat and tac.

Cat dumps text file contents on screen.

	-A shows all non-printable characters
	-b numbers lines
	-s suppressess repreated empty lines.


---------------------------------------------------------

Using grep

grep is excrellent to find text in files or in output.

ps aux | grep ssh

grep linda *

grep -i linda *

grep -A5 linda /etc/passwd

grep -R root /etc


ps aux | grep ssh
	tac is doing the same, but in reversed order.

































