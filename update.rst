.. _update:


Update instructions
===================

Upgrade from 2.1 to 2.2
***********************

Starting with version 2.2 we removed the single user function in RUNALYZE. If you using the multi-user version you can skip the first steps

ToDos for single user versions
-------------------------------

1. Change the configuration setting to multi-user. Edit the `config.php` and change the following line::

    define('USER_MUST_LOGIN', false);

to::

    define('USER_MUST_LOGIN', true);

2. Create/Register an new account

3. Exctract the archive of RUNALYZE (2.2). Remove all files except the `config.php`

4. Execute the SQL statements in the file `inc/install/switch-accountid-to-1.sql`

5. Continue with step 2 of the "Normal update of a multi-user installation"

Normal update of a multi-user installation
--------------------------------------------
1. Extract the archive of RUNALYZE (2.2). Remove all files except the `config.php`.

2. If you want to use InnoDB as your storage engine you have to execute manually the sql statements in `inc/install/innodb.sql`
You may have problems with the `SET GLOBAL` statements. (As described in the file). Just leave them out.

3. Open `update.php` in your browser and update from version 2.1 to 2.2.

4. For this update of RUNALYZE you have to run another refactor script. Set your database connection in the file `refactor-equipment.php`.

5. If you don't want or can't use InnoDB as your storage engine set::

    define('CHECK_INNODB', true);

to::

    define('CHECK_INNODB', false);

6. Run the script `refactor-equipment.php` in your browser or cli

Common problems
----------------
