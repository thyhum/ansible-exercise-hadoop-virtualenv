<!-- TOC -->

- [1. Ansible Exercise](#1-ansible-exercise)
  - [1.1. Hadoop installation](#11-hadoop-installation)
  - [1.2. Virtualenv installation](#12-virtualenv-installation)
- [2. Inventories](#2-inventories)
  - [2.1. Running it on Vagrant and VirtualBox](#21-running-it-on-vagrant-and-virtualbox)
  - [2.2. Vagrant Plugin - vagrant-vbguest (Optional)](#22-vagrant-plugin---vagrant-vbguest-optional)
- [3. Example](#3-example)
  - [3.1. Git clone and bring up the VMs](#31-git-clone-and-bring-up-the-vms)
  - [3.2. Run the playbooks to the both VMs](#32-run-the-playbooks-to-the-both-vms)
  - [3.3. Run the playbooks to centos VM](#33-run-the-playbooks-to-centos-vm)

<!-- /TOC -->

# 1. Ansible Exercise

Ansible exercise for installing Apache Hadoop and Virtualenv

## 1.1. Hadoop installation

Ansible role to install Apache Hadoop standalone cluster, reference: https://hadoop.apache.org/docs/r3.0.3/hadoop-project-dist/hadoop-common/SingleCluster.html

The role is [roles/hadoop](roles/hadoop/)

## 1.2. Virtualenv installation

This role for installing Python VirtualEnv 

The role is [roles/virtualenv](roles/virtualenv/)

# 2. Inventories

You can add/delete more hosts and group_vars in [inventories/](inventories/) for multiple environments (eg. for vagrant/prod/uat/aws/gcp).

## 2.1. Running it on Vagrant and VirtualBox

There is a Vagrantfile containing CentOS and Ubuntu VMs, you need to have [Vagrant](https://www.vagrantup.com/) and [VirtualBox](https://www.virtualbox.org).

## 2.2. Vagrant Plugin - vagrant-vbguest (Optional)

You can install vagrant-vbguest to automate vbguest-tool on the VMs

$ vagrant plugin install vagrant-vbguest

# 3. Example

## 3.1. Git clone and bring up the VMs

$ git clone https://github.com/thyhum/ansible-exercise-hadoop-virtualenv.git  
$ cd ansible-exercise-hadoop-virtualenv  
$ vagrant up

## 3.2. Run the playbooks to the both VMs

$ ansible-playbook playbooks/01-hadoop.yml  
$ ansible-playbook playbooks/02-virtualenv.yml  

## 3.3. Run the playbooks to centos VM

$ ansible-playbook playbooks/01-hadoop.yml -l centos  
$ ansible-playbook playbooks/02-virtualenv.yml -l centos  

