Configure /etc/hosts
=========

An Ansible Role that adds rules to /etc/hosts in accordance with playbook inventory.

Requirements
------------

None.

Role Variables
--------------

Role use variables from inventory file: `{{ hostvars[item].specified_ip }}` and `{{ hostvars[item]['inventory_hostname'] }}`.

Dependencies
------------

None.

Example Playbook
----------------

    - hosts: all
      roles:
        - role: configure-network

Inside `inventory/hosts`:

```
[web]
fo-1

[backend]
app-1

[dbs]
db-1
```

Inside `inventory/host_vars/fo-1`:

```
---
ansible_ssh_host: 123.123.123.123
specified_ip: 123.123.123.123
```

Inside `inventory/host_vars/app-1`:

```
---
ansible_ssh_host: 124.124.124.124
specified_ip: 10.10.10.10
```

Inside `inventory/host_vars/db-1`:
```
---
ansible_ssh_host: 125.125.125.125
specified_ip: 10.10.10.11
```

License
-------

MIT

