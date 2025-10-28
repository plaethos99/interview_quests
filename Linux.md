

---

### **Category 1: File & Directory Operations (Questions 1-10)**

1.  How do you find all files in the current directory and all subdirectories that are larger than 100MB?
2.  What is the difference between a hard link and a symbolic (soft) link? What happens to each when you delete the original file?
3.  Write a command to find all files ending with `.tmp` and delete them. Do this in two ways: one using `find`'s `-exec` action and another piping to `xargs`.
4.  How would you list the 5 most recently modified files in the `/var/log` directory?
5.  Explain the purpose of the `xargs` command. Why is it often preferred over `find ... -exec` for a large number of files?
6.  How can you create a blank file or update the timestamp of an existing file without opening an editor?
7.  What command would you use to see the disk usage of a directory in a human-readable format, sorted by size?
8.  How do you find all files owned by the user `www-data`?
9.  What is a "sticky bit" on a directory? What is its common use case?
10. How would you recursively change the permissions of all directories to `755` and all files to `644` inside `/path/to/dir`?

---

### **Category 2: Text Processing & Regular Expressions (Questions 11-20)**

11. Using `grep`, how would you search for the exact word "error" in a log file, but not match "terror" or "errorless"?
12. What is the difference between `grep`, `egrep`, and `fgrep`? (Hint: Consider regular expressions).
13. Write a `sed` command to replace all occurrences of "192.168.1.100" with "10.0.0.5" in a file named `config.conf`.
14. How would you use `sed` to print only lines 15 through 30 of a large file?
15. Using `awk`, print the third and fifth columns of a comma-delimited file named `data.csv`.
16. Write an `awk` one-liner to calculate the sum of the second column in a file named `numbers.txt`.
17. How do you use `sort` to sort a file numerically and in reverse order?
18. What command would you use to find the 10 most common words in a text file?
19. Write a regular expression to match a valid email address.
20. How can you use `tr` to convert all uppercase letters in a file to lowercase?

---

### **Category 3: Process Management & Monitoring (Questions 21-30)**

21. Explain the difference between `kill`, `pkill`, and `killall`.
22. What is the difference between `SIGTERM` (signal 15) and `SIGKILL` (signal 9)? When should you use each?
23. How would you find the Process ID (PID) of a running process named `nginx`?
24. What command would you use to see all the processes running by a specific user, e.g., `postgres`?
25. Explain what `nohup` and `disown` do. When would you use them?
26. In `top` or `htop`, what do the `S` (or `STAT`) column codes `S`, `R`, and `D` mean?
27. How can you change the priority (niceness) of a running process?
28. What is the purpose of the `/proc` filesystem? Give an example of a file in `/proc` and what it shows.
29. How would you see the full command line arguments of all running `java` processes?
30. Explain what a "zombie" process is and whether it can be safely killed.

---

### **Category 4: Shell Scripting & Bash (Questions 31-45)**

31. What is the difference between `$VAR` and `${VAR}`? When is the latter necessary?
32. How do you check if a file exists and is a regular file in a Bash script?
33. Explain the difference between the `test` command (`[ ]`) and the double-bracket `[[ ]]` construct.
34. Write a Bash `for` loop that renames all `.jpeg` files in the current directory to `.jpg`.
35. How do you read a file line by line in a shell script?
36. What is the purpose of `set -e` and `set -u` in a script?
37. How do you create a function in Bash that takes two arguments and prints their sum?
38. Explain the difference between command substitution using backticks (`` `command` ``) and `$(command)`. Which is preferred?
39. How would you get the number of seconds since the Unix epoch in a script?
40. What does `exec > file.txt 2>&1` do at the beginning of a script?
41. How can you create an array in Bash and loop through its elements?
42. What is a "here document" (`<<EOF`) and how is it used?
43. How do you parse command-line options in a script (e.g., `-h` for help, `-f` for a file)?
44. What is the difference between sourcing a script (`source script.sh`) and executing it (`./script.sh`)?
45. How do you trap a signal (like SIGINT or SIGTERM) in a script to perform cleanup actions?

---

### **Category 5: User & Group Management (Questions 46-50)**

