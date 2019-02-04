[![Build Status](https://travis-ci.org/CSCfi/ansible-role-kill_libvirt_vm.svg?branch=master)](https://travis-ci.org/CSCfi/ansible-role-kill_libvirt_vm)
ansible-role-kill_libvirt_vm
=========

 - check if the VM is running on the hypervisor
 - destroy the VM (stops it)
 - undefines it (optionally also --remove-all-storage)
 - remove host cert from puppetmaster (optional)

Requirements
------------

Libvirt

Role Variables
--------------

 - hyper: the hypervisor where the inventory_hostname is running
 - puppetmaster: the address to the puppetmaster, in case
   - kill_clean_puppet_cert: is True
 - kill_libvirt_clean_storage: False
   - By default the role just undefines the VM which leaves any disk&storage associated with the VM
   - Setting this to True the role instead runs a "virsh undefine --remove-all-storage" command


Dependencies
------------

TODO
-------

 - Can we setup a libvirt VM that spawns a VM or two and then we can try to destroy them? Paravirtualized or lxc or some other container perhaps?

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```
    - hosts: servers
      roles:
         - { role: ansible-role-kill_libvirt_vm, when protected == "no" }

    - hosts: someotherservers
      roles:
         - { role: ansible-role-kill_libvirt_vm, when protected == "no" }

```

Then have group_vars that set "protected: no" for for example the development servers.

And then run ansible-playbook like this:

```
$ ansible-playbook site.yml -l develserver.example.org
```

Or if you want to do the same for a production server then (note the extra space at the beginning):

```
$ export HISTCONTROL="ignorespace"
$ HISTCONTROL="ignorespace"
$  ansible-playbook site.yml -l develserver.example.org -e protected=no
```

License
-------

MIT

Author Information
------------------

  * Original author Risto Laurikainen @ CSC
  * Oscar Kramer
  * Johan Guldmyr
  * Jukka Nousiainen
