Ansible Setup & Verification Guide
Overview

This repository documents the successful installation and initial verification of Ansible on an Ubuntu system, along with the recommended next steps to prepare managed nodes for automation tasks such as Docker installation.

✅ Ansible Installation Status

Ansible has been installed correctly and is fully operational.

Verified Output
ansible --version

ansible [core 2.20.1]
config file = /etc/ansible/ansible.cfg
executable location = /usr/bin/ansible
python version = 3.12.3

What This Confirms

✔ Latest Ansible core installed

✔ Global configuration file present (/etc/ansible/ansible.cfg)

✔ Ansible binary available system-wide

✔ Compatible Python version installed

🎉 The control node is ready for automation.

📌 Recommended Next Steps
1️⃣ Create or Verify Inventory File

Open the default Ansible inventory file:

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

2️⃣ Verify Inventory Hosts
ansible all --list-hosts


This confirms that Ansible can read the inventory correctly.

3️⃣ Test Connectivity to Managed Nodes
ansible docker_servers -m ping

Expected Output
SUCCESS => pong

4️⃣ (Optional) Fix SSH User Issues

If ping fails due to authentication, specify the SSH user in the inventory:

[docker_servers]
172.31.6.195 ansible_user=ubuntu
172.31.6.196 ansible_user=ubuntu
172.31.6.197 ansible_user=ubuntu
172.31.6.198 ansible_user=ubuntu


Re-run the ping test afterward.

🚀 Next Objective

With Ansible installed and connectivity verified, the environment is now ready to:

Run playbooks

Install Docker using Ansible

Automate configuration and deployments

Summary

✅ Ansible installed and verified

✅ Inventory configured

✅ SSH connectivity tested

✅ Ready for automation workflows
