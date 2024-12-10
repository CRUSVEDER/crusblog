---
title: 7. Kali, linux Commands
date: 2024-12-05
draft: 
tags:
  - basic
  - tips_tricks
---

---

# Linux Commands Cheat Sheet

## 1. **File and Directory Management**

- **`ls`**  
    List files and directories.  
    _Example:_
    
    ```bash
    ls
    ```
    
- **`ls -l`**  
    List files with detailed information.  
    _Example:_
    
    ```bash
    ls -l
    ```
    
- **`mkdir`**  
    Create a new directory.  
    _Example:_
    
    ```bash
    mkdir new_folder
    ```
    
- **`rmdir`**  
    Remove an empty directory.  
    _Example:_
    
    ```bash
    rmdir empty_folder
    ```
    
- **`rm`**  
    Delete files or directories.  
    _Example:_
    
    ```bash
    rm file.txt
    ```
    
- **`cp`**  
    Copy files or directories.  
    _Example:_
    
    ```bash
    cp source.txt destination.txt
    ```
    
- **`mv`**  
    Move or rename files.  
    _Example:_
    
    ```bash
    mv old_name.txt new_name.txt
    ```
    
- **`pwd`**  
    Show the current directory.  
    _Example:_
    
    ```bash
    pwd
    ```
    

## 2. **File Viewing**

- **`cat`**  
    Display file contents.  
    _Example:_
    
    ```bash
    cat file.txt
    ```
    
- **`less`**  
    View file with pagination.  
    _Example:_
    
    ```bash
    less file.txt
    ```
    
- **`head`**  
    Display the first 10 lines of a file.  
    _Example:_
    
    ```bash
    head file.txt
    ```
    
- **`tail`**  
    Display the last 10 lines of a file.  
    _Example:_
    
    ```bash
    tail file.txt
    ```
    
- **`tail -f`**  
    Follow updates to a file (e.g., log file).  
    _Example:_
    
    ```bash
    tail -f log.txt
    ```
    

## 3. **File Permissions and Ownership**

- **`chmod`**  
    Change file permissions.  
    _Example:_
    
    ```bash
    chmod 755 script.sh
    ```
    
- **`chown`**  
    Change file ownership.  
    _Example:_
    
    ```bash
    chown user:group file.txt
    ```
    
- **`ls -l`**  
    View file permissions and ownership.  
    _Example:_
    
    ```bash
    ls -l
    ```
    

## 4. **Searching**

- **`grep`**  
    Search for a pattern in a file.  
    _Example:_
    
    ```bash
    grep "search_term" file.txt
    ```
    
- **`grep -r`**  
    Search recursively in directories.  
    _Example:_
    
    ```bash
    grep -r "search_term" directory/
    ```
    
- **`find`**  
    Locate files by name or criteria.  
    _Example:_
    
    ```bash
    find /path -name "file.txt"
    ```
    
- **`locate`**  
    Search files quickly using a pre-built database.  
    _Example:_
    
    ```bash
    locate file.txt
    ```
    
- **`updatedb`**  
    Update the database for `locate`.  
    _Example:_
    
    ```bash
    sudo updatedb
    ```
    

## 5. **Disk Usage**

- **`df -h`**  
    Show free disk space in human-readable format.  
    _Example:_
    
    ```bash
    df -h
    ```
    
- **`du -h`**  
    Show disk usage of files/directories.  
    _Example:_
    
    ```bash
    du -h directory/
    ```
    

## 6. **Networking**

- **`ip addr`**  
    Display network interfaces and IP addresses.  
    _Example:_
    
    ```bash
    ip addr
    ```
    
- **`ping`**  
    Test connectivity to a host.  
    _Example:_
    
    ```bash
    ping google.com
    ```
    
- **`netstat`**  
    View network connections.  
    _Example:_
    
    ```bash
    netstat -tuln
    ```
    
- **`nslookup`**  
    Query DNS records for a domain.  
    _Example:_
    
    ```bash
    nslookup example.com
    ```
    
- **`traceroute`**  
    Trace the route to a host.  
    _Example:_
    
    ```bash
    traceroute google.com
    ```
    

## 7. **User Management**

- **`adduser`**  
    Add a new user.  
    _Example:_
    
    ```bash
    sudo adduser username
    ```
    
- **`deluser`**  
    Remove a user.  
    _Example:_
    
    ```bash
    sudo deluser username
    ```
    
- **`whoami`**  
    Show the current logged-in user.  
    _Example:_
    
    ```bash
    whoami
    ```
    
- **`who`**  
    Show logged-in users.  
    _Example:_
    
    ```bash
    who
    ```
    

## 8. **Process Management**

- **`ps aux`**  
    List all running processes.  
    _Example:_
    
    ```bash
    ps aux
    ```
    
- **`top`**  
    Display real-time process usage.  
    _Example:_
    
    ```bash
    top
    ```
    
- **`kill`**  
    Terminate a process by PID.  
    _Example:_
    
    ```bash
    kill 1234
    ```
    
- **`killall`**  
    Terminate processes by name.  
    _Example:_
    
    ```bash
    killall firefox
    ```
    

## 9. **Package Management (Debian-based Systems)**

- **`apt update`**  
    Update package lists.  
    _Example:_
    
    ```bash
    sudo apt update
    ```
    
- **`apt upgrade`**  
    Upgrade installed packages.  
    _Example:_
    
    ```bash
    sudo apt upgrade
    ```
    
- **`apt install`**  
    Install a package.  
    _Example:_
    
    ```bash
    sudo apt install curl
    ```
    
- **`apt remove`**  
    Remove a package.  
    _Example:_
    
    ```bash
    sudo apt remove package_name
    ```
    
- **`apt search`**  
    Search for a package.  
    _Example:_
    
    ```bash
    apt search package_name
    ```
    

## 10. **System Monitoring**

- **`uname -a`**  
    Display system information.  
    _Example:_
    
    ```bash
    uname -a
    ```
    
- **`free -h`**  
    Show memory usage in human-readable format.  
    _Example:_
    
    ```bash
    free -h
    ```
    
- **`uptime`**  
    Show system uptime.  
    _Example:_
    
    ```bash
    uptime
    ```
    


---
[Crusveder]