---
### What is Ansible Vault?
Ansible Vault is an Ansible feature that lets you encrypt confidential and sensitive information. Ansible Vault can encrypt text files, variables, and entire YAML playbooks. It uses AES 256 algorithm to provide symmetric encryption. 

Ansible Vault allows users to encrypt sensitive data such as passwords, API keys, and other confidential information by using symmetric encryption to encrypt files and their contents, which can be decrypted using a password or key.

To be more specific, Ansible vault performs the following tasks:
1. creates an encrypted file
2. Encrypts and decrypts files
3. Views encrypted files without compromising the encryption
4. Edits encrypted files
5. Resets encrypted keys

### How to use Ansible Vault and create a New Encrypted File Using Ansible Vault?

```
ansible-vault create secrets.yml
```
Once you run the command, you will be prompted for a vault password. Provide it and confirm it.

```
cat secrets.yml
```
### How To View an Encrypted File?

```
ansible-vault view secrets.yml
```

[Official Ansible Vault Reference](https://docs.ansible.com/ansible/2.9/user_guide/vault.html)


