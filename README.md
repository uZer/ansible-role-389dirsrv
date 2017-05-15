ansible-role-389dirsrv
======================

Work in progress

[![Build Status](https://travis-ci.org/uZer/ansible-role-389dirsrv.svg?branch=master)](https://travis-ci.org/uZer/ansible-role-389dirsrv)

This role installs 389dirsrv from apt/yum repository, configures system
max files and TCP ports, installs / configure ldap instance.
If the instance is already configured, won't replace it.

All variables should be configured in `host_vars` or `group_vars`. Check
`defaults/main.yml` for a full list of variables you can use. All intrusive
system tunning can be disables according to your needs.

Inspired by CSCfi's original role https://github.com/CSCfi/ansible-role-389-ds.
Difference is I don't install RHEL and give more variables for customization.

Dependencies
------------
Should work on Centos, Redhat, Ubuntu, Debian.

Usage
-----

    Work in progress

License
-------
"THE (extended) BEER-WARE LICENSE" (Revision 42.0815):

As long as you retain this notice you can do whatever you want with this stuff.
If we meet some day, and you think this stuff is worth it, you can buy me some
beers in return.

Author Information
------------------
Youenn Piolet
