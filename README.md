Machine commons
=========

This role is common across machines of National Library of the Czech Republic.  
This role installs few handy apps (git, vim, etc.) for start, sets smtp host in postfix, sync clock using NTP, sets timezone.
Packages for provision is default to present

Requirements
------------

None

Role Variables
--------------

defaults/main.yml
```
packages:
  names: [ ntp ]
    state: latest

    timezone: Europe/Prague

    smtp_host: localhost
    hostname: '{{ ansible_nodename }}'

    ntp_servers: |
      server: tik.cesnet.cz
      server: tak.cesnet.cz
```
Dependencies
------------

None

Example Playbook
----------------

update package to latest
```
- name: Common configuration for all servers
  hosts: all
    roles:
      - { role: NLCR.common, packages: { name: [ git, vim, unzip ], state: latest } }
```
or more verbose and readable with default to stable
```
  roles:
    - role: NLCR.common
      packages:
        name: [ mc, nano ]
```

License
-------

BSD

Author Information
------------------

Rudolf Kreibich | rudolf.kreibich@nkp.cz | National Library of the Czech Republic
