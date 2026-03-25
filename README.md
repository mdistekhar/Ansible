# What is  Ansible 

## Overview
Ansible is an open-source IT automation tool used to configure systems, deploy applications, and orchestrate workflows—without installing any agent on target machines.

🎯 One-line Definition

Ansible automates infrastructure by running tasks over SSH using simple YAML files.

---

🐧 1) Install Ansible on Linux

Ansible has been installed successfully and is working as expected.

### Install :-
```
sudo apt-add-repository ppa:ansible/ansible
sudo apt update
sudo apt install ansible

```
### Verify:
```
ansible --version
```
### Difference between Ansible and Chef :-
  🎯 Core Difference (quick mental model)

Ansible → Agentless, push-based, YAML, simple

Chef → Agent-based, pull-based, Ruby DSL, more control

---

🧠 Analogy 

🟢 Ansible = “Remote Control”

You directly tell servers:
---
### 🧠 Final Summary
🔐 Security

Ansible → SSH-based authentication

Chef → Certificate-based secure communication

---

# Ansible Setup & Server Connection Guide

## 📌 Overview

This guide explains how to:

* Install Ansible
* Configure SSH access
* Create an inventory file
* Connect and manage remote servers

---

## 🧱 Prerequisites

* Linux/macOS system (Control Node)
* Python installed (usually pre-installed)
* SSH access to target servers
* Target servers (Linux-based)

---


---

## 📄 Step 3: Create Inventory File

Create a file named `inventory.ini`:

```ini
[web]
server1 ansible_host=192.168.1.10 ansible_user=ubuntu

[db]
server2 ansible_host=192.168.1.20 ansible_user=ubuntu

[all:vars]
ansible_ssh_private_key_file=~/.ssh/id_rsa
ansible_python_interpreter=/usr/bin/python3
```

---

## 🧪 Step 4: Test Connection

```bash
ansible all -i inventory.ini -m ping
```

### Expected Output:

```json
server1 | SUCCESS => {
    "ping": "pong"
}
```

---

## ⚡ Step 5: Run Ad-hoc Commands

```bash
ansible all -i inventory.ini -m shell -a "uptime"
```

---

## 🚀 Step 6: Create and Run a Playbook

### Create `install-nginx.yml`:

```yaml
- name: Install Nginx
  hosts: web
  become: yes
  tasks:
    - name: Install nginx
      apt:
        name: nginx
        state: present
```

### Run Playbook:

```bash
ansible-playbook -i inventory.ini install-nginx.yml
```

---

## ☁️ AWS EC2 Example

Inventory file with `.pem` key:

```ini
[web]
ec2-instance ansible_host=3.x.x.x ansible_user=ubuntu

[all:vars]
ansible_ssh_private_key_file=~/mykey.pem
```

---

## ⚠️ Troubleshooting

### Permission Denied:

```bash
chmod 400 mykey.pem
```

### Host Unreachable:

* Check Security Group (Port 22 open)
* Verify IP address

### Python Not Found:

```bash
ansible all -m raw -a "sudo apt install python3 -y"
```

---

## 🧠 Key Concepts

| Concept      | Description                        |
| ------------ | ---------------------------------- |
| Control Node | Machine where Ansible is installed |
| Managed Node | Target servers                     |
| Inventory    | List of servers                    |
| Module       | Task execution unit                |
| Playbook     | YAML automation file               |

---

## 🎯 Summary

* Install Ansible on one machine (control node)
* Configure SSH access to servers
* Define servers in inventory file
* Run commands or playbooks to automate tasks

---

## 📚 Useful Commands

```bash
ansible all -m ping
ansible all -m shell -a "df -h"
ansible-playbook playbook.yml
```

---

## ✅ Best Practices

* Use SSH keys instead of passwords
* Organize inventory by environment (dev/staging/prod)
* Use roles for reusable configurations
* Store secrets securely (Ansible Vault)

---

## 🏁 Conclusion

Ansible enables simple, agentless automation using SSH and YAML-based playbooks. Once configured, it can efficiently manage multiple servers at scale.

---

### 🎯 What is an Ansible Playbook?

An Ansible Playbook is a YAML file that defines a set of tasks to be executed on target servers.

It’s the main way you automate things in Ansible.

🧠 Simple Analogy

Think of a playbook like a recipe:

Ingredients → Servers (hosts)

Steps → Tasks

Recipe → Playbook

👉 You follow the recipe → dish gets prepared
👉 Ansible follows playbook → servers get configured

⚙️ Basic Structure of a Playbook
```
- name: Install nginx
  hosts: web
  become: yes

  tasks:
    - name: Install nginx package
      apt:
        name: nginx
        state: present
```

---
### 🎯 What is Ansible Tower?

Ansible Tower is a web-based UI and management layer for Ansible that helps you automate, control, and scale Ansible operations.

It is the enterprise version of Ansible (now called AWX / Red Hat Ansible Automation Platform).

🧠 Simple Analogy
🟢 Ansible (CLI)
🔵 Ansible Tower ( Control dashboard )

---

⚙️ What Ansible Tower Provides
1. 🌐 Web UI

Run playbooks from browser

No need to remember CLI commands

----
