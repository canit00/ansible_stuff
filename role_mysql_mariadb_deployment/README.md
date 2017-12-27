Role Name
=========

A brief description of the role goes here.

Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:
```
---
# Ansible playbook to deploy mariadb / secure / and enable service.
# Optionally, we can deploy a specific datadir, user & db for an application which is how we want to deploy mariadb in our environment.
# How-to-run playbook: > ansible-playbook -l <hostname> playbooks/pb_mariadb_mysql.yaml -v --ask-vault-pass -e "custom=true datadir=/opt/mysql db_user=zenoss db_name=zenossdb"

- hosts: all
  become: true
  become_method: sudo

  roles:
  - { role: role_mysql_mariadb_deployment }
```

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
