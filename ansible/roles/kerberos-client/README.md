# Kerberos Client

Role to setup a [Kerberos Client](https://web.mit.edu/kerberos/krb5-devel/doc/admin/install_clients.html).

## Requirements

The role was created using [Ansible v.2.7](https://docs.ansible.com/ansible/2.7/index.html) for macOS and tested using the [centos/7](https://app.vagrantup.com/centos/boxes/7) boxes for [Vagrant v.2.2.0](https://www.vagrantup.com/docs/index.html) with [VirtualBox](https://www.virtualbox.org/) as a Provider.

The [Ansible modules](https://docs.ansible.com/ansible/2.7/modules/modules_by_category.html) used in the role are:

- [include_tasks](https://docs.ansible.com/ansible/2.7/modules/include_tasks_module.html#include-tasks-module) - new in version 2.4, previously [include](https://docs.ansible.com/ansible/2.7/modules/include_module.html#include-module) was used;
- [yum](https://docs.ansible.com/ansible/latest/modules/yum_module.html#yum-module) - requires Python 2 and `yum` (for Python 3 see [dnf](https://docs.ansible.com/ansible/latest/modules/dnf_module.html#dnf-module));
- [lineinfile](https://docs.ansible.com/ansible/latest/modules/lineinfile_module.html#lineinfile-module)
- [template](https://docs.ansible.com/ansible/2.7/modules/template_module.html#template-module)

> This role was tested using [CentOS 7](https://www.centos.org/) only.

## Role Tasks

The role is organised in two tasks files:

- [install](./tasks/install.yml) - ensure all kerberos client packages are installed;
- [setup](./tasks/setup.yml) - perform some common setup to ensure that:
  - kerberos server is present at the hosts file;
  - [krb5.conf](https://web.mit.edu/kerberos/krb5-1.12/doc/admin/conf_files/krb5_conf.html) file is setup accordingly.

## Role Variables

The role uses the `krb_clt_packages` to store the kerberos packages to be installed, defined in the [defaults](./defaults/main.yml) file.

Regarding Kerberos settings, in the [vars](./vars/main.yml) file are defined: 

- `krb_realm` - the kerberos realm;
- `krb_kdc_ip` - the kdc server ip address (this role assumes the admin server to be the same);
- `krb_kdc_hostname` - the kdc server FQDN (this role assumes the admin server to be the same).

Those should be change to match the environment.

## Dependencies

This role should be applied after the [base role](../base/README.md).

## Example Playbook

A full working example using [Vagrant](https://www.vagrantup.com/docs/index.html) is available in the [tests directory](./tests/) directory.