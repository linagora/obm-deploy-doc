
This documentation is based on [Oliver Welge's article].

Manual installations methods are to work with almost all Linux or BSD flavors, including OSX.

We recommend you to choose a manual installation strategy even if this is a little bit difficult.

-----------------------------

[TOC]

-----------------------------

Common packages for all methods
============================

First of all, you need to install git.

Install common packages on Debian GNU/Linux Wheezy
---------------------------------------------------------------------------

*This step should also works on other .deb based distros (Ubuntu, Mint ...).*

```.bash
$ sudo aptitude install git python-dev wget
```

Install common packages on CentOS Linux 6
-----------------------------------------------------------

*This step should also works other .rpm based distros (Fedora, Mandriva ...).*

```.bash
$ sudo yum install git python-devel wget
```

Packages based installation
=======================

Currently, only dependencies can be installed using packages.

This is why everyone needs git to obtain obm-deploy sources.

Packages installation on Debian GNU/Linux Wheezy
---------------------------------------------------------------------

### Enable Wheezy Backports

*This step is not needed on other .deb based distros (Ubuntu, Mint ...).*

```.bash
$ sudo su -c "echo 'deb http://http.debian.net/debian wheezy-backports main' >> /etc/apt/sources.list"
```

### Install packages

*This step should also works on other .deb based distros (Ubuntu, Mint ...).*

```.bash
$ sudo aptitude install ansible
```

Packages installation on CentOS Linux 6
-----------------------------------------------------

### Enable EPEL repository

*This step is not needed on other .rpm based distros (Fedora, Mandriva ...).*

```.bash
$ sudo yum install wget
$ wget http://dl.fedoraproject.org/pub/epel/6/`uname -m`/epel-release-6.8.noarch.rpm
$ sudo rpm -Uvh epel-release-6.8.noarch.rpm
```

### Install packages

*This step should also works on other .rpm based distros (Fedora, Mandriva ...).*

```.bash
$ sudo yum install ansible
```

Common prerequisites for manual methods
====================================

Install prerequisites on Debian GNU/Linux Wheezy
--------------------------------------------------------------------

### Enable Wheezy Backports

*This step is not needed on other .deb based distros (Ubuntu, Mint ...).*

```.bash
$ sudo su -c "echo 'deb http://http.debian.net/debian wheezy-backports main' >> /etc/apt/sources.list"
```

### Install packages

*This step should also works on .deb based distros (Debian, Mint ...).*

```.bash
$ sudo aptitude install python-virtualenv python-pip
```

Install prerequisites on CentOS Linux 6
----------------------------------------------------

### Enable EPEL repository

*This step is not needed on other .rpm based distros (Fedora, Mandriva ...).*

```.bash
$ sudo yum install wget
$ wget http://dl.fedoraproject.org/pub/epel/6/`uname -m`/epel-release-6.8.noarch.rpm
$ sudo rpm -Uvh epel-release-6.8.noarch.rpm
```

### Install packages

*This step should also works on other .rpm based distros (Fedora, Mandriva ...).*

```.bash
$ sudo yum install python-virtualenv python-pip
```

Manual installation using PIP and virtualenv
=====================================

Clone OBM-Deploy GIT repository
--------------------------------------------

```.bash
$ git clone https://github.com/linagora/obm-deploy
```

Create a Python virtualenv in obm-deploy directory
--------------------------------------------------------------------

```.bash
$ cd obm-deploy
$ virtualenv --no-site-packages obm-deploy-env
```

Activate your virtualenv
--------------------------------

```.bash
$ source obm-deploy-env/bin/activate
```

Install dependencies into your virtualenv
-------------------------------------------------------

```.bash
$ pip install paramiko PyYAML jinja2 pyasn1 pycrypto python-keyczar==0.71b
```

Clone Ansible GIT repository
--------------------------------------

```.bash
$ git clone https://github.com/ansible/ansible -b release1.7.2
```

Activate Ansible environment
----------------------------------------

```.bash
$ source ansible/hacking/env-setup
```

Exit from your virtualenv
---------------------------------

```.bash
$ deactivate
```

Each time you want to work with OBM-Deploy
-------------------------------------------------------------

```.bash
$ cd obm-deploy
$ source obm-deploy-env/bin/activate
$ source ansible/hacking/env-setup
```

Manual installation using virtualenvwrapper (recommended)
==================================================

Install virtualenvwrapper on Debian GNU/Linux Wheezy
---------------------------------------------------------------------------

*This step should also works on other .deb based distros (Ubuntu, Mint ...).*

```.bash
$ sudo aptitude install virtualenvwrapper
```

Install virtualenvwrapper on CentOS Linux 6
-------------------------------------------------------------

*This step should also works on other .rpm based distros (Fedora, Mandriva ...).*

```.bash
$ yum install python-virtualenvwrapper
```

Clone OBM-Deploy GIT repository
---------------------------------------------

```.bash
$ git clone https://github.com/linagora/obm-deploy
```

Create a Python virtualenv in obm-deploy directory
--------------------------------------------------------------------

```.bash
$ cd obm-deploy
$ mkvirtualenv -p /usr/bin/python2 --no-site-packages obm-deploy-env
```

Activate your virtualenv
--------------------------------

```.bash
$ workon obm-deploy-env
```

Install dependencies into your virtualenv
-------------------------------------------------------

```.bash
$ pip install paramiko PyYAML jinja2 pyasn1 pycrypto python-keyczar==0.71b
```

Clone Ansible GIT repository
--------------------------------------

```.bash
$ git clone https://github.com/ansible/ansible -b release1.7.2
```

Activate Ansible environment
----------------------------------------

```.bash
$ source ansible/hacking/env-setup
```

Activate Ansible auto-setup in your virtualenv
-------------------------------------------------------------

```.bash
$ cat > ~/.virtualenvs/obm-deploy-env/bin/postactivate << EOF
#!/bin/bash
cd $(pwd)
source ansible/hacking/env-setup
EOF
$ chmod +x ~/.virtualenvs/obm-deploy-env/bin/postactivate
```

Exit from your virtualenv
---------------------------------

```.bash
$ deactivate
```

Each time you want to work with OBM-Deploy
-------------------------------------------------------------

```.bash
$ workon obm-deploy-env
```

> Written with [StackEdit](https://stackedit.io/).

[Oliver Welge's article]: http://weluse.de/blog/installing-ansible-on-os-x.html "Oliver Welge's article about Ansible installation"