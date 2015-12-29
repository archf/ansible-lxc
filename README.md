ansible-lxc
=========

An ansible role to install and configure lxc on a host.

Requirements
------------

None.

Role Variables
--------------

defaults/main.yml:

```yaml
lxc_pkg_state: installed
```

vars/Debian.yml:

```yaml
lxc_packages:
  - lxc
  - lxc-templates
  - python3-lxc
```

vars/RedHat.yml:

```yaml
lxc_packages:
  - lxc
  - lxc-extra
  - lxc-templates
```

Dependencies
------------

None.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yaml
    - hosts: servers
      roles:
         - { role: archf.lxc }
```

License
-------

BSD

Author Information
------------------

Felix Archambault
