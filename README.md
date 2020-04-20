# ansible-role-common

**Ansible role for installing base packages and some scripts.**

## Supported Platforms

- Alpine 3.11
- Amazonlinux 2
- Archlinux
- CentOS 7, 8
- Debian 9, 10
- Fedora 31
- Oraclelinux 7, 8
- Suse 15
- Ubuntu 18.04, 20.04

## Requirements

Ansible 2.8 or higher is recommended.

## Variables

Variables for this role:

```yaml
---
# role: ansible-role-common
# file: defaults/main.yml

# The role is disabled by default, so you do not get in trouble.
# Checked in tasks/main.yml which includes tasks.yml if enabled.
common_role_enabled: False

# List of custom packages to be installed on systems,
# in addition to the ones installed via the vars/*.yml files.
# NOTE: This variable can be set in an host_vars-file to distinguish between
# different distributions.
common_custom_packages: []
```

## Dependencies

None.

## Example Playbook

```yaml
---
# playbook: all
# file: site.yml

- hosts: all
  roles:
    - role: ansible-role-common
```

## License and Author

- Author:: [jam82](https://github.com/jam82/)
- Copyright:: 2020, [jam82](https://github.com/jam82/)

Licensed under [MIT License](https://opensource.org/licenses/MIT).
See [LICENSE](https://github.com/jam82/ansible-role-hostname/blob/master/LICENSE) file in repository.
