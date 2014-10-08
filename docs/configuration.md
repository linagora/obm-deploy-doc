Ansible brought to OBM-Deploy the ability to be configured in many ways to perfectly fit to your needs.

OBM-Deploy uses a large amount of configuration files but don't panic, they are organized is such a manner that makes it easy to understand.

To learn more about Ansible variables precedence, please refer to the [dedicated documentation](http://docs.ansible.com/playbooks_variables.html#variable-precedence-where-should-i-put-a-variable "Variables precedence on docs.ansible.com").

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Global configuration](#global-configuration)
- [Specific configuration](#specific-configuration)
  - [Group specific configuration](#group-specific-configuration)
  - [Host specific configuration](#host-specific-configuration)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

<a name="global-configuration"></a>

Global configuration
=================

Global configuration is done in config.yml.

OBM-Deploy can work with an empty config.yml, default values are stored in group_vars/all.

Variables in this file are used by all hosts unless you override them using group or host specific configuration.

<a name="specific-configuration"></a>

Specific configuration
==================

Role specific default configuration, if applicable, is stored in roles/*role_name*/vars/main.yml file.

As a user, you never have to edit this files but each default global or role variable can be overridden on per-host or a per-group basis.

<a name="group-specific-configuration"></a>

Group specific configuration
-------------------------------------

In the group_vars/*group_name*.yml file, you can override some variables for the related group.

<a name="host-specific-configuration"></a>

Host specific configuration
-----------------------------------

In the host_vars/*host_name*.yml file, you can override some variables for the related host.

[dedicated documentation]: http://docs.ansible.com/playbooks_variables.html#variable-precedence-where-should-i-put-a-variable "Variables precedence on docs.ansible.com"
