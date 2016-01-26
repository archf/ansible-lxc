ansible-lxc
=========

An ansible role to install and configure lxc and lxd on a host.

It will:
  - install the packages (if on ubuntu will install the ppa).
  * template lxc config files
    - system wide files
    - unprivileged users config file

After that, your are ready to spawn lxc containers. Check out my ansible-lxcm
('m' for manager) role.

Requirements
------------

You have to setup networking. Basically, you have the following options:

  1. Use lxc-net service (on ubuntu)
  2. Use libvirt `virbr0` bridge.
  3. Create your own brigde.

It is not within the scope of this role to alter in any way your network stack.

Role Variables
--------------

```yaml
lxc_pkg_state: installed
```

Dependencies
------------

None.

Example Playbook
----------------

```yaml
    - hosts: lxchosts
      roles:
         - { role: archf.lxc }
```

License
-------

MIT

Author Information
------------------

Felix Archambault
