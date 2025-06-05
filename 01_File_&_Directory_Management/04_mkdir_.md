# `mkdir` Command — "Make Directories"
**Basic Syntax:**
```bash
mkdir [options] directory_name
```
* `mkdir` is used to **create new directories** (folders) in Linux.
* You can create one or multiple directories.
* Useful options include creating **nested directories**, setting **permissions**, and **printing** creation messages.

---

## Most Common `mkdir` Options:
| **Option**  | **Description**                                                      | **Example**              | **Real-World Use Case**                                 |
| ----------- | -------------------------------------------------------------------- | ------------------------ | ------------------------------------------------------- |
| `-p`        | Create parent directories as needed (no error if they already exist) | `mkdir -p a/b/c`         | Create nested directory structures in a single command  |
| `-v`        | Verbose mode – shows a message for each directory created            | `mkdir -v mydir`         | Useful for debugging and visual confirmation in scripts |
| `-m mode`   | Set permissions (mode) for the directory in octal format             | `mkdir -m 755 publicdir` | Set correct permissions while creating a directory      |
| `--help`    | Display the help manual for `mkdir`                                  | `mkdir --help`           | View all options and usage examples                     |
| `--version` | Show the version of `mkdir` (coreutils version)                      | `mkdir --version`        | Useful to know in debugging or compatibility checks     |

---

## Examples

| **Command**                          | **What It Does**                                                           |
| ------------------------------------ | -------------------------------------------------------------------------- |
| `mkdir test`                         | Creates a single directory named `test`                                    |
| `mkdir dir1 dir2 dir3`               | Creates multiple directories at once                                       |
| `mkdir -p a/b/c`                     | Creates nested directories, even if `a` or `b` don’t exist                 |
| `mkdir -v myfolder`                  | Creates `myfolder` and prints confirmation message                         |
| `mkdir -m 700 secure`                | Creates `secure` directory with only user access permissions (`rwx------`) |
| `mkdir -pvm 755 proj/{src,bin,logs}` | Creates multiple structured directories with set permissions, verbosely    |

---

# Real-World Scenarios

## 1: Creating Nested Project Structure
```bash
mkdir -p myapp/{src,tests,logs/output,docs}
```
> The `{}` syntax uses brace expansion to generate multiple directory paths under myapp.
> The `-p` flag ensures parent directories are created as needed (no error if already exist).

Final Directory Structure Created:
```text
myapp/
├── src/
├── tests/
├── logs/
│   └── output/
└── docs/
```
✅ Quickly sets up folders for source code, test scripts, logs, and documentation in one go.

### If you add `-v`:
```bash
mkdir -pv myapp/{src,tests,logs/output,docs}
```
You would see:
```bash
mkdir: created directory 'myapp'
mkdir: created directory 'myapp/src'
mkdir: created directory 'myapp/tests'
mkdir: created directory 'myapp/logs'
mkdir: created directory 'myapp/logs/output'
mkdir: created directory 'myapp/docs'
```

## 2: Secure Folder for Sensitive Data

```bash
mkdir -m 700 ~/.ssh_keys
```
> `mkdir`: Creates a new directory.  
> `-m 700`: Immediately sets the permission mode of the directory.  
> `~/.ssh_keys`: Creates the directory inside the user's home directory.  

### About Permission Mode `700`
> This mode is represented in binary as `rwx------`  
> So, only you (the owner) can access or view this directory.

| Entity     | Permissions | Meaning                           |
| ---------- | ----------- | --------------------------------- |
| **User**   | `rwx`       | Full access: read, write, execute |
| **Group**  | `---`       | No access                         |
| **Others** | `---`       | No access                         |

✅ Only the current user can access this folder — perfect for storing private SSH keys.

> To verify the permission was applied: `ls -ld ~/.ssh_keys`

## 3: Verbose Script Logging

```bash
mkdir -pv /var/www/mywebsite/{html,logs,cgi-bin}
```
`/var/www/mywebsite/{html,logs,cgi-bin}`: Uses brace expansion to create three directories under `/var/www/mywebsite`:
- `html`
- `logs`
- `cgi-bin`

If `/var/www/mywebsite` or its parent directories don’t exist, `-p` ensures they get created automatically.

### Resulting Directory Structure
```css
/var
└── www
    └── mywebsite
        ├── html/
        ├── logs/
        └── cgi-bin/
```
### Expected Terminal Output (due to -v)
```bash
mkdir: created directory '/var'
mkdir: created directory '/var/www'
mkdir: created directory '/var/www/mywebsite'
mkdir: created directory '/var/www/mywebsite/html'
mkdir: created directory '/var/www/mywebsite/logs'
mkdir: created directory '/var/www/mywebsite/cgi-bin'
```
> If any parent directories already exist, those lines will be skipped.

✅ Clear visibility during automation or Docker setup — prints every directory created.

## 4: Directory Creation with Permission Control

```bash
mkdir -m 755 /shared/project
```
### About Permission Mode `755`
| Entity     | Permissions | Meaning                               |
| ---------- | ----------- | ------------------------------------- |
| **User**   | `rwx`       | Read, write, execute (full access)    |
| **Group**  | `r-x`       | Read and execute, but no write access |
| **Others** | `r-x`       | Read and execute, but no write access |

✅ Makes the folder readable and executable by everyone, writable only by owner — great for teams.

## 5: Idempotent Folder Creation

```bash
mkdir -p existingdir
```

✅ Will not throw an error if the directory already exists — perfect for safe re-runs in CI/CD.

---

# Bonus Tips

## 1. Create folders using brace expansion:

```bash
mkdir -p project/{src,bin,docs}
```

✅ Creates `project/src`, `project/bin`, `project/docs`.

---

## 2. Create folders for dates or logs:

```bash
mkdir -p logs/$(date +%Y/%m/%d)
```
✅ Automatically organize logs by year/month/day.

---

## 3. Use in shell scripts for deployment:
```bash
#!/bin/bash
mkdir -p /opt/app/{logs,tmp,conf}
mkdir -m 700 /opt/app/secrets
```
✅ Ensures correct structure and security in deployments.

---

## 4. Combine with `&&` to perform actions after directory creation:
```bash
mkdir -p reports && cd reports && touch summary.txt
```
✅ Create folder → enter it → create a file.

---

## 5. Use in Dockerfiles:
```dockerfile
RUN mkdir -p /app/logs && chown -R appuser:appgroup /app
```
`&&`: Logical AND to chain commands; the second runs only if the first succeeds.  
`chown -R appuser:appgroup /app`:  
- Changes ownership of `/app` and all its contents recursively (`-R`).
- Sets the user owner to `appuser`.
- Sets the group owner to `appgroup`.

✅ Prepares container filesystem with necessary directories and ownership.

---

# Summary: 
| **Use Case**          | **Example Command**             | **Purpose**                                    |
| --------------------- | ------------------------------- | ---------------------------------------------- |
| Single directory      | `mkdir temp`                    | Create a folder named `temp`                   |
| Multiple directories  | `mkdir one two three`           | Create several folders in one command          |
| Nested structure      | `mkdir -p a/b/c`                | Automatically creates intermediate directories |
| Set permissions       | `mkdir -m 700 secret`           | Secure folder at creation                      |
| Verbose creation      | `mkdir -v newdir`               | Print each creation message                    |
| Help/Documentation    | `mkdir --help`                  | View usage options                             |
| Coreutils version     | `mkdir --version`               | Show command version info                      |
| Safe repeat execution | `mkdir -p already/exists`       | Prevents failure if folder already exists      |
| DevOps / automation   | `mkdir -p /app/{bin,logs,conf}` | Setup for applications or containers           |

