---
### What is Ansible Playbook?
An Ansible Playbook is a YAML file where you define the automation tasks to achieve a desired state on managed nodes. 

- **Example: Playbook for Patching a Server**:

```
- name: Patch and update servers
  hosts: all
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
