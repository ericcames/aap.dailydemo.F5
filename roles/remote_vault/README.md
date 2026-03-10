remote_vault
=========
```
Gather remote vaulted variables
```
Requirements
------------

Role Variables
--------------
```
my_remote_vault: >-
  https://raw.githubusercontent.com/ericcames/sourcefiles/refs/heads/main/vault_ames.yml
```
Dependencies
------------

Example Playbook
----------------
```
---
- name: Registering system with Red Hat Subscription Management
  hosts: satellite
  gather_facts: no

  roles:

    - role: remote_vault
```
License
-------

https://opensource.org/license/mit
