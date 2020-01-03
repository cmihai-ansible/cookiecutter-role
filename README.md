Ansible Cookiecutter with Molecule Tests
========================================

Install prerequisities
----------------------

```bash
pip3 install --user ansible molecule[docker]
pip3 install --user ansible molecule[podman]
pip3 install --upgrade --user molecule-libvirt libvirt
```

Creating a new role
-------------------

```bash
molecule init template \
  --url https://github.com/cmihai-ansible/cookiecutter-role.git \
  --role-name myrole
```

Testing your role with molecule
-------------------------------

```bash
cd roles/myrole
molecule test
```

Using KVM
---------

Install the libvirt driver for vagrant:

```bash
sudo yum install libvirt-devel ruby-devel gcc
export VAGRANT_DEFAULT_PROVIDER=libvirt
export VAGRANT_PREFERRED_PROVIDERS=libvirt
export CONFIGURE_ARGS="with-libvirt-include=/usr/include/libvirt with-libvirt-lib=/usr/lib64"
vagrant plugin install vagrant-libvirt
```

Use KVM:

```bash
molecule -s kvm create
molecule -s kvm login
```

Cleanup:

```
vagrant global-status
vagrant destroy ID
```

TODO
----

1. Add support for non x86-64 platforms (ex: ARM)
2. Platform support: Fedora 29-31, Ubuntu 18.04+, Amazon Linux
3. Support for packer and building images and containers
4. Support for vagrant
