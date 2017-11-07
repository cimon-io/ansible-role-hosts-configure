# Ansible configure hosts role

An ansible role that adds rules to `/etc/hosts` in accordance with the playbook inventory.

The role includes the following tasks:

1. Set a current hostname according to the inventory.
2. Bind the hostname `inventory_hostname` along with `inventory_hostname_short` to 127.0.0.1.
3. Bind all other hosts from `inventory` to their private IPs adding corresponding rules to the file `/etc/hosts`.

This role can be run under all versions of Ubuntu and Debian.

## Requirements

None

## Role Variables

The only role variable is a private IP address:

```yaml
network_private_ip: ""
```

## Dependencies

None

## Example Playbook

```yaml
    - hosts: all
      roles:
        - role: hosts-configure
```

You can add hosts at `inventory`:

```yaml
[web]                                                   # A group name
fo-1.example.com network_private_ip=10.0.123.123        # A host name

[backend]
app-1.example.com network_private_ip=10.0.123.23

[dbs]
db-1.example.com network_private_ip=10.0.123.12
```

## License

Licensed under the [MIT License](https://opensource.org/licenses/MIT).
