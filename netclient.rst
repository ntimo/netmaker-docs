================================
Netclient Setup
================================

The Netclient manages WireGuard on client devices (nodes). This document walks through setting up the netclient on machines, including install, management, and uninstall.

The netclient is supported on the following operating systems:
- Linux (most distributions)
- Windows
- Mac
- FreeBSD

For unsupported devices, please use the external client, wich is just a static, vanilla, WireGuard configuration file, which can be added to any device that supports WireGuard.

******************
Installation
******************


Before adding the machine to a network, the netclient must be installed. A successful installation sets up the netclient executable on the machine and adds it as a system daemon. The daemon will listen for changes for any network it joins.

The client install **does not** add the client as a member of any network. Once the client is installed, you must run:

.. code-block::

  netclient join -t <token>

The following are install instructions for most operating systems.

Linux
=============

Debian Distros (debian/ubuntu/mint/pop-os)
------------------------------------------------------

.. code-block::

  curl -sL 'https://apt.netmaker.org/gpg.key' | sudo tee /etc/apt/trusted.gpg.d/netclient.asc
  curl -sL 'https://apt.netmaker.org/debian.deb.txt' | sudo tee /etc/apt/sources.list.d/netclient.list
  sudo apt update
  sudo apt install netclient


Red Hat Distros (fedora/redhat/centos/rocky)
---------------------------------------------------------------------

.. code-block::

  curl -sL 'https://rpm.netmaker.org/gpg.key' | sudo tee /tmp/gpg.key
  curl -sL 'https://rpm.netmaker.org/netclient-repo' | sudo tee /etc/yum.repos.d/netclient.repo
  sudo rpm --import /tmp/gpg.key
  sudo dnf check-update
  sudo dnf install netclient

Arch Distros (arch/manjaro/endeavouros)
------------------------------------------------

.. code-block::

  yay -S netclient

Windows
===============

Installer: <installer link coming soon>

Mac
============

Brew Install
---------------

.. code-block::

  brew tap gravitl/netclient
  (optional) brew audit netclient
  brew install netclient

Installer
---------------

Installer: <installer link coming soon>

FreeBSD
=============

A FreeBSD package is coming soon. In the meantime, please use this install script:

.. code-block::

  curl -sfL https://raw.githubusercontent.com/gravitl/netmaker/master/scripts/netclient-install.sh | VERSION="<your netmaker version>" sh -


******************
Joining a Network
******************

.. code-block::

  netclient join -t <token>

Use the -vvv flag if installation fails and report logs.

*********************
Managing Netclient
*********************

Leave a network:

.. code-block::

  netclient leave -n network


******************
Uninstalling
******************

Leave a network:

First, uninstall from CLI:

.. code-block::

  netclient uninstall

Then, Uninstall from system (use equivalent command for your OS):

.. code-block::

  apt remove netclient
