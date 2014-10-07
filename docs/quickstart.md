
This documentation makes the assumption that your shell is located to the directory where you cloned obm-deploy repository.

Also, regarding to the installation method you use, your virtualhost must be activated.

-----------------------------

[TOC]

-----------------------------

Prerequisites
===========

Root access
---------------

OBM-Deploy uses SSH to connect to remote hosts using root account.

This is a prerequisite but we will try to allow remove this need in the future.

So, ensure that you can connect to your remote hosts as root before trying to run OBM-Deploy.

Host names resolving
----------------------------

Another constraint is that OBM-Deploy needs to be able to resolve host names.

So, you need to add all your remote hosts with their IP addresses in your /etc/hosts file or add them in your DNS server.

SSH connection without a key pair
----------------------------------------------

OBM-Deploy needs, if you want to do a full unattended deployment, that your SSH public key has been added to /root/.ssh/authorized_keys.

It is also possible to authenticate using a password but you need to do two things :

 - Add this option in ansible.cfg :

```.bash
ask_pass = True
```

 - Add this configuration in /home/*your_username*/.ssh/config file :

```.bash
Host your_remote_host
    PubkeyAuthentication no
```

Sudo usage
---------------

Sudo usage has been disabled in obm-deploy for the moment.

We will probably reintroduce it in the future.

OBM-Deploy usage
================

Installing an obm-full (all services on the same host)
----------------------------------------------------------------------

If you have an already running remote hosts or a VM on your desktop, you can directly use the obmfull-example inventory provided by OBM-Deploy.

The only thing you need to do is to replace obm.example.com with your hostname in the file.

Then, you can make your first automated deployment :

```.bash
$ ansible-playbook -i obmfull-example obm.yml
```

> Written with [StackEdit](https://stackedit.io/).