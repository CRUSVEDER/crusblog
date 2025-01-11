---
title: 14. windows command
date: 2024-12-14
Toc: true
draft: 
tags:
  - basic
---
---

## Directory Navigation

- `c:` - Switch to the C:\ drive.
- `d:` - Switch to the D:\ drive.
- `CD c:\path\to\my_folder` - Change directory to `c:\path\to\my_folder`.
- `CD ..` - Move to the parent directory.
- `CD .\new_folder` - Move to the folder `new_folder` in the current directory.
- `CD /D d:\videos\` - Switch to D:\ drive and go to `videos` folder.
- `DIR` - List files and folders in the current directory.
- `DIR /A c:\apps\` - Show files and folders in `c:\apps`.
- `DIR /A:D` - Show only folders.
- `DIR /A:-D` - Show only files.
- `DIR /A:H` - Show hidden files and folders.
- `DIR /O` - List files and folders alphabetically.
- `DIR /O:S` - Sort by file size (smallest to largest).
- `DIR /O:-S` - Sort by file size (largest to smallest).
- `DIR /B` - Show only file and folder names.
- `SORT` - Sort input alphabetically.
- `MOVE c:\f1\text.txt c:\f2` - Move `text.txt` from `f1` to `f2`.
- `MD new_folder` - Create a folder named `new_folder`.
- `RD new_folder` - Remove a folder named `new_folder`.
- `TREE` - Show directory structure.
- `ATTRIB +H +S +R myItem` - Hide `myItem`.
- `ATTRIB -H -S -R myItem` - Unhide `myItem`.

---

## File Management

- `COPY text.txt C:\schoolwork` - Copy `text.txt` to `C:\schoolwork`.
- `DEL text.txt` - Delete `text.txt`.
- `REN text.txt script.bat` - Rename `text.txt` to `script.bat`.
- `REPLACE .\src\hey.txt .\dest` - Replace `hey.txt` in `dest` with the one in `src`.
- `XCOPY /S folder1 folder2` - Copy `folder1` and subfolders to `folder2`.
- `ROBOCOPY` - Copy files/directories with advanced options.
- `EXPAND gameData.cab` - Decompress `gameData.cab`.
- `FC file1.ext file2.ext` - Compare contents of two files.
- `FIND "python" run.bat` - Find lines containing `python` in `run.bat`.
- `PRINT resume.txt` - Print `resume.txt`.
- `TYPE test.txt` - Display `test.txt` contents.
- `MORE` - Display file contents one screen at a time.
- `NOTEPAD filename.ext` - Open `filename.ext` in Notepad.

---

## Disk Management

- `CHKDSK` - Check and repair disk issues.
- `CIPHER /E folder` - Encrypt `folder`.
- `CIPHER /D file` - Decrypt `file`.
- `DEFRAG` - Defragment a disk.
- `CHKNTFS` - Modify disk-checking on startup.
- `FORMAT` - Format a disk.
- `DISKPART` - Manage disk partitions.
- `LABEL d:x` - Rename D:\ drive to X:.
- `RECOVER d:\data.dat` - Recover `data.dat` from D:.
- `VOL` - Show disk volume label and serial number.
- `SFC /SCANNOW` - Scan and update protected system files.

---

## System Info & Networking

- `VER` - Show OS version.
- `SYSTEMINFO` - Show system configuration.
- `HOSTNAME` - Show computer's hostname.
- `DATE` - Display/set system date.
- `IPCONFIG` - Show IP configuration.
- `PING google.com` - Check connectivity to `google.com`.
- `PATHPING` - Trace route with latency and packet loss.
- `TRACERT` - Trace route to a host.
- `NET` - Access network services.
- `NETSTAT` - Show network connections and stats.
- `NSLOOKUP` - Look up IP addresses.
- `ROUTE` - Manage routing tables.
- `GETMAC` - Show MAC addresses.

---

## Process Management

- `SCHTASKS` - Create/edit scheduled tasks.
- `SET` - List environment variables.
- `PATH` - Display or modify the `PATH` environment variable.
- `SHUTDOWN /R` - Restart the computer.
- `SHUTDOWN /S /T 60` - Shut down in 60 seconds.
- `TASKLIST` - List running tasks.
- `TASKKILL /IM "process_name"` - Terminate tasks by name.
- `TASKKILL /PID process_id` - Terminate tasks by process ID.
- `REGEDIT` - Open Registry Editor.
- `RUNAS /USER:username program` - Run a program as another user.
- `POWERSHELL` - Open a PowerShell instance.

---

## Batch Scripting

- `REM` - Add a single-line comment.
- `GOTO` - Jump to a labeled section.
- `SET /A var=expression` - Perform arithmetic operations.
- `TIMEOUT seconds` - Pause for a specified time.
- `PAUSE` - Wait for user input.
- `CHOICE` - Prompt for user selection.
- `CLS` - Clear the screen.
- `COLOR` - Set console colors.
- `ECHO` - Display text.
- `HELP` - Get help for a command.
- `PROMPT` - Change the command prompt appearance.
- `START` - Open a file or program in a new window.
- `TITLE` - Set the console window title.
- `EXIT` - Close the command prompt.

---

## Flow Control

- `IF condition command` - Execute a command if the condition is true.
- `IF condition (command1) ELSE (command2)` - Execute one of two commands based on a condition.
- `:label` - Define a marker for loops.
- `GOTO label` - Jump to a marker.

---

## Shortcut Keys

- **Tab** - Autocomplete commands and paths.
- **Ctrl+F** - Search within the console.
- **F1, F3, F5, F8** - Recall previous commands.
- **F7** - Display command history.
- **F9** - Execute a specific command from history.

---

## 1 Line Common Commands
### Files and Folders Management

- **COPY** - Copies files to another location
- **DIR** – Displays files and folders in current directory
- **DEL or ERASE** - Deletes files
- **EDIT** - Starts file editor
- **CD** - Changes directory
- **EXPAND** - Decompresses compressed files
- **FC** - Compares files and shows the differences between them
- **FIND** - Finds a text string in the file
- **MD or MAKEDIR** - Creates a folder
- **MOVE** - Moves files from one folder to another
- **PRINT** - Prints out the text file contents
- **RD or RMDIR** - Deletes a folder
- **REN or RENAME** - Renames a file or folder
- **REPLACE** - Replaces files in one directory with files of the same name in another directory (overwrite)
- **ROBOCOPY** - Uses an advanced tool to copy files and directories
- **TREE** - Shows directory structure of a disk or folder
- **TYPE** - Displays the contents of text files
- **OPENFILES** – Manages opened local or network files
- **XCOPY** - Copies files and directory trees

### Applications and Processes

- **SCHTASKS** - Executes a command or start a scheduled application (Task Scheduler)
- **SHUTDOWN** - Shutdowns or reboots your computer
- **TASKLIST** - Lists the tasks being performed
- **TASKKILL** - Stops or halts a task (to stop a task you use a PID which you can find out from TASKLIST)
- **REG** – Starts registry editor
- **RUNAS** - Launches the task as another user

### Disks Management

- **CHKDISK** - Checks disk and shows statistics
- **DEFRAG** – Starts disk defragmentation
- **CHKNTFS** - Displays or changes execution of disk check at boot
- **COMPACT** - Displays and change the compression of files in NTFS partitions
- **CONVERT** - Converts FAT disk volume to NTFS
- **DISKPART** - Displays and adjusts disk partition properties
- **FORMAT** - Formats the disk
- **FSUTIL** - Displays and configures file system properties
- **LABEL** - Creates, changes, or deletes a disk volume label
- **RECOVER** - Recovers data from a bad or damaged disk
- **VOL** - Displays volume label and serial number for the disk

### System Information

- **DATE** - Outputs or sets the current date
- **TIME** - Displays or sets the system time
- **DRIVERQUERY** - Displays the current state and properties of the device driver
- **HOSTNAME** - Displays name of the computer
- **SYSTEMINFO** - Shows configuration information about your computer
- **VER** - Allows you to view the Windows version
- **GPRESULT** – Displays current applied group policies (RSoP)
- **GPUPDATE** – Updates group policies

### Network

- **IPCONFIG** - Shows information about network interfaces
- **PING** – Sends ICMP requests to the target host, checks host availability
- **TRACERT** - Finds the path for packets traveling over the network
- **NSLOOKUP** - Finds IP address by resource name
- **ROUTE** - Displays network route tables
- **ARP**- Shows a table with IP addresses converted into physical addresses
- **NETSH** – Starts is a network settings control program
- **GETMAC** - Shows the MAC address of the network adapter
- **TFTP** – Starts TFTP client in console

### Command Line Setup

- **CLS** - Clears screen
- **CMD** - Displays another command prompt
- **COLOR** - Sets the text and background color
- **PROMPT** - Changes the command line prompt
- **TITLE** - Assigns a title for the current session
- **HELP** – Launches CMD help
- **EXIT** - Exits the command line