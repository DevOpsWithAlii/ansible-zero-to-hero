---
### What are Ansible Handlers?
Handlers are special tasks triggered by a notify statement in other tasks. They are typically used for restarting services.

- **Example: Using a Handler**:

```
- name: Install Apache on RHEL server
  hosts: webserver
  tasks:
    - name: Install the latest version of Apache
      dnf:
        name: httpd
        state: latest

      notify:
       - Start Apache

  handlers:
     - name: Start Apache
       service:
         name: httpd
         state: started
```
The playbook consists of a regular task and a handler. The regular task installs the Apache HTTP server on the target system. Once installed the notify directive calls the handler task which starts the Apache service.

During playbook runtime, the regular task is executed first followed by the handler.

[Official Handlers References](https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_handlers.html#handler-example)


