[![Ansible Galaxy](https://raw.githubusercontent.com/roles-ansible/ansible_role_acmetool/main/.github/galaxy.svg?sanitize=true)](https://galaxy.ansible.com/do1jlr/acmetool) [![MIT License](https://raw.githubusercontent.com/roles-ansible/ansible_role_acmetool/main/.github/license.svg?sanitize=true)](https://github.com/roles-ansible/ansible_role_acmetool/blob/main/LICENSE)

 Acmetool LE client
==================

Install and configure the `acmetool` LE client.


 Variables
-----------

* ``acme_notification_email:`` (Default: ``root@example.org``):
  LE account email. The default needs to be changed!

* ``submodules_versioncheck:`` (Default: ``false``):
  Enable basic versionscheck. *(``true`` is recomended)*

References
----------

* [acmetool](https://github.com/hlandau/acmetool)
* [acmetool user's guide](https://hlandau.github.io/acmetool/userguide)
