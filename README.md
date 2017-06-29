verify-tower-setup
=========

Playbook to verify tower's setup. Assumes that this is a production system, so contains at least 3 nodes

Requirements
------------

* Ansible 2.3+

Role Variables
--------------

* tower_web_mgmt_port: Usually is 443 or port 80, if ``disable_https`` is used in the tower setup [all:vars] settings. But for whatever reason if the UI mgmt port is changed, make sure this variable reflects that change

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
