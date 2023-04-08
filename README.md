# Install Wordpress using ansible 

### Establish Passwordless Authentication between ansible node and target node

### Generate ssh-key pair
```
ssh-keygen -t rsa -b 4096 -C "email@mail.com"
```
### copy-ssh-key

```
ssh-copy-id user@target-node-ip
```

### ssh-to-target-wordpress-server
```
	ssh user@target-node-ip
```
	
### disable password authentication
```
sudo nano /etc/ssh/sshd_config
```
### Uncomment and Change PasswordAuthentication Yes to no
``` PasswordAuthentication no ```
```
sudo systemctl reload ssh
```
## Install Ansible

```
sudo apt-add-repository ppa:ansible/ansible

sudo apt update

sudo apt install ansible

ansible –version
```

### Add wordpress node to Ansible hosts 
```
sudo nano /etc/ansible/hosts
```
```
[wordpress]
1.2.3.4

```

### Ping wordpress node from Ansible Master node

```
ansible wordpress -m ping
```

## Run the Playbook
```
ansible-playbook -l wordpress -u root wp-playbook.yml
```

**************************
## This Script will install LAMP Stack, configure Apache2, and install wordpress.
## vars.yml contains all the variable such as user, host, sql password, etc.  
## apache.conf.j2 jinja template to configure apache2
## wp-config.php.j2 for wordpress config
## wp-playbook.yml file contains the IaC script

