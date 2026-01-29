# Ansible
✅ Perfect — Ansible is installed correctly and fully working.

Let’s break down what this confirms and what you should do next.

What This Output Confirms
ansible [core 2.20.1]


✔ Latest Ansible core installed

config file = /etc/ansible/ansible.cfg


✔ Ansible configuration file exists (good sign)

executable location = /usr/bin/ansible


✔ Ansible binary is available system-wide

python version = 3.12.3


✔ Compatible Python version

Everything is set up correctly 🎉

Recommended Next Steps (In Order)
1️⃣ Check / Create Inventory File
sudo nano /etc/ansible/hosts


Example:

[docker_servers]
172.31.6.195
172.31.6.196
172.31.6.197
172.31.6.198


Save → Ctrl + O, Exit → Ctrl + X

2️⃣ Test Ansible Connectivity
ansible all --list-hosts


Then:

ansible docker_servers -m ping


Expected:

SUCCESS => pong

3️⃣ (Optional) If Ping Fails – Add SSH User

Edit hosts file:

[docker_servers]
172.31.6.195 ansible_user=ubuntu
172.31.6.196 ansible_user=ubuntu

4️⃣ Install Docker Using Ansible (Next Big Step)

You are now 100% ready to run playbooks.
