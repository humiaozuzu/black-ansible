# Black Ansible

playbooks and tasks to do server connection init and basic setup

## plays and roles included

### process

When you get new servers from your cloud computing provider, your get password or ssh key auth to servers.

```
# setup connection (auth by username and password)
ansible-playbook -i inventory/prod/hosts plays/init-connection.yml -u your-user -kK -l 'your-node'

# setup connection (auth by ssh key)
ansible-playbook -i inventory/prod/hosts plays/init-connection.yml -u your-user --private-key=~/.ssh/id_rsa -l 'your-node'

# when connection is initialized, you can run custom roles
ansible-playbook -i inventory/prod/hosts plays/setup-server.yml -l 'your-node'
```

### server connection init

- configure sudoer
- add system admin users and ssh key pairs
- configure ssh

### server setup related roles

- configure apt
- disable ipv6
- configure dns 
- configure hosts
- common settings
	- hostname
	- package upgrade
	- package install/remove
	- set default editor
- configure timezone
- configure locale
- configure ntp
- configure sysctl
- pin linux kernel
- manage iptables with ufw
- manage users and ssh keys (support host-level management)

## how to add to your existing ansible project

put it in `requirements.yml`

```
- src: https://github.com/humiaozuzu/ansible-role-server-setup
  name: humiaozuzu.server-setup
  version: master
```

 ## testing

All roles tested on ubuntu 14.04 and part are tested on 16.04

## TODO

- add config example
- seperate reboot role
- add missing default for roles

