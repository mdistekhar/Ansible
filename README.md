# Ansible Setup and Verification

## Overview
This project documents the successful installation and verification of **Ansible** on an Ubuntu control node.  
It also outlines the required steps to configure inventory, test connectivity, and prepare for running playbooks (e.g., Docker installation).

---

## ✅ Ansible Installation Status

Ansible has been installed successfully and is working as expected.

### Verification Command
```bash
ansible --version

Verified Output

ansible [core 2.20.1]
config file = /etc/ansible/ansible.cfg
executable location = /usr/bin/ansible
python version = 3.12.3

📁 Inventory Configuration
Create or Edit Inventory File
sudo nano /etc/ansible/hosts

Example Inventory
[docker_servers]
172.31.6.195
172.31.6.196
172.31.6.197
172.31.6.198


Save the file:

Ctrl + O → Enter

Ctrl + X

🔍 Verify Inventory
ansible all --list-hosts

🔗 Test Connectivity
ansible docker_servers -m ping

Expected Output
SUCCESS => pong

⚠️ Optional: Fix SSH User Issue

If ping fails due to SSH authentication, update the inventory:

[docker_servers]
172.31.6.195 ansible_user=ubuntu
172.31.6.196 ansible_user=ubuntu
172.31.6.197 ansible_user=ubuntu
172.31.6.198 ansible_user=ubuntu


Re-run the ping command after updating.
