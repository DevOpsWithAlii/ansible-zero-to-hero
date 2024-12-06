---
### What are Ansible Roles?

Roles are a way to organize playbooks into reusable components. A role typically includes tasks, templates, files, handlers, and variables.

Ansible roles are a way to organize playbooks into reusable components. They help break down a playbook into smaller, more manageable pieces, making it easier to scale and maintain. Each role is essentially a directory structure with predefined files and folders that Ansible recognizes and uses to perform specific tasks.

### Role Directory Structure?
When you create a role, Ansible expects a standard directory layout.

```
roles/
  <role_name>/
    tasks/         # Defines the main tasks for the role (main.yml is mandatory).
    handlers/      # Defines handlers (e.g., restart services).
    templates/     # Stores Jinja2 templates for configuration files.
    files/         # Contains static files to be copied to the target machine.
    vars/          # Stores variables specific to the role.
    defaults/      # Stores default variables (overridden by other variable sources).
    meta/          # Metadata about the role, including dependencies.

```

### How to Create a Role?
To create a role named webserver, use the command.

```
ansible-galaxy init webserver

```
This creates the directory structure for the webserver role.

- **Example: Role Directory Structure**:

```
roles/
  webserver/
    tasks/
      main.yml
    templates/
      index.html.j2
    vars/
      main.yml
    handlers/
      main.yml

```

