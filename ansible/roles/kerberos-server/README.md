# Kerberos Server

Role to setup a simple [Master KDC Server](https://web.mit.edu/kerberos/krb5-devel/doc/admin/install_kdc.html#install-and-configure-the-master-kdc).

## Requirements

The role was created using [Ansible v.2.7](https://docs.ansible.com/ansible/2.7/index.html) for macOS and tested using the [centos/7](https://app.vagrantup.com/centos/boxes/7) boxes for [Vagrant v.2.2.0](https://www.vagrantup.com/docs/index.html) with [VirtualBox](https://www.virtualbox.org/) as a Provider.

The [Ansible modules](https://docs.ansible.com/ansible/2.7/modules/modules_by_category.html) used in the role are:

- [include_tasks](https://docs.ansible.com/ansible/2.7/modules/include_tasks_module.html#include-tasks-module) - new in version 2.4, previously [include](https://docs.ansible.com/ansible/2.7/modules/include_module.html#include-module) was used;
- [yum](https://docs.ansible.com/ansible/latest/modules/yum_module.html#yum-module) - requires Python 2 and `yum` (for Python 3 see [dnf](https://docs.ansible.com/ansible/latest/modules/dnf_module.html#dnf-module));
- [template](https://docs.ansible.com/ansible/2.7/modules/template_module.html#template-module)
- [command](https://docs.ansible.com/ansible/2.7/modules/command_module.html#command-module)
- [service](https://docs.ansible.com/ansible/latest/modules/service_module.html#service-module)

> This role was tested using [CentOS 7](https://www.centos.org/) only.

## Role Variables

The role uses the `kerberos_server_packages` to store the kerberos packages to be installed, defined in the [defaults](./defaults/main.yml) file.

Regarding Kerberos settings, in the [defaults](./defaults/main.yml) file is defined the kerberos realm in the `kerberos_server_realm` variable, that take the value of the `ansible_domain` fact. It's also defined the master password for the Kerberos database, stored in `kerberos_server_master_pw`, and the admin user to be created, under the `kerberos_server_admin` dictionary.

The `kerberos_server_user_princ` variable is available at the [vars](./vars/main.yml) file to easily custom the UPNs needed to be created.

> Keep in mind that when passwords are in use, one should put [Ansible Vault](https://docs.ansible.com/ansible/latest/user_guide/vault.html) in action.

## Dependencies

This role should be applied after the [base role](../base/README.md).

## Example Playbook

A full working example using [Vagrant](https://www.vagrantup.com/docs/index.html) is available in the [tests directory](./tests/) directory.
