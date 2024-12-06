---
### What are Ansible Facts?
Facts are system variables collected by Ansible from managed nodes. They provide information about the system's state (e.g., OS, IP addresses).

Ansible facts are the information collected by Ansible regarding the managed hosts. Facts detail a complete snapshot of the state of each host system, including hardware, network configuration, operating system, and software installed. These facts are gathered automatically when a playbook is executed, unless explicitly disabled.

- **Example: Displaying Specific Facts**:

```
- name: Display system information
  hosts: all
  gather_facts: yes
  tasks:
    - name: Display hostname
      debug:
        msg: "The hostname of this system is {{ ansible_facts['hostname'] }}"
    - name: Display OS type
      debug:
        msg: "This system is running {{ ansible_facts['os_family'] }} OS"
```

[Official Ansible Facts Reference](https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_vars_facts.html)
