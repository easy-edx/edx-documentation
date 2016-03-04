.. _Retrieving RDX Packages:

########################
Retrieving RDX Packages
########################

The process for retrieving RDX data packages is similar to

You download files from AWS, and then extract the contents.

.. contents::
   :local:
   :depth: 2

.. _Amazon S3 Buckets and Directories for RDX Data:

********************************************
Amazon S3 Buckets and Folders for RDX Data
********************************************

Data package files are located at the following Amazon S3 destinations.

* The ``s3://edx-course-data/`` folder contains the daily
  ``{org}-{course?}-prod-events-{date}.log.gz.gpg`` files of course event data.

* The ``s3://course-data`` bucket contains the ``{org}-{course?}-{date}.zip``
  database snapshot files.

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
    own organization's data and the bucket for RDX data. You might need to
    disconnect from Amazon S3 and then reconnect to the RDX destination.

#. Use the AWS Command Line Interface or a third-party tool to connect to the
   ``s3://edx-course-data/`` folder on Amazon S3.

   For information about providing your credentials to connect to Amazon S3,
   see :ref:`Access Amazon S3`.

#. Navigate within ``s3://edx-course-data/`` to locate the RDX folder.

   ``RDX? {org}/prod/events/{year}`` TBD

#. Download the ``RDX? {org}-{date}.zip`` database data file.

#. Download the compressed, encrypted ``RDX?
   {org}-prod-events-{date}.log.gz.gpg`` file.


*********************************************************
Extract the ``{org}-prod-events-{date}.log.gz.gpg`` File
*********************************************************

The ``{org}-prod-events-{date}.log.gz.gpg`` file contains all event data for
a single? all requested? courses on the edx.org site for one 24-hour period. After you download a
``{org}-prod-events-{date}.log.gz.gpg`` file for an approved RDX research
project, you complete these tasks.

#. Use your private key to decrypt the file. See :ref:`Decrypt an Encrypted
   File`.

#. Extract the log file from the compressed .gz file. The result is a single
   file named ``{org}-prod-events-{date}.log``. (Alternatively, the data can
   be decompressed in stream using a tool such as gzip.)

For more information about the events in this file, see :ref:`Tracking Logs`.



****************************************
Extracted the ``{org}-{date}.zip`` File
****************************************

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

