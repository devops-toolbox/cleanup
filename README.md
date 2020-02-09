Role Name
=========

cleanup: Cleanup

[![Build Status](https://travis-ci.org/cmihai-ansible/cleanup.svg?branch=master)](https://travis-ci.org/cmihai-ansible/cleanup)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devopstoolbox.cleanup](https://galaxy.ansible.com/devopstoolbox.cleanup)

```bash
ansible-galaxy install devopstoolbox.cleanup
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
cleanup_packages_state: present
cleanup_remove_packages: true
cleanup_enable_service: true
cleanup_enable_selinux: true
cleanup_copy_templates: true
cleanup_firewall_configure: true
cleanup_firewall_rules:
  - service: ssh
  - port: 3389
cleanup_users:
  - user: devops
    group: docker
cleanup_selinux_booleans:
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
- name: Install cleanup on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: cleanup is configured
      import_role:
        name: devopstoolbox.cleanup
      vars:
        cleanup_packages_state: present
        cleanup_remove_packages: true
        cleanup_enable_service: true
        cleanup_enable_selinux: true
        cleanup_copy_templates: true
        cleanup_firewall_configure: true
        cleanup_firewall_rules:
          - service: ssh
          - port: 3389
        cleanup_users:
          - user: devops
            group: docker
        cleanup_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: cleanup
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devopstoolbox.)
