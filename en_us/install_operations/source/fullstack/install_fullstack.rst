.. _Installing Open edX Fullstack:

####################################
Installing Open edX Fullstack
####################################

This section describes how to install the Open edX fullstack.

.. contents::
   :local:
   :depth: 1

**********
Overview
**********

Open edX fullstack is a Vagrant instance designed for deploying all Open edX
services on a single server.

See the `Vagrant documentation`_ for more information.

********************
Components
********************

Open edX fullstack includes the following edX components.

* The Learning Management System (LMS).
* EdX Studio.
* XQueue, the queuing server that uses `RabbitMQ`_ for external graders.
* Discussion Forums.
* Open Response Assessor (ORA).
* `Discern`_, the machine-learning-based automated textual classification API
  service.
* `Ease`_, a library for the classification of textual content.

**************************
Knowledge Prerequisites
**************************

To use fullstack, you should meet the following knowledge requirements.

* Understand basic terminal usage. If you are using a Mac computer, see
  `Introduction to the Mac OS X Command Line`_. If you are using a Windows
  computer, see `Windows Command Line Reference`_.

* Understand Vagrant commands. See the `Vagrant Getting Started`_ guide for
  more information.

**************************
Software Prerequisites
**************************

To install and run Open edX fullstack, you must first install the following
software.

* `VirtualBox`_ 4.3.12 or higher

* `Vagrant`_ 1.6.5 or higher

* A Network File System (NFS) client, if your operating system does not include
  one. Fullstack uses VirtualBox Guest Editions to share folders through NFS.

.. _Install Open edX Fullstack:

*********************************
Install Open edX Fullstack
*********************************

To install Open edX fullstack directly from the command line, follow the
instructions below.

Before beginning the installation, ensure that you have your local computer's
administrator's password. The password is needed so that NFS can be set up to
allow users to access code directories directly from your computer.

#. Ensure the ``nfsd`` client is running.

#. Create the ``fullstack`` directory and navigate to it in the command prompt.

   .. code-block:: bash

     mkdir fullstack
     cd fullstack

#. Download the fullstack Vagrant file.

   .. code-block:: bash

     curl -L https://raw.githubusercontent.com/edx/configuration/master/vagrant/release/fullstack/Vagrantfile > Vagrantfile

#. Install the Vagrant ``hostsupdater`` plugin.

   .. code-block:: bash

     vagrant plugin install vagrant-hostsupdater

#. Create the fullstack virtual machine.

   .. code-block:: bash

     vagrant up

   The first time you create the fullstack virtual machine, Vagrant downloads
   the base box, which has a file size of about 4GB. If you destroy and
   recreate the virtual machine, Vagrant re-uses the box it downloaded. See
   `Vagrant's documentation on boxes`_ for more information.

#. When prompted, enter the administrator password for your local computer.

**********************************************
Browser Login to Open edX Fullstack
**********************************************

In your browser, go to ``preview.localhost``, which is an alias entry for
192.168.33.10 that was created in your ``/etc/hosts`` file.

The latest version of fullstack is preloaded with the demonstration course and
the same set of :ref:`default user accounts<Default Accounts on Devstack>` that
is created for devstack.

.. include:: ../../../links/links.rst
