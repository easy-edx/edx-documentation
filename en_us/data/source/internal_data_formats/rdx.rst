.. _Research Data Exchange:

######################
Research Data Exchange
######################

The edX research data exchange (RDX) program gives research teams at participating partner institutions the opportunity to obtain data from any edx.org course. Researchers must propose and be approved for a specific educational research project to receive data through this program. Before delivering the data, edX obfuscates personally identifying information (PII).  The data czar of the institution can then download the RDX package for the research team from the Amazon S3 storage service.

The topics in this section provide an overview of the data files that are included in an RDX package and the obfuscation process.

.. contents::
   :local:
   :depth: 1

For more information about joining the RDX program or proposing an educational
research project, see

.. TBD the partner portal

.. _RDX Files:

**********************
RDX Data Files
**********************

An RDX data package consists of files for one or more completed courses from
one or more participating partner instituitons. Both event data and database
data are included.

.. note:: In all file names, the date is in {YYYY}-{MM}-{DD} format.

RDX data files are located in different Amazon S3 buckets and folders than the data files for your organization's data package.

.. Differences in naming conventions, otherwise see :ref:`Data Package Contents`.

============
Event Data
============

The ``{org}-prod-events-{date}.log.gz.gpg`` file contains a daily log of
course events. A separate file is available for each course.

For a partner organization named UniversityX, these daily files are identified
by the organization name, the edx.org site name, and the date. For example,
``universityx-prod-events-2016-07-25.log.gz.gpg``.

.. For information about the contents of these files, see :ref:`Data Package Contents`.

==================
Database Data
==================

The ``{org}-{date}.zip`` file contains views on database tables. This file
includes data as of the time of the export, for one organization's
course or courses on the edx.org sites.

For a course at A participating organization named UniversityX, each weekly file is identified by
the organization name and its extraction date. For example,
``universityx-2016-10-27.zip``.

.. For information about the contents of this file, see :ref:`Data Package Contents`.

.. _Amazon S3 Buckets and Directories for RDX Data:

********************************************
Amazon S3 Buckets and Folders for RDX Data
********************************************

Data package files are located at the following Amazon S3 destinations:

* The ``s3://edx-course-data/{org}`` folder contains the daily
  ``{org}-prod-events-{date}.log.gz.gpg`` files of course event data.

* The ``s3://course-data`` bucket contains the weekly ``{org}-{date}.zip``
  database snapshot.

.. _Download Data Packages from Amazon S3:

*******************************************
Download an RDX Package from Amazon S3
*******************************************

Only the data czar at a participating partner institution can download an RDX
data package.

To download an RDX data package from the Amazon S3 storage service, follow
these steps.

.. note:: If you are using a third-party tool to connect to Amazon S3, you
    might not be able to navigate directly from the bucket that contains your
    organization's data and the RDX bucket. You might need to disconnect from
    Amazon S3 and then reconnect to the other destination.

#. Use the AWS Command Line Interface or a third-party tool to connect to the
   ``s3://edx-course-data/{org}`` folder on Amazon S3.

   For information about providing your credentials to connect to Amazon S3,
   see :ref:`Access Amazon S3`.

#. Navigate within ``s3://edx-course-data/{org}`` to locate the RDX folder.

   ``RDX? {org}/prod/events/{year}`` TBD

#. Download the ``RDX? {org}-{date}.zip`` database data file.

#. Download the compressed, encrypted ``RDX?
   {org}-prod-events-{date}.log.gz.gpg`` file.

.. _RDX Data Package Contents:

**************************
RDX Data Package Contents
**************************

Each of the files you download contains one or more files of research data.

.. Differences in naming conventions, otherwise see :ref:`Data Package Contents`.

================================================================
Extracted Contents of ``{org}-prod-events-{date}.log.gz.gpg``
================================================================

The ``{org}-prod-events-{date}.log.gz.gpg`` file contains all event data for
courses on a single edX site for one 24-hour period. After you download a
``{org}-prod-events-{date}.log.gz.gpg`` file for an approved RDX research
project, you complete these tasks.

#. Use your private key to decrypt the file. See :ref:`Decrypt an Encrypted
   File`.

#. Extract the log file from the compressed .gz file. The result is a single
   file named ``{org}-prod-events-{date}.log``. (Alternatively, the data can
   be decompressed in stream using a tool such as gzip.)

For more information about the events in this file, see :ref:`Tracking Logs`.

============================================
Extracted Contents of ``{org}-{date}.zip``
============================================

After you download the ``{org}-{date}.zip`` file for an approved RDX research
project, you complete these tasks.

#. Extract the contents of the file. When you extract (or unzip) this file, all
   of the files that it contains are placed in the same directory. All of the
   extracted files end in ``.gpg``, which indicates that they are encrypted.

#. Use your private key to decrypt the extracted files. See
   :ref:`Decrypt an Encrypted File`.

The result of extracting and decrypting the ``{org}-{date}.zip`` file is the
same set of .sql, .csv, and .mongo files that you download for your
organization. For more information, see :ref:`Data Package Contents`.


.. _RDX Data Obfuscation:

**************************
RDX Data Obfuscation
**************************



============================================
Obfuscating User Identifiers in SQL Tables
============================================






============================================

============================================





.. include:: ../../../links/links.rst
