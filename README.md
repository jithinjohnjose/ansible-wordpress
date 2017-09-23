                              How To Automate Installing WordPress on Ubuntu 16.04 Using Ansible

Introduction:

Ansible is a simple, agentless way to automate your infrastructure. If you find yourself deploying WordPress over and over again, Ansible could save you a lot of time.

With a few lines of YAML (a straighforward markup language), we will automate the typically tedious process of setting up WordPress on a fresh Ubuntu 14.04 server. We will install WordPress more or less according to the process outlined in this tutorial, but automatically.

We will use two servers: A build server running Ansible, and a target server on which we will install WordPress using Ansible.

Prerequisites:

1) In order to complete this tutorial, you will need to have the following set up:

2) A build server running Ubuntu 14.04. We will install Ansible on this server (referred to in this tutorial as the build-server). We will log into this server, and all the files and commands for this tutorial will be run on this server. A target server running Ubuntu 16.04. We will install WordPress (via Ansible) on this server (referred to in this tutorial as the wordpress-server)

3) Sudo non-root users configured for both servers

4) Add the SSH key of your build-server sudo user to your wordpress-server's sudo user's authorized_keys. You can set this up by following this tutorial. You should run the tutorial from your build-server and upload the key to your wordpress-server

                                        " Things to done before installation"

1) Edit hosts and update following

nano ~/ansible-wordpress/hosts

[wordpress]

wordpress_server_ip 

[wordpress:vars]

ansible_ssh_user=root

ansible_python_interpreter=/usr/bin/python  


2) Add mysql password, wordpress user, wordpress db name and wordpress password in 

nano ~/ansible-wordpress/roles/mysql/defaults/main.yml

---
mysql_root_password: your mysql password

wp_db_user: wordpress

wp_db_password: wordpress

wp_db_name: wordpress


3) again add wordpress user, wordpress db name and wordpress password in

nano ~/ansible-wordpress/roles/wordpress/defaults/main.yml

---
wp_db_user: wordpress

wp_db_password: wordpress

wp_db_name: wordpress
