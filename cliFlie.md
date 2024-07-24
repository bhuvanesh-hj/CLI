### **Command Line Interface (CLI) Basics**

**1. What is a Shell?**
- A shell is a command-line interface that allows users to interact with the operating system by typing commands.
- Popular Linux shells include BASH, CSH, KSH, and TCSH.

**2. Shell Prompt Access:**
- **Terminal**: Use applications like XTerm, Gnome Terminal, or KDE Terminal.
- **SSH**: Access a remote server's shell.
- **Console**: Direct access upon system login.

**3. Determine Your Shell:**
```bash
echo $SHELL
ps $$
ps -p $$
```
- Output might show `bash` indicating you're using the BASH shell.

**4. Unix Philosophy:**
- *Do one thing and do it well.*
- *Everything is a file.*
- *Small is beautiful.*
- *Store data in text files.*
- *Use shell scripts for automation.*
- *Chain programs to complete tasks.*
- *Keep it simple.*

**5. Directory Structure:**
- `/`: Root directory.
- `/bin`: Essential binaries.
- `/etc`: Configuration files.
- `/home`: User home directories.
- `/opt`: Optional software.
- `/root`: Root user's home directory.
- `/sbin`: System administration binaries.
- `/tmp`: Temporary files.
- `/usr`: User binaries and data.
- `/var`: Variable data files.

---

### **Practice Drill 1: Directory and File Operations**

1. **Create Directory Structure:**
   ```bash
   mkdir -p hello/five/six/seven
   mkdir -p hello/one/two/three/four
   touch hello/five/six/c.txt
   touch hello/five/six/seven/error.log
   touch hello/one/a.txt
   touch hello/one/b.txt
   touch hello/one/two/d.txt
   touch hello/one/two/three/e.txt
   touch hello/one/two/three/four/access.log
   ```

2. **Delete `.log` Files:**
   ```bash
   find hello -name "*.log" -delete
   ```

3. **Add Content to `a.txt`:**
   ```bash
   echo "Unix is a family of multitasking, multiuser computer operating systems that derive from the original AT&T Unix, development starting in the 1970s at the Bell Labs research center by Ken Thompson, Dennis Ritchie, and others" > hello/one/a.txt
   ```

4. **Delete Directory `five`:**
   ```bash
   rm -r hello/five
   ```

5. **Rename Directory `one` to `uno`:**
   ```bash
   mv hello/one hello/uno
   ```

6. **Move `a.txt` to `two`:**
   ```bash
   mv hello/uno/a.txt hello/uno/two/
   ```

---

### **Practice Drill 2: Pipes and Redirection**

1. **Download the Book:**
   ```bash
   curl -O https://raw.githubusercontent.com/bobdeng/owlreader/master/ERead/assets/books/Harry%20Potter%20and%20the%20Goblet%20of%20Fire.txt
   ```

2. **Print First Three Lines:**
   ```bash
   head -n 3 Harry\ Potter\ and\ the\ Goblet\ of\ Fire.txt
   ```

3. **Print Last 10 Lines:**
   ```bash
   tail -n 10 Harry\ Potter\ and\ the\ Goblet\ of\ Fire.txt
   ```

4. **Word Occurrences:**
   ```bash
   grep -o -i "Harry" Harry\ Potter\ and\ the\ Goblet\ of\ Fire.txt | wc -l
   grep -o -i "Ron" Harry\ Potter\ and\ the\ Goblet\ of\ Fire.txt | wc -l
   grep -o -i "Hermione" Harry\ Potter\ and\ the\ Goblet\ of\ Fire.txt | wc -l
   grep -o -i "Dumbledore" Harry\ Potter\ and\ the\ Goblet\ of\ Fire.txt | wc -l
   ```

5. **Print Lines 100 to 200:**
   ```bash
   sed -n '100,200p' Harry\ Potter\ and\ the\ Goblet\ of\ Fire.txt
   ```

