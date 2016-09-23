# ansible-packages

Ansible role to install packages on a host

## Requirements

### Ansible version

Minimum required ansible version is 2.0.

## Description

Ansible role to
- configure yum or dnf repository
- install default packages
- configure repositories ( currently only dnf//yum repos )
- disable selinux on rhel
- add mounts in the fstree

### Add a mount to fstab

```yaml
# List of mounts to add to fstab.
mounts:
  - dev: '/dev/mapper/data_vg-home_lv'
    path: '/media/home_lv'
    state: mounted
    fstype: ext4
    opts: 'defaults,acl'
    group: users
    passno: X # defaults to 2
    dump: Y # defaults to 1
```


## Role Variables

### Variables conditionally loaded

Those variables from `vars/*.{yml,json}` are loaded dynamically during task
runtime using the `include_vars` module.

Variables loaded from `vars/CentOS.yml`.

```yaml
# List of packages to install by default on any CentOS family system
common_pkgs:
  - tmux
  - urlview
  - sudo
  - git
  - python34
  - htop
  - tree
  - openssh-server
  - gdisk
  - rsync
  - lvm2
  - ncurses-devel
  - ncurses
  - nmap
  - vim-common
  - vim-X11
  - zsh
  - curl
  - wget
  - libselinux-python
  - man
  - sshpass

```

Variables loaded from `vars/OpenWrt.yml`.

```yaml
# List of packages to install by default on any openwrt system
common_pkgs:
  - 6rd
  - zsh
  - vim
  - tmux
  - git
  - tcpdump
  - nmap
  - mtr
  - rsync
  - shadow
  - sudo
  - bind-dig
  - python
  - block-mount
  - kmod-usb-storage
  - kmod-fs-ext4
  - curl
  - wget
  - wol
  - etherwake
  - less
  - zsh
  - openssh-client
  - openssh-server
  - openssh-keygen
  - openssh-sftp-server
  - openssh-client-utils
  - ca-certificates
  - python-openssl

# cobbler requirements
    # createrepo
    # httpd (apache2 for Debian/Ubuntu)
    # mkisofs
    # mod_wsgi (libapache2-mod-wsgi for Debian/Ubuntu)
    # mod_ssl (libapache2-mod-ssl)
    # python-cheetah
    # python-netaddr
    # python-simplejson
    # python-urlgrabber
    # PyYAML (python-yaml for Debian/Ubuntu)
    # rsync
    # syslinux
    # tftp-server (atftpd for Debian/Ubuntu, though others may work)
    # yum-utils

```

Variables loaded from `vars/Debian.yml`.

```yaml
# List of packages to install by default on any debian family system.
common_pkgs:
  - tmux
  - urlview
  - mosh
  - git
  - vim-gtk3
  - vim
  - python3
  - htop
  - fakeroot
  - tree
  - openssh-server
  - gdisk
  - rsync
  - lvm2
  - libncurses5-dev
  - libncurses5
  - nmap
  - linux-kernel-headers
  - zsh
  - ssh-askpass
  - sshpass
  - curl
  - wget
  - python-selinux
  # - ntopng

```

Variables loaded from `vars/RedHat.yml`.

```yaml
# List of packages to install by default on any rhel family system.
common_pkgs:
  - tmux
  - urlview
  - mosh
  - sudo
  - git
  - python3
  - htop
  - tree
  - openssh-server
  - gdisk
  - rsync
  - lvm2
  - ncurses-devel
  - ncurses
  - nmap
  - vim-common
  - vim-X11
  - zsh
  - sshpass
  - curl
  - wget
  - libselinux-python

```

### Default vars

Defaults from `defaults/main.yml`.

```yaml
common_pkg_state: latest

selinux_state: disabled

# Default repos to configure on a target host.
RedHat_repodest: "/etc/yum.repos.d"
RedHat_repolist: []

Debian_repodest: '/etc/apt/sources.list.d'
Debian_repolist: []

```


## Installation

### Install with Ansible Galaxy

```shell
ansible-galaxy install archf.packages
```

Basic usage is:

```yaml
- hosts: all
  roles:
    - role: archf.packages
```

### Install with git

If you do not want a global installation, clone it into your `roles_path`.

```shell
git clone git@github.com:archf/ansible-packages.git /path/to/roles_path
```

But I often add it as a submdule in a given `playbook_dir` repository.

```shell
git submodule add git@github.com:archf/ansible-packages.git <playbook_dir>/roles/packages
```

As the role is not managed by Ansible Galaxy, you do not have to specify the
github user account.

Basic usage is:

```yaml
- hosts: all
  roles:
  - role: packages
```

## Ansible role dependencies

None.

## Todo

  * legacy package removal?

## License

MIT.

## Author Information

Felix Archambault.

## Role stack

This role was carefully selected to be part an ultimate deck of roles to manage
your infrastructure.

All roles' documentation is wrapped in this [convenient guide](http://127.0.0.1:8000/).


---
This README was generated using ansidoc. This tool is available on pypi!

```shell
pip3 install ansidoc

# validate by running a dry-run (will output result to stdout)
ansidoc --dry-run <rolepath>

# generate you role readme file
ansidoc <rolepath>
```

You can even use it programatically from sphinx. Check it out.