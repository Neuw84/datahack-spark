# Zeppelin role for Ansible
=====================

Based on [https://github.com/kevincoakley/ansible-role-zeppelin](https://github.com/kevincoakley/ansible-role-zeppelin)

Install Apache Zeppelin - https://zeppelin.apache.org . Tested with CentOS 7, Ubuntu 14.04 and Ubuntu 16.04.

Requirements
------------

None

Role Variables
--------------

See defaults/main.yml

Dependencies
------------

Java

Example Playbook
----------------

    - name: Zeppelin role for CentOS and Ubuntu systems
      hosts: zeppelin
      become: yes
      become_method: sudo
    
      vars:
        - zeppelin_notebook_dir: /mnt/notebooks
    
      roles:
        - ansible-role-zeppelin
    
      tags:
        - zeppelin
    
License
-------
BSD

Author Information
------------------
Angel Conde (aconde@ikerlan.es)
