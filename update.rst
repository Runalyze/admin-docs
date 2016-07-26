.. _update:


Update instructions for v3.x
============================

General instructions
********************

* RUNALYZE follows `semantic versioning <http://semver.org/>`_.
* If not stated otherwise, patch updates do not require any further adjustments.
  Just copy the files into your working directory.
* If not stated otherwise, major and minor updates require specific adjustments.
  You have to follow the update process for each minor version. We can't
  guarantee that the latest version will contain all required files for an
  update to a previous version.
* Execute the update via cli if you have big installations or a slow server.

.. warning:: Never ever forget to make a backup before updating or changing your
    RUNALYZE installation. (You break it - you fix it)

Upgrade from 2.6 to 3.0
***********************
Since version 3.0, RUNALYZE is based on Symfony. This causes some major changes,
especially under the hood, but will simplify a lot of things in the future.

1. Purge your runalyze/ directory except for the ``data/`` directory and extract
   the downloaded archive of v3.0.

2. Create an empty directory ``data/sessions``.

3. Make sure that ``data/sessions``, ``var/cache`` and ``var/logs`` are
   writable.

4. Copy ``app/config/default_config.yml`` to ``data/config.yml`` and adjust
   the settings to your needs. These are mainly the settings from your
   ``data/config.php`` in a new format, see :doc:`configuration <configuration>`.
   You can delete your ``data/config.php`` afterwards.

5. The new ``web/`` directory will be used for all page requests. We strongly
   recommend you to use an individual (sub)domain for your installation and let
   it point directly to ``web/``.
   There's an ``.htaccess`` in the root directory that should forward all
   requests to ``web/`` otherwise, but it's your responsibility that nobody can
   access your ``data/config.yml``.
