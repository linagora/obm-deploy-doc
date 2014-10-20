
Inventory file allow to describe your OBM infrastructure.

For more information about inventory files, please refer to [Ansible's dedicated documentation](http://docs.ansible.com/intro_inventory.html "Inventory on docs.ansible.com").

#### Table of contents

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [obmfull-example inventory file](#obmfull-example-inventory-file)
  - [Quick introduction](#quick-introduction)
  - [First customization steps](#first-customization-steps)
- [More advanced customization](#more-advanced-customization)
  - [Nested groups](#nested-groups)
  - [Ansible limitation in nested groups](#ansible-limitation-in-nested-groups)
  - [Focus on groups](#focus-on-groups)
  - [Advanced example](#advanced-example)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

<a name="obmfull-example-inventory-file"></a>

obmfull-example inventory file
==========================

This inventory is provided as an example of how to deploy OBM on a single host.

<a name="quick-introduction"></a>

Quick introduction
-------------------------

Let's take a look at the first part of the file :

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

As you probably know if you've read [Ansible's dedicated documentation](http://docs.ansible.com/intro_inventory.html "Inventory on docs.ansible.com"), inventory files are a kind of INI files where you can find groups between brackets and hosts.

This example inventory allows you to deploy a single OBM host supporting all services by simply replacing obm.example.com by your own hostname in obmfull group.

<a name="first-customization-steps"></a>

First customization steps
-------------------------------------

As you can see, there are other groups with no hosts in this part of the file.

You can use them to split your deployment into more than one remote host.

For example, you can store your database on a separate server as below :

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

That's all. Pay attention to not update the second part of file. It will be explained later.

*cyrusmupdateservers* and *cyrusfrontendservers* aren't required unless you want to deploy a Cyrus cluster.

You can now launch your deployment as usual :

    $ ansible-playbook -i customized-example obm.yml

<a name="more-advanced-customization"></a>

More advanced customization
=========================

While the first part of the file is provided to simplify your life, the second part is where the magic happens.

<a name="nested-groups"></a>

Nested groups
-------------------

The groups in the second part are the most important ones. Only them are associated with roles

In the obmfull-example inventory file, they are composed of nested groups from the first part.

`obmfullservers` group is contained in all of them, this is why you can install all the services on a single host using it.

A `parent` group is identified by the `:children` suffix after its name.

<a name="ansible-limitation-in-nested-groups"></a>

Ansible limitation in nested groups
-----------------------------------------------

The problem is you need to choose between groups of hosts or groups of groups.

Indeed, a group can't contain other groups and hosts.

To deploy a fine tuned distributed OBM infrastructure you'll need to rewrite the second part putting host names in all the groups.

<a name="focus-on-groups"></a>

Focus on groups
----------------------

Some of the groups in the second part must contain only one host but in other, you can put more of them.

To see a detailed list of all roles and their corresponding groups, please refer to [roles reference](./roles.md "Roles reference").

<a name="advanced-example"></a>

Advanced example
-------------------------

Here is a common example of distributed installation for large deployments :

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