46. How do you add a new user named `johndoe`, create a home directory for them, and set their shell to `/bin/bash`?
47. What command would you use to lock a user's account so they cannot log in?
48. How do you add an existing user, `jane`, to an existing group, `developers`?
49. Explain the purpose of the `/etc/sudoers` file. What command should you use to edit it safely?
50. Where are user passwords stored on a modern Linux system? What format are they in?

---

### **Category 6: Permissions & Ownership (Questions 51-55)**

51. What does the permission `chmod 2755` mean? Explain the `2` (setgid) bit.
52. How do you recursively change the owner of a directory to `root` and the group to `wheel`?
53. What is the `umask`? How would you set a default `umask` of `022` for all new users?
54. How can you find files with world-writable permissions on your system?
55. Explain the difference between ACLs (Access Control Lists) and standard Unix permissions.

---

### **Category 7: Archiving & Compression (Questions 56-60)**

56. Write a command to create a gzipped tar archive of the `/home/user/documents` directory, named `backup.tar.gz`.
57. How would you extract the contents of `backup.tar.gz` to a specific directory, like `/tmp/restore`?
58. What is the difference between `.tar.gz` and `.tar.bz2`? Which generally provides better compression?
59. How can you list the contents of a tar archive without extracting it?
60. Write a command to compress a single large file, `database.sql`, using `xz`.

---

### **Category 8: Networking Fundamentals (Questions 61-70)**

61. What is the difference between `ping` and `traceroute`?
62. How do you find the IP address associated with a domain name (e.g., `google.com`)?
63. What command would you use to see all active network connections and the processes that own them?
64. Explain the difference between TCP and UDP.
65. How would you check which ports are listening on your local machine?
66. What is the purpose of the `/etc/hosts` file?
67. How can you see the routing table on a Linux system?
68. What is the `ss` command, and why is it often preferred over the older `netstat`?
69. How would you securely transfer a file `local_file.txt` to a remote server at `192.168.1.10` using the `scp` command?
70. Explain the basic concept of a firewall. Name a common Linux firewall tool.

---

### **Category 9: System Information & Performance (Questions 71-80)**

71. What command would you use to get detailed information about the system's hardware (CPU, memory, etc.)?
72. How do you check the system's uptime and load average?
73. Explain what `vmstat` reports.
74. How can you monitor real-time I/O statistics for your disks?
75. What command would you use to see all available kernel modules?
76. How do you check the amount of free and used memory on the system? Why might the "free" memory seem low?
77. What is `journalctl` and how is it different from reading `/var/log/messages`?
78. How can you filter `journalctl` logs for a specific service, like `nginx.service`?
79. What is the purpose of the `dmesg` command?
80. How would you find out the version of the Linux kernel you are running?

---

### **Category 10: Package Management & System Services (Questions 81-90)**

81. On a Debian/Ubuntu system, how do you search for a package related to "web server"?
82. How would you install a `.deb` package file manually on a Debian-based system?
83. On a RHEL/CentOS/Fedora system, what is the difference between `yum` and `dnf`?
84. How do you enable a service (like `sshd`) to start automatically on boot?
85. What is the difference between `systemctl start` and `systemctl restart`?
86. How can you see the status and recent logs of a specific service in one command?
87. How would you prevent a package from being updated during a system-wide upgrade on a Debian-based system?
88. What command lists all installed packages on a RHEL/Fedora system?
89. How do you add a new software repository (PPA) on Ubuntu?
90. Explain the role of `systemd` as the init system.

---

### **Category 11: Advanced & Miscellaneous (Questions 91-100)**

91. What is an LVM (Logical Volume Manager) and what are its main advantages over traditional partitioning?
92. Explain the difference between a container (like Docker) and a virtual machine.
93. What is `cron`? Write a cron job expression to run a script at 2:30 AM every Sunday.
94. How can you limit the CPU usage of a process?
95. What is the purpose of the `chroot` command?
96. Explain the difference between `PATH` and `LD_LIBRARY_PATH`.
97. How would you securely generate a random password of 16 characters in the command line?
98. What is the `fstab` file and what is its purpose?
99. How do you check the integrity of a downloaded file using a checksum (e.g., SHA256)?
100. What is SELinux? What are its two main modes?

