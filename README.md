[![Ansible Galaxy](https://raw.githubusercontent.com/roles-ansible/ansible_role_acmetool/main/.github/galaxy.svg?sanitize=true)](https://galaxy.ansible.com/ui/standalone/roles/l3d/acmetool/) [![MIT License](https://raw.githubusercontent.com/roles-ansible/ansible_role_acmetool/main/.github/license.svg?sanitize=true)](https://github.com/roles-ansible/ansible_role_acmetool/blob/main/LICENCE)

 Acmetool LE client
==================

Install and configure the `acmetool` LE client.

We recomend to use this role together with the [do1jlr.nginx](https://github.com/do1jlr/ansible_role_nginx.git) ansible role. But this role has a standalone version too.

The ``do1jlr.nginx`` role installs a hook to enable nginx https sites and is running the ``acmetool want $domain`` command. Or you add the domains you need to the ``acme_domain_want_list: []``. But make sure you your acmetool is able to request the domains. Maybe you want to configure the ``response-file.yml.j2`` for that.


 Variables
-----------

* ``acme_notification_email:`` (Default: ``root@example.org``):
  LE account email. The default needs to be changed!

* ``acme_reload_services:`` (Default: ``[]``):
  Services that need a reload by certificat change
  *(There are some services pre-defined in the [files/reload](files/reload) file)*

* ``acme_restart_services:`` (Default: ``[]``):
  Services that need a restart by certificat change

* ``acme_domain_want_list:`` (Default: ``[]``):
  A list of domain you want to enable. Example:
```yml
acme_domain_want_list:
  - name: 'www.example.com'
```

* ``acme_domain_unwant_list:`` (Default: ``[]``):
  Disable a enabled domain. Same syntax than ``acme_domain_want_list``.

* ``submodules_versioncheck:`` (Default: ``false``):
  Enable basic versionscheck. *(``true`` is recomended)*


 Files
-------
* We search the ``response-file.yml.j2`` using the [first_found_lookup](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/first_found_lookup.html) with the following config:
```yaml
  files:
    - "response-file.{{ inventory_hostname }}.yml.j2"
    - 'response-file.yml.j2'
  paths:
    - 'templates/acmetool'
    - "templates/{{ inventory_hostname }}"
    - 'files/acmetool'
    - "files/{{ inventory_hostname }}"
    - 'templates'
```
This file is configuring the acmetool behaviour like certificate type, challange methode, acme notification email and so on. Change the values by providing your own ``response-file.yml.j2``.

* We search the ``reload`` and ``restart`` hook using the [first_found_lookup](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/first_found_lookup.html) with the config defined in ``vars/main.yml``.

* We deploy the ``acme-reload`` and ``acme-restart`` configuration based on the ``acme_reload_services:`` and ``acme_restart_services:`` variables

 References
------------

* [acmetool](https://github.com/hlandau/acmetool)
* [acmetool user's guide](https://hlandau.github.io/acmetool/userguide)

 Good to know
--------------
+ If you are using debian buster, you are probably interested in a more up to date version of acmetool. Have a look at the [do1jlr.acmetool_fix](https://galaxy.ansible.com/do1jlr/acmetool_fix) role, that will install a specific version of acmetool on debian based systems.
+ To add a domain manually to acmetool run ``acmetool want example.com``
+ To remove a domain manually from acmetool, ``acmetool unwant example.com``

