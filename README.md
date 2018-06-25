Role Name
=========

A quick simple `firewalld` configuration role.

Requirements
------------

None

Role Variables
--------------

There are currently three hashes:
  - firewalld_services
  - firewalld_ports
  - firewalld_rich_rules

Values for these are as follows:

```
firewalld_services:
  - service: <serice_name>
    zone: [zone]                  # Default: public
    permanenet: [true|false]      # Default: true
    state: [enabled|disabled]     # Default: enabled

firewalld_ports:
  - ports: <port/protocol>
    zone: [zone]                  # Default: public
    permanenet: [true|false]      # Default: true
    state: [enabled|disabled]     # Default: enabled

firewalld_rich_rules:
  - rich_rule: '<rich_rule>'
    permanenet: [true|false]      # Default: true
    state: [enabled|disabled]     # Default: enabled
```
Dependencies
------------

`firewalld` being present in your distro's repos

Example Playbook
----------------

```
- hosts: all
  vars:
    firewalld_services:
      - service: http
        zone: drop
        permanent: true
        state: "disabled"
      - service: https
      - service: ssh
    firewalld_ports:
      - port: 6443
      - port: 8080
        zone: drop
        permanent: true
        state: "disabed"
      - port: 8443
  roles:
    - role: kirikae.firewalld
```

TODO
----

* Test `rich_rule` settings
* Add options for [added|removing] zones
* Add masquerade options
* Add interface specific options

License
-------

MIT

Author Information
------------------

Kirikae <kirikae@mm.st>
