# Nexcloud instantiation using Ansible Pull
This repository contains the Ansible configuration, used to deploy  
a Nextcloud instance on a Ubuntu machine.

## Disclaimer
This is a personal repository, don't use it without checking what the  
actual configuration does.

## Prerequisites
- You need to install `ansible`.
- This ansible configuration is configured to run on an Ubuntu distribution.

# Running
First, you need to create a local `inventory` file, that contains the 
necessary variables. Here you can specify your own `mysql_root_password`,  
nextcloud database password and a public ssh key, for the nextcloud user:  
```
[all:vars]
mysql_root_password=mypassword
nextcloud_db_password=mypassword
nextcloud_ssh_key="ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIH4WZuw5w4DPGm/0zj1VWG2prAJbwh4Z50gwEPJasOhk ansible"
```

To install nextcloud, simply run this command on the server, where you  
wish to install the nexcloud instance:
```
sudo ansible-pull https://github.com/klemenStanic/nextcloud_ansible.git -i inventory
```

