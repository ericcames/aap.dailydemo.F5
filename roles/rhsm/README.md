rhsm
=========
```
This role manages your red hat subs with the redhat customer portal
```
Requirements
------------

Role Variables
--------------
```
# Use a Red Hat Customer Portal credential
# customer_portal_username: mikey.mouse
# customer_portal_password: redhat123
redhat_subscription_manager_status: present
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

    - role: rhsm
        status: present
```
License
-------

https://opensource.org/license/mit
