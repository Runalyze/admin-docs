.. _update:


Update instructions
===================

General instructions
********************

* RUNALYZE follows `semantic versioning <http://semver.org/>`_.
* If not stated otherwise, patch updates do not require any further adjustments. Just copy the files into your working directory.
* If not stated otherwise, major and minor updates require specific adjustments. You have to follow the update process for each minor version. We can't guarantee that the latest version will contain all required files for an update to a previous version.
* From v2.4 on, all installation specific files are in ``data/``. Take care that you don't overwrite this directory.
* Execute the update (sql files in `inc/install/`) or refactorscripts via cli if you have big installations or a slow server 

.. warning:: Never ever forget to make a backup before updating or changing your RUNALYZE installation. (You break it - you fix it)

Upgrade from 2.5 to 2.6
***********************
1. Purge your runalyze/ directory except for the ``data`` folder and extract the downloaded archive of v2.6.

2. Open ``runalyze/update.php`` in your browser and update from v2.5 to v2.6. 

3. Done! Really! No further steps are necessary! ;)

Upgrade from 2.4 to 2.5
***********************
1. Purge your runalyze/ directory except for the ``data`` folder and extract the downloaded archive of v2.5.

2. Open ``runalyze/update.php`` in your browser and update from v2.4 to v2.5. 

.. note:: The following step is an optional enhancement. Skip this step if you cannot or do not want to get a working spatialite lib.

3. We use a sqlite3 database for the timezone recognization. You need the packages `spatialite-bin` and `php5-sqlite` installed on your system. 

You also need to download ``http://cdn.runalyze.com/update/timezone.sqlite`` and put the database to the ``data``-directory. 
In addition, you have to edit your php.ini and make sure that ``sqlite3.extension_dir`` is set correctly. (Wherever `mod_spatialite` is located)

4. Execute the ``refactor-timezone.php`` script. (no database connection has to be set)

5. Everything should be fine now. Please login into you account. You may have to change your timezone in the account settings. 

Upgrade from 2.3 to 2.4
***********************
1. Purge your runalyze/ directory except for ``config.php`` and extract the downloaded archive of v2.4.

2. Move ``config.php`` to ``data/config.php``

3. Add ``$port = 3306;`` to ``data/config.php`` (3306 is the default mysql-port)

4. Open ``runalyze/update.php`` in your browser and update from v2.3 to v2.4.

5. You should run ``build/global.routefix.php`` (Set the database connection in the file) (To access this script via browser just rename the ``.htaccess`` file in the ``build/`` directory. Don't forget to rename the file afterwards)

6. You should run now ``refactor-night.php`` (no database connection has to be set)

7. Maybe you have to adjust the permissions for ``data/*``

.. note:: If have local srtm files you should move them from ``inc/data/gps/srtm`` to ``data/srtm``

Upgrade from 2.2 to 2.3
***********************
1. Purge your runalyze/ directory except for config.php and extract the downloaded archive of v2.3.

2. Open ``runalyze/update.php`` in your browser and update from v2.2 to v2.3.

3. Insert your database connection in ``refactor-geohash.php`` and adjust the other settings, e.g. the prefix if it's not ``runalyze_``.

4. Run ``refactor-geohash.php`` via command line or browser. (We recommend to run this script via command line, because of long execution times)

5. Remember to remove your credentials from ``refactor-geohash.php`` afterwards.

6. We haved moved the Perl path setting to your config.php (or via admin.php). You may have to changed this path

Upgrade from 2.1 to 2.2
***********************

.. note:: Please directly update from 2.1 to 2.2.1 to avoid any known problems with upgrading from single-user installations.

From v2.2+ RUNALYZE does not support single-user installations without account anymore. You can skip this section if your installation does use an account.

Upgrade single-user installation
--------------------------------

1. Edit your ``config.php`` and set ``USER_MUST_LOGIN`` to true (this definition is ignored from v2.2+ anyway)::

    define('USER_MUST_LOGIN', true);

2. Open ``runalyze/login.php`` in your browser and register a new account

3. Purge your ``runalyze/`` directory except for ``config.php`` and extract the downloaded archive of v2.2.

4. Attention! Instead of importing ``inc/install/switch-accountid-to-1.sql`` to your database use `this one <https://raw.githubusercontent.com/Runalyze/Runalyze/support/2.2.x/inc/install/switch-accountid-to-1.sql>`_.

5. Continue with step 2 of the "Upgrade multi-user installation"

Upgrade multi-user installation
-------------------------------
1. Purge your ``runalyze/`` directory except for ``config.php`` and extract the downloaded archive of v2.2.

2. We highly recommend using InnoDB as storage engine for your database. Please import ``inc/install/innodb.sql`` to your database (you may have problems with ``SET GLOBAL`` statements, just leave them out).

3. Open ``runalyze/update.php`` in your browser and update from v2.1 to v2.2. You can ignore errors like the following if you don't want to use InnoDB as storange engine::

    SQLSTATE[HY000]: General error: 1005 Can't create table 'd03e141b.#sql-592_6c53c5' (errno: 150)

4. For this update of RUNALYZE you have to run another refactor script. Insert your database connection in ``refactor-equipment.php`` and adjust the other settings, e.g. the prefix if it's not ``runalyze_``..

5. If you don't want or can't use InnoDB as your storage engine you have to adjust ``CHECK_INNODB`` to::

    define('CHECK_INNODB', false);

6. Run ``refactor-equipment.php`` via command line or browser.

7. Remember to remove your credentials from ``refactor-equipment.php`` afterwards.

Common problems
----------------
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
** Error in query (1193): Unknown system variable .... during importing innodb.sql
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Comment or remove the "SET GLOBAL" lines and try it again
