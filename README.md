verify-tower-setup
=========

Existing Tower verification scripts are not good. This verification role should be in included in the ``install.yml`` of the Tower setup project. Existing tower verification does not work to my satisfaction. This role verifies the following:

1. Mgmt UI access is available from all Tower nodes
2. All Tower nodes can connect to the Postgres DB
3. API reports Tower HA mode is true
3. All Tower nodes are listed in the Rabbitmq cluster

This role is future proofed by auto detecting the Tower API version.

Requirements
------------

* Ansible 2.3+

Role Variables
--------------

* ``nginx_https_port``: Default is ``443``. Matches the variable used in the Tower setup project. If this role is added to a Tower setup, which is the assumption, then it should pick up the value set
in the project

* ``nginx_http_port``: Default is ``80``. Matches the variable used in the Tower setup project. If this role is added to a Tower setup, which is  the assumption, then it should pick up the value set
in the project

* ``nginx_disable_https``: Default is ``false``. Matches the variable used in the Tower setup project. If this role is added to a Tower setup, which is  the assumption, then it should pick up the value set
in the project

* ``rabbitmq_mgmt_user``: Defaults is ``guest``. Used to access ``rabbitmqctl`` output in JSON format

* ``rabbitmq_mgmt_user_password``: Default is ``guest``. Used to access ``rabbitmqctl`` output in JSON format.

Dependencies
------------

None

Example Playbook
----------------

Create a new playbook in the ansible tower setup directory. Call it ``verify.yml``

```
-
  hosts: tower
  gather_facts: false
  roles:
    - role: verify-tower-setup
```

Then run the playbook

```
ansible-playbook -i inventory verify.yml
```


License
-------

MIT

Author Information
------------------
Stanley Karunditu
