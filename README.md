Machine commons
=========

This role is common across machines of National Library of the Czech Republic
This role installs few handy apps (git, vim, etc.) for start, sets smtp host in postfix, sync clock using NTP, sets timezone.

Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

Role Variables
--------------

defaults/main.yml

packages:
  names: [ ntp ]
    state: latest

    timezone: Europe/Prague

    smtp_host: localhost
    hostname: '{{ ansible_nodename }}'

    ntp_servers: |
      server: tik.cesnet.cz
      server: tak.cesnet.cz

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

- name: Common configuration for all servers
  hosts: all
    roles:
      - { role: NLCR.common, packages: { name: [ git, vim, unzip ], state: latest } }

License
-------

BSD

Author Information
------------------

Rudolf Kreibich | rudolf.kreibich@nkp.cz | National Library of the Czech Republic
