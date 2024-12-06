---
### What is Ansible Playbook?
An Ansible Playbook is a YAML file where you define the automation tasks to achieve a desired state on managed nodes. 

- **Example: Playbook for Patching a Server**:

```
- name: Patch and update servers
  hosts: servers
  become: yes
  tasks:
    - name: Update the package manager cache
      apt:
        update_cache: yes
      when: ansible_os_family == "Debian"

    - name: Update all packages to their latest version (Debian-based)
      apt:
        upgrade: dist
      when: ansible_os_family == "Debian"

    - name: Update the package manager cache (RHEL-based)
      yum:
        name: '*'
        state: latest
      when: ansible_os_family == "RedHat"

    - name: Reboot the server if a kernel update was installed
      reboot:
        reboot_timeout: 300
```

- **Executing the Playbook**:

Step 1: Prepare the Inventory - Create an inventory file named hosts to define the servers.

```
  [servers]
  node1 ansible_host=3.142.79.205
  node2 ansible_host=3.143.210.190

  [all:vars]
  ansible_python_interpreter=/usr/bin/python3
  ansible_user=ubuntu
  ansible_ssh_private_key_file=/home/ubuntu/keys/ansible-master-key.pem

```

Step 2: Execute the playbook using the ansible-playbook command.

```
ansible-playbook -i hosts patch_server.yml
```

