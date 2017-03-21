Machine commons
=========

This role is common across machines of National Library of the Czech Republic.  
This role installs few handy apps (git, vim, etc.) for start, sets smtp host in postfix, sync clock using NTP, sets timezone.

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

```
- name: Common configuration for all servers
  hosts: all
    roles:
      - { role: NLCR.common, packages: { name: [ git, vim, unzip ], state: latest } }
```

License
-------

BSD

Author Information
------------------

Rudolf Kreibich | rudolf.kreibich@nkp.cz | National Library of the Czech Republic
