[![Ansible Galaxy](https://raw.githubusercontent.com/roles-ansible/ansible_role_acmetool/main/.github/galaxy.svg?sanitize=true)](https://galaxy.ansible.com/do1jlr/acmetool) [![MIT License](https://raw.githubusercontent.com/roles-ansible/ansible_role_acmetool/main/.github/license.svg?sanitize=true)](https://github.com/roles-ansible/ansible_role_acmetool/blob/main/LICENCE)

 Acmetool LE client
==================

Install and configure the `acmetool` LE client.


 Variables
-----------

* ``acme_notification_email:`` (Default: ``root@example.org``):
  LE account email. The default needs to be changed!

* ``submodules_versioncheck:`` (Default: ``false``):
  Enable basic versionscheck. *(``true`` is recomended)*


 Files
-------
* We search the ``response-file.yml.j2`` using the [first_found_loopup](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/first_found_lookup.html) with the following config:
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

 References
------------

* [acmetool](https://github.com/hlandau/acmetool)
* [acmetool user's guide](https://hlandau.github.io/acmetool/userguide)

 Good to know
--------------
If you are using debian buster, you are probably interested in a more up to date version of acmetool. Have a look at the [do1jlri.acmetool_fix](https://galaxy.ansible.com/do1jlr/acmetool_fix) role, that will install a specific version of acmetool on debian based systems.

 Testing
---------
We are using the following github actions for testing and releasing to ansible galaxy.

| Action Status | Marketplace |
| ------------- | ----------- |
| [![Ansible Lint check](https://github.com/roles-ansible/ansible_role_acmetool/actions/workflows/ansible-linting-check.yml/badge.svg)](https://github.com/roles-ansible/ansible_role_acmetool/actions/workflows/ansible-linting-check.yml) | [ansible-lint](https://github.com/marketplace/actions/ansible-lint) |
| [![Galaxy release](https://github.com/roles-ansible/ansible_role_acmetool/actions/workflows/galaxy.yml/badge.svg)](https://github.com/roles-ansible/ansible_role_acmetool/actions/workflows/galaxy.yml) | [publish-ansible-role-to-galaxy](https://github.com/marketplace/actions/publish-ansible-role-to-galaxy) |
| [![Yamllint GitHub Actions](https://github.com/roles-ansible/ansible_role_acmetool/actions/workflows/yamllint.yaml/badge.svg)](https://github.com/roles-ansible/ansible_role_acmetool/actions/workflows/yamllint.yaml) | [yamllint-github-action](https://github.com/marketplace/actions/yamllint-github-action) |