---

### **Answers**

1.  `find . -type f -size +100M`
2.  A hard link is a direct pointer to the same inode (data on disk). A symbolic link is a separate file that points to the original file's path. If you delete the original file, the hard link remains valid, but the symbolic link becomes "broken".
3.  `find . -name "*.tmp" -exec rm {} \;` and `find . -name "*.tmp" | xargs rm`
4.  `ls -lt /var/log | head -n 5`
5.  `xargs` builds and executes command lines from standard input. It's often more efficient as it can pass multiple file names as arguments to a single command, reducing the number of process creations compared to `-exec`, which runs the command once per file (unless you use `+`).
6.  `touch filename`
7.  `du -sh /path/to/dir/* | sort -hr`
8.  `find / -user www-data`
9.  The sticky bit is a permission bit (`t`) set on a directory. It ensures that only the owner of a file (or the owner of the directory) can delete or rename the files within it, even if other users have write permissions. Common use case: `/tmp`.
10. `find /path/to/dir -type d -exec chmod 755 {} \;` and `find /path/to/dir -type f -exec chmod 644 {} \;`
11. `grep -w "error" logfile.log` (The `-w` flag matches whole words).
12. `grep` uses basic regular expressions (BRE). `egrep` (or `grep -E`) uses extended regular expressions (ERE), allowing for more complex patterns without escaping characters like `(`, `)`, `|`. `fgrep` (or `grep -F`) interprets the pattern as a fixed string, not a regex, which is faster.
13. `sed -i 's/192.168.1.100/10.0.0.5/g' config.conf` (`-i` for in-place edit, `g` for global replacement).
14. `sed -n '15,30p' large_file.txt` (`-n` suppresses default output, `p` prints the specified line range).
15. `awk -F, '{print $3, $5}' data.csv` (`-F,` sets the field separator to a comma).
16. `awk '{sum += $2} END {print sum}' numbers.txt`
17. `sort -nr file.txt` (`-n` for numeric, `-r` for reverse).
18. `cat file.txt | tr -s '[:space:]' '\n' | sort | uniq -c | sort -nr | head -n 10`
19. A common, but not perfect, regex: `^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$`
20. `tr '[:upper:]' '[:lower:]' < input.txt > output.txt`
21. `kill` sends a signal to a specific PID. `pkill` finds processes based on their name and other attributes and sends a signal to them. `killall` sends a signal to all processes with an exact name match.
22. `SIGTERM` is a termination request that can be caught and ignored by the process, allowing it to shut down gracefully. `SIGKILL` is a "kill" signal that cannot be caught or ignored; it forces the kernel to terminate the process immediately. Use `SIGTERM` first, and only use `SIGKILL` if the process is unresponsive.
23. `pgrep nginx` or `ps aux | grep nginx | grep -v grep`
24. `ps -u postgres` or `ps -U postgres -u postgres`
25. `nohup` (no hangup) allows a command to continue running after you log out, by ignoring the SIGHUP signal. `disown` removes a job from the shell's job table, making it immune to SIGHUP when the shell exits. Use them to run long-running background tasks persistently.
26. `S` (Sleeping): The process is waiting for an event (e.g., I/O). `R` (Running): The process is currently running or on the run queue. `D` (Uninterruptible Sleep): The process is waiting for I/O (usually disk) and cannot be interrupted by signals.
27. Use the `renice` command: `sudo renice -n 10 -p <PID>` (higher niceness = lower priority). To start a process with a specific niceness, use `nice -n 10 command`.
28. `/proc` is a virtual filesystem that provides a mechanism for the kernel to send information to processes. It doesn't exist on disk. Example: `/proc/meminfo` shows detailed memory statistics.
29. `ps -f -C java` or `ps aux | grep '[j]ava'`
30. A zombie process is a process that has completed execution but still has an entry in the process table. This happens because the parent process has not yet read its child's exit status. They consume very little resources and cannot be killed. They are removed when the parent process reaps them (or when the parent itself dies).
31. The `${}` syntax allows for more complex operations, like parameter expansion (`${VAR}_suffix`) and handling of unset variables (`${VAR:-default}`). It's necessary when the variable name is ambiguous.
32. `if [ -f "$filename" ]; then ... fi`
33. `[[ ]]` is a Bash keyword that provides more features than `[ ]`. It handles word splitting and filename expansion differently (more safely), supports pattern matching (`==` with glob patterns) and logical operators (`&&`, `||`) without escaping.
34. `for file in *.jpeg; do mv "$file" "${file%.jpeg}.jpg"; done`
35. `while IFS= read -r line; do echo "$line"; done < file.txt`
36. `set -e` causes the script to exit immediately if a command exits with a non-zero status. `set -u` treats unset variables as an error.
37. `sum() { echo $(($1 + $2)); }` and then call it with `sum 5 10`.
38. `$(command)` is the modern, preferred syntax. It nests cleanly and is more readable. Backticks are the older, legacy syntax and can be harder to read and use in complex cases.
39. `date +%s`
40. It redirects all standard output (`stdout`) and standard error (`stderr`) from the script and all commands run within it to `file.txt`.
41. `my_array=("one" "two" "three")` and `for item in "${my_array[@]}"; do echo "$item"; done`
42. A here document is a way to feed a multi-line string into a command. Example: `cat <<EOF > file.txt\nLine 1\nLine 2\nEOF`
43. Use the `getopts` built-in command or a `while` loop with a `case` statement to parse `$1`, `$2`, etc.
44. Sourcing (`source` or `.`) executes the script in the current shell, so any variables, functions, or aliases it sets affect the current shell. Executing it (`./script.sh`) runs it in a new subshell, and changes are lost when it finishes.
45. Use the `trap` command: `trap 'echo "Cleaning up..."; rm -f /tmp/tempfile; exit' SIGINT SIGTERM`
46. `sudo useradd -m -s /bin/bash johndoe`
47. `sudo usermod -L johndoe` (To unlock: `sudo usermod -U johndoe`)
48. `sudo usermod -aG developers jane` (`-a` is crucial to append, not replace the groups).
49. It defines which users can run which commands with `sudo`. You should always use `sudo visudo` to edit it, as this command checks the file for syntax errors before saving, preventing you from locking yourself out.
50. In `/etc/shadow`. They are stored as a salted hash (e.g., using SHA-512, `$6$`).
51. `2755` means `rwxr-sr-x`. The `2` sets the `setgid` bit. When set on a directory, any new file or subdirectory created within it will inherit the group ownership of the parent directory, not the primary group of the user who created it.
52. `sudo chown -R root:wheel /path/to/dir`
53. The `umask` is a system setting that determines the default permissions for new files and directories. It "subtracts" permissions from the base `666` for files and `777` for directories. To set it for all users, you can add `umask 022` to `/etc/profile` or a related global profile script.
54. `find / -type f -perm /o+w` (or `find / -type f -perm -0002` on older systems).
55. Standard Unix permissions have one owner, one group, and a set of permissions for "other". ACLs allow you to define permissions for specific, additional users and groups beyond these three, providing much finer-grained control.
56. `tar -czvf backup.tar.gz /home/user/documents`
57. `tar -xzvf backup.tar.gz -C /tmp/restore`
58. `.tar.gz` uses gzip compression. `.tar.bz2` uses bzip2 compression. Bzip2 generally provides better compression but is slower than gzip.
59. `tar -tzvf backup.tar.gz`
60. `xz database.sql` (This creates `database.sql.xz`).
61. `ping` sends ICMP echo requests to a host to check basic connectivity and latency. `traceroute` shows the path (the "hops" or routers) that packets take to get to the destination, and the latency at each hop.
62. `host google.com` or `dig google.com` or `nslookup google.com`
63. `sudo netstat -tulnp` or `sudo ss -tulnp` (`-t`=TCP, `-u`=UDP, `-l`=listening, `-n`=numeric, `-p`=process).
64. TCP is connection-oriented, reliable, and ordered. It establishes a connection via a three-way handshake and ensures data arrives intact and in order. UDP is connectionless, faster, but unreliable. It sends datagrams without establishing a connection, and there's no guarantee of delivery or order.
65. `sudo netstat -tuln` or `sudo ss -tuln`
66. It's a simple text file used for mapping hostnames to IP addresses before DNS. It's checked before a DNS query is made.
67. `ip route show` or `route -n`
68. `ss` (socket statistics) is a modern utility to investigate sockets. It's faster and provides more information than the older `netstat`, which is considered deprecated on many systems.
69. `scp local_file.txt user@192.168.1.10:/remote/path/`
70. A firewall is a network security system that monitors and controls incoming and outgoing network traffic based on predetermined security rules. Common tools: `iptables`, `firewalld`, `ufw`.
71. `lscpu` for CPU, `free -h` for memory, `lsblk` for block devices, or `dmidecode` for a comprehensive hardware report.
72. `uptime`
73. `vmstat` (virtual memory statistics) reports information about processes, memory, paging, block I/O, traps, and CPU activity. It's useful for identifying system bottlenecks.
74. `iostat -x 1` (The `-x` gives extended stats, `1` makes it update every second).
75. `lsmod`
76. `free -h`. The "free" memory might seem low because Linux uses free memory for disk caching (`buff/cache`). This cache is "freeable" and will be released by the kernel if an application needs it.
77. `journalctl` is a utility for querying the `systemd` journal, which is a centralized logging system. It's different because it collects logs from kernel, `systemd` services, and other sources in a binary format, offering advanced filtering and querying capabilities that plain text files lack.
78. `journalctl -u nginx.service`
79. `dmesg` prints the kernel ring buffer messages. It's used to see boot-time messages and hardware/driver-related events.
80. `uname -r`
81. `apt-cache search "web server"` or `apt search "web server"`
82. `sudo dpkg -i package.deb`
83. `dnf` (Dandified YUM) is the next-generation version of `yum`. It is faster, has better dependency resolution, and is the default on modern Fedora and RHEL/CentOS versions. For most common tasks, the commands are the same.
84. `sudo systemctl enable sshd`
85. `start` starts a service that is currently stopped. `restart` stops a running service and then starts it again. If the service is already stopped, `restart` will just start it.
86. `systemctl status nginx.service`
87. `sudo apt-mark hold package_name` (To unhold: `sudo apt-mark unhold package_name`)
88. `dnf list installed` or `rpm -qa`
89. `sudo add-apt-repository ppa:user/ppa-name` followed by `sudo apt update`.
90. `systemd` is the init system and service manager for Linux. It is the first process to run (PID 1) and is responsible for bringing the system up, managing services, mounting filesystems, and handling system events.
91. LVM is a storage management system that provides a layer of abstraction over physical disks. Advantages include: easy resizing of logical volumes (partitions), creating snapshots, and spanning multiple physical disks into a single volume group.
92. A VM is a full emulation of a computer system, including its own kernel, running on a hypervisor. A container is an isolated set of processes running on a shared host kernel. VMs are heavier and use more resources but provide stronger isolation. Containers are lightweight and faster to start.
93. `cron` is a time-based job scheduler. The expression is: `30 2 * * 0 /path/to/script.sh` (minute, hour, day-of-month, month, day-of-week).
94. Using the `cpulimit` command: `cpulimit -l 50 -p <PID>` (limits to 50% CPU). Or using `nice` and `ionice` to adjust scheduling priority.
95. `chroot` (change root) changes the apparent root directory for the current running process and its children. It's often used for recovery, testing, or creating a sandboxed environment.
96. `PATH` is an environment variable that tells the shell which directories to search for executable programs. `LD_LIBRARY_PATH` tells the dynamic linker which directories to search for shared libraries (`.so` files) needed by an executable.
97. `openssl rand -base64 16` or `tr -dc 'A-Za-z0-9!@#$%^&*' < /dev/urandom | head -c 16`
98. `/etc/fstab` (File System Table) contains information about disk partitions and other storage devices. It's used by the system to automatically mount these devices at boot time.
99. `sha256sum downloaded_file.iso` and then compare the output hash with the one provided on the download page.
100. SELinux (Security-Enhanced Linux) is a security architecture that integrates into the Linux kernel to provide a Mandatory Access Control (MAC) system. Its two main modes are **Enforcing** (denies actions based on policy and logs them) and **Permissive** (does not deny actions but logs what *would* have been denied). The third mode is **Disabled**.
