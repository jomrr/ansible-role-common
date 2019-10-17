# ansible-role-common

Ansible role for installing base packages, configuring hostname and enabling/disabling IPv6.

## Supported Platforms

* Ubuntu 18.04

## Requirements

Ansible 2.7 or higher is recommended.

## Variables

Variables for this

| variable | default value in defaults/main.yml | description |
| -------- | ---------------------------------- | ----------- |
| role_common_enabled | False | determine whether role is enabled (True) or not (False) |

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