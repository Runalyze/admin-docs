.. _commands:

Commands
==============

Install/Update
---------------

Install RUNALYZE
^^^^^^^^^^^^^^^^^^
.. code-block:: php

   runalyze:install

Creates RUNALYZE database schema


Update RUNALYZE
^^^^^^^^^^^^^^^^^

.. code-block:: php

   doctrine:migrations:migrate

Update database schema

Cleanup
--------

Cleanup Registrations
^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: php

   runalyze:cleanup:registrations <days>

Remove all not activated users older than x (default 7) days.

Activities
---------------

Bulk import
^^^^^^^^^^^^^

.. code-block:: php

   runalyze:activity:bulk-import <username> <path to folder with activity files>

Imports all activity files within a folder. Will check for duplicates. 
