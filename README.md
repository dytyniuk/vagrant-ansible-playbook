# Ansible playbook for CentOS 7

This repository contains an Ansible playbook to bootstrap Vagrant box as a local development environment.

Playbook has been tested on [centos/7](https://app.vagrantup.com/centos/boxes/7) Vagrant box.

## Roles
* *common* - installs a set of basic utilities
* *percona* - installs Percona Server for MySQL v5.7 with a set of additional tools for it
* *php* - installs PHP v7.1
* *nginx* - installs NGINX web server and alters it's configuration:
    * makes NGINX to work from `vagrant` user
    * sets `worker_processes` to `4`
    * sets `sendfile` to `off` to work properly with VirtualBox shared folders
    * sets default `server_name` to machine's hostname using `{{ ansible_nodename }}` variable
    * sets default `root` to `/vagrant/www`

* *nginx-php-fpm* - installs PHP-FPM and configures NGINX to work with it