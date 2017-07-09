verify-tower-setup
=========

Playbook to verify tower's setup. This verification check is for a 3 node setup

Requirements
------------

* Ansible 2.3+

Role Variables
--------------

* tower_web_mgmt_port: Default is ``443``. Change this value to ``80``, if ``disable_https=True`` is used in the tower setup [all:vars] settings. 

Dependencies
------------

None

Example Playbook
----------------

    - hosts: tower
      roles:
         - { role: , tower_web_mgmt_port: 80 }

License
-------

MIT

Author Information
------------------

stanley at linuxsimba dot com
