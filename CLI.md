# Practice Drill 1
------------------------------------
1. Creating the directory structure :-
	mkdir -p hello/five/six/seven 
		- "mkdir" --> to create directory, 
		- "-p" --> check if the file exist or if not create a 		 new one
	mkdir -p hello/one/two/three/four
	touch hello/five/six/c.txt
		- "touch" --> to create new file
	touch hello/five/six/seven/error.log
	touch hello/one/a.txt
	touch hello/one/b.txt
	touch hello/one/two/d.txt
	touch hello/one/two/three/e.txt
	touch hello/one/two/three/four/access.log
	
2. Delete ".log" files :-
	find hello -name "*.log" -delete (find <directory name> <specific name> <find string> <operation need to perform"
		- "find" --> to query the particular file name in the mentioned directory
		
3. Add content to a.txt file :-
	echo "Unix is a family of multitasking, multiuser computer operating systems that derive from the original AT&T Unix, development starting in the 1970s at the Bell Labs research center by Ken Thompson, Dennis Ritchie, and others" > hello/one/a.txt
		- ">" --> redirect operation 

4. Delete the directory named "five" :-
	rm -r hello/five
		"rm" --> rm used to remove the file or folder
		"-r" --> options to specify remove if the directory contains some data
		
5. Rename directory "one" to "uno" :-
	mv hello/one hello/uno
		"mv" --> mv stands for the move the file or the folder & Also we ca use this to rename the file or folder
	
6 . Move "a.txt" to "two" :-
	mv hello/uno/a.txt hello/uno/two
		"mv" --> here we are using the mv command to move the file from one folder to another

# Practice drill 2
-----------------------------

1. Print First Three Lines:
   head -n 3 Harry\ Potter\ and\ the\ Goblet\ of\ Fire.txt
   	"head" --> this will go in to the top of the file
   	"-n" --> this tells the head to check specified number of line

2. Print Last 10 Lines:
   tail -n 10 Harry\ Potter\ and\ the\ Goblet\ of\ Fire.txt
   	"tail" --> this will go in to the end of the file

3. Word Occurrences:

   	a. grep -o -i "Harry" Harry Potter and the Goblet of Fire.txt | wc -l
   	"grep" --> used to search the pattern 
   	"-o" --> only outputs the matched pattern
   	"-i" --> case insensitive
   	"wc" --> word count
   	"-l" --> in list
   	
   	b. grep -o -i "Ron" Harry Potter and the Goblet of Fire.txt | wc -l
   	c. grep -o -i "Hermione" Harry Potter and the Goblet of Fire.txt | wc -l
   	d. grep -o -i "Dumbledore" Harry Potter and the Goblet of Fire.txt | wc -l

4. Print Lines 100 to 200:
   sed -n '100,200p' Harry Potter and the Goblet of Fire.txt
   	"sed" --> its a built in stream editor
   	"-n" --> numbers of line to print
   	"100,200p' --> Regex

5. Unique Words Count:
   cat Harry Potter and the Goblet of Fire.txt | sort | uniq | wc -l
   	"sort" --> sorting in the specified way
   	"uniq" --> output should not contain dupicates

Processes and Ports

1. List Browser Process IDs:
   pgrep -l firefox
   	"p" --> to list process

2. Stop Browser Application:
   pkill firefox
   	"pkill" --> to the process 

3. Top 3 CPU Usage Processes:
   top -bn1 | grep "^ *[0-9]" | sort -rk 9 | head -n 3
   	"top" --> to see the CPU running tasks
   	"-b" --> run in a batch
   	"-n1" --> run only one time
   	"-r" --> reverse the sorting
   	"-k" --> sort by referring the column number

4. Top 3 Memory Usage Processes:
   top -bn1 | grep "^ *[0-9]" | sort -rk 10 | head -n 3
	
5. Start Python HTTP Server on Port 8000:
   python3 -m http.server 8000

6. Stop Previous Python HTTP Server:
   - Use `ps aux | grep http.server` to find the PID and `kill PID`.

7. Start Python HTTP Server on Port 90:
   python3 -m http.server 90

8. Display Active Connections:
   netstat -tuln
   	"netstat" --> network utility
	"-t" --> tcp (Transmission Control Protocol sockets)
	"-u" --> udp (User Datagram Protocol sockets)
	"-l" --> listening sockets

9. Find PID on Port 5432:
   lsof -i :5432
   	"lsof" --> list of open files
   	"-i" --> to check the sockets

Managing Software

1. Install Packages (Ubuntu):
   sudo apt update
   sudo apt install htop vim nginx
   	"sudo" --> super user do (root) user
   	"apt" --> advanced package tool

2. Uninstall `nginx`:
   sudo apt remove nginx


Miscellaneous Commands:

1. Local IP Address:
   ip addr show | grep inet
	"ip" --> Internet protocol
	"addr" --> address
	"show" --> view 
	"grep" --> filter
	
2. Find IP of `google.com`:
   nslookup google.com
   	"nslookup" --> network systems look up

3. Check Internet Connectivity:
   ping -c 4 google.com
   	"ping" --> checking the connectivity

4. Locate `node` and `code` Commands:
   which node
   which code
   	"which" --> to locate the executable file
   	"node" --> nodejs
   	"code" --> VSCode
   	
   	
## Commands and Concepts

1. Basic Commands
---------------------
- man: Displays manual pages for commands.
  Example: man ls

- cd: Changes the current directory.
  Flags: . (current directory), .. (parent directory), ~ (home directory), - (previous directory)
  Example: cd /home/user/Documents

- mkdir: Creates a new directory.
  Example: mkdir new_directory

- mv: Moves or renames files and directories.
  Example: mv oldname.txt newname.txt

- cp -r: Copies files or directories recursively.
  Example: cp -r source_directory/ destination_directory/

- ls: Lists directory contents.
  Flags: -a (hidden files), -l (long format), -t (sort by time), -r (reverse), -h (human-readable)
  Example: ls -la

- pwd: Prints the current working directory.
  Example: pwd

- rm: Removes files or directories.
  Flags: -r (recursive), -f (force)
  Example: rm file.txt

- chmod: Changes file permissions.
  Numeric Mode: 755 (rwxr-xr-x)
  Symbolic Mode: u+x (add execute permission for user)
  Example: chmod 755 file.txt

- chown: Changes file owner and group.
  Example: chown user:group file.txt

- sudo: Executes commands with superuser privileges.
  Example: sudo apt update

- apt: Manages packages.
  Commands: update (update package lists), upgrade (upgrade packages)
  Example: sudo apt update

- touch: Creates or updates file timestamps.
  Example: touch newfile.txt

- cat: Concatenates and displays file content.
  Example: cat file.txt

- less: Views file content interactively.
  Example: less file.txt

- more: Views file content with forward navigation.
  Example: more file.txt

- tail: Displays the last part of a file.
  Flags: -n (number of lines), -f (follow updates)
  Example: tail -n 10 file.txt

- rsync: Syncs files and directories.
  Example: rsync -av source/ destination/

- grep: Searches for patterns in files.
  Example: grep "pattern" file.txt

- find: Searches for files and directories.
  Example: find /path -name "filename"

- sort: Sorts lines of text files.
  Example: sort file.txt

- date: Displays or sets the system date and time.
  Example: date

- tree: Displays directory structure (needs installation).
  Example: tree

- wc: Counts lines, words, and characters.
  Example: wc file.txt

2. OS/Process Related Commands
-------------------------------
- ps: Displays active processes.
  Example: ps aux

- top: Shows real-time process and resource usage.
  Example: top

- df: Reports disk space usage.
  Example: df -h

- uname: Displays system information.
  Flags: -a (all), -r (kernel version)
  Example: uname -a

- free: Displays memory usage.
  Example: free -h

- lspci: Lists PCI devices.
  Example: lspci

- kill: Sends signals to processes.
  Flags: -9 (forceful termination)
  Example: kill 1234

3. Network Related Commands
-----------------------------
- ping: Tests connectivity to a host.
  Example: ping google.com

- ifconfig: Displays/configures network interfaces (deprecated).
  Example: ifconfig

- ssh: Connects to a remote host via SSH.
  Example: ssh user@host

4. Bash Related Commands
-------------------------
- xargs: Builds and executes command lines from standard input.
  Example: find . -name "*.txt" | xargs cat

- printenv: Prints environment variables.
  Example: printenv

- nano: Simple text editor.
  Example: nano file.txt

- awk: Programming language for pattern scanning.
  Example: awk '{print $1}' file.txt

- sed: Stream editor for text manipulation.
  Example: sed 's/old/new/g' file.txt

- Pipe Operator `|`: Passes output of one command as input to another.
  Example: ls -l | grep "pattern"

5. Actions and Tasks
---------------------
- Create/Read/Update/Move Files and Folders
  Example: mkdir new_dir, cat file.txt, touch file.txt, mv file.txt new_dir/

- Check Disk Status
  Example: df -h

- Check Status of Processes and Extract PIDs
  Example: ps aux | grep process_name

- Get the Most Senior Parent Process
  Example: ps -o ppid= -p <pid>

- Change File Permissions
  Example: chmod 755 file.txt, chown user:group file.txt

- Extract Last X Lines, Word Count
  Example: tail -n X file.txt, grep -o "word" file.txt | wc -l

- Basics of `sed` and `awk`
  Example: sed 's/old/new/g' file.txt, awk '{print $2}' file.txt

- Absolute vs. Relative Paths
  Example: /home/user/file.txt (absolute), file.txt (relative)

- Use the `find` Command
  Example: find /home/user -name "*.txt"

- `ls` with Common Flags
  Example: ls -altrh

- Terminal Control Codes
  Example: Ctrl + C (terminate), Ctrl + Z (suspend), Ctrl + R (reverse search), Tab (autocompletion), Arrow Keys (navigate history)

6. Sample Review Questions
---------------------------
1. Go into your home directory: `cd ~`
2. Create a directory `d1`: `mkdir d1`
3. Create a file `a.txt` inside it: `touch d1/a.txt`
4. Check permission of `a.txt`: `ls -l d1/a.txt`
5. Change permissions of `a.txt` to 755: `chmod 755 d1/a.txt`
6. Add a directory `d2`: `mkdir d1/d2`
7. Add `b.txt` inside `d2`: `touch d1/d2/b.txt`
8. Change permissions of `d2` (and everything inside) to 755: `chmod -R 755 d1/d2`
9. Start Firefox browser: `firefox &`
10. List all processes: `ps aux`
11. Find PID of Firefox Browser: `ps aux | grep firefox`
12. Kill the process: `kill <pid>`
13. What is your user: `whoami`
14. What is your group: `groups`
15. What is your computer architecture: `uname -m`
16. What is your audio driver: `lspci | grep -i audio`
17. Find all occurrences of "java" text: `find ~ -type '*java'`
18. List everything in home directory, sorted by time in reverse with human-readable file sizes: `~ ls -lh`
19. Get last x lines for "Harry Potter": `tail -n 10 file.txt`
20. Get word counts for particular words: `grep -o "the" file.txt | wc -l`
