.. _update:


Update instructions
===================

Upgrade from 2.1 to 2.2
***********************

From v2.2+ RUNALYZE does not support single-user installations without account anymore. You can skip this section if your installation does use an account.

Upgrade single-user installation
--------------------------------

1. Edit your ``config.php`` and set ``USER_MUST_LOGIN`` to true (this definition is ignored from v2.2+ anyway)::

    define('USER_MUST_LOGIN', true);

2. Open ``runalyze/login.php`` in your browser and register a new account

3. Purge your ``runalyze/`` directory except for ``config.php`` and extract the downloaded archive of v2.2.

4. Import ``inc/install/switch-accountid-to-1.sql`` to your database.

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

7. Remember to remove your credentials from ``refactor-equipemtn.php`` afterwards.

Common problems
----------------
