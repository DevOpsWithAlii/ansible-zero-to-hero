# 🚀 Ansible Zero to Hero

![Ansible Logo](https://github.com/ansible/logos/blob/main/community-usage/correct-use-white.png)  
*A comprehensive guide to mastering Ansible for DevOps Engineers*

---

# 🧩 Ansible Master–Node Setup (Ubuntu)

### 1️⃣ Update & Install Ansible

```bash
sudo add-apt-repository ppa:ansible/ansible
sudo apt-get update -y
sudo apt install ansible -y
```

---

### 2️⃣ SSH Key Setup (if not already done)

```bash
cd ~/.ssh
vim ansible_key          # paste your private key if you created it earlier
chmod 700 ~/.ssh
chmod 600 ~/.ssh/ansible_key
```

---

### 3️⃣ Verify Key & Connect to Node

```bash
ssh -i ~/.ssh/ansible_key ubuntu@3.145.29.59
```

---

### 4️⃣ Check Ansible Inventory File

```bash
cd /etc/ansible
or
cat /etc/ansible/hosts
```

---

### 5️⃣ Create Custom Inventory Directory

```bash
mkdir ~/ansible
cd ~/ansible
vim hosts
```

**Example Ansible inventory `hosts` file:**

```
[servers]                                     #it is a group {group of servers}
server1 ansible_host=3.145.29.59              #ansible_host is a keyword
server2 ansible_host=3.150.114.25             #ansible_host is a keyword


[all:vars]
ansible_user=ubuntu
ansible_python_interpreter=/usr/bin/python3
ansible_ssh_private_key_file=/home/ubuntu/.ssh/ansible_key

```

---

### 6️⃣ Verify Inventory

```bash
ansible-inventory --list       or
ansible-inventory --list -y      or
ansible-inventory --list -y -i /home/ubuntu/ansible/hosts
```

---

### 7️⃣ Test Ansible Connection

```bash
ansible all -m ping -i /home/ubuntu/ansible/hosts    or
ansible all -m ping

```

---

### 8️⃣ Run Test Command on All Nodes

```bash
ansible all -a "free -h" -i /home/ubuntu/ansible/hosts    or
ansible all -a "free -h" 

```


## 🧰 Ansible Ad-Hoc Commands Cheat Sheet

### ✅ **Inventory and SSH Setup**

```bash
# Inventory file path
INVENTORY="/home/ubuntu/ansible/hosts"

# SSH key for connection
KEY="--private-key=~/.ssh/ansible_key"
```

---

### 📦 **Install Nginx (Ubuntu/Debian)**

```bash
ansible all -m apt -a "name=nginx state=present update_cache=yes" -b -i $INVENTORY $KEY
```
---
```

ansible all \                        # Run this on all hosts in the inventory
  -m apt \                           # Use the Ansible apt module (for Debian/Ubuntu package management)
  -a "name=nginx state=present update_cache=yes" \  # Arguments to the module:
                                                    # name=nginx         → Package to install
                                                    # state=present      → Ensure it's installed (if already installed, do nothing)
                                                    # update_cache=yes   → Run 'apt-get update' before installing
  -b \                               # Run with sudo (become)
  -i $INVENTORY \                    # Path to inventory file (list of hosts)
  $KEY                               # SSH private key to access target machines

---

### 🛑 **Stop and Disable Nginx**

```bash
# Stop the nginx service
ansible all -m ansible.builtin.service -a "name=nginx state=stopped" -b -i $INVENTORY $KEY

# Disable nginx from starting on boot
ansible all -a "systemctl disable nginx" -b -i $INVENTORY $KEY
```

---

### ❌ **Remove Nginx**

```bash
# Uninstall nginx (keeps config files)
ansible all -m apt -a "name=nginx state=absent" -b -i $INVENTORY $KEY

# OR uninstall and remove config files
ansible all -m apt -a "name=nginx state=absent purge=yes" -b -i $INVENTORY $KEY
```

---

### 📊 **System Monitoring Commands**

```bash
# Memory usage
ansible all -a "free -h" -i $INVENTORY $KEY

# Disk usage
ansible all -a "df -h" -i $INVENTORY $KEY

# CPU and uptime
ansible all -a "uptime" -i $INVENTORY $KEY

# Hostname
ansible all -a "hostname" -i $INVENTORY $KEY

# OS info
ansible all -a "cat /etc/os-release" -i $INVENTORY $KEY
```

---

### 🔧 **Package Management Examples**

```bash
# Install multiple packages
ansible all -m apt -a "name=curl,git,state=present update_cache=yes" -b -i $INVENTORY $KEY

# Upgrade all packages
ansible all -m apt -a "upgrade=dist" -b -i $INVENTORY $KEY
```

---

### 🛠️ **Service Management Examples**

```bash
# Start nginx
ansible all -m ansible.builtin.service -a "name=nginx state=started" -b -i $INVENTORY $KEY

# Restart nginx
ansible all -m ansible.builtin.service -a "name=nginx state=restarted" -b -i $INVENTORY $KEY

# Check if nginx is active
ansible all -a "systemctl is-active nginx" -b -i $INVENTORY $KEY
```

---

### 📁 **Useful File/Log Commands**

```bash
# View disk usage by user
ansible all -a "du -sh /home/*" -b -i $INVENTORY $KEY

# Show last 50 lines of syslog
ansible all -a "tail -n 50 /var/log/syslog" -b -i $INVENTORY $KEY
```

---

## ✅ Notes

* All commands assume you have passwordless SSH set up using `ansible_key`.
* `-b` is used to escalate privilege (like `sudo`) where required.
* Replace `all` with group names if your inventory defines them (e.g., `webservers`).

---
