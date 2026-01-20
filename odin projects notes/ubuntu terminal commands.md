## Basic Directory Names (by convention)
- `~` → your **home directory**
- `/` → **root** (top of the file system)
- `Desktop` → desktop files
- `Documents` → docs, schoolwork
- `Downloads` → downloaded files
- `Pictures` → images
- `Videos` → videos
- `Music` → audio
- `bin` → user executables
- `etc` → system config files
- `var` → logs, variable data
- `usr` → installed programs
- `tmp` → temporary files
## Directory Navigation
- `pwd` → show current directory
- `ls` → list files
- `ls -l` → detailed list
- `ls -a` → show hidden files
- `cd foldername` → move into folder
- `cd ..` → go up one directory
- `cd ~` → go home
- `cd /` → go to root
- `cd -` → go to previous directory

## Creating & Removing Directories
- `mkdir foldername` → create a directory
- `mkdir folder1 folder2` → create multiple
- `mkdir -p a/b/c` → create nested directories
- `rmdir foldername` → remove empty directory
- `rm -r foldername` → remove directory + contents (**dangerous**)
## File Creation & Management
- `touch file.txt` → create empty file
- `nano file.txt` → edit file (simple editor)
- `code file.txt` → open in VS Code
- `cat file.txt` → show file contents
- `less file.txt` → scroll file
- `cp a.txt b.txt` → copy file
- `mv a.txt folder/` → move file
- `mv old.txt new.txt` → rename file
- `rm file.txt` → delete file
## Hidden Files
- Start with a dot: `.git`, `.bashrc`
- Show hidden files: `ls -a`
## Permissions (important)
- `ls -l` → view permissions
- `chmod +x file.sh` → make executable
- `chmod 755 file` → common permission
- `chown user:user file` → change owner (sudo)
## Search & Find
- `find . -name file.txt` → find file
- `grep "text" file.txt` → search inside file
- `grep -r "text" folder/` → recursive search

## Shortcuts (VERY IMPORTANT)
- `Ctrl + C` → stop running command
- `Ctrl + Z` → pause process
- `Ctrl + D` → exit terminal
- `Ctrl + L` → clear screen
- `Tab` → auto-complete
- `↑ / ↓` → command history
- `!!` → run last command
- `Ctrl + R` → search command history

## System / Task Commands
- `clear` → clear terminal
- `history` → show command history
- `top` → running processes
- `htop` → better process viewer (if installed)
- `ps aux` → list processes
- `kill PID` → stop process
- `df -h` → disk space
- `du -h` → folder size
- `free -h` → RAM usage

## Package Management (Ubuntu)
- `sudo apt update`
- `sudo apt upgrade`
- `sudo apt install packagename`
- `sudo apt remove packagename`

## Paths Explained (EXAM FAVORITE)
- **Absolute path:** `/home/diego/Documents/file.txt`
- **Relative path:** `Documents/file.txt`
- `.` → current directory
- `..` → parent directory