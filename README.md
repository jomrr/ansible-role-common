# ansible-role-common

![GitHub](https://img.shields.io/github/license/jam82/ansible-role-common) [![Build Status](https://travis-ci.org/jam82/ansible-role-common.svg?branch=main)](https://travis-ci.org/jam82/ansible-role-common)

**Ansible role for configuring base packages and repos.**

## Supported Platforms

- Alpine 3.12, 3.13
- Amazonlinux 2
- Archlinux
- CentOS 7, 8
- Debian 10, 11
- Fedora 32, 33
- Manjaro
- OpenSuse Leap 15.x, Tumbleweed
- Oraclelinux 7, 8
- Ubuntu 18.04, 20.04

## Requirements

Ansible 2.9 or higher is recommended.

## Variables

Variables and defaults for this role:

```yaml
---
# role: ansible-role-common
# file: defaults/main.yml

# The role is disabled by default, so you do not get in trouble.
# Checked in tasks/main.yml which uses a tasks block if enabled.
common_role_enabled: false

# APT Archive types to use.
# AFFECTS: ansible_os_family == 'Debian'.
common_apt_archives:
  - deb
  # - deb-src

# Components for repositories. Key is ansible_distribution.
# AFFECTS: ansible_os_family == 'Debian'.
common_apt_components:
  Debian:
    - main
    - contrib
    - non-free
  Ubuntu:
    - main
    - restricted
    - universe
    - multiverse

# APT repositories to enable/disable.
#
# AFFECTS: ansible_os_family == 'Debian'.
common_apt_enable_backports: true
#
# AFFECTS: ansible_distribution == 'Debian'.
common_apt_enable_debug: false
#
# AFFECTS: ansible_distribution == 'Ubuntu'.
common_apt_enable_proposed: false
#
# AFFECTS: ansible_distribution == 'Debian'.
common_apt_enable_security: true
#
# AFFECTS: ansible_os_family == 'Debian'.
common_apt_enable_updates: true

# Set apt-preferences files, e.g. pin-priority for repositories like Backports.
# Use distinguished "name" tags for multiple entries, as the last one
# will overwrite the preceeding ones with the same name (loop/template module).
# Prio 100 means, you have to manually install a package from backports,
# e.g. via "apt -t buster-backports install <package>".
# "name" attribute corresponds with the file name in /etc/apt/preferences.d/.
# Set prio to > 500 to automatically install available packages from repo.
# AFFECTS: ansible_os_family == 'Debian'.
common_apt_preferences:
  - file: backports
    package: '*'
    pin: "release a={{ ansible_distribution_release | lower }}-backports"
    priority: 100

# APT repository base urls.
# AFFECTS: ansible_os_family == 'Debian'.
common_apt_repo_base_urls:
  Debian: http://ftp.de.debian.org
  Ubuntu: http://de.archive.ubuntu.com

# Enable Archlinux User Repositories.
# AFFECTS: ansible_os_family == 'Archlinux'.
common_aur_enabled: true

# List of AUR packages to install.
# As AUR packages may require custom repo keys, e.g. spotify-bin,
# this is a list of dictionaries with package name and optional key parameters.
# AFFECTS: ansible_os_family == 'Archlinux'.
common_aur_packages: []
# - name: visual-studio-code-bin
# or
# - name: spotify
#   keyid: 8FD3D9A8D3800305A9FFF259D1742AD60D811D58
# or
# - name: spotify
#   key: https://download.spotify.com/debian/pubkey_0D811D58.gpg

# Enable EPEL for RHEL/CentOS
# AFFECTS: ansible_distribution == 'CentOS' and 'RedHat'.
common_epel_enabled: true

# List of custom packages to be installed on systems,
# in addition to the ones installed via vars.
# NOTE: This variable can be set in an host_vars- or group_vars-file
# to distinguish between different hosts(-groups)/distributions.
# AFFECTS: all.
common_install: []
```

## Dependencies

None.

## Example Playbook

```yaml
---
# playbook: all
# file: site.yml

- hosts: all
  become: true
  gather_facts: true
  roles:
    - role: ansible-role-common
```

## Acknowledgements

This role uses the [ansible-aur](https://github.com/pigmonkey/ansible-aur) module from [pigmonkey](https://github.com/pigmonkey).

Thank you for putting this under MIT License and making it available.

## License and Author

- Author:: [jam82](https://github.com/jam82/)
- Copyright:: 2021, [jam82](https://github.com/jam82/)

Licensed under [MIT License](https://opensource.org/licenses/MIT).
See [LICENSE](https://github.com/jam82/ansible-role-common/blob/main/LICENSE) file in repository.
