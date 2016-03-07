.. _Retrieving RDX Packages:

########################
Retrieving RDX Packages
########################

Data czars retrieve an RDX package for an approved research project from AWS.
The procedures for downloading RDX data packages and extracting their contents
is similar to the procedures you follow for your organization's data.

The topics in this section describe the differences between RDX packages and
organizational data packages.

.. contents::
   :local:
   :depth: 2

For more information about downloading and extracting your organizational data
packages, see :ref:`Package`.

.. _RDX Package Identifiers:

***************************
Identifying an RDX Package
***************************

When researchers propose projects that require RDX data, they request data
either for specific courses or for courses that meet specified criteria. For
approved projects, edX assigns an RDX request ID to the set of courses that
meet these specifications.

Each RDX data package contains both database data and all event files for every
course in the approved set, and is identified on AWS by the request ID.




.. _Amazon S3 Buckets and Directories for RDX Data:

********************************************
Locating RDX Data on Amazon S3
********************************************

The data package for an RDX request is located in the Amazon S3
``s3://edx-course-data/{org}/rdx/{request ID}`` folder. For each course
in the requested set, this folder contains one ``{course}.tar.gz.gpg`` file.

The ``{course}.tar.gz.gpg`` file contains a database file and daily event files for the requested time period in the course's history.
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
Extract the ``{course}.tar.gz.gpg`` File
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


When you decrypt the ``{course}.tar.gz.gpg`` file and extract the contents,

::
  metadata_file.json
  /events
    <filename-friendly-course-id>-events-CCYY-MM-dd.log.gz
    ...
  /state
    /<date when state files were originally dumped, as CCYY-MM-dd>
      <filename-friendly-course-id>-<dump-file-suffix>
      ...

The ``metadata_file.json`` file contains the version of the analytics pipeline that was used to produce the RDX package.