6. **Unique Words Count:**
   ```bash
   tr -c '[:alnum:]' '[\n*]' < Harry\ Potter\ and\ the\ Goblet\ of\ Fire.txt | sort | uniq | wc -l
   ```

---

### **Processes and Ports**

1. **List Browser Process IDs:**
   ```bash
   pgrep -l browser_name
   ```

2. **Stop Browser Application:**
   ```bash
   pkill browser_name
   ```

3. **Top 3 CPU Usage Processes:**
   ```bash
   top -bn1 | grep "^[0-9]" | sort -rk 9 | head -n 3
   ```

4. **Top 3 Memory Usage Processes:**
   ```bash
   top -bn1 | grep "^[0-9]" | sort -rk 10 | head -n 3
   ```

5. **Start Python HTTP Server on Port 8000:**
   ```bash
   python3 -m http.server 8000
   ```

6. **Stop Previous Python HTTP Server:**
   - Use `ps aux | grep http.server` to find the PID and `kill PID`.

7. **Start Python HTTP Server on Port 90:**
   ```bash
   python3 -m http.server 90
   ```

8. **Display Active Connections:**
   ```bash
   netstat -tuln
   ```

9. **Find PID on Port 5432:**
   ```bash
   lsof -i :5432
   ```

---

### **Managing Software**

1. **Install Packages (Ubuntu):**
   ```bash
   sudo apt update
   sudo apt install htop vim nginx
   ```

2. **Uninstall `nginx`:**
   ```bash
   sudo apt remove nginx
   ```

---

### **Miscellaneous Commands**

1. **Local IP Address:**
   ```bash
   ip addr show | grep inet
   ```

2. **Find IP of `google.com`:**
   ```bash
   nslookup google.com
   ```

3. **Check Internet Connectivity:**
   ```bash
   ping -c 4 google.com
   ```

4. **Locate `node` and `code` Commands:**
   ```bash
   which node
   which code
   ```

---

### **Sample Review Questions**

1. **Go to Home Directory:**
   ```bash
   cd ~
   ```

2. **Create Directory and File:**
   ```bash
   mkdir d1
   touch d1/a.txt
   ```

3. **Check Permissions:**
   ```bash
   ls -l d1/a.txt
   ```

4. **Change Permissions to 755:**
   ```bash
   chmod 755 d1/a.txt
   ```

5. **Add Directory and File:**
   ```bash
   mkdir d1/d2
   touch d1/d2/b.txt
   ```

6. **Change Permissions of `d2` to 755:**
   ```bash
   chmod -R 755 d1/d2
   ```

7. **Start Firefox Browser:**
   ```bash
   firefox &
   ```

8. **List All Processes:**
   ```bash
   ps aux
   ```

9. **Find PID of Firefox:**
   ```bash
   pgrep -fl firefox
   ```

10. **Kill Firefox Process:**
    ```bash
    pkill firefox
    ```

11. **User and Group Information:**
    ```bash
    whoami
    id -g -n
    ```

12. **Computer Architecture:**
    ```bash
    uname -m
    ```

13. **Audio Driver:**
    ```bash
    lspci | grep -i audio
    ```

14. **Find Files Containing "java":**
    ```bash
    find ~ -name "*java*"
    ```

15. **List Files Sorted by Time:**
    ```bash
    ls -lt --human-readable
    ```

16. **Get Last X Lines and Word Counts:**
    ```bash
    tail -n X Harry\ Potter\ and\ the\ Goblet\ of\ Fire.txt
    grep -o -i "word" Harry\ Potter\ and\ the\ Goblet\ of\ Fire.txt | wc -l
    ```

---

**Additional Notes:**
- **`man`**: Access manual pages for command documentation.
- **File Permission Conversion**: Binary to decimal for `chmod`.
- **Pipes (`|`)**: Chain commands together.
- **File Commands**: Learn `find`, `grep`, `awk`, `sed`, `chmod`, `chown`.

This summary should give you a robust foundation in Linux command-line basics and practical operations.
