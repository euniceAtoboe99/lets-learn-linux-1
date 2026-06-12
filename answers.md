
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

I used the `-p` flag with the mkdir command. This allowed the parent directories to be created automatically and prevented errors if a directory already existed.

I also used Bash brace expansion to create the entire folder structure in a single command. This saved time and made the command much cleaner than creating each directory one by one.

I could have created the directories individually, but it would have taken longer and increased the chance of making mistakes. Using brace expansion was the faster and more efficient approach.# Section 1 – Orient Yourself

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
A DevSecOps engineer might use a tree to quickly verify that a deployment or automation script created the correct folder structure.
Section 3 – Write and Read Files

## Q8

The > operator replaces everything in a file, while >> adds new content to the end of the file without removing what is already there.

When I tested >, the previous log entries were overwritten, and only the new entry remained. Using >> allowed me to keep the existing logs and add new entries below them.

In a production environment, using > by mistake could delete important logs and make troubleshooting much harder.

## Q9

The cat command displays a file from top to bottom, while tac displays it in reverse order.

When investigating a large log file, I would usually check the most recent entries first because they are more likely to explain the current issue.

Another useful command is tail, which can be used to display only the last few lines of a file. For example, tail -10 filename shows the last 10 lines.

## Q10

A heredoc makes it possible to write multiple lines into a file in a single operation. It is cleaner and easier to manage than using several separate echo commands.

The difference between 'EOF' and EOF is that quoted delimiters prevent variable expansion, while unquoted delimiters allow variables to be expanded before being written to the file.

Using a heredoc is often faster and more practical when creating configuration files, scripts, or sample log data.

## Q11

Both less and more are used to read files one page at a time. However, less provides more navigation features and is generally easier to use with large files.

If I were working with a large log file, I would choose less because it allows me to search through the file and move around more efficiently.
If I was working with a large log file, I would choose less because it allows me to search through the file and move around more efficiently.
Q12

I used cp to create a copy of the error log while keeping the original file unchanged. I then used mv to rename the access log with the required date in the filename.

After renaming the file with mv, the old filename no longer existed because it had been replaced by the new one. In contrast, using cp left both the original file and the copied version available.

When copying a large file, the system needs to create another copy of the data on disk, which can take time and use additional storage space.


## Q13

The empty directory was removed successfully using rmdir. However, when I tried to remove the logs directory, the command failed because it was not empty.

The main difference is that rmdir only removes empty directories, while rm -r can remove directories together with everything inside them.

The rm -rf command is powerful but risky because it permanently deletes files and folders without asking for confirmation. Before using it, I would always double-check the path to avoid deleting important data by mistake.


## Q14

The final directory structure still matches the original layout that was created earlier in the lab. The only changes were the renamed and archived log files, which were part of the task requirements.

Having a clean and predictable directory structure makes it easier for automation scripts, monitoring tools, and log collectors to find the files they need. It also helps when troubleshooting because everything is stored in expected locations.

## Q15

After creating the hard link, I noticed that both files had the same inode number. This showed that they were pointing to the same file on disk rather than creating a separate copy.

The link count increased because there were now two filenames referring to the same inode.

In simple terms, an inode is where Linux stores information about a file, such as its location, permissions, ownership, and other metadata.

## Q16

Even after deleting the original db.conf file, I was still able to access the contents through the hard link. This happened because the data remains available as long as at least one link still points to the inode.

When I checked the inode information again, the link count had decreased, but the file itself was still available.

This shows that deleting a filename does not always remove the actual data immediately if another hard link still exists.

## Q17

The l at the beginning of the permissions string identified the file as a symbolic link.

After deleting the original app.conf file, the symbolic link no longer worked because its target file no longer existed. This created what is known as a broken or dangling symlink.

Broken symlinks can cause issues in deployment environments because applications may still expect the original file to be present.

## Q18

## Property                                Hard Link          Soft Link

Shares inode with original?                 Yes               No

Works across different filesystems          No                Yes

Survives deletion of original?              Yes               No

Can link to a directory?                    No                Yes

Shows as l in ls -la?                       No                Yes

Detectable by matching inodes in ls -li?    Yes               No

## Q19

The directory listing for the existing path was written to stdout_output.txt, while the error message for the missing path was written to stderr_output.txt.

Linux uses three standard streams:

* stdin (0) for input
* stdout (1) for normal output
* stderr (2) for error messages

The 2> operator specifically redirects error output to a file.

The command 2>&1 sends error output to the same destination as standard output. This is useful when you want both normal messages and errors recorded in a single log file.

## Q20

I used an unquoted delimiter because I wanted variable expansion to be available if needed.

When the delimiter is quoted, variables are treated as plain text. When it is unquoted, variables are expanded before being written to the file.

A quoted heredoc is useful when you want to preserve text exactly as written. An unquoted heredoc is useful when generating reports or configuration files that include variables.

## Q21

This lab helped me understand how different Linux commands work together to manage files, logs, links, and reports in a structured environment.

One command that changed how I think about Linux is ln, because it showed me the difference between hard links and symbolic links at the filesystem level.

Another command was tree, which made it much easier to visualise and verify directory structures. I can see how it would be useful when reviewing deployments, troubleshooting issues, or checking whether automation scripts created the expected files and folders.
