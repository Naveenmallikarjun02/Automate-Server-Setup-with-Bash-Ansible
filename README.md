Project 1: Automate Server Setup with Bash & Ansible.

This project will help you:
- Learn basic Bash scripting.
- Automate server provisioning using Ansible.
- Understand configuration management principles.

Step 1: Clone the repo to your local machine

git clone https://github.com/your-username/server-automation-ansible.git
cd server-automation-ansible

Step 2: Create a Bash Script to Install Packages

Task: Install basic software on a Linux server
We’ll create a script that:
- Updates system packages.
- Installs Nginx, Git, and Curl.
- Enables and starts the Nginx service.

-----------------
-----------------
Create install.sh
-----------------
-----------------

#!/bin/bash

# Update system packages
echo "Updating system packages..."
sudo apt update -y && sudo apt upgrade -y

# Install necessary packages
echo "Installing Nginx, Git, and Curl..."
sudo apt install -y nginx git curl

# Start and enable Nginx
echo "Starting and enabling Nginx..."
sudo systemctl start nginx
sudo systemctl enable nginx

# Confirm installation
- echo "Installation complete!"


 Make it Executable
- chmod +x install.sh

Run the Script
- ./install.sh

Step 3: Automate with Ansible

Use Ansible to Automate the Setup on Remote Servers
We’ll create:
- An Ansible inventory file (hosts).
- An Ansible playbook (playbook.yml).
- A configuration for SSH key-based authentication.


Install Ansible

- sudo apt update && sudo apt install -y ansible

Create an Inventory File (hosts)

- [web]
your-server-ip ansible_ssh_user=ubuntu ansible_ssh_private_key_file=~/.ssh/id_rsa

Create playbook.yml
-

---
- name: Automate Server Setup
  hosts: web
  become: true
  tasks:
    - name: Update and upgrade system packages
      apt:
        update_cache: yes
        upgrade: yes

    - name: Install required packages
      apt:
        name:
          - nginx
          - git
          - curl
        state: present

    - name: Start and enable Nginx
      service:
        name: nginx
        state: started
        enabled: yes

Run the Ansible Playbook

- ansible-playbook -i hosts playbook.yml


Step 4: Push to GitHub

- git add .
- git commit -m "Added Bash script and Ansible playbook for server automation"
- git push origin main


-----------------------------------------------------------
-----------------------------------------------------------

What You Have Achieved
- Created a Bash script to automate software installation.
- Used Ansible to automate server configuration remotely.
- Pushed everything to GitHub for portfolio showcasing.




  

