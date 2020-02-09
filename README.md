Role Name
=========

conver2rhel: Conver2rhel

[![Build Status](https://travis-ci.org/cmihai-ansible/conver2rhel.svg?branch=master)](https://travis-ci.org/cmihai-ansible/conver2rhel)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devops-toolbox.conver2rhel](https://galaxy.ansible.com/devops-toolbox.conver2rhel)

```bash
ansible-galaxy install devops-toolbox.conver2rhel
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
conver2rhel_packages_state: present
conver2rhel_remove_packages: true
conver2rhel_enable_service: true
conver2rhel_enable_selinux: true
conver2rhel_copy_templates: true
conver2rhel_firewall_configure: true
conver2rhel_firewall_rules:
  - service: ssh
  - port: 3389
conver2rhel_users:
  - user: devops
    group: docker
conver2rhel_selinux_booleans:
  - name: ftp_home_dir
    state: true
    persistent: true
```

Dependencies
------------

- For Red Hat, subscription-manager.

Example Playbook
----------------

```yaml
---
- name: Install conver2rhel on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: conver2rhel is configured
      import_role:
        name: devops-toolbox.conver2rhel
      vars:
        conver2rhel_packages_state: present
        conver2rhel_remove_packages: true
        conver2rhel_enable_service: true
        conver2rhel_enable_selinux: true
        conver2rhel_copy_templates: true
        conver2rhel_firewall_configure: true
        conver2rhel_firewall_rules:
          - service: ssh
          - port: 3389
        conver2rhel_users:
          - user: devops
            group: docker
        conver2rhel_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: conver2rhel
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devops-toolbox.)
