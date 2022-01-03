+++
chapter = false
title = "Ansible"
weight = 5
+++

# Ansible notes

## basic concepts
- *Control Node* is any machine with Ansible installed
- *Managed Node* is any machine controlled with Ansible
- *Inventory* is a list of all managed nodes, with options for grouping
- *Collection* distribution format for content, can include playbooks, roles,
modules and plugins. Collections are installed through Ansible Galaxy
- *Modules* are the units of code that ansible executes
- *Tasks* are the unit of Actions in Ansible
- *Playbook* is an ordered list of tasks

## Inventory
Inventory is a grouped list of managed nodes / hosts,
typically `ini` or `yaml` file. ini example:
```
mail.example.com

[webservers]
foo.example.com
bar.example.com

[dbservers]
one.example.com
two.example.com
three.example.com
```
- default path for inventory is `/etc/ansible/hosts`
- alternative inventory file can be given with `-i` flag

## Basic command
`ansible [pattern] -m [module] -a "[module options]"`

- default module is the `command` module
- this is the ad-hoc way to issue commands (as opposed to playbooks)

## Playbooks
- offer repeatable, reusable, simple configuration management
- expressed in `yaml` files
- playbook consists of multiple 'plays', each of which executes a series of tasks
- each task calls an ansible module
- playbook runs from top to bottom
- playbooks are run with `ansible-playbook` command

## Roles

## Modules in `ansible.builtin` collection
- `template`
- `copy` to copy files, and `fetch` to copy to local machine
- `file` to manage or change owner and file permissions 
- `yum` or others to manage packages
- `user` to manage users
- `service` to manage state of services
- `setup` module to gather facts about the systems

