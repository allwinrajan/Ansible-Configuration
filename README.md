
# Ansible Commands Cheat Sheet 📜

This repository contains a collection of commonly used Ansible commands for managing remote servers, installing packages, creating/removing files and directories, and interacting with Docker and Git repositories.

## Table of Contents
- [Copy Files](#copy-files)
- [Create Files](#create-files)
- [Remove Files](#remove-files)
- [Create and Remove Directories](#create-and-remove-directories)
- [Change Directory](#change-directory)
- [Install Packages](#install-packages)
- [Docker Operations](#docker-operations)
- [Git Operations](#git-operations)
- [File Permissions](#file-permissions)

---

## Copy Files 📝

**Copy a file from local to remote server**  
To copy a file from the local server to the remote server:

```bash
ansible <worker-host> -b -m copy -a "src=/home/ansible/copy.txt dest=/home/ansible/"
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
