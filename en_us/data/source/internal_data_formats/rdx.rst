.. _Research Data Exchange:

######################
Research Data Exchange
######################

The edX research data exchange (RDX) program gives research teams at
participating partner institutions the opportunity to obtain data from any
completetd course on the edx.org website. Researchers at participating partner
institutions must propose, and be approved for, a specific educational research
project to receive RDX data. Before delivering the data, edX obfuscates
personally identifying information (PII). The data czar of the institution can
then download the RDX package for the research team from the Amazon S3 storage
service.

The topics in this section provide an overview of the data files that are
included in an RDX package and the obfuscation process.

.. contents::
   :local:
   :depth: 2

For more information about joining the RDX program or proposing an educational
research project, see

For more information for data czars about downloading RDX packages, see

.. TBD the partner portal

.. _RDX Files:

**********************
RDX Data Files
**********************

An RDX data package consists of files for one or more completed courses from
one or more participating partner instituitons. Both event data and database
data are included.

==================
Event Data Files
==================

Each ``{org}-{course?}-prod-events-{date}.log.gz.gpg`` file contains a daily log
of course events. A separate file is available for each course.

For a partner organization named UniversityX, these daily files are identified
by the organization name, the course name, the edx.org site name (prod), and the date. For example,
``universityx-{course?}-prod-events-2016-07-25.log.gz.gpg``.

.. note:: In all file names, the date is in {YYYY}-{MM}-{DD} format.

.. Differences in naming conventions, otherwise see :ref:`Data Package Contents`.

===================
Database Data Files
===================

The ``{org}-{course?}-{date}.zip`` file contains views on database tables. This
file includes data as of the time of the export, for one organization's course
on the edx.org sites.

For a course at a participating organization named UniversityX, each
file is identified by the organization name, the course name?, and the extraction date. For
example, ``universityx-{course?}-2016-10-27.zip``.

.. Differences in naming conventions, otherwise see :ref:`Data Package Contents`.

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
