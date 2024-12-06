---
### What is Ansible Modules?
Modules (also referred to as “task plugins” or “library plugins”) are discrete units of code that can be used from the command line or in a playbook task. Ansible executes each module, usually on the remote managed node, and collects return values. In Ansible 2.10 and later, most modules are hosted in collections.

- **Example: Using the yum Module**:

```
- name: Install Apache
  hosts: webservers
  tasks:
    - name: Install httpd
      yum:
        name: httpd
        state: present
```
