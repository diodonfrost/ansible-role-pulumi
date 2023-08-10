# ansible-role-pulumi

[![molecule](https://github.com/diodonfrost/ansible-role-pulumi/workflows/molecule/badge.svg)](https://github.com/diodonfrost/ansible-role-pulumi/actions)
[![Ansible Galaxy](https://img.shields.io/badge/galaxy-diodonfrost.pulumi-660198.svg)](https://galaxy.ansible.com/diodonfrost/pulumi)

This role provide a compliance for install pulumi on your target host.

## Requirements

This role was developed using Ansible 2.8 Backwards compatibility is not guaranteed.
Use `ansible-galaxy install diodonfrost.pulumi` to install the role on your system.

Supported platforms:

```yaml
- name: EL
  versions:
    - 8
    - 7
    - 6
- name: Fedora
  versions:
    - 32
    - 31
    - 30
    - 29
    - 28
    - 27
    - 26
- name: Debian
  versions:
    - buster
    - stretch
    - jessie
- name: Ubuntu
  versions:
    - focal
    - bionic
    - xenial
    - trusty
- name: Amazon
  versions:
    - Candidate
    - 2017.12
    - 2016.03
- name: opensuse
  versions:
    - any
- name: ArchLinux
  versions:
    - any
- name: Alpine
  versions:
    - any
- name: Gentoo
  versions:
    - any
- name: ClearLinux
  versions:
    - any
- name: Windows
  versions:
    - 2016
    - 2012R2
```

## Role Variables

This role has multiple variables. The defaults for all these variables are the following:

```yaml
---
# defaults file for ansible-role-pulumi

# Define Pulumi version to install
# Default: latest (https://www.pulumi.com/latest-version)
pulumi_version: "latest"

# Define where to install Pulumi binary
# Default: use local system path defined in Ansible vars/*.yml
pulumi_path: "{{ pulumi_default_path }}"
```

## Dependencies

None

## Example Playbook

This is a sample playbook file for deploying the Ansible Galaxy pulumi role in a localhost and installing the latest version of pulumi.

```yaml
---
- hosts: localhost
  become: true
  roles:
    - role: diodonfrost.pulumi
```

This role can also install a specific version of pulumi.

```yaml
---
- hosts: localhost
  become: true
  roles:
    - role: ansible-role-pulumi
      vars:
        pulumi_version: 2.5.0
```

## Local Testing

This project uses [Molecule](http://molecule.readthedocs.io/) to aid in the
development and testing.

To develop or test you'll need to have installed the following:

* Linux (e.g. [Ubuntu](http://www.ubuntu.com/))
* [Docker](https://www.docker.com/)
* [Python](https://www.python.org/) (including python-pip)
* [Ansible](https://www.ansible.com/)
* [Molecule](http://molecule.readthedocs.io/)
* [Libvirt](https://www.virtualbox.org/) (windows tests only)
* [Vagrant](https://www.vagrantup.com/downloads.html) (if you test windows system)

### Testing with Docker

```shell
# Test ansible role with centos 8
molecule test

# Test ansible role with ubuntu 20.04
image=ansible-ubuntu:20.04 molecule test

# Test ansible role with alpine latest
image=ansible-alpine:latest molecule test

# Create centos 7 instance
image=ansible-centos:7 molecule create

# Apply role on centos 7 instance
image=ansible-centos:7 molecule converge

# Launch tests on centos 7 instance
image=ansible-centos:7 molecule verify
```

### Testing with Libvirt

```shell
# Test ansible role with Windows
molecule test -s windows
```

## License

Apache 2

## Author Information

This role was created in 2020 by diodonfrost.
