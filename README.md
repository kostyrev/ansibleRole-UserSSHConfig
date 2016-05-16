UserSSHConfig
=========

Simple role to manage user's .ssh/config, by default the role won't make any changes unless "user_ssh_config" variable defined.

Currently the role support Host defenition for multiple users and multiple hosts per that user.


Role Variables
--------------

user_ssh_config (REQUIRED)


Example Playbook
----------------

Example play:
```
	- hosts: app-example-org
	  roles:
	   - User_ssh_config
```


Variable defenition can go to group_vars or host_vars.

group_vars/app-example-org.yml

```
	user_ssh_config:
	 - user: root
	   user_home: /
	   hosts:
		- {alias: "github.com-main", Hostname: "github.com", User: "git", IdentityFile: "awesome_key"}
	 - user: sponge
	   user_home: /home
	   hosts:
		- {alias: "gitlab.int-main", Hostname: "gitlab.local", User: "git", IdentityFile: "sponge_bob_rsa"}
		- {alias: "jumpbox", Hostname: "jumpbox.examlpe.org", User: "bill", IdentityFile: "bill_id_rsa", IdentitiesOnly: "yes"}
		- {alias: "node_behind_proxy", Hostname: "192.168.0.10", User: "star", IdentityFile: "StarKey", ProxyCommand:  "ssh -i ~/.ssh/ProxyKey star@myproxy.examlpe.org nc %h %p 2> /dev/null"}
```


Author Information
------------------

Tal Lannder

Tal@Pjili.com
