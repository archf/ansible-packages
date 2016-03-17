Ansible packages role
=====================

Ansible role to:
  - configure yum or dnf repository
  - install default packages
  - configure repositories ( currently only dnf//yum repos )
  - disable selinux on rhel

It will also:
  - add mounts to fs

Repos config file is embedded in the role.

Requirements
------------

None.

Role Variables
--------------

On Redhat derivatives:

```yaml
packages:
  - tmux
  - mosh
  - sudo
  - git
  - python3
  - htop
  - git
  - tree
  - openssh-server
  - gdisk
  - rsync
  - lvm2
  - ncurses-devel
  - ncurses
  - nmap
  - fail2ban
  - gcc
  - kernel-devel
  - vim-common
  - vim-X11
  - zsh
  - sshpass
  - urlview
  - rxvt-unicode-256color
```

On debian derivatives:

```yaml
packages:
  - tmux
  - mosh
  - git
  - vim-gtk
  - vim
  - python3
  - htop
  - git
  - fakeroot
  - tree
  - openssh-server
  - gdisk
  - rsync
  - lvm2
  - libncurses5-dev
  - libncurses5
  - nmap
  - fail2ban
  - gcc
  - linux-kernel-headers
  - zsh
  - sshpash
  - urlview
```

On openwrt platforms:

```yaml
packages:
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
```

Dependencies
------------

None.

Example Playbook
-------------------------

```yaml
- hosts: servers
  roles:
    - { role: archf.common }
        ```

License
-------

MIT

Author Information
------------------

Felix Archambault
