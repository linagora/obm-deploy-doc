
Inventory file allows you to describe your OBM infrastructure.

For more informations about inventory files, please refer to [Ansible's dedicated documentation].

-----------------------------
<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](http://doctoc.herokuapp.com/)*

  - [](#)
  - [](#-1)
- [obmfull-example inventory file](#obmfull-example-inventory-file)
  - [Quick introduction](#quick-introduction)
  - [First steps of customization](#first-steps-of-customization)
- [More advanced customization](#more-advanced-customization)
  - [Nested groups](#nested-groups)
  - [Ansible limitation in nested groups](#ansible-limitation-in-nested-groups)
  - [Focus on groups](#focus-on-groups)
  - [Advanced example](#advanced-example)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

-----------------------------

obmfull-example inventory file
==========================

This inventory is provided has an example of how to deploy OBM on a single host.

Quick introduction
-------------------------

Let's take a look at the first part of the file :

```.bash
#
# OBM-Full example inventory file
#

[obmfullservers]
obm.example.com

[directoryservers]
[certservers]
[nosqlservers]
[dbservers]
[webservers]
[javaservers]
[cyrusmupdateservers]
[cyrusbackservers]
[cyrusfrontservers]
[smtpservers]
```

Has you probably know if you've read [Ansible's dedicated documentation], inventory files are a kind of INI files where you can find groups between brackets and hosts.

This example inventory allows you to deploy a single OBM hosts supporting all services by simply replacing obm.example.com by your own hostname in obmfull group.

First steps of customization
-------------------------------------

As you can see, there are other groups with no hosts in the part of the file.

You can use them to split your deployment into more than one remote host.

For example, you can store your database on a separated server as below :

```.bash
#
# Customized example inventory file with separated database server
#

[obmfullservers]

[directoryservers]
obm.example.com

[certservers]
obm.example.com

[nosqlservers]
obm.example.com

[dbservers]
database.example.com

[webservers]
obm.example.com

[javaservers]
obm.example.com

[cyrusmupdateservers]

[cyrusbackservers]
obm.example.com

[cyrusfrontservers]

[smtpservers]
obm.example.com
```

That's all. Pay attention to not update the second part of file. It will be explained later.

*cyrusmupdateservers* and *cyrusfrontendservers* aren't required unless you want to deploy a Cyrus cluster.

You can now launch your deployment as usual :

```.bash
$ ansible-playbook -i customized-example obm.yml
```

More advanced customization
=========================

While the first part of the file is provided to simplify your life, the second part is where the magic happens.

Nested groups
-------------------

Groups in the second part are the most important ones. Only them are associated with roles

In the obmfull-example inventory file, they are composed of nested groups from the first part.

`obmfullservers` group is contained in all of them, this is why you can install all the services on a single host using it.

A `parent` group is identified by the `:children` suffix after its name.

Ansible limitation in nested groups
-----------------------------------------------

The problem is you need to choose between groups of hosts or groups of groups.

Indeed, a group can't contain other groups and hosts.

To deploy a fine tuned distributed OBM infrastructure you'll need to rewrite the second part putting host names in all the groups.

Focus on groups
----------------------

Some of the second part groups must contain only one host but in other, you can put more of them.

To see a detailed list of all roles and their corresponding groups, please refer to [roles reference].

Advanced example
-------------------------

Here is a common example of distributed installation for large deployments :

```.bash
# Distributed inventory example

[caservers]
ldap.example.com

[autoconfservers]
java.example.com

[databaseservers]
db.example.com

[ldapservers:children]
ldap.example.com

[uiservers]
obm-ui.example.com

[webmailservers]
obm-ui.example.com

[syncservers]
obm-sync.example.com

[solrservers]
java.example.com

[cassandraservers]
cassandra1.example.com
cassandra2.example.com
cassandra3.example.com

[opushservers]
opush.example.com

[spushnikservers]
java.example.com

[cyrusmurderservers]
cyrus-murder.example.com

[cyrusfrontendservers]
cyrus-front1.example.com
cyrus-front2.example.com

[cyrusbackendservers]
cyrus-back1.example.com
cyrus-back2.example.com

[postfixservers]
smtp1.example.com
smtp2.example.com
```

> Written with [StackEdit](https://stackedit.io/).

[Ansible's dedicated documentation]: http://docs.ansible.com/intro_inventory.html "Inventory on docs.ansible.com"

[roles reference]: ../roles.md "Roles reference"
