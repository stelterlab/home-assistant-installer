# homeassistant-installer
Ansible Playbook for Installing Home Assistant Supervised

## Motivation

From time to time I want to test new features and/or setups for my Home Assistant installation. Instead of messing up my working installation I then install a virtual machine (KVM) and deploy a new fresh instance.

Because I'm a lazy devops engineer I wrote an ansible playbook for it.

## Known problems

I'm using ansible_architecture for choosing the version of the os-agent. The corresponding packages of the release are named differently for the Raspberry Pis as in armv7l instead of armv7 (name of the package in the release of the os agent).

Will have to build a workaround for that...
