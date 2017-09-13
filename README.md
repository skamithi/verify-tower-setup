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

Place this in the Tower ``install.yml`` at the end like so:

```

- name: "Install Tower node(s)"
  hosts: tower
  gather_facts: false
  roles:
    - role: packages_el
    ....
    ............
    .................

    - role: misc
      tags: misc
      cluster_host_identifier: "{{ rabbitmq_host|default(ansible_host) }}"

    - role: verify-tower-setup
```

License
-------

MIT

Author Information
------------------
Stanley Karunditu
