# ansible-role-common

Ansible role for installing base packages, configuring hostname, /etc/hosts and enabling/disabling IPv6.

## Supported Platforms

* Ubuntu 18.04

## Requirements

Ansible 2.7 or higher is recommended.

## Variables

Variables for this

| variable | default value in defaults/main.yml | description |
| -------- | ---------------------------------- | ----------- |
| common_enabled | False | Determine whether role is enabled (True) or not (False) |
| common_ipv6_enabled | False | Enable (True) or disable (False) obtaining an IPv6 address for all interfaces via sysctl |
| common_hostname | {{ ansible_hostname }} | Hostname in /etc/hostname via ansible module hostname and for /etc/hosts |
| common_fqdn | {{ ansible_fqdn }} | FQDN for entry in /etc/hosts |
| common_etc_hosts_ipv4_entries | [] | Individual IPv4 entries in /etc/hosts, i.e. for resolving static ips with dnsmasq |
| common_etc_hosts_ipv6_entries | [] | Individual IPv6 entries in /etc/hosts, i.e. for resolving static ips with dnsmasq |

## Dependencies

None.

## Example Playbook

```yaml
---
# role: ansible-role-common
# file: site.yml

- hosts: common_servers
  roles:
    - role: ansible-role-common
```

## License and Author

- Author:: Jonas Mauer (<jam@kabelmail.net>)
- Copyright:: 2019, Jonas Mauer

Licensed under MIT License;
See LICENSE file in repository.

## References

[ArchWiki](https://wiki.archlinux.org/)