# Fruit-Basket-App

[![N|Solid](http://www.ansible.com/hubfs/2016_Images/Blog_Headers/Ansible-Docker-Blog-2.png)](https://nodesource.com/products/nsolid)

## Overview
allow us to deploy this container to multiple servers and environments.

## prerequisites 

Need to have read write and execution permission for the logged in user to the Ansible configuration server.
Need to have an editor tool (VIM , Nano etc..)

## Tested OS Version
Ubuntu Server 18.04 LTS 

Make sure to have git installed as Ansible in the controller server (Configuration Server)
```sh
sudo apt-add-repository ppa:ansible/ansible
```
Press ```ENTER ```when prompted to accept the PPA addition.

Next, refresh your system’s package index so that it is aware of the packages available in the newly included PPA:
```sh
sudo apt update
```
Following this update, you can install the Ansible software with:
```sh
sudo apt install ansible
```

Navigate to the ```/etc/ansible/ansible.cfg ``` file and place your PEM file location which contains the private key that can use acorss the nodes to establish the SSH connection.

Sample Config will like something like below

```sh
...
# if set, always use this private key file for authentication, same as
# if passing --private-key to ansible or ansible-playbook
private_key_file = /home/ubuntu/new/dasitha2.pem

# If set, configures the path to the Vault password file as an alternative to
# specifying --vault-password-file on the command line.
#vault_password_file = /path/to/vault_password_file
...
```


### Cloning the Ansible Playbook

Clone the application using the below command

```sh
git clone https://github.com/Dasithz/AnsiSimpleContainer.git
```
Navigate to the application folder 
```sh
cd AnsiSimpleContainer
```

Open the hosts file located under ``` AnsiSimpleContainer/production ``` for production use and add the IP addresses of the hosts that you whish to deploy this containerized application.

As same as above you can navigate to the ``` AnsiSimpleContainer/dev ``` and change the IP addresses of the hosts file for deployments to the lower level environments

Once All set you can run the below commands based on your environment to deploy the application

For Development environment deployment run;
```sh
ansible-playbook -i dev site.yml
```
For Production environment deployment 
```sh
ansible-playbook -i production site.yml
```
### Sample Out put

![Execution](https://github.com/Dasithz/AnsiSimpleContainer/blob/main/Images/Web_OutPut.PNG?raw=true)
