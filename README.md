Role Name
=========

This role builds a windows vm from template:
- Configures hostname a network
- Join the VM to a Domain;
- Configures/enable Winrm for Ansible
- Adds a specified user/group to local group of the Machine
- Extends the C:\ drive if more space is available
- Initialize disk 1
- Creates partition on disk 1, ,give drive letter and assign label
- Formats the drive

Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

Role Variables
--------------

defaults/Keys.yaml: Contains the passwords of vCenter, Windows domain admin user, and the new password for local administrator.This file can be encrypted to ensure security, you can use ansible vault to do this.
defaults/main.yml: Contains variables for the guest VM
A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

To provision de VM, you can create a deploy.yml file and execute de playbook
```
- name: Create VM from a template
  hosts: localhost
  roles:
  - VM_Windows

- hosts: new_vm
  tasks:
  - import_role:
      name: VM_Windows
      tasks_from: win_conf
```
$ ansible-playbook -i inventory deploy.yml

License
-------

BSD

Author Information
------------------

Manuel Nhiuana | email: manuel.nhiuana@gmail.com | website: VirtualClusterIT.net
