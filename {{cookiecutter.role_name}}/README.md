Role Name
=========

{{ cookiecutter.role_name }}

[![Build Status](https://travis-ci.org/cmihai-ansible/{{ cookiecutter.role_name }}.svg?branch=master)](https://travis-ci.org/cmihai-ansible/{{ cookiecutter.role_name }})

Ansible galaxy:
---------------

[https://galaxy.ansible.com/crivetimihai/{{ cookiecutter.role_name }}](https://galaxy.ansible.com/crivetimihai/{{ cookiecutter.role_name }})

```bash
ansible-galaxy install crivetimihai.{{ cookiecutter.role_name }}
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.

Role Variables
--------------

```yaml
{{ cookiecutter.role_name }}_remove_packages: true
{{ cookiecutter.role_name }}_enable_service: true
{{ cookiecutter.role_name }}_enable_selinux: true
{{ cookiecutter.role_name }}_firewall_configure: true
{{ cookiecutter.role_name }}_firewall_rules:
  - service:
```

Dependencies
------------

- For Red Hat, subscription-manager.

Example Playbook
----------------

```yaml
---
- name: Install {{ cookiecutter.role_name }} on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: {{ cookiecutter.role_name }} is configured
      import_role:
        name: crivetimihai.{{ cookiecutter.role_name }}
      vars:
        {{ cookiecutter.role_name }}_remove_packages: true
        {{ cookiecutter.role_name }}_enable_service: true
        {{ cookiecutter.role_name }}_firewall_configure: true
        {{ cookiecutter.role_name }}_firewall_rules:
          - service:
      tags: {{ cookiecutter.role_name }}
```

Using KVM
---------

Install the libvirt driver for vagrant:

```bash
sudo yum install libvirt-devel ruby-devel gcc
export VAGRANT_DEFAULT_PROVIDER=libvirt
export VAGRANT_PREFERRED_PROVIDERS=libvirt
```

Use KVM:

```bash
molecule -s kvm create
molecule -s kvm login
```

License
-------

MIT

Author Information
------------------

- {{ cookiecutter.author_information }}
