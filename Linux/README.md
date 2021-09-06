### 1. What is Linux?
Linux is an open source operating system developed by Linus Torvalds. Linux is just a kernel and a linux distribution makes it a usable operating system.

### 2. Simple Architecture:
![image](https://user-images.githubusercontent.com/43535914/126981748-d943ccd4-f290-4a13-a276-2fe6d7639650.png)

### 3. What is Kernel?
kernel is the core of the operating system that manages everything. Kernel is kind of a thing which interacts with your hardware and manages CPU resources, memory resources, processes on any computer. Kernel is responsible for tasks like:
- Allocating memory
- Schedule processes
- Control CPU

### 4. What is Shell?
The shell acts as an interface between kernel and end user or application. Shell is just a program, a friendly interface that translates your commands into some low-level calls to the kernel.

### 5. What are Linux Distros?
Distros nothing but distributions are specific group of software
In all linux distributions:
* Linux kernel is same (mostly). 
* Tools from GNU General public license is different.

The Linux operating system isn’t produced by a single organization. Few companies take the linux kernel and put up some modified version of their software on top of it and launch their own distributions of linux. They govern all the things like updation of the software, package repository, release of the new security patches etc.

Companies that are launching these distros are: Arch | Debian | Red hat | Slackware etc
Below mentioned are flavors of the above mentioned distributions
Debian	=>	Mint, kali, Ubuntu, Parrot, Deepin 
Red hat	=> 	Fedora, Centos (Community Enterprise Operating System), RHEL (Red Hat Enterprise Linux) 

### 6. File system hierarchy:
![image](https://user-images.githubusercontent.com/43535914/127991861-133917f3-befc-4280-8e35-351801895156.png)

Directory | Name | Description
--------- | ---- | --------------
**/** | The Root Directory | This is top level directory, also called as ROOT directory. Everything on your Linux system is located under the / directory.
**/root** | Root Home Directory | It is home directory for root user (super user). Instead of being located at /home/root, it’s located at /root. This is distinct from /, which is the system root directory.
**/home** | Home Folders | It provide working environment for all users other than root. /home Contains a home folder for each user. <br> **Ex:** if you create a user named "bob" then you will have a home folder located at /home/bob. <br> Each user only has write access to their own home folder and must obtain elevated permissions (become the root user) to modify other files on the system.
**/usr** | User Binaries & Read-Only Data | This directory contains libraries, source code, binaries and documentation required for second-level programs. The binary files of a user is stored in /usr/bin and the binary files of the system are stored in /usr/sbin. The system libraries are stored in /usr/lib. <br> **Ex:** useradd, atd, cron, userdel. 
**/bin** | Essential User Binaries | Contains essential user binaries. Applications, programs, and commands that we use are located in this directory. <br> **Ex:** ps, ls, ping, grep, cp.
**/sbin** | System Administration Binaries | It contains essential binaries that are generally intended to be run by the root user for system administration.
**/lib** | Essential Shared Libraries | It holds the libraries needed by the binaries in /bin and /sbin directories.
**/opt** | Optional Packages | Used for installing/storing the files of third-party applications that are not available from the distribution’s repository.
**/dev** | Device Files | Stores device files. These include terminal devices, usb, or any device attached to the system. <br> **Ex:** /dev/tty1, /dev/usbmon0
**/etc** | Configuration Files | Contains core configuration files. It controls the behavior of an operating system or application. This directory also contains startup and shutdown program scripts that are used to start or stop individual programs. <br> **Ex:** /etc/resolv.conf, /etc/logrotate.conf
**/var** | Variable Files | This is where programs store runtime information like system log files (/var/log); packages and database files (/var/lib); emails (/var/mail); print queues (/var/spool); lock files (/var/lock); temp files needed across reboots (/var/tmp); etc <br> The files stored here are NOT cleaned automatically and hence it provides a good place for system administrators to look for information about their system behavior. <br> **Ex:** If you want to check the login history in your Linux system, just check the content of the file in /var/log/wtmp.
**/boot** | Static Boot Files | Contains files needed to boot the system
**/mnt** | Temporary Mount Points | Temporary mount directory for mounting file system
**/lost+found** | Recovered Files | Same as "restore". Each Linux file system has a lost+found directory and is useful for recovering files which may be broken due to unexpected shut-down.
**/proc** | Kernel & Process Files |  It contains special files that represent system and process information. <br> 1. This is a pseudo filesystem contains information about running process. <br> **Ex:** /proc/{pid} directory contains information about the process with that particular pid. <br> 2. This is a virtual filesystem with text information about system resources. <br> **Ex:** if you want to check processor information in Linux (refer to the file /proc/cpuinfo); if you want to check memory usage of your Linux system(refer to /proc/meminfo file); If ypu want to know uptime (refer to /proc/uptime file)
**/tmp** | Temporary Files | Applications store temporary files in the /tmp directory. Files under this directory are deleted when system is rebooted.
**/selinux** | SELinux Virtual File System | If your Linux distribution uses SELinux for security (Fedora and Red Hat, for example), the /selinux directory contains special files used by SELinux. It’s similar to /proc. Ubuntu doesn’t use SELinux

### 7. Terminal:
Terminal or command line or command prompt is basically a text interface to your computer. It allows us to send simple text commands to our computer to do things like navigate through a directory, copy a file, etc.

![image](https://user-images.githubusercontent.com/43535914/126983919-41650416-3a27-4641-ba95-7c725a9ebe24.png)

**\#** prompt indicates root user whereas **$** prompt indicates other users.

#### Below are few terminal shortcuts:
Command | Description
------- | --------------
ctrl+Alt+T |	Open terminal
ctrl+c | Stop the current command execution
TAB key |	To auto complete file or folder names
ctrl+a	| move cursor to beginning of line
ctrl+f	| move cursor to end of line
clear (or) ctrl+l	| To clear the terminal screen.
exit | close the terminal or logout of current session.
Up and Down arrow keys | To cycle through recently used commands in the terminal.

### 8. What are commands in linux?
Linux commands are simply programs which are executed by the shell. In linux there are thousands of commands. Sometimes the command which you are executing may not be available in your OS. In that case download & install required package from respective repository (like apt, yum) and then execute.

**Ex:**
"command not found" error while executing tree command
tree is a command which is available in tree package. Download tree package and then execute that command

### 9. How to install softwares/packages?
In Linux, installation files are distributed as packages. A repository is a storage location from which your system retrieves and installs OS updates and applications. It is like a warehouse that consists of all packages.

**Ex:** Inorder to install a package in ubuntu 
1. update the repository &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&nbsp;&nbsp; It will update/install dependent packages &emsp;&nbsp; apt-get update                    
2. Download & install the required package	&emsp;	It will install actual software &emsp; &emsp;&emsp;&emsp;&emsp;&emsp;&emsp; apt-get install <package-name>

Likewise "yum" is a repository for CentOS, "apk" is a repository for Alpine, etc
  
### 10.  Basic linux commands:
Command | Usage | Description
------- | ----- | ------------
date | date | Show the current date and time
cal	|	cal | Show the month's calendar
history |	history | Displays a list of all recently used commands.
alias	| alias \<alias-name\>="some command" | Defines shortcut for a long command. <br> **Ex:** To create an alias named CD for command "cd /usr/local/bin" <br> alias CD="cd /usr/local/bin"  <br> Use *unalias \<alias-command\>* to delete an alias
man	| man \<command name\> |	Displays a help page based on your search query
whatis |	whatis \<command name\> |	Displays brief description of command
echo	| echo “Some text” |	Display contents

### 11. File permissions:
**11.1. Types of permissions:**
Permission | Alphabetical notation | Numerical notation
---------- | --------------------- | ------------------
Read |	r |	4
Write	| w	| 2
Execute	| x	| 1
No permissions |  | 0   

"chmod" command is used to change the read, write, and execute permissions of a file/folder.

**Ex:**
##### Change permissions using numerical notation:
    chmod 755 <File/Folder name>
    Here 7, 5 and 5 individually represent permissions of User, Group and Others

##### Recursively apply permissions to all sub-folders and files recursively
    chmod -R 755 <Folder name>

##### Change permissions using alphabetical notation:
    +  is for giving permissions
    -  is for removing permissions
    =  is for replacing existing permissions
    chmod o+r file1       provide read permissions for others for file1
    chmod o+r+w+x file1   provide all permissions to others
    chmod u+x,g-w file1   add execute permission to owner and remove write permission to group
    chmod u=w file1       Replace existing permissions with new permissions (For suppose owner has rwx permissions and you want to replace with only write permission then you                             can use this)
  
**11.2. Types of ownership:** 
owner | Notation
----- | --------
User | u
Group | g
Others | o

"chown" command is used to change the user and/or group that owns a file/folder.

**Syntax:**  chown USER:GROUP <File/Folder name>
**Ex:**
    Both user & group:   chown dave:mary example.txt
    Only user:           chown dave: example.txt
    Only group:          chown :mary example.txt
  
### 12. Identifying file types:
A file type helps us in identifying the type of content that is saved in the file. Linux supports seven different types of files. 
Symbol	| Type of file
------- | ------------
\-	| Normal file
b	| Block special file (Hard disk or floppy disk)
c	| Character special file
s | local socket file
d	| Directory
l	| Link files
p | named pipe
  
When you list files or directories, you can identify a file type by viewing the first character as shown below.
![image](https://user-images.githubusercontent.com/43535914/126990264-4d9aecf8-0caa-434e-b436-b1fb07e52752.png)


### 13. what is the use of !! command?
Simply typing !! in command line will repeat the execution of your previous command
If you use it in conjunction with some other command then your last run command will be replaced by !! 
 
![image](https://user-images.githubusercontent.com/43535914/127644819-0faec6be-5e0a-4b66-8e8f-cf5b81667ca3.png)

### 14. What is the use of nohup command? 
Nohup, short for no hang up is a command in Linux systems that keep processes running even after exiting the shell or terminal. The nohup command executes another program specified as its argument and ignores all SIGHUP (hangup) signals. SIGHUP is a signal that is sent to a process when its controlling terminal is closed. <br> Usually, when you run a program over SSH, if your connection drops or you log out, the session is terminated and all the processes executed from the terminal will stop. This is where the nohup command comes in handy. It ignores all hangup signals, and the process will continue to run. 

To run the command in the background, append the & symbol at the end of the command as shown below.
 
    syntax: nohup \<some command\> &
    Ex: nohup java -jar abc.jar &
    o/p: [1] 25177
    The output includes the shell job ID (surrounded with brackets) and process ID. You can use the job ID to bring the command into the foreground using the fg command.
 
*Note:* 
 
- nohup redirects the command output to the nohup.out file. This file is created in the current working directory. If the user running the command doesn’t have write permissions to the working directory, the file is created in the user’s home directory.
- If you don't include **&** at the end command then it will run the command in foreground giving the following output. Using nohup in the foreground is not very useful because you won’t be able to interact with the shell until the command completes.
 
**o/p:**  nohup: ignoring input and appending output to 'nohup.out'

### 15. What is /etc/resolv.conf file?
The /etc/resolv. conf is resolver configuration file. It is used to configure DNS nameservers.
 
**Ex:**
 
    search devops.local
    nameserver 172.16.192.55

### 16. What is /dev/null? 
/dev/null in Linux is a null device file. It’s a special file that’s present in every single Linux system. However, unlike most other virtual files, instead of reading, it’s used to write. Whatever you write to /dev/null will be discarded, forgotten into the void. This is a command-line hack that acts as a vacuum, that sucks anything thrown to it.
This is not an executable file, so we cannot use piping using | operator to redirect to /dev/null. The only way is to use file redirections (\>, \>\>, or \<, \<\<).
**Ex:**
Lets say you are searching for a string "hello" in "/usr" directory. However, it will generate a lot of error as without root privilege, grep can’t access a number of files. In such a case, it’ll result in “Permission denied” errors. 
grep -r hello /usr/

![image](https://user-images.githubusercontent.com/43535914/127679508-4863d34a-ff2d-49f4-835c-44cd76e08c76.png)

Now, we can get a clearer output by redirecting unnecessary errors using /dev/null as shown below.
grep -r hello /usr/ 2> /dev/null
 
![image](https://user-images.githubusercontent.com/43535914/127679620-9f3530cf-2734-4e71-9333-0c3271f34c5c.png)


### 17. What are hidden files/directories and how to list them?
A hidden folder/file is a folder or file which filesystem utilities do not display by default when showing a directory listing. Files with names beginning with a dot are hidden files. An example of these files are .bashrc, .KUBECONFIG, etc. <br> The command used to list them is, **ls -a**
 

### 18. What is systemd?
- Systemd (System 'd', d stands from daemon) is a system and service manager for Linux operating systems.
- systemd is the first daemon to start during booting and the last daemon to terminate during shutdown. As an init implementation, it has a PID of 1.
- If we visualize the unix/linux system in layers, systemd would fall directly after the linux kernel.
**Hardware -> Kernel -> Daemons, System Libraries, Server Display**
- Systemd provides a standard process for controlling what programs run when a Linux system boots up. The systemctl command is the primary tool to manage and interact with processes that are controlled by systemd.
- On a system which uses systemd we would use "**journalctl**" to display the logs

### 19. How to make a certain process/app a service?
Say you have a JAR file and you need to run it as a service. Additionally, you want it to start automatically if/when system restarts. Linux has a built-in mechanism to create custom services, enabling them to get started at system boot time and start/stop them as a service.
#####Step 1: Create a Service
sudo vim /etc/systemd/system/my-webapp.service
Copy/paste the following into the file /etc/systemd/system/my-webapp.service
 
    [Unit]
    Description=My Webapp Java REST Service
    [Service]
    User=ubuntu
    # The configuration file application.properties should be here:

    #change this to your workspace
    WorkingDirectory=/home/ubuntu/workspace
    
    #path to executable. The executable is a bash script which calls jar file 
    ExecStart=/home/ubuntu/workspace/my-webapp

    SuccessExitStatus=143
    TimeoutStopSec=10
    Restart=on-failure
    RestartSec=5

    [Install]
    WantedBy=multi-user.target
 
##### Step 2: Create a Bash Script to Call Your Service and provide execute permission for the file: sudo chmod u+x my-webapp
Here’s the bash script that calls your JAR file: my-webapp

    #!/bin/sh
    sudo /usr/bin/java -jar my-webapp-1.0-SNAPSHOT.jar server config.yml


##### Step 3: Start the Service
    sudo systemctl daemon-reload
    sudo systemctl enable my-webapp.service
    sudo systemctl start my-webapp
    sudo systemctl status my-webapp 
 

### 19. What is SSH and why SSH is considered better than telnet?
SSH, or Secure Shell, is a cryptographic network protocol for operating network services securely over an unsecured network. In simple words, SSH is a secure protocol used as the primary means of connecting to Linux servers remotely. An SSH server will have SSH daemon running and depends on the distribution, you should be able to check whether the service is running (e.g. systemctl status sshd).
Telnet also allows you to connect to a remote host but as opposed to SSH where the communication is encrypted, in telnet, the data is sent in clear text, so it doesn't considered to be secured because anyone on the network can see what exactly is sent, including passwords.

### 20. What is stored in ~/.ssh/known_hosts?
This is a very important file for SSH. The ~/.ssh/known_hosts file contains the SSH fingerprints of machines you've logged into. These fingerprints are generated from the remote server's SSH key when you secure shell into a remote machine for the first time. The known_hosts file lets the client authenticate the server, to check that it isn't connecting to an impersonator. 
Note:
If you get error like "Host key verification failed" when you try to ssh to a server then this means that the key of the remote host was changed and doesn't match the one that stored on the machine (in ~/.ssh/known_hosts).

### 21.What is ssh-keygen used for?
ssh-keygen is a tool for creating new authentication key pairs for SSH. Such key pairs are used for automating logins, single sign-on, and for authenticating hosts. 
 
## Linux-commands 
  
<details>
<summary>View files/directories</summary><br>    
  
Command |	Usage	| Description
------- | ----- | -----------
ls | ls |	lists all directories/files in the current terminal directory.
|  | ls -l	| lists files/folders in long table format (shows file permissions, ownership, number of links, file/directory size, last modified date & time)
|  | ls –a	| List all the files including the hidden ones
|  | ls –t |	List the files sorted by last modified time
|  | ls -lrt  (or)  ll |	lists the contents of the directory with all the details, in reverse order of their modification time (older files will be displayed first).
pwd |  |	Show present working directory path.
tree	| tree \<dir_name\> | view hierarchical structure of a directory in tree format.
file | file \<filename\> | Determine the type of a file 
  
</details> 
  
<details>
<summary>Read a file</summary><br>    

Command	| Usage	| Description
------- | ----- | -----------
cat	| cat \<filename\> | Read contents of the file
less | less \<filename\>	| Displays contents of file page by page. With cat command if the file is huge, it will quickly scroll everything and you can see only bottom part of file. To have file navigational control you can use less command. (give enter to navigate page, use “q” to come out of the command)
head | head \<filename\> | To view first 10 lines of a file.
|  | head -5 \<filename\> |	To view first 5 lines of file.
tail	| tail \<filename\>	| output the last 10 lines of file    

</details> 
  
  
<details>
<summary>Create and delete files/directories</summary><br>    

Command	| Usage	| Description
------- | ----- | -----------
touch | touch \<filename\> | It is used to create empty file (0 bytes). It is also used to create, change and modify time stamps of a file.
vi | vi \<filename\> | vi stands for ‘Visual Improved’. Open editor by using command vi. The vi editor has 2 modes: 1) Insert mode 2) for editing <br> Go to insert mode, by pressing letter **i** on keyboard as it allows you to edit the file. <br> Once you are done editing the file, Exit insert mode – Press **ESCAPE** key. <br>  **:wq** --- Save and quit (w for save(write) and q for quit). <br>  **:q** --- quit without save if no changes are made to file. <br> **:q!** --- quit without saving changes made to a file
cat |	cat > [filename]	| Create a file and insert contents to that file on terminal. Press Ctrl+D to exit. If file already exists it overwrites.
|  | cat [file1] \> [file2] | Copy contents of one file to another. (\>  Can also be used to redirect the output of cat command to a file rather than standard output)
|  |cat [file1] \>\> [file2] | Instead of overwriting file2, it appends contents of file1 to file2 using redirection operator \>\>
|  |	cat \>\> file.txt << EOF <br> Insert multiple lines <br> EOF	| Write multiple lines from the command line.  <br> **Ex:** <br> cat << EOF <br> The current working directory is: $PWD <br> You are logged in as: $(whoami) <br> EOF
mkdir	| mkdir \<dir_name\> | Creates a directory
|  |	mkdir -p d1/d2/d3	| Create multiple sub directories (-p means Parent)
rmdir	| rmdir \<dir\>	| Removes empty directory
| rm |	rm \<file\>	| Delete a file
|  | rm -r \<dir\> |	Delete empty/non-empty directories recursively.
|  | rm -f \<file\>	| Prompts error while deleting non-existent file/directory. Use -f to suppress such prompts

##### Vi Editor shortcuts
1) Copy a word <br>
**yw** – copies a word – from where the cursor is placed till the end of the word (**Y** stands for yank (Greek word) which means copy, **P** – paste) <br>
**2yw** – copies 2 words.
2) Copy a line <br>
**yy** – copies entire line <br>
**5yy** – copies 5 entire lines
3) Delete word <br>
**dw** – deletes a word
4) Delete a line <br>
**dd** – deletes a line <br>
**5dd** – deletes 5 entire lines
  
</details> 
  
  
<details>
<summary>Manage files/directories</summary><br>    

Command	| Usage	| Description
------- | ----- | -----------
cd	| cd /path/to/directory	| Change directory
|  |	cd  (or)  cd ~ 	| Navigate to home directory
|  |	cd /	| Navigate to root directory
|  |	cd ..	| Navigating up one directory level (Ex: If you are in /usr/bin folder then typing cd .. command will navigate to /usr folder)
|  | cd - | Change to last visited path
cp |	cp \<file1\> \<file2\>	| Makes a copy of a file
|  |	cp -p \<file1\> \<file2\> |	Copy file by preserving time stamp.
|  | cp -i \<file1\> \<file2\>	| cp and mv commands doesn’t prompt while overwriting an existing file. Use -i interactive option to enable prompt.
|  |	\cp \<file1\> \<file2\> |	Use a backward slash before the cp command to force cp command to overwrite without confirmation 
|  |	cp \<file\> \<dir\> |	Copy file to a directory
|  |	cp -r \<dir1\> <dir2\>	| copy dir1 to dir2; create dir2 if it doesn't exist
mv	|	 | mv can be used to rename or move a file
|  |	mv \<file1\> \<file2\>	| Renames a file if moved in same dir (file1 disappears and file2 appears with same content as file1)
|  |	mv \<file1\> \<dir\>	| Move a file to a directory (mv command works like cut and paste)
diff	| diff \<file1\> \<file2\>	| compares two text files and shows the differences between them.
stat |  |	Display when a file was last accessed, modified, or changed.
  
</details> 
  
  
<details>
<summary>Finding files and directories</summary><br>    

Command	| Usage	| Description
------- | ----- | -----------
whereis	| whereis \<filename\>	| Shows possible locations of file.
which	| which \<filename/app\> |	Shows which app will be run by default. <br> **Ex:** which java
locate |	locate \<filename\>	| Find all instances of file using indexed database built from updatedb command. It searches a prebuilt database of files (updatedb) that needs to be updated regularly (once a day). Much faster than find, but if a file is deleted still will show matched, if the file image still exist in the database.
find	| find \<folder-path-in-which-to-find\> -options \<filename\>	| Find all instances of a files/directories in real system. <br> **Ex:1** find /home -name test.txt <br> Find a file named test.txt under /home directory. Use -iname option if you want to ignore case (ie., filename can contain upper/lower case letters) <br> **Ex:2** find / -type d -name "tomcat" <br> Find directory named tomcat under / path 

</details>   


<details>
<summary>Links</summary><br>    

Link is similar to the shortcut concept that we have in windows. Imagine that you have files in D drive. You can create a shortcut on desktop so that you can simply click on shortcut and start accessing the files. 
There are two types of links available.
-  Soft link
-  Hard link
  
#### 1. Soft link:  (Shortcut file)
With soft link you can use the shortcut to access data as long as the original data is present.
Syntax:	ln -s {source-filename} {symbolic-filename}

**Ex:**  To create a soft link named file2 for file1 (both in the current directory). Whatever content present file1, the same content you can see via file2.
 
    ln -s file1 file2
##### Advantage of soft link:
Suppose there are files which you don’t want to give direct access to some users. In that case you can create a soft link out of original files and give soft link file access to other users. So even if the soft link file gets deleted, the original data will still remain. But if the original data itself is deleted then the soft link cannot do anything.

#### 2. Hard link:  (Backup file)
In case of hard link even though the original file is deleted still you can access the data via hard link file.
Syntax:	ln {source-filename} {symbolic-filename}
 
**Ex:** To create a hard link named file2 for file1 (both in the same directory)
 
    ln file1 file2
##### Difference between copy and hard link?
If you create a file1 with some content and copy it to file2 then it gets copied successfully. But if you make further modifications in file1 then those changes will not be reflected to file2. But with hard link all changes made to file1 will be reflected to file2.
  

</details> 

  
<details>
<summary>Environment variables</summary><br>    

Command	| Description | Example
------- | ----------- | ---------
echo $VARIABLE	| To display value of a variable | echo $PATH <br> To display value of PATH variable
env	| Displays all environment variables | 
VARIABLE_NAME=variable_value |	Create a new variable | VAR1=/usr/java/
unset VARIABLE_NAME |	Remove a variable	| unset VAR1
export Variable=value	| To set value of an environment variable |	export VAR1=/usr/tmp  

</details>

  
<details>
<summary>Standard I/O Streams</summary><br>    

In Bash and other Linux shells, when a program is executed, it uses three standard I/O streams. Each stream is represented by a numeric file descriptor:
- 0 - stdin, the standard input stream.
- 1 - stdout, the standard output stream.
- 2 - stderr, the standard error stream.
When you execute a command, you might notice that the output/error messages are printed on the screen. With the help of above file descriptors, you can redirect them to a file.   

</details>  
 

<details>
<summary>I/O Redirection</summary><br>    

Redirection is a feature in Linux such that when executing a command, you can change the standard input/output devices.
  
**Ex:** With the help of redirection operators you can copy the output of any command(s), file(s) into a file.
  
Redirection	| Usage |	Description
----------- | ----- | ------------
Input Redirection ( \< ) |	command \< file |	**Ex:**  If you want to attach a file to email you can use the input re-direction operator in the following format. <br> mail -s "Subject" Recipient_MailID < Filename
Output Redirection ( \> ) |	command \> file	| Redirecting output to a file. Instead of displaying output on the cmd screen it will redirect to file. <br> **Ex:1**  ls -l \> file1 <br> **Ex:2**  data \> file1 <br> If you enter wrong command and redirect the output to file then it will display error on screen. Error will not be stored in file
Error redirection ( 2\> )	|command 2\> file |	Redirects error message to the file you specify. <br> **Ex:1**  mkdir dir1/dir2/dir3 2\> file1 <br> It redirects the error message of mkdir to file1 <br> **Ex:2**  (data;cal) 2\> file1 <br> The error message will be redirected to file1 and the output of cal command will be displayed on screen.
Redirecting output and error ( &\> ) |	command &\> file |	If you want to store both output and error message in a file. <br> **Ex:** (data;cal) &\> file1
Redirecting output and error ( 2\>&1 ) | command > file 2\>&1 <br> (OR) <br> command 2\>&1 > file | This is another alternative to redirect both output and error message to a file <br> **Ex:** (data;cal) 2\>&1 \> file1 
Appending ( \>\> ) |	command \>\> file | Append to file. If you do not want a file to be overwritten but want to add more content to an existing file
Redirecting  error without overriding ( 2\>\> ) |	command 2\>\> file |	Redirects error message without overriding the contents of file. <br> Every time you execute 2\>, it will override the previous error message that is stored in file. But with 2\>\> it will append the error to the file.
Redirecting output and error without overriding ( &\>\> ) |	command &\>\> file |	Redirects both output and error without overriding the contents of file. Every time you execute &\>, it will override the previous output/error that is stored in file. But with &\>\> it will append the data to the file.
Heredoc ( \<\< ) |	Command \<\< delimiter <br> Any text/input <br> delimiter | \<\< is a type of redirection that allows you to pass multiple lines of input to a command. It reads the input until it finds a line containing the specified delimiter. Delimiter can be of any name, but note that you end with the same delimiter. <br> **Ex:** <br> wc -l << EOF <br> This is a <br> simple lookup program <br> EOF <br> o/p:  2
\| 	| command1 \| command2	| A pipe is a form of redirection that lets you run two or more commands, such that output of one command serves as input to the next command. <br> **Ex:** <br> head -5 file1 | tail -1 <br> head -5 file1 provides five lines and tail -1 provides last line that got from head command. So you will get fifth line from file1  

</details>
  
<details>
<summary>Metacharacters</summary><br>    

Symbol	| Description | Example
------ | ----------- | --------- 
&&	| AND conditional execution 	| command1 && command2
\|\| |	OR conditional execution	| command1 \|\| command2
; |	Command separator. Execute multiple commands at once such that each command is separated by a semi colon |	ls;date;cal
( )	| Groups commands |	date;cal \> file1 <br> Output of date command will be displayed on CMD and output of cal command will be stored in file1. When there are multiple commands which are given on same line then the redirection operator will work only on the immediate command not on previous commands. <br> If you want to redirect output of multiple commands to a file then ensure that the commands are enclosed in parenthesis <br> (date;cal) \> file1
$	| Variable substitution |	set name=Tom <br> Sets the variable name to Tom ; <br> echo $name <br> displays the value stored there
&	| Run a command in the background	|  |
| #	| Comment |	#This is a comment line
\ |	Avoid interpretation of meta-characters. Any meta-character immediately following backslash loses its special meaning. Sometimes we need to pass meta-characters to the command being run and do not want the shell to interpret them | echo Hello; world <br> **o/p:** <br> Hello <br> -bash: world command not found <br> <br> echo Hello\\; world <br> **o/p:** <br> Hello; world
‘ ‘	| All special characters between these quotes lose their special meaning | Consider an echo command that contains many special shell characters <br> echo \<-$1500.\*\*\>; <br> Putting a backslash in front of each special character is tedious and makes the line difficult to read. <br> echo \\<-\\$1500.\\*\\\*\\\>\\; <br> In that case simply Put a single quote (') at the beginning and at the end of the string. <br> echo '\<-$1500.\*\*\>;' 
“ “ |	Use double quotes when you want to display the real meaning of special variables. Double quotes take away the special meaning of all characters except the following. <br> $ Parameter Substitution <br> ` Backquotes <br> \\$ Literal Dollar Sign <br> \\´ Literal Backquote <br> \\” Embedded Doublequote <br> \\\\ Embedded Backslashes	| **Ex:1:** <br> echo "Hostname=$HOSTNAME ; &nbsp; &nbsp; &nbsp; Current User=\`whoami\` ; Message=\\$ is USD" <br> **o/p:** <br> Hostname=dev-db ; &nbsp; &nbsp; &nbsp; Current User=Tom ; Message=$ is USD <br> <br> **Ex:2** <br> echo "Hello &nbsp; &nbsp; &nbsp; \\"World\\"" <br> **o/p:** <br> Hello &nbsp; &nbsp; &nbsp; "World
\` \`	| Anything in the back quote will be treated as a command and would be executed |	D=\`date\` <br> echo "Current Date: $D" <br> **o/p:** <br> Current Date: Thu Jul  2 05:28:45 MST 2020  

</details>
  
<details>
<summary>Regular expressions</summary><br>    

A regular expression or regex is a pattern of text you define to filter text.
**Below mentioned are few Wildcard characters:**
  
Symbol	| Description | Example
------ | ----------- | --------- 
^ |	Matches start of the string |	**Ex:**  cat sample \| grep ^A <br> Display all lines that start with A
$	| Matches end of string | **Ex:** <br> cat sample | grep s$ <br> Display all lines that end with s
.	| Replaces any character	|  |
[...] |	Any character within the specified range	| **Ex:** <br>  ls -l [abcdef]ile <br> The name of the file can start with either a or b or c or d or e or f. The first character should be one of the characters that are enclosed in square brackets.
\*	| Represents zero or more number of characters. Those characters can be anything number/alphabet/special character. |	**Ex:** <br>  ls -l file* <br> Lists all files starting with word file followed by zero or any number of characters
?	| Represents only one character	| **Ex:1** ls -l file? <br> It searches for all files whose name is starting with word file and then it should have only one character. <br> **Ex:2** ls -l file?? <br> It searches for all files whose name is starting with word file and then it should have two characters.
 
</details>  

<details>
<summary>Text processing</summary><br>    

Command	| Usage	| Description
------- | ----- | -----------
wc |	wc \<filename\> |	Prints the number of bytes, words and lines in a file.
|  |	wc -l \<filename\> |	Prints number of lines in a file
|  |	wc -w \<filename\> |	Prints number of words in a file
|  |	ls -1 \| wc -l	| Prints number of files/directories
sort |	sort \<filename\>	| Sort command by default performs alphabetical sort. Which means it sorts based on the first character. <br> **Ex:** <br> Consider file1 data like:  25 &nbsp; 34 &nbsp; 28 &nbsp; 33 &nbsp; 22 <br> **Output:** 25 &nbsp; 28 &nbsp; 22 &nbsp; 34 &nbsp; 33
|  | sort -n \<filename\> |	Numerical sort. <br> For the same above example the output will be: <br> 22 &nbsp; 25 &nbsp; 28 &nbsp; 33 &nbsp; 34
cut |	cut -d “\<delimiter\>” -f \<columns_to_display\> \<filename\>	| Cut is used for displaying data in column fashion. <br> **Ex:** Consider file1 data <br> Hi:Hello:Welcome <br> This:is:xxx <br> **Command:** cut -d “:“ -f 1,3 file1 <br> **Output:** Hi:Welcome <br>This:xxx	
awk	|  |	awk is a general-purpose scripting language designed for advanced text processing. It is used for manipulating data and generating reports. <br> **Ex:** when you run "who" command perhaps we don’t need all of that information presented in the output, but, rather, just want to see the names on the accounts. We can use pipe and send the output from who into awk command, and then tell awk to print only the first field. <br> who \| awk '{print $1}'  

</details> 
  
<details>
<summary>Searching</summary><br>    

Command	| Usage	| Description
------- | ----- | -----------
grep | grep \<string\>	| Global Regular Expression Print (GREP) utility searches for specified string/pattern in a file/files and displays all lines containing that pattern. <br> **Ex:**  grep ubuntu /etc/passwd <br> It will search for text "ubuntu" in "/etc/passwd" path
|  | grep -i \<string\> \<filename\> |	Since linux is case sensitive use -i option for case insensitive search. **Ex:** grep -i Ubuntu /etc/passwd
|  | grep -n \<string\> \<filename\> |	Displays lines along with line number
|  |	command \| grep \<pattern\> |	Search for pattern in the output of command <br> **Ex:** history \| grep "ls" <br> It will search for all the commands with "ls" from previous history of commands
sed |	sed -i 's/old-text/new-text/g' file.txt |	(Stream editor) To find and replace text in a file. <br> s - Substitute, can be normal string or regex <br> g  -  Global replacement string <br> i  -  used to edit In-place on the file  

</details> 
  
<details>
<summary>Managing users and groups</summary><br>    

Command | Description
------- | -----------
useradd \<username\>	(OR) adduser \<username\> |	Create/add new user. (Note: A home directory for user will be created under /home directory) 
passwd	| Update password for your username 
passwd \<username\>	| If you as root user, changing password for a particular user
userdel \<username\>	| Delete user
groupadd \<groupname\> |	Create a new group
groupdel \<groupname\> |	Delete an existing group
usermod –aG \<groupname\> \<username\>	| Add existing user to a secondary group. <br> When a user creates a file, the file’s group is set to the user’s primary group. Usually primary group is same as the name of the user (you can check this info in /etc/passwd file). 
gpasswd –d \<username\> \<groupname\>	| Remove user from a group
|  |	/etc/passwd  -  Contains user account information <br> /etc/group   -  Contains group account information <br> Whenever a new user is added, you can find an entry in these files
su <username> |	used to switch to another user
sudo su	 | To elevate your privileges to super user for subsequent command execution.
visudo  (OR)  vi /etc/sudoers	| Sudoers file. You can provide sudo privileges to a user by adding user to this file.
usermod -aG root \<username\>	| Adding user to root group. <br> **Ex:** Lets say you have Created a user, but that user is unable to view files under /root folder. In that case, add user to root group. Now the user will have read-only access and cannot modify any files. If user have to modify anything then user need to be added in sudoers file.  

</details>   

<details>
<summary>Check user information</summary><br>    

Command | Description
------- | -----------
Whoami	| Displays as which user you are logged in as.
finger \<username\>	| Display information about the user.
users  (or)  id	| Shows user information
w	| lists the currently logged in users and what they are doing.
who |	lists the currently logged in users.
last	| This picks information from /var/log/wtmp file to display the user login information. Shows list of all users logged in (and out) since that file was created. <br> **Ex:1**  last reboot <br> Display previous reboot date and time for the system. <br> **Ex:2**  last <username> <br> To view the user’s login and logout details
 
Below are few files that contain user login information:
 
    /var/run/utmp: It contains information about the users who are currently logged in. Who command is used to fetch the information from the file.
    /var/log/wtmp: It keeps the users login and logout history. The last command uses this file to display the information.
    /var/log/btmp: It contains bad login attempts. 
  

</details> 
  
<details>
<summary>Check system information</summary><br>    

Command | Description
------- | -----------
uname -a	| Displays system information, including machine name, kernel name & version, hardware, OS etc.
arch |	To find whether it is 32 bit or 64 bit OS
lscpu |	displays system’s CPU architecture information (such as number of CPUs, threads, cores, sockets, and more).
cat /proc/cpuinfo |	Displays CPU information
cat /proc/meminfo |	Displays memory information
lsb_release -a  (OR)  cat /etc/lsb-release	| prints version information for the Linux release you're running. In some systems os-release file will be there instead of lsb-release file
uptime	| Shows since how long system has been running, number of users currently logged in and also displays load average for 1,5 and 15 minutes intervals.
shutdown |	Shutdown machine
reboot |	Restart machine
  

</details> 
  
<details>
<summary>Hardware related</summary><br>    

Command | Description
------- | -----------
df |	displays file system disk space usage for all mounted partitions. Shows the size, used space, and available space on the mounted file systems of your computer (Like C Drive in windows)
df -Th \| grep "^/dev"	| To find the file system type
fdisk -l	| Shows disk partitions, sizes and types
fdisk -l \| grep Disk |	Display total hard disk size
du |	Displays the disk usage by directory(directory space usage). <br> **Ex:** Faced issue as disk space full. <br> df -h command is showing that 44 GB is full, whereas in real it is not <br> Filesystem &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Size &nbsp;&nbsp;&nbsp; Used &nbsp;&nbsp; Avail &nbsp;&nbsp; Use% &nbsp;&nbsp; Mounted on <br> /dev/mapper/centos-home 44G &nbsp;&nbsp; 44G &nbsp;&nbsp; 53M &nbsp;&nbsp; 100% &nbsp;&nbsp; /home <br> du -h /home \| sort -rn <br> Used the above command to sort files under home directory by size in order to know which file/folder is consuming more disk space <br> du -h /home 2>/dev/null \| grep '[0-9\\.]\\+G' <br> This command shows disk usage for folders in GB
free	| displays the amount of free and used memory in the system.
grep MemTotal /proc/meminfo	| To get total amount of memory (ie., RAM size)
lsblk |	List block devices
Options or flags that can be used for df, du, free commands: megabytes (m), gigabytes (g), human readable (h)
  
</details>   
 
<details>
<summary>Process related</summary><br>    

Command	| Usage	| Description
------- | ----- | -----------
ps	| ps -ef \| grep java (OR) ps -aux	| (Process Status) Displays a list of currently running processes along with process id’s (PID). <br> -e means Display all processes <br> -f means Display a full listing
pstree |  |		Visualizing processes in tree model
kill	| kill \<pid\>	| Kill process by using process id(pid)
|  |	kill -9 \<pid\> |	Force kill a process. Internally it sends a signal, and depending on what you want to do. (-9 signal to kill)
killall	| Killall proc	| lets you kill all processes named proc.
top	 |   | The top ('table of processes') command displays list of all running processes, sorted by how much CPU each processes uses. Unlike ps, this command regularly updates in real-time. Basically a terminal equivalent to Task Manager. To exit top, press "q"
lsof |   |		Lists files that are open by processes
fg	| fg \<Job_name\>	| Run a program in the foreground
bg	|   |Run a service in background   

</details> 
  
<details>
<summary>Network related</summary><br>    

Command	| Usage	| Description
------- | ----- | ----------- 
ifconfig (OR) ip addr show |   |		Stands for “interface configuration." It is used to view and change the configuration (IP address, network interfaces, bandwidth usage, and more) of the network interfaces on your system.
hostname	|   |	Shows the system hostname
|   |	hostname -i	| Displays ip address of the system
|   |	vi /etc/hostname	| Location of file where you can change hostname of system. <br> The other place to change is /etc/hosts file and then restart the system.
ping |	ping \<ip or hostname\>	| Used to check your connectivity status to a server and the speed of that network connection. 
telnet |	telnet \<target_ip\> \<port\>	| Connect to remote host or check port availability status.
dig |	dig gmail.com |	Look up a domain's DNS address. to get the IP address and information about the name servers of the domain gmail.com
wget |	wget \<url\> |	lets you perform a non-interactive download of packages/software.
curl	| curl \<url\>	| retrieve information and files from URL’s or internet addresses. Access the application as from browser.
netstat	|	  | (Network statistics) provides information and statistics about protocols in use and current TCP/IP network connections. 
|   |	netstat -tulpn \| grep LISTEN <br> (OR) <br> netstat -aon |	To check which ports are listening
firewall	| firewall-cmd --state |	Check firewall status
|   |	systemctl disable firewalld |	Disable firewall
|   |	systemctl stop firewalld |	Stop firewall
|   |	firewall-cmd --permanent --add-port=6443/tcp |	Add firewall rules on ports   

</details> 
  
<details>
<summary>Service</summary><br>    

Command	| Usage	| Description
------- | ----- | -----------  
service	| service \<service_name\> start |	To start a service
|   |	service \<service_name\> stop/status/restart/reload	| Likewise, can stop service or restart or check status of service whether it is running or not
chkconfig |   |		It is used to list all available services and view or update their run level settings. This command controls which services are set to start on boot 
   

</details> 
  
  
<details>
<summary>Remote Login</summary><br>    

Command	| Usage	| Description
------- | ----- | ----------- 
ssh	| ssh [user-name]@[remote-ip] | SECURE SHELL. Used to connect and login to a remote server and provides secure encrypted communication (ssh default port 22)
logout |   |		To logout from already taken remote console. 

</details>   


<details>
<summary>File transfer</summary><br>    

To copy files between servers
  
**Windows to Linux (or) Linux to windows:**		winscp

**Linux to Linux:**		SCP (secure copy)
  
Command	| Usage	| Description
------- | ----- | -----------  
scp	|  |	Command line utility that allows you to securely copy files and directories between two systems.
|   |	scp root@192.168.0.106:/data/abc.txt /root/	| Used to check your connectivity status to a Copy Data from Remote System to Local
|   |	scp /root/database.txt root@192.168.0.106:/data/	| Copy Data from Local System to remote (User -r option to recursively copy directory.  

</details> 
  
  
<details>
<summary>Compression or archieve</summary><br>    


</details>   
 

<details>
<summary>Crontab</summary><br>    
  
CronTab (Cron Table) is a system process that will automatically perform tasks as per the specific schedule.
Crontab Syntax:
Crontab of Linux has six fields. The first five fields define the time and date of execution, and the 6'th field is used for command execution. 

![image](https://user-images.githubusercontent.com/43535914/127639759-6cb9b716-ce1b-413a-a875-c9305d925b97.png)
- Astrics (*): Use for matching
- Define range: Allows you to define a range with the help of hyphen like 1-10 or 30-40 or jan-mar, mon-wed.
- Define multiple ranges: Allows you to define various ranges with command separated like apr-jun,oct-dec.
**Ex:**  0 7,17 * * * /scripts/script.sh
 
Command	| Description
------- | -----------
crontab -e |	Edit crontab
crontab -l	| View crontab entries for current user
crontab -u \<username\> -l |	View crontab entries of a specific user
crontab -r |	Remove your crontab tasks 
 
</details>   
   

 
 
