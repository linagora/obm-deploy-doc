
Ansible is a tool to automate tasks execution on remote hosts.

#### Table of contents

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Ansible documentation](#ansible-documentation)
  - [YAML Syntax](#yaml-syntax)
  - [Jinja2 Templates](#jinja2-templates)
  - [Official documentation](#official-documentation)
- [Ansible terminology](#ansible-terminology)
  - [Inventory](#inventory)
  - [Module](#module)
  - [Task](#task)
  - [Role](#role)
  - [Playbook](#playbook)
  - [Handler](#handler)
  - [Variable](#variable)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Ansible documentation
===================

YAML Syntax
----------------

[YAML syntax] is used everywhere in Ansible.

Jinja2 Templates
---------------------

[Jinja2 engine] is used for templating.

Official documentation
-----------------------------

[Ansible official documentation] is a good place to start.

Ansible terminology
=================

Inventory
------------

An [inventory] defines all your hosts and groups.

Module
---------

A [module] abstracts an action to run on remote hosts like file copy or package installation.
Here is a list of [available modules].

Task
-----

A [task] uses an Ansible [module] to define an atomic action to run on remote hosts.

Role
-----

A [role] regroups a set of related tasks.

Playbook
------------

A [playbook] associates hosts or groups of hosts to corresponding roles.

Handler
----------

An  [handler] is a special task within a role not run directly but triggered by other tasks.

Variable
----------

Do I really need to define what is a [variable] ?

> Written with [StackEdit](https://stackedit.io/).

[YAML syntax]: http://docs.ansible.com/YAMLSyntax.html "YAML syntax on docs.ansible.com"

[Jinja2 engine]: http://docs.ansible.com/playbooks_variables.html "Jinja2 engine on docs.ansible.com"

[Ansible official documentation]: http://docs.ansible.com "Ansible official documentation on docs.ansible.com"

[inventory]: http://docs.ansible.com/intro_inventory.html "Inventory on docs.ansible.com"

[module]: http://docs.ansible.com/modules.html "Modules on docs.ansible.com"

[available modules]: http://docs.ansible.com/modules_by_category.html "Available modules on docs.ansible.com"

[task]: http://docs.ansible.com/glossary.html#tasks

[role]: http://docs.ansible.com/playbook_rtoles.html "Role on docs.ansible.com"

[playbook]: http://docs.ansible.com/playbooks.html "Playbook on docs.ansible.com"

[handler]: http://docs.ansible.com/glossary.html#handlers "Handler on docs.ansible.com"

[variable]: http://docs.ansible.com/playbook_variables.html "Variable on docs.ansible.com"
