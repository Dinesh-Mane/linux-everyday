# Most useful and commonly used Linux commands

## 1. File & Directory Management
| Command | Description                                 | Example                                     |
| ------- | ------------------------------------------- | ------------------------------------------- |
| `ls`    | List directory contents                     | `ls -la`                                    |
| `cd`    | Change directory                            | `cd /etc`                                   |
| `pwd`   | Show current directory                      | `pwd`                                       |
| `mkdir` | Create a directory                          | `mkdir test_dir`                            |
| `rmdir` | Remove an empty directory                   | `rmdir test_dir`                            |
| `rm`    | Remove files/directories                    | `rm file.txt`, `rm -rf dir/`                |
| `cp`    | Copy files or directories                   | `cp file1.txt file2.txt`, `cp -r dir1 dir2` |
| `mv`    | Move or rename files                        | `mv old.txt new.txt`                        |
| `touch` | Create empty file                           | `touch file.txt`                            |
| `find`  | Search files/directories                    | `find / -name "file.txt"`                   |
| `tree`  | Directory structure as tree (install first) | `tree /home/user`                           |

## 2. File Viewing & Editing
| Command         | Description          | Example                            |
| --------------- | -------------------- | ---------------------------------- |
| `cat`           | View file content    | `cat file.txt`                     |
| `less` / `more` | Paginated viewing    | `less file.txt`                    |
| `head`          | Show first N lines   | `head -n 10 file.txt`              |
| `tail`          | Show last N lines    | `tail -f log.txt` (real-time logs) |
| `nano`          | Terminal text editor | `nano file.txt`                    |
| `vi` / `vim`    | Advanced text editor | `vi file.txt`                      |


## 3. File Permissions & Ownership
| Command | Description             | Example                                |
| ------- | ----------------------- | -------------------------------------- |
| `chmod` | Change file permissions | `chmod +x script.sh`, `chmod 755 file` |
| `chown` | Change file owner       | `chown user:group file.txt`            |
| `umask` | Default permission mask | `umask 022`                            |


## 4. File Compression & Archiving
| Command           | Description         | Example                               |
| ----------------- | ------------------- | ------------------------------------- |
| `tar`             | Archive files       | `tar -czvf archive.tar.gz dir/`       |
| `unzip`           | Extract zip files   | `unzip file.zip`                      |
| `gzip` / `gunzip` | Compress/decompress | `gzip file.txt`, `gunzip file.txt.gz` |


## 5. Process Management
| Command           | Description                           | Example                |
| ----------------- | ------------------------------------- | ---------------------- |
| `ps`              | Show running processes                | `ps aux`               |
| `top`             | Real-time process monitoring          | `top`                  |
| `htop`            | Better version of top (install first) | `htop`                 |
| `kill`            | Terminate process by PID              | `kill 1234`            |
| `killall`         | Kill process by name                  | `killall firefox`      |
| `nice` / `renice` | Set priority                          | `nice -n 10 script.sh` |


## 6. Disk & File System
| Command            | Description             | Example                |
| ------------------ | ----------------------- | ---------------------- |
| `df`               | Disk usage (filesystem) | `df -h`                |
| `du`               | File/folder size        | `du -sh *`             |
| `mount` / `umount` | Mount/Unmount drives    | `mount /dev/sdb1 /mnt` |
| `lsblk`            | List block devices      | `lsblk`                |
| `blkid`            | Show block device UUIDs | `blkid`                |
| `fsck`             | File system check       | `fsck /dev/sda1`       |


## 7. Networking
| Command              | Description                | Example                             |
| -------------------- | -------------------------- | ----------------------------------- |
| `ip a` or `ifconfig` | Show IP address            | `ip a`                              |
| `ping`               | Check connectivity         | `ping google.com`                   |
| `netstat`            | Network status             | `netstat -tuln`                     |
| `ss`                 | Faster netstat alternative | `ss -tuln`                          |
| `curl`               | Fetch URL content          | `curl https://example.com`          |
| `wget`               | Download from web          | `wget https://example.com/file.zip` |
| `scp`                | Secure file copy           | `scp file.txt user@remote:/path`    |
| `rsync`              | Efficient file sync        | `rsync -av dir/ user@remote:/path`  |
| `traceroute`         | Trace route to host        | `traceroute google.com`             |
| `dig`                | DNS lookup                 | `dig openai.com`                    |
| `nmap`               | Network scanning           | `nmap -sV 192.168.1.1`              |


## 8. User & Group Management
| Command               | Description         | Example                 |
| --------------------- | ------------------- | ----------------------- |
| `whoami`              | Show current user   | `whoami`                |
| `id`                  | Show UID, GID       | `id`                    |
| `adduser` / `useradd` | Add new user        | `adduser john`          |
| `passwd`              | Set/change password | `passwd john`           |
| `deluser` / `userdel` | Delete user         | `deluser john`          |
| `groupadd`            | Create group        | `groupadd devs`         |
| `usermod`             | Modify user         | `usermod -aG devs john` |


## 9. Package Management
### 1. Debian/Ubuntu:
| Command       | Description         | Example                  |
| ------------- | ------------------- | ------------------------ |
| `apt update`  | Update package list | `sudo apt update`        |
| `apt upgrade` | Upgrade packages    | `sudo apt upgrade`       |
| `apt install` | Install package     | `sudo apt install nginx` |
| `apt remove`  | Uninstall package   | `sudo apt remove nginx`  |

### 2. RedHat/CentOS:
| Command       | Description                | Example                  |
| ------------- | -------------------------- | ------------------------ |
| `yum install` | Install                    | `sudo yum install httpd` |
| `dnf`         | Modern replacement for yum | `sudo dnf update`        |


## 10. System Monitoring & Info
| **Command** | **Description**                                | **Example** |  
| ----------- | ---------------------------------------------- | ----------- | 
| `uptime`    | Show system uptime                             | `uptime`    |  
| `free -h`   | RAM usage (human-readable)                     | `free -h`   | 
| `vmstat`    | Virtual memory stats                           | `vmstat`    |
| `iostat`    | CPU & I/O stats (from `sysstat`)               | `iostat`    | 
| `uname -a`  | Kernel and system info                         | `uname -a`  | 
| `hostname`  | Show current hostname                          | `hostname`  | 
| `dmesg`     | View kernel ring buffer (boot and system logs) | `dmesg \| tail` |



## 11. System Shutdown & Reboot
| Command              | Description              | Example                   |
| -------------------- | ------------------------ | ------------------------- |
| `shutdown`           | Power off                | `sudo shutdown now`       |
| `reboot`             | Reboot system            | `sudo reboot`             |
| `halt`               | Halt system              | `sudo halt`               |
| `systemctl poweroff` | Another way to power off | `sudo systemctl poweroff` |


## 12. Services & Daemons
| Command             | Description        | Example                        |
| ------------------- | ------------------ | ------------------------------ |
| `systemctl start`   | Start a service    | `sudo systemctl start nginx`   |
| `systemctl stop`    | Stop service       | `sudo systemctl stop nginx`    |
| `systemctl status`  | Service status     | `sudo systemctl status nginx`  |
| `systemctl enable`  | Auto-start service | `sudo systemctl enable nginx`  |
| `systemctl disable` | Disable auto-start | `sudo systemctl disable nginx` |


## 13. Logs
| Command                   | Description           | Example                   |
| ------------------------- | --------------------- | ------------------------- |
| `journalctl`              | System logs (systemd) | `journalctl -xe`          |
| `tail -f /var/log/syslog` | Live system logs      | `tail -f /var/log/syslog` |
| `cat /var/log/auth.log`   | Auth logs             | `cat /var/log/auth.log`   |


