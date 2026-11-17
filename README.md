Ansible Role for OpenBao
=========

Example Requirements
--------------------

```yml
---
roles:
  - name: ansible-role-pkcs11
    src: git+https://github.com/moukail/ansible-role-pkcs11.git
    version: main
  - name: ansible-role-softhsm
    src: git+https://github.com/moukail/ansible-role-softhsm.git
    version: main

```

Example Playbook
----------------

```yaml
---
- name: Install pkcs11
  hosts: all
  become: true

  vars:
    softhsm_version: 2.7.0

  tasks:
    - name: Install SoftHSM
      ansible.builtin.include_role:
        name: ansible-role-softhsm

    - name: Configure pkcs11
      ansible.builtin.include_role:
        name: ansible-role-pkcs11
    