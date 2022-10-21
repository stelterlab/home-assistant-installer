# home-assistant installer
Ansible Playbook for Installing Home Assistant Supervised

## Motivation

From time to time I want to test new features and/or setups for my Home Assistant installation. Instead of messing up my working installation I then install a virtual machine (KVM) and deploy a new fresh instance.

Because I'm a lazy devops engineer I wrote an ansible playbook for it.

## Preparation

Install your host with a supported Ubuntu (or Debian) version. Deploy your ssh key for the user that you want to use. Standard is ubuntu for Ubuntu, but you can change to whatever you like.

Just make sure that your new user is able to execute sudo without a password. And you will have to change the hosts file used as ansible inventory.

```
[server]
hassio ansible_host=192.168.23.42 ansible_user=ubuntu
```
Change ansible_host to the IP address of your new host. Or use localhost if you want to execute it directly onto your new host. Or use a hostname instead of "hassio" that resolves in your local dns and remove the ansible_host part.

## Installation

Deploy home assistant just via calling:

```
ansible-playbook -i hosts deploy.yml
```

This will install required packages, docker and of course the home-assistant with supervised as described in the [offical documentation](https://github.com/home-assistant/supervised-installer/).


## Known problems

I'm using ansible_architecture for choosing the version of the os-agent. The corresponding packages of the release are named differently for the Raspberry Pis as in armv7l instead of armv7 (name of the package in the release of the os agent).

Will have to build a workaround for that...
