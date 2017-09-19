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

Clears the production environment cache, the same is possible for the dev
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

Clear Notifications
^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: php

   runalyze:notification:clear

Removes all expired notifications from database


Activities
------------

Bulk import
^^^^^^^^^^^^^

.. code-block:: php

   runalyze:activity:bulk-import <username> <path to folder with activity files>

Imports all activity files within a folder. Will check for duplicates.

Notifications
--------------
Creates notifications for either all user or specific users (by language or id).
Template must exists in ``data/views/notifications`` and has to be a yaml file.

.. code-block:: php

   runalyze:notification:create <TemplateName>

Example notification (e.g. ``update.yaml``):

.. code-block:: php

    text: "We've updated RUNALYZE. Have a look at what's new."
    link: http://blog.runalyze.com/

Optional parameters (examples):

.. code-block:: php

    --lang=de                           # add notification to all users where the actual set language is "de" (german)
    --exclude-lang=de                   # add notification to all users where the actual set language is not "de"
    --account=1                         # add notification to user with id 1 (add multiple ids by adding a further parameters: --account=1 --account=2 )
    --registration-before <timestamp>   # add notificatoin to all users who registered before <timestamp>
    --registration-after <timestamp>    # add notificatoin to all users who registered after <timestamp>
    --last-action-before <timestamp>    # add notificatoin to all users who where active before <timestamp>
    --last-action-after <timestamp>     # add notificatoin to all users who where active after <timestamp>
    --lifetime <integer>                # notification lifetime in days
    --force                             # do not ask to create notification(s)
