# Nexcloud instantiation using Ansible Pull
This repository contains the Ansible configuration, used to deploy  
a Nextcloud instance on a Ubuntu machine.

## Disclaimer
This is a personal repository, don't use it without checking what the  
actual configuration does.

## Prerequisites
- You need to install [ansible](https://www.ansible.com/). You can achieve this by running these commands:
  ```
  sudo apt update
  sudo apt install -y software-properties-common
  sudo apt-add-repository -y --update ppa:ansible/ansible
  sudo apt install -y ansible
  ```
- This ansible configuration is configured to run on an **Ubuntu** distribution.

## Running
First, you need to create a local `env.json` file, that contains the 
necessary variables. Here you can specify your own MariaDB root password,  
nextcloud database password and a public ssh key for the nextcloud user:  
```
{
	"mysql_root_password": "mypassword",
	"nextcloud_db_password": "mypassword",
	"nextcloud_ssh_key": "ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIH4WZuw5w4DPGm/0zj1VWG2prAJbwh4Z50gwEPJasOhk ansible"
}
```

To install nextcloud, simply run this command on the server, where you  
wish to install the nextcloud instance:
```
sudo ansible-pull -U https://github.com/klemenStanic/nextcloud_ansible.git -e @env.json 
```

You can then ssh into the server, using the `nextcloud` username:
```
ssh nextcloud@<server_ip> -i <private key corresponding with nextcloud_ssh_key>
```

Next, you need to create a nextcloud admin account. To achieve this, go  
to `<server ip address>` and fill out the necessary fields.

## Enabling nextcloud memory caching
To enable memory caching (for better performance), refer to this [link](https://docs.nextcloud.com/server/latest/admin_manual/configuration_server/caching_configuration.html#id1).
