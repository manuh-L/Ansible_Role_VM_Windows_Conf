Role Name
=========

This role builds a windows vm from template:
- Configures hostname and network
- Join the VM to a Domain;
- enables WinRM for Ansible
- Add a specified user/group to local group of the Machine
- Extends the C:\ drive if more space is available
- Initialize disk 1
- Creates partition on disk 1, assign drive letter label
- Formats the drive

Requirements
------------
- pyVmomi module


Role Variables
--------------

defaults/Keys.yaml: Contains the passwords of vCenter, Windows domain admin user, and the new password for local administrator.This file can be encrypted to ensure security, you can use ansible vault.

defaults/main.yml: Contains variables for the guest VM, vCenter Connection, WinRM connection



Example Playbook
----------------

To provision de VM, you can create a deploy.yml file and execute the playbook
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

Manuel Nhiuana | email: manuel.nhiuana@gmail.com | website: www.VirtualClusterIT.net
