# ansible-wp
A repo with examples of how can Ansible be used in order to automate WordPress day-to-day tasks. Related to talk: https://www.softwaretalks.io/v/9826/getting-more-done-in-less-time-wordcamp-singapore-2019

The repository contains really simple examples that are used in the talk above and its aim is to help peopel using WordPress get familiar with automating via Ansible, test different things and play around with some basic code to get used to it.

The content of the repo is really simple and basic, as it's aim is to be presented and used by people who haven't used Ansible before.

## Inventory

The inventory folder contains olny one "hosts" file which contains specific information for the servers that the Ansible playbooks will be executed on and specific variables realted to the roles for each server/system. This file is very specific for each user, so I've added to information there, jsut a dummy values to the variables. You will need to populate the file with the specific information about your system. Of course, it's not necessary to be ecaxtly 4 - that's just an example. 
The inventory folder contains olny one "hosts" file which contains specific information for the servers that the Ansible playbooks will be executed on and specific variables realted to the roles for each server/system. This file is very specific for each user, so I've added to information there, jsut a dummy values to the variables. You will need to populate the file with the specific information about your system. Of course, it's not necessary to be ecaxtly 4 - that's just an example.

## Roles

The roles folder contains all of the roles created so far which will be used in the playbooks

## Playbooks

The playbooks folder contains the actual playbooks that will be executed. An example of how an execution is triggered:

 ansible-playbook -c ssh -D -i $inventory_hosts $playbook_name.yml
 
 ### plugins.yml
 
The plugins.yml playbook is calling the manage_plugins role. --extra-vars need to be passed in oredr to identify what exactly you'd like the playbook to do. The vars are boolean and are:

plg_install

plg_activate

plg_deactivate

plg_delete

plg_update

plg_find

and plugin_name should be specified. 

So for example if you want to install the plugin 'random-plugin-name' your playbook should be invoke like that:

ansible-playbook -c ssh -D -i $inventory_hosts plugins.yml --extra-vars "plg_install=true plugin_name=random-plugin-name"
 
