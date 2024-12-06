---
### What is Ansible Variables?
Variable in playbooks are very similar to using variables in any programming language. It helps you to use and assign a value to a variable and use that anywhere in the playbook. 

Variables allow dynamic content in playbooks. They can be defined in multiple ways, such as within playbooks, inventory, or external files.

- **Example: Simple Playbook that prints a message to stdout**:

```
- hosts: all
  vars:
    greetings: Hello Cloud & DevOps Learners!

  tasks:
  - name: Ansible Simple Variable Example Usage
    debug:
      msg: "{{ greetings }}, Let’s learn Ansible variables"
```
The definition of a variable starts with the vars block followed by the variable name and its corresponding value. In this example, greetings is the variable name while Hello everyone! is the value assigned to it.

To reference the value of the variable, encapsulate the variable inside double curly braces as such {{ greetings }}.

When the playbook is executed, the value of the variable is accessed and printed to stdout followed by the rest of the string.

- **Example: Playbook to Install and start Apache using Variable**:

```
- name: Install and start Apache
  hosts: webservers
  become: true
  tasks:
    - name: Ensure the httpd package is installed
      ansible.builtin.package:
        name: "{{ package_name }}"
        state: present
```

