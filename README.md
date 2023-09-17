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
