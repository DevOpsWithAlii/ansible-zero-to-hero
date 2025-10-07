# 🚀 Ansible Zero to Hero

![Ansible Logo](https://github.com/ansible/logos/blob/main/community-usage/correct-use-white.png)  
*A comprehensive guide to mastering Ansible for DevOps Engineers*

---

# 🧩 Ansible Master–Node Setup (Ubuntu)

### 1️⃣ Update & Install Ansible

```bash
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
cat /etc/ansible/hosts
```

---

### 5️⃣ Create Custom Inventory Directory

```bash
mkdir ~/ansible
cd ~/ansible
vim hosts
```

**Example `hosts` file:**

```
[servers]
server1 ansible_host=3.145.29.59
server2 ansible_host=3.150.114.25

[all:vars]
ansible_python_interpreter=/usr/bin/python3
```

---

### 6️⃣ Verify Inventory

```bash
ansible-inventory --list -y -i /home/ubuntu/ansible/hosts
```

---

### 7️⃣ Test Ansible Connection

```bash
ansible all -m ping -i /home/ubuntu/ansible/hosts --private-key=~/.ssh/ansible_key
```

---

### 8️⃣ Run Test Command on All Nodes

```bash
ansible all -a "free -h" -i /home/ubuntu/ansible/hosts --private-key=~/.ssh/ansible_key
```

---

### ✅ Summary

* Installed and configured **Ansible**
* Created SSH key and connected to node
* Added host info in custom inventory file
* Verified connection using **`ansible ping`**
* Executed remote command successfully using Ansible 🎯

## 📚 Overview

Welcome to **Ansible Zero to Hero**, your one-stop resource for learning and mastering Ansible! Whether you're a beginner or an experienced DevOps engineer, this repository has everything you need to automate your infrastructure with Ansible.

This guide covers:

- **Installation**: Step-by-step instructions for getting Ansible up and running.
- **Hosts Configuration**: How to set up and manage your inventory.
- **Ad-Hoc Commands**: Quick and powerful commands for one-time tasks.
- **Playbooks**: Automate complex tasks with reusable Ansible playbooks.
- **Real-World Examples**: Practical examples to help you apply what you've learned.

---
