# How to run
First, define the remote host in hosts:

	[test-servers]
	192.168.56.11
	192.168.56.12

	[all:vars]
	ansible_ssh_user=vagrant
	ansible_ssh_pass=vagrant
	ansible_ssh_common_args='-o StrictHostKeyChecking=no'


execute ansible like below:

	ansible-playbook -i hosts simple-playbook.yml

# Ansible Install

The ansible in ubuntu default package is old:

	vagrant@master:~/ansible-test$ ansible --version
	ansible 2.5.1
	  config file = /etc/ansible/ansible.cfg
	  configured module search path = [u'/home/vagrant/.ansible/plugins/modules', u'/usr/share/ansible/plugins/modules']
	  ansible python module location = /usr/lib/python2.7/dist-packages/ansible
	  executable location = /usr/bin/ansible
	  python version = 2.7.15+ (default, Nov 27 2018, 23:36:35) [GCC 7.3.0]

So, remove the old package:

	$ sudo apt remove ansible

Install the [new version](https://docs.ansible.com/ansible/2.9_ja/installation_guide/intro_installation.html#ubuntu-ansible):

	$ sudo apt update
	$ sudo apt install software-properties-common
	$ sudo apt-add-repository --yes --update ppa:ansible/ansible
	$ sudo apt install ansible

Check the new version:

	vagrant@master:~/ansible-test$ ansible --version
	ansible 2.9.27
	  config file = /etc/ansible/ansible.cfg
	  configured module search path = [u'/home/vagrant/.ansible/plugins/modules', u'/usr/share/ansible/plugins/modules']
	  ansible python module location = /usr/lib/python2.7/dist-packages/ansible
	  executable location = /usr/bin/ansible
	  python version = 2.7.15+ (default, Nov 27 2018, 23:36:35) [GCC 7.3.0]

You can use `ansible-galaxy` as well:

	vagrant@master:~/ansible-test$ ansible-galaxy collection install community.general
	Process install dependency map
	Starting collection install process
	Installing 'community.general:7.4.0' to '/home/vagrant/.ansible/collections/ansible_collections/community/general'

