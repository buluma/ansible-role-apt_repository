# Ansible role [apt_repository](https://galaxy.ansible.com/ui/standalone/roles/buluma/apt_repository/documentation)

Manage apt repositor(y|ies).

|GitHub|Version|Issues|Pull Requests|Downloads|
|------|-------|------|-------------|---------|
|[![github](https://github.com/buluma/ansible-role-apt_repository/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-apt_repository/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-apt_repository.svg)](https://github.com/buluma/ansible-role-apt_repository/releases/)|[![Issues](https://img.shields.io/github/issues/buluma/ansible-role-apt_repository.svg)](https://github.com/buluma/ansible-role-apt_repository/issues/)|[![PullRequests](https://img.shields.io/github/issues-pr-closed-raw/buluma/ansible-role-apt_repository.svg)](https://github.com/buluma/ansible-role-apt_repository/pulls/)|[![Ansible Role](https://img.shields.io/ansible/role/d/buluma/apt_repository)](https://galaxy.ansible.com/ui/standalone/roles/buluma/apt_repository/documentation)|

## [Example Playbook](#example-playbook)

This example is taken from [`molecule/default/converge.yml`](https://github.com/buluma/ansible-role-apt_repository/blob/master/molecule/default/converge.yml) and is tested on each push, pull request and release.

```yaml
---
- name: Converge
  hosts: all
  become: yes
  gather_facts: yes

  roles:
    - role: buluma.apt_repository
      apt_repositories:
        - repo: "deb https://dl.yarnpkg.com/debian/ stable main"
```

The machine needs to be prepared. In CI this is done using [`molecule/default/prepare.yml`](https://github.com/buluma/ansible-role-apt_repository/blob/master/molecule/default/prepare.yml):

```yaml
---
- name: Prepare
  hosts: all
  become: yes
  gather_facts: no

  roles:
    - role: buluma.bootstrap

  tasks:
    - name: install apt-transport-https ca-certificates
      ansible.builtin.package:
        name: "{{ item }}"
      loop:
        - apt-transport-https
        - ca-certificates

    - name: install yarn public key
      ansible.builtin.apt_key:
        url: "https://dl.yarnpkg.com/debian/pubkey.gpg"
        validate_certs: no
```

Also see a [full explanation and example](https://buluma.github.io/how-to-use-these-roles.html) on how to use these roles.

## [Role Variables](#role-variables)

The default values for the variables are set in [`defaults/main.yml`](https://github.com/buluma/ansible-role-apt_repository/blob/master/defaults/main.yml):

```yaml
---
# defaults file for apt_repositories

# You can add or remove repositories:
# apt_repositories:
#   - repo: ppa:rabbitvcs/ppa
#   - repo: ppa:something/ppa
#     state: absent

apt_repositories: []
```

## [Requirements](#requirements)

- pip packages listed in [requirements.txt](https://github.com/buluma/ansible-role-apt_repository/blob/master/requirements.txt).

## [State of used roles](#state-of-used-roles)

The following roles are used to prepare a system. You can prepare your system in another way.

| Requirement | GitHub | Version |
|-------------|--------|--------|
|[buluma.bootstrap](https://galaxy.ansible.com/buluma/bootstrap)|[![Ansible Molecule](https://github.com/buluma/ansible-role-bootstrap/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-bootstrap/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-bootstrap.svg)](https://github.com/shadowwalker/ansible-role-bootstrap)|

## [Context](#context)

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://buluma.github.io/) for further information.

Here is an overview of related roles:

![dependencies](https://raw.githubusercontent.com/buluma/ansible-role-apt_repository/png/requirements.png "Dependencies")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/buluma):

|container|tags|
|---------|----|
|[Ubuntu](https://hub.docker.com/repository/docker/buluma/ubuntu/general)|all|

The minimum version of Ansible required is 2.12, tests have been done to:

- The previous version.
- The current version.
- The development version.

If you find issues, please register them in [GitHub](https://github.com/buluma/ansible-role-apt_repository/issues)

## [Changelog](#changelog)

[Role History](https://github.com/buluma/ansible-role-apt_repository/blob/master/CHANGELOG.md)

## [License](#license)

[Apache-2.0](https://github.com/buluma/ansible-role-apt_repository/blob/master/LICENSE)

## [Author Information](#author-information)

[Shadow Walker](https://buluma.github.io/)

