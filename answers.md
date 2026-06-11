# Section 1 – Orient Yourself

## Q1

### What does each command tell you?

#### pwd
The `pwd` command displays the current working directory. It helps determine where files will be created, modified, or accessed.

#### whoami
The `whoami` command displays the username of the currently logged-in user. This is important for understanding permissions and access levels.

#### uname -a
The `uname -a` command displays detailed system information including the kernel version, hostname, architecture, and operating system details.

### Why does a DevSecOps engineer run these commands first?

A DevSecOps engineer runs these commands immediately after connecting to a server to understand their environment. Knowing the current directory prevents mistakes when working with files. Knowing the logged-in user helps determine available permissions. The operating system and kernel version are important for identifying compatibility issues and known vulnerabilities (CVEs) that may affect the system.

---

## Q2

### Five directories and their purpose

#### /etc
Contains system-wide configuration files.

#### /home
Stores personal files and directories for users.

#### /var
Contains variable data such as logs, caches, and application data.

#### /usr
Contains installed applications, libraries, and documentation.

#### /tmp
Stores temporary files used by applications and the operating system.

### What is the Filesystem Hierarchy Standard (FHS)?

The Filesystem Hierarchy Standard (FHS) defines a common directory structure for Linux systems so that files and directories are stored in predictable locations.

### Why does it exist?

FHS provides consistency across Linux distributions, making administration, automation, troubleshooting, and software deployment easier.

### What breaks without it?

Without FHS, administrators and automation tools would not know where to find configuration files, logs, applications, and libraries. This would make system management and collaboration much more difficult.

---

## Q3

### What is different between the two outputs?

The `ls` command displays only visible files and directories. The `ls -la` command displays all files, including hidden files, and provides detailed information such as permissions, ownership, size, and timestamps.

### What makes a file hidden in Linux?

A file is hidden when its name begins with a period (`.`). Linux does not use a special hidden attribute; hidden files are identified by their naming convention.

### Two hidden files found in a home directory

#### .bashrc
Contains shell configuration settings, aliases, environment variables, and startup commands for the Bash shell.

#### .profile
Contains commands and environment settings that are executed when a user logs in.


