# Linux Commands Reference

Essential Linux commands for DevOps and system administration.

---

## File & Directory Management
- `ls` / `ls -la` - List files (with details and hidden files)
- `cd <directory>` - Change directory
- `pwd` - Print working directory
- `mkdir <name>` - Create directory
- `rm <file>` - Remove file
- `rm -rf <directory>` - Remove directory recursively
- `cp <source> <dest>` - Copy files
- `mv <source> <dest>` - Move or rename files
- `touch <file>` - Create empty file
- `find <path> -name <pattern>` - Search for files

## File Viewing & Editing
- `cat <file>` - Display file contents
- `less <file>` - View file with pagination
- `head <file>` - Show first 10 lines
- `tail <file>` - Show last 10 lines
- `tail -f <file>` - Follow file updates in real-time (logs)
- `grep <pattern> <file>` - Search text in files
- `nano <file>` / `vi <file>` - Text editors

## Permissions & Ownership
- `chmod 755 <file>` - Change file permissions
- `chown user:group <file>` - Change file owner
- `sudo <command>` - Execute command as superuser

## Process Management
- `ps aux` - List all running processes
- `top` / `htop` - Monitor system resources
- `kill <pid>` - Terminate process by ID
- `kill -9 <pid>` - Force kill process
- `jobs` - List background jobs
- `bg` / `fg` - Background/foreground jobs

## Network & Connectivity
- `ping <host>` - Test network connectivity
- `curl <url>` - Transfer data from URLs
- `wget <url>` - Download files
- `ssh user@host` - Secure shell connection
- `scp <source> user@host:<dest>` - Secure copy files
- `netstat -tuln` - Show listening ports
- `ifconfig` / `ip addr` - Display network interfaces

## System Information
- `df -h` - Show disk space usage
- `du -sh <directory>` - Show directory size
- `free -h` - Show memory usage
- `uname -a` - System information
- `uptime` - System uptime and load

## Package Management
- `apt update` / `apt upgrade` - Update packages (Ubuntu/Debian)
- `apt install <package>` - Install package
- `yum install <package>` - Install package (CentOS/RHEL)

## Archive & Compression
- `tar -czvf archive.tar.gz <directory>` - Create compressed archive
- `tar -xzvf archive.tar.gz` - Extract archive
- `zip -r archive.zip <directory>` - Create zip file
- `unzip archive.zip` - Extract zip file

## Text Processing
- `awk '{print $1}' <file>` - Process columns
- `sed 's/old/new/g' <file>` - Stream editor for replacing text
- `sort <file>` - Sort lines
- `uniq` - Remove duplicate lines
- `wc -l <file>` - Count lines

## DevOps Specific
- `docker ps` - List running containers
- `docker logs <container>` - View container logs
- `systemctl status <service>` - Check service status
- `systemctl restart <service>` - Restart service
- `journalctl -u <service>` - View service logs
- `crontab -e` - Edit scheduled tasks
- `env` - Show environment variables
- `export VAR=value` - Set environment variable

## Piping & Redirection
- `command1 | command2` - Pipe output to another command
- `command > file` - Redirect output to file (overwrite)
- `command >> file` - Append output to file
- `command 2>&1` - Redirect stderr to stdout

---

**Last Updated:** February 25, 2026
