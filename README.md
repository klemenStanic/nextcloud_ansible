# Deploy a nextcloud server using ansible

It includes an ansible playbook, that deploys a nextcloud application alongside apache2 http server
to a Ubuntu server.

Note that this is a personal repository, and many things could be improved.

## How to use
You need to have ansible installed on your local machine.  
First, create an ssh key:
```
ssh-keygen -t ed25519 -C "ansible"
``` 
Then, copy the public key to the server, where you want to install the nextcloud instance:
```
ssh-copy-id -i .ssh/ansible.pub <username>@<server_ip>
```
Then, in the `inventory` file, change the `ansible_user` field to the user on the server.  
You should also change the `mysql_root_password` and the `nextcloud_db_password` to a more secure one. 
Change the server's ip in the `nextcloud_servers` section.

In the `ansible.cfg` file, change the `remote_user` field to the username on the server.
Finally, run:
ansible-playbook --ask-become-pass site.yml

This will set everything up and you can access your nextcloud server at the IP address of the server.

To create an SSL certificate, run on the server:
```bash
sudo add-apt-repository ppa:certbot/certbot
sudo certbot --apache -d <domain> 
```
