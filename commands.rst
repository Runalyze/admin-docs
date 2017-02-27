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

Clears the production environment cache

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

Others
---------

JSON Export for GpxTrackPoster
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. note:: From version 3.2

.. code-block:: php

   runalyze:athlete:poster-json <username> <export directory> <year> <sportid>

Exports the json files for the GPXTrackPoster tool by Florian Pigorsch into a folder. Races (special parameter for the tool) will be exported into the file ``special.params`` and are shown after the creation of the files.

You need to install the adjusted version of `GPXTrackPoster for RUNALYZE by laufhannes <https://github.com/laufhannes/GpxTrackPoster/tree/runalyze>`_. The parameter ``--json-dir`` must point to the folder containing the json-files. Add the ``special params`` to the command.

A svg-file will be created. Use e.g. ``inkscape -z -e <poster.png> -h7020 <poster.svg>`` to convert it to a png file.
