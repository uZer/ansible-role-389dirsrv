ansible-role-389dirsrv
======================

[![Build Status](https://img.shields.io/travis/uZer/ansible-role-389dirsrv.svg?style=flat-square)](https://travis-ci.org/uZer/ansible-role-389dirsrv)
[![Galaxy](http://img.shields.io/badge/galaxy-uZer.389dirsrv-blue.svg?style=flat-square)](https://galaxy.ansible.com/uZer/389dirsrv/)
[![GitHub Stars](https://img.shields.io/github/stars/uZer/ansible-role-389dirsrv.svg)](https://github.com/uZer/ansible-role-389dirsrv)

This role installs 389dirsrv from apt/yum repository, configures system
max files and TCP ports, installs / configure ldap instance.
If the instance is already configured, won't replace it: *the role only performs
initial installation and ldap initialization*.

All variables should be configured in `host_vars` or `group_vars`. Check
`defaults/main.yml` for a full list of variables you can use. All intrusive
system tunning can be disables according to your needs.

Inspired by CSCfi's original role https://github.com/CSCfi/ansible-role-389-ds.
Difference is I don't install RHEL and provide more variables for customization.

Dependencies
------------
Should work on Centos, Redhat, Ubuntu, Debian.

Parameters
----------

- Minimum variables to define:

```yaml
## IN VAULT
vault_dirsrv_password: "<password>"
vault_dirsrv_admin_password: "<admin-password>"

## IN GROUP_VARS/HOST_VARS
dirsrv_server_id: "<instance fqdn>"
dirsrv_admin_domain: "<instance domain>"
dirsrv_suffix: "<dc=<instance domain>>"
```

- Exhaustive variables definition:

```yaml
# Manage max open files in sysctl
dirsrv_manage_filemax: yes

# Manage dynamic tcp ports > 1024 in sysctl
dirsrv_manage_tcp: yes

# Store config in ldap (yes) or in directory (no)
dirsrv_config_in_ldap: yes

# Dirsrv install
dirsrv_server_id: "instance01"
dirsrv_admin_domain: "void"
dirsrv_suffix: "dc=void"

# If these 2 values are different, ldap will be installed as a replica of master
dirsrv_master_fqdn: "{{ ansible_fqdn }}"
dirsrv_local_fqdn: "{{ ansible_fqdn }}"

dirsrv_user: dirsrv
dirsrv_group: dirsrv
dirsrv_port: 389
dirsrv_service_name: dirsrv
dirsrv_package_state: installed
dirsrv_password: "{{ vault_dirsrv_password }}"
dirsrv_rootdn: "cn=Directory Manager"
dirsrv_admin_port: '9830'
dirsrv_admin_ip: '0.0.0.0'
dirsrv_admin_service_name: dirsrv-admin
dirsrv_admin_password: "{{ vault_dirsrv_admin_password }}"

# Extra variables per OS:
dirsrv_packages: <this list should not be edited>
dirsrv_service_name: dirsrv
dirsrv_user: dirsrv
dirsrv_group: dirsrv
```

License
-------
"THE (extended) BEER-WARE LICENSE" (Revision 42.0815):

As long as you retain this notice you can do whatever you want with this stuff.
If we meet some day, and you think this stuff is worth it, you can buy me some
beers in return.

Testing with Travis
-------------------
I'm using excellent geerlingguy's test suite.

Author Information
------------------
Youenn Piolet
