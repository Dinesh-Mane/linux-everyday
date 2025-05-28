# `pwd` Command — "Print Working Directory"
**Basic Purpose** The `pwd` command displays the full, absolute path of the current working directory in the shell.

**Why is pwd Important?**  
When navigating around directories using cd, it’s easy to forget where you are. pwd lets you check your exact location in the filesystem — especially critical in large or nested directory structures.

**Basic Syntax**
```bash
pwd [OPTION]
```

---

## Most Used Variants
| **Command** | **Description**                                       |
| ----------- | ----------------------------------------------------- |
| `pwd`       | Show the current working directory (default behavior) |
| `pwd -L`    | Show the logical path (includes symlinks)             |
| `pwd -P`    | Show the physical path (resolves symlinks)            |


---


# Real-World Scenarios
## 1: 1: Basic Usage
```bash
pwd
```
Output:
```arduino
/home/user/Documents
```
✅ Use case: Quickly verify your current location after multiple cd commands.



## 2: Symbolic Links (Logical vs Physical Path)
Assume:
```bash
/home/user/docs → /mnt/shared/docs
```
is a symbolic link.
```bash
cd ~/docs
pwd -L
```
Output:
```arduino
/home/user/docs
```
```bash
pwd -P
```
Output:
```bash
/mnt/shared/docs
```
✅ Use case: If you're troubleshooting or writing scripts, physical paths (`-P`) can help avoid errors due to symlink confusion.

**Flag Explanation**
| **Flag** | **Full Form** | **Behavior**                                                               |
| -------- | ------------- | -------------------------------------------------------------------------- |
| `-L`     | Logical path  | Shows the path as typed or from symlink traversal (default in many shells) |
| `-P`     | Physical path | Resolves symlinks and shows the actual physical filesystem path            |

> Note: Some shells like bash may default to -L, but pwd -P gives the true disk-level path.

# Practical Scenarios
## 1: Confirming Script Path Location
You are writing a deployment script and want to ensure it’s run from the correct location:
```bash
#!/bin/bash
if [ "$(pwd)" != "/opt/deploy/scripts" ]; then
  echo "Please run this script from /opt/deploy/scripts"
  exit 1
fi
```

## 2: Dealing with Symlinks in Automation
You're debugging a CI/CD pipeline where a path might be symlinked:
```bash
cd /var/www/html
pwd -P  # Ensure you're on the actual deployment volume
```

## 3: Audit File Locations in Scripts
You want to log exact locations where certain jobs are running:
```bash
echo "Backup started from directory: $(pwd -P)" >> backup.log
```


---

## Use in Scripts
Often used in shell scripts to capture the starting directory, so you can return later:
```bash
START_DIR=$(pwd)
cd /tmp/some_task
# do work
cd "$START_DIR"  # go back to where you started
```
> Permissions Note: `pwd` works as long as you have read (execute) permissions to traverse the directory tree. If not, it may give errors or incorrect paths.





