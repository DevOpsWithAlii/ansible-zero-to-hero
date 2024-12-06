---
### What is Ansible Tasks?
Tasks are the individual actions executed on the target machines. A playbook consists of a sequence of tasks.

- **Example: Tasks in a Playbook**:

```
tasks:
  - name: Create a directory
    file:
      path: /var/www/html
      state: directory

```
