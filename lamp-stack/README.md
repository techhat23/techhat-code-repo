Building a LAMP stack using Ansible Playbooks.
-------------------------------------------

These playbooks require Ansible 1.9.

This LAMP stack can be on a single node or multiple nodes. The inventory file
'hosts' defines the nodes in which the stacks should be configured.

        [webservers]
        appserver01

        [dbservers]
        database01

Here the webserver would be configured on a server called "appserver01" and the dbserver on a
server called "database01".

Before running install the Ansible Galaxy roles using `ansible-galaxy`:

		ansible-galaxy --roles-path galaxy-roles/ install -r requirements.yml

On setting up a brand new server, the stack can be deployed using the following command:
		
		ansible-playbook -i inventories/production/hosts site.yml -e 'first_run=1' -k

Upon subsequent runs, the stack can be deployed / updated using the following command:

		ansible-playbook -i inventories/production/hosts site.yml
