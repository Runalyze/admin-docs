.. _commands:

Commands
==============

RUNALYZE offers cli commands for simplifying some tasks.
You can run them with::

    php bin/console <command>

To see all available commands just execute::

    php bin/console

General
--------

Clear cache
^^^^^^^^^^^^
.. code-block:: php

   cache:clear --env=prod

Clears the production environment cache, he same is possible for the dev
environment with ``--env=dev``. This command clears the general cache for e.g.
the app kernel, the DI container, annotations and twig templates. For clearing
doctrine's cache (if you changed some entities), you need to run
``doctrine:cache:clear-metadata`` or clear ``var/cache/doctrine/`` manually.

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
------------

Bulk import
^^^^^^^^^^^^^

.. code-block:: php

   runalyze:activity:bulk-import <username> <path to folder with activity files>

Imports all activity files within a folder. Will check for duplicates.

