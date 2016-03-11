.. _Migrating CSMH:

########################################################
Migrating the ``courseware_studentmodulehistory`` Table
########################################################

This section describes a change to the ``courseware_studentmodulehistory``
database table that requires a new database configuration and a migration.
These changes took place for the edx.org and edX Edge sites during the first
two weeks of March 2016.

All Open edX installations that use the latest software available on the master
branch of the edx-platform repository, including devstack installations, must
also complete this migration.

.. contents::
   :local:
   :depth: 1

.. note:: This change to the ``courseware_studentmodulehistory`` database
 table will be required during the upgrade to the Open edX Eucalyptus release.
 It is not required or supported for the Dogwood release.

****************************
Why Is a Migration Needed?
****************************

The ``courseware_studentmodulehistory`` database table contains a record for
each attempt learners make to answer ``problem`` type XBlocks correctly. This
database table is a standard ``StudentModuleHistory`` Django model. It has an
``id`` column with a type of signed integer, and therefore has a maximum
capacity of 2,147,483,647 records.

Typically, ``courseware_studentmodulehistory`` is the largest table in the
database. On the edx.org site, 20,000 to 80,000 records are written to this
table every hour. A migration to replace the current form of the
``courseware_studentmodulehistory`` table with a higher capacity form is
required to assure that no data is lost for the edx.org site.

A new database table, ``courseware_studentmodulehistoryextended``, replaces the
``courseware_studentmodulehistory`` table. The
``courseware_studentmodulehistoryextended`` table uses a custom Django field
type to add an unsigned integer ``id`` column type, which offers an
exponentially larger storage capacity.

********************************
Database Configuration Strategy
********************************

A data migration within a database can take from seconds to days to complete,
depending on the number of records involved. To prevent data loss while a
migration takes place, a site can be taken offline. For the edx.org site, both
data loss and the amount of time needed for a migration to a new table in the
same database was unacceptable.

* To avoid site downtime, you create the
  ``courseware_studentmodulehistoryextended`` table in a separate database
  named ``student_module_history``. The software available on the master branch
  of the edx-platform repository as of 16 March 2016 writes records to this
  database and table.

* To avoid data loss, the system reads the records in both tables, ``courseware_studentmodulehistory`` in the default database and ``courseware_studentmodulehistoryextended`` in the ``student_module_history`` database.
  .. something about how the script iterates back to make sure new records written since the migration started are also migrated...

After the migration is complete, you have the option to leave both tables in place, with the overhead of doing lookups in both. Alternatively, you can configure your system to read only from the new table and truncate the old table.



***********************
Post-Migration Options
***********************

The following post-migration options   are available.

* Migrate data from After you create the database and the table,
This option is suitable for installations that have a large number of records in the ``courseware_studentmodulehistoryextended`` table.




, ``student_module_history``

``courseware_studentmodulehistory`` table in default database


``courseware_studentmodulehistoryextended`` table in student_module_history database with huge primary keys






====================================

====================================

.. include:: ../../links/links.rst
