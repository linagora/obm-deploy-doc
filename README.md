
Ansible based Open Business Management (**[OBM]**) full-featured deployment tool.

*OBM Installations made easy !*

-----------------------------

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [OBM-Deploy project](#obm-deploy-project)
  - [Objectives](#objectives)
  - [Current Status](#current-status)
  - [Disclaimer](#disclaimer)
  - [Need Help](#need-help)
- [Documentation](#documentation)
  - [About ansible](#about-ansible)
  - [Installation](#installation)
  - [Quick start](#quick-start)
  - [Inventories](#inventories)
  - [Configuration](#configuration)
  - [Roles index](#roles-index)
  - [Mirror Mode](#mirror-mode)
- [Development](#development)
  - [Roadmap](#roadmap)
  - [Get involved](#get-involved)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

-----------------------------

OBM-Deploy project
=================

Objectives
--------------

 - Quickly build deployment environments
 - Standardize OBM installations
 - Extract configuration management from packaging
 - Make deployments costless and more efficients

Current Status
-------------------

 - Centos 6 and RHEL 6 support
 - OBM 2.5 and OBM 3.0 branches
 - Support connectionless remote hosts
 - No clustering feature available yet

Disclaimer
--------------

OBM-Deploy automatically updates and sometimes overwrites your configuration files.
It's behavior is subject to change. Use it with caution, especially in production.
We discourage you to use it to update an already installed OBM infrastructure.
OBM-Deploy isn't included yet in Linagora's commercial support offers.

Need Help
--------------

Need help using obm-deploy ?
Use our **[mailing-list]** or our **[#obm IRC channel]** on freenode to ask your questions.

-----------------------------

Documentation
=============

About ansible
------------------

[About ansible](docs/ansible.md) : Become familiar with Ansible basic concepts

Installation
---------------

[Installation](docs/installation.md) : Instructions to install OBM-Deploy.

Quick start
---------------

[Quickstart](docs/quickstart.md) : Run your first deployment now.

Inventories
---------------

[Inventories](docs/inventories.md) : Construct more complex infrastructures.

Configuration
------------------

[Configuration](docs/configuration.md) : Learn how to fine-tune your deployment.

Roles index
---------------

[Roles](docs/roles.md) : Take a look under the hood.

Mirror Mode
----------------

[Mirror-mode](docs/mirror-mode.md) : Deploy remote nodes without Internet access.

-----------------------------

Development
===========

Roadmap
------------

[Roadmap](docs/roadmap.md) : What you can hope for the future.

Get involved
-----------------

[Contribute](docs/contribute.md) : Leave your own mark on the project.

-----------------------------

> Written with [StackEdit](https://stackedit.io/).

[OBM]: http://obm.org "The new generation of collaborative software"

[mailing-list]: http://obm.org/node/19 "OBM official mailing-list"

[#OBM irc channel]: http://irc.lc/freenode/obm/ "Webchat to official #obm channel on freenode"
