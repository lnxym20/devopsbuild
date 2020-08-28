# devopsbuild
My personal linux devops build

This is a project to build Centos VMs as developer machines. 

The original project was based on the following platforms:

   - Windows 10 Pro
   - Hyper-V
   - Vagrant 2.27
   - Git Bash

I assume you know how to install the above tools on top of Windows 10 Pro.

This branch is for Hyper-V with file and shell provisioning.

This project was a learning exercise for myself to use Vagrant, Hyper-V and Anisble to create a Centos VM with my DevOps toolkit.

# What is in the VM?

* Centos 7 (Vagrant image)
* terraform
* vault
* git
* jq
* packer
* kubectl
* docker-ce
* docker-compose
* awscli

# How to use ths project

* clone this project to using Git bash to your computer
* cd into your repo directory

## Setup your local account on the VM

* generate a ssh key for you user_ssh_key file 

`ssh-keygen`

* copy the .pub file into provisioning/roles/create-local-user/files/

`cp ~/.ssh/id-rsa.pub  provisioning/roles/create-local-user/files/`

* edit the provisioning/group_vars/all to set your user_acc (e.g. user1) and user_ssh_key filename (the one you just copied into files/)

Note: there is a demo rsa key files in the provisioning/roles/create-local-user/files/ You should remove these.

## Create the VM

* Run vagrant up

`vagrant up`

## Login for the first time

The default SSH port setup by vagrant is 2222, but you can check by running:

`vagrant port`

Login to your server using the account you entered earlier,

`ssh -p 2222 -i ./provisioning/roles/create-local-user/files/demo_id_rsa  user1@localhost`

You can still use the default vagrant account,

`vagrant ssh`

