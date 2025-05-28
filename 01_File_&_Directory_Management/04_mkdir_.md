# `mkdir` Command — "Make Directory"
**Purpose:** The `mkdir` command is used to create new directories in Linux.

**Basic Syntax:**
```bash
mkdir [OPTIONS] directory_name
```
> You can create single or multiple directories and even nested structures.

---

## Common Use Cases
| **Command**       | **Action**                             |
| ----------------- | -------------------------------------- |
| `mkdir test`      | Creates a new directory called `test`  |
| `mkdir dir1 dir2` | Creates multiple directories           |
| `mkdir -p a/b/c`  | Creates nested directories recursively |

**Permission Reminder:** You need write and execute permissions in the parent directory to create new ones. Use `ls -ld` . to check current permissions.

---

## Important Flags & Options
| **Flag** | **Full Form** | **Description**                                                                            | **Example**                      |
| -------- | ------------- | ------------------------------------------------------------------------------------------ | -------------------------------- |
| `-p`     | `--parents`   | Creates **parent directories** as needed; avoids error if intermediate folders don’t exist | `mkdir -p /var/www/html/project` |
| `-v`     | `--verbose`   | Shows a message for each created directory                                                 | `mkdir -v myfolder`              |
| `-m`     | `--mode=MODE` | Set **permissions** (file mode) for new directories (like `chmod`)                         | `mkdir -m 755 logs`              |


---

# Real-World Examples
## 1: Basic Folder Creation
```bash
mkdir reports
```
Creates a directory named `reports` in the current location.

## 2: Creating Multiple Folders
```bash
mkdir jan feb mar
```
Creates three directories in one go — useful for organizing by date/project/module.

## 3: Create Nested Folders Recursively
```bash
mkdir -p project/src/utils
```
Even if `project` or `src` doesn’t exist, it creates the entire structure — saves from doing it step-by-step.

## 4: Verbose Output (Logging)
```bash
mkdir -vp data/{raw,processed,results}
```
Creates three folders inside ``data/` and prints each step. Useful in scripts to log folder creation.

## 5: Create Directory With Custom Permissions
```bash
mkdir -m 700 secure_folder
```
Creates a folder only accessible by the owner (read/write/execute) — helpful for sensitive logs, keys, etc.

## 6: Safe Creation — Prevent “Already Exists” Error
If `reports/2024/jan` doesn't exist, this:
```bash
mkdir -p reports/2024/jan
```
won’t throw an error. Without `-p`, you'd get:
```bash
mkdir: cannot create directory ‘reports/2024/jan’: No such file or directory
```

---

## Error Scenarios & Fixes
| **Issue**                          | **Cause**                 | **Fix**                                |
| ---------------------------------- | ------------------------- | -------------------------------------- |
| `mkdir: Permission denied`         | No write permission       | `sudo mkdir ...` or change permissions |
| `mkdir: File exists`               | Directory already exists  | Use `-p` to suppress error             |
| `mkdir: No such file or directory` | Parent path doesn’t exist | Use `-p` to create recursively         |

---

## Alternative Commands to `mkdir`

### 1. `install -d`
```bash
install -d -m 755 newdir
```
- Creates directory like `mkdir`
- Can set permissions immediately
- Often used in Makefiles and scripts

### 2. `python -m os` (in scripts)
```python
import os
os.makedirs("a/b/c", exist_ok=True)
```
- Used in Python scripts to create directories

### 3. `ansible.builtin.file` (in automation)
```yaml
- name: Ensure directory exists
  file:
    path: /data/mydir
    state: directory
    mode: '0755'
```
- Declarative creation in Ansible

## Summary Table
| **Command**                      | **Purpose**                     |
| -------------------------------- | ------------------------------- |
| `mkdir folder`                   | Create a directory              |
| `mkdir dir1 dir2`                | Create multiple directories     |
| `mkdir -p a/b/c`                 | Create nested directories       |
| `mkdir -v folder`                | Show verbose output             |
| `mkdir -m 755 folder`            | Set permissions during creation |
| `mkdir -p -v -m 700 secure/logs` | All features combined           |

## Tip
Combine `mkdir` with `&&` or `||` in scripts:
```bash
mkdir -p logs || echo "Failed to create logs directory"
```
