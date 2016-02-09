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
  3. Create your own linux brigde.
  4. Use an openvswitch bridge

It is not within the scope of this role to alter in any way your network stack. On the opposite, you must specify this role what network infrastructure to use.

Role Variables
--------------

These are the default containers settings. Replace the "_" by "." and this correlates exactly to lxc options as seen in the lxc documentation at the exception of `lxc_network_bridge_type`.

```yaml
# /etc/lxc/default.conf | ~/.config/lxc/default.conf
lxc_network_type: veth
lxc_network_link: lxcbr0
lxc_network_bridge_type: bridge
lxc_network_flags: up
lxc_network_hwaddr: '00:16:3e:xx:xx:xx'
lxc_network_ipv4_gateway: auto
lxc_network_ipv6_gateway: auto
```

Use `lxc_network_link` to specify the network device to use.
Use `lxc_network_bridge_type` to specify bridge type to use.
Either:
  * `bridge`
  * `ovsbridge`

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
