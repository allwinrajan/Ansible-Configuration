
# Ansible Commands Cheat Sheet 📜

This repository contains a collection of commonly used Ansible commands for managing remote servers, installing packages, creating/removing files and directories, and interacting with Docker and Git repositories.

## Copy Files 📝

**Copy a file from local to remote server**  
To copy a file from the local server to the remote server:

```bash
ansible dev -b -m copy -a "src=/home/ansible/copy.txt dest=/home/ansible/"
```

---

## Create Files ✨

**Create a file on the remote server**  
To create a file on the remote server:

```bash
ansible dev -b -m file -a "name=sample.txt state=touch"
```

---

## Remove Files 🗑️

**Remove a file from the remote server**  
To remove a file from the remote server:

```bash
ansible dev -b -m file -a "src=/home/ansible/sample.txt state=absent"
```

---

## Create and Remove Directories 📂

**Create a directory on the remote server**  
To create a directory on the remote server:

```bash
ansible dev -b -m shell -a "mkdir confidential"
```

**Remove a directory on the remote server**  
To remove a directory from the remote server:

```bash
ansible dev -b -m shell -a "rmdir confidential"
```

---

## Change Directory ⬇️

**Change the directory in the remote server and list contents**  
To change the directory and run a command:

```bash
ansible dev -b -m shell -a "cd /home/ansible/sample && ls 'Directory Changed'"
```

---

## Install Packages ⚙️

**Install Git on the remote server**  
To install Git on the remote server:

```bash
ansible dev -b -m yum -a "pkg=git state=present"
```

**Install Docker on the remote server**  
To install Docker on the remote server:

```bash
ansible dev -b -m yum -a "pkg=docker state=present"
```

---

## Docker Operations 🐳

**Pull an HTTPD image on the remote server**  
To pull the `httpd` image from Docker Hub:

```bash
ansible dev -b -m shell -a "docker pull httpd"
```

**Run a container on the remote server**  
To run a Docker container in detached mode:

```bash
ansible dev -b -m shell -a "docker run -it -d --name webapp -p 8000:80 httpd"
```

---

## Git Operations 🧑‍💻

**Clone a Git repository on the remote server**  
To clone a repository from GitHub:

```bash
ansible dev -b -m shell -a "git clone https://github.com/allwinrajan/Ansible-Configuration.git"
```

---

## File Permissions 🔐

**Create a file with 0777 permissions on the remote server**  
To create a file with specific permissions (0777):

```bash
ansible dev -b -m file -a "path=/home/ansible/sample/all.txt mode=0777 state=touch"
```

**Remove a file with specific permissions from the remote server**  
To remove the file:

```bash
ansible dev -b -m file -a "path=/home/ansible/sample/all.txt state=absent"
```

---

# Ansible Commands for Apache HTTP Server Operations 🚀

This section includes a set of commonly used Ansible commands to manage the Apache HTTP Server (`httpd`) on remote hosts, along with file and directory management commands.

---

## Working with Directories 🗂️

**Print the current working directory on each host**  
To print the current working directory (`pwd`) on each host:

```bash
ansible dev -a "pwd"
```

**List the files in the current directory on each host**  
To list the files in the current directory on each host:

```bash
ansible dev -a "ls"
```

**List all files (including hidden ones) in the current directory on each host**  
To list all files, including hidden files (`ls -a`), on each host:

```bash
ansible dev -a "ls -a"
```

---

## Install Apache HTTP Server (httpd) 🔥

**Install Apache HTTP Server (httpd) on remote hosts**  
To install the Apache HTTP Server (`httpd`) on the remote hosts:

```bash
ansible dev -a "sudo yum install httpd -y"
```

**Locate the installation path of the httpd binary on remote hosts**  
To find the location of the `httpd` binary:

```bash
ansible dev -a "sudo which httpd"
```

---

## Manage Apache HTTP Server (httpd) Service ⚙️

**Check the status of the httpd (Apache) service with elevated privileges**  
To check the status of the Apache HTTP Server service:

```bash
ansible dev -b -a "systemctl status httpd"
```

**Start the httpd (Apache) service on remote hosts with elevated privileges**  
To start the Apache HTTP Server service:

```bash
ansible dev -b -a "systemctl start httpd"
```

**Stop the httpd (Apache) service on remote hosts with elevated privileges**  
To stop the Apache HTTP Server service:

```bash
ansible dev -b -a "systemctl stop httpd"
```

**Remove the httpd package (Apache HTTP Server) from remote hosts with elevated privileges**  
To remove the Apache HTTP Server package:

```bash
ansible dev -b -a "sudo yum remove httpd -y"
```
