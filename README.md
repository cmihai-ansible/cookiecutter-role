Ansible Cookiecutter with Molecule Tests
========================================

Install prerequisities
----------------------

```bash
pip3 install --user ansible molecule[docker]
```

Creating a new role
-------------------

```bash
molecule init template \
  --url https://github.com/cmihai-ansible/ansible-cookiecutter-role.git \
  --role-name myrole
```

Testing your role with molecule
-------------------------------

```bash
cd roles/myrole
molecule test
```

TODO
----

1. Add support for non x86-64 platforms (ex: ARM)
2. Platform support: Fedora 29-31, Ubuntu 18.04+, Amazon Linux
3. Support for packer and building images and containers
4. Support for vagrant
