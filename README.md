Role Name
=========

qradar: Qradar

[![Build Status](https://travis-ci.org/cmihai-ansible/qradar.svg?branch=master)](https://travis-ci.org/cmihai-ansible/qradar)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devopstoolbox.qradar](https://galaxy.ansible.com/devopstoolbox.qradar)

```bash
ansible-galaxy install devopstoolbox.qradar
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
qradar_packages_state: present
qradar_remove_packages: true
qradar_enable_service: true
qradar_enable_selinux: true
qradar_copy_templates: true
qradar_firewall_configure: true
qradar_firewall_rules:
  - service: ssh
  - port: 3389
qradar_users:
  - user: devops
    group: docker
qradar_selinux_booleans:
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
- name: Install qradar on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: qradar is configured
      import_role:
        name: devopstoolbox.qradar
      vars:
        qradar_packages_state: present
        qradar_remove_packages: true
        qradar_enable_service: true
        qradar_enable_selinux: true
        qradar_copy_templates: true
        qradar_firewall_configure: true
        qradar_firewall_rules:
          - service: ssh
          - port: 3389
        qradar_users:
          - user: devops
            group: docker
        qradar_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: qradar
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devopstoolbox.)
