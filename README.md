ansible_ipmi_lan_manage
=======================

Ansible role for managing IPMI LAN settings with [ipmitool](https://sourceforge.net/projects/ipmitool). Local fact in /etc/ansible/facts.d on remote host is created and used.

This role needs to run as root to use ipmitool, so include it in your playbook with:
```
roles:
  - { role: ansible_ipmi_lan_manage, become: yes }
```
or simply use `--sudo` with your ansible-playbook command.

# Variables:

```bash
get_ipmi: True  # Default: False
```
Query the current IPMI settings for each host and attempt to save them to host_vars/{{inventory_hostname_short}}/ipmi
unless you already have ipmi: defined somewhere.

```bash
set_ipmi: True  # Default: False
```
By default this role will only report on differences.  Use `-e "set_ipmi=True"` to
"arm" ipmi and run the `ipmi lan set` commands if necessary.

**P.S.** If this code is useful for you - don't forget to put a star on it's [github repo](https://github.com/selivan/ansible_ipmi_lan_manage).
