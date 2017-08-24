Rocannon
=========

[![Build Status](https://travis-ci.org/ilbonzo/Rocannon.svg?branch=master)](https://travis-ci.org/ilbonzo/Rocannon)

This is `Ansible` playbook for workshop to learn ansible.
http://magni.me/Introduction-to-DevOps-with-Ansible

The project build a three tier  architecture:

 * Nginx loadbalancer
 * Apache web server
 * Mysql database

For testing playbook you can use vagrant with multimachine configuration.

Vagrantfile is configured to create one loadbalancer, two webserver and one database

## run project
```
$ git clone https://github.com/ilbonzo/Rocannon.git
$ cd Rocannon
$ vagrant up
```

## run project with docker
```
$ git clone https://github.com/ilbonzo/Rocannon.git
$ cd Rocannon
$ docker-compose up --build
```



