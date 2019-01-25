[![Build Status](https://travis-ci.org/CSCfi/ansible-role-kill_libvirt_vm.svg?branch=master)](https://travis-ci.org/CSCfi/ansible-role-kill_libvirt_vm)
ansible-role-kill_libvirt_vm
=========

Destroys a libvirt VM

Requirements
------------

Libvirt

Role Variables
--------------

 - hyper: the hypervisor where the inventory_hostname is running
 - puppetmaster: the address to the puppetmaster, in case
   - kill_clean_puppet_cert: is True


Dependencies
------------

TODO
-------

 - Can we setup a libvirt VM that spawns a VM or two and then we can try to destroy them? Paravirtualized or lxc or some other container perhaps?
 - Is command undefine enough, might need a "virsh undefine --remove-all-storage" or add some tasks that sorts out the pools?


Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: ansible-role-kill_libvirt_vm }

License
-------

MIT

Author Information
------------------

  * Original author Risto Laurikainen @ CSC
