## Q4

I used the `-p` flag with the mkdir command. This allowed the parent directories to be created automatically and prevented errors if a directory already existed.

I also used Bash brace expansion to create the entire folder structure in a single command. This saved time and made the command much cleaner than creating each directory one by one.

I could have created the directories individually, but it would have taken longer and increased the chance of making mistakes. Using brace expansion was the faster and more efficient approach.# Section 1 – Orient Yourself

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


## Q4

To create the directory structure, I used the -p flag with the mkdir command. The -p flag allows parent directories to be created automatically if they do not already exist. It also prevents errors if a directory already exists.

I also used brace expansion in Bash. Brace expansion allows multiple directory names to be generated from a single command, which makes it possible to create the entire folder structure in one step instead of creating each folder individually.

Without brace expansion, I would have needed several separate mkdir commands to create each directory one at a time. While that would still work, it would be slower and more likely to result in mistakes. Using brace expansion made the command shorter, easier to read, and more efficient, especially when creating a large directory structure.

## Q5

I used the touch command to create the required files. Besides creating empty files, touch can also update the timestamp of an existing file.

If the file already exists, the contents stay the same, but the access and modification times are updated. This is useful in automation because scripts can safely create required files without overwriting existing data.

## Q6

The files currently show a size of 0 bytes because they are empty placeholder files. The permission string shows who can read, write, or execute the file.

For example, -rw-r--r-- means the owner can read and write the file, while the group and other users can only read it.

The -h option makes file sizes easier to read by displaying them in a human-readable format.

## Q7

The tree command displays files and folders in a clear hierarchy, making it easier to understand the structure of a project. On the other hand, ls -R lists files recursively but can be harder to follow when there are many directories.

A DevSecOps engineer might use a tree to quickly verify that a deployment or automation script created the correct folder structure.
