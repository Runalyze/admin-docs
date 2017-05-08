
==========================
Frequently Asked Questions
==========================

General
********

When do you release new versions?
**********************************
We are deploying new release in the first place to our official hosted version at `RUNALYZE.com <https://runalyze.com>`_.

This allows us to identify problems before we release new versions for you all. Consider this as a quality assurance.

Releasing a new version takes time and effort (updating the documentation, writing blog entries, distribute the releases on all our communication channels). Just relax and wait patiently for new releases.

Normally we are releasing a new version within a week after deploying it to our official hosted version.

Error messages
**************

Fatal error: Maximum execution time of 30 seconds exceeded in
--------------------------------------------------------------
Set the max_execution_time in your ``php.ini`` file higher than 30 seconds or add ``ini_set('max_execution_time', 300);`` to your index.php or update.php (where it happens).

If you are trying to update RUNALYZE, try to run the respective update file (you will find the sql-file in ``inc/install``) manually.

„out of memory“ or „Maximum execution“
--------------------------------------
Depending on your server settings RUNALYZE may have problems with large files.
Especially logbook files can be large or if the Forerunner is set to "Record a data point every second" these problems may occur. The frequency of recording can be changed in the settings of the Forerunner.



PHP Parse error: syntax error, unexpected '['
------------------------------------------------------
The following error may appear while trying to view an activity::

    PHP Parse error: syntax error, unexpected '[' in /runalyze/inc/core/View/Activity/Plot/Series/Pace.php on line 210

**Answer:**

Your PHP version is too old. RUNALYZE 2.1+ requires at least PHP 5.4. Please update your server or ask your provider.

.. note:: We recommend PHP 5.6 pr PHP 7.0!


PHP Warning: Missing date.timezone setting
-------------------------------------------
Error message in the error log of the webserver::

    PHP Warning:  date(): It is not safe to rely on the system's timezone settings. You are *required* to use the date.timezone setting or the date_default_timezone_set() function.

**Answer:**
Set the right date.timezone in your ``php.ini`` file. E.g. for Germany::

    date.timezone = "Europe/Berlin"

Internal Server Error 500
-------------------------
This is a very inprecise error message. Sometimes there is only a problem with your ``.htaccess``, but in most cases there is another problem.

Please have a look at your server log, where you will find the exact error message.
If you have this problem you should attach the log to your post.

MySQL error: Cannot add or update a child row
---------------------------------------------
The following error may appear while trying to update your database::

    #1452 - Cannot add or update a child row: a foreign key constraint fails (`runalyze`.`#sql-4a8_39`, CONSTRAINT ...

**Answer:**
From RUNALYZE v2.2 on we are using foreign keys to keep the database consistent.
It seems that your table contains at least one row that should be deleted, for example because the respective activity does not exist anymore.
Please read the exact error message (which constraint fails?), find the faulty row and delete it.

**Example:**
The constraint ``(activityid) REFERENCES runalyze_training (id)`` fails while trying to alter table ``runalyze_trackdata``.
You can find the faulty row with::

    SELECT runalyze_trackdata.*, runalyze_training.id FROM runalyze_trackdata LEFT JOIN runalyze_training ON runalyze_trackdata.activityid = runalyze_training.id WHERE ISNULL(id)

Remember the shown ``activityid``, delete this row from ``runalyze_trackdata`` by hand and try the respective line from the database update again.

Common problems
***************

.. _sql_mode_only_full_group_by:

RUNALYZE does not show up completely (MySQL Only Full Group by problem)
------------------------------------------------------------------------

Some queries are not `ONLY_FULL_GROUP_BY` compatible. If you are using MySQL 5.7 the sql mode `ONLY_FULL_GROUP_BY` is enabled by default. You have to `disable this mode <http://stackoverflow.com/questions/23921117/disable-only-full-group-by/36033983#36033983>`_.

.. note::
    There's an `open issue <https://github.com/Runalyze/Runalyze/issues/1790>`_ to make all queries `ONLY_FULL_GROUP_BY` compatible.

Import/Export is not working
----------------------------
Check that the following directories exist and are writable::

        /data/backup-tool/
        /data/cache/
        /data/import/
        /data/log/
        /data/poster/
        /data/sessions/

My RUNALYZE version is only in english
--------------------------------------
*On Linux (Ubuntu/Debian):*

Maybe you are missing the gettext PHP package. Please install the package ``php-gettext``. Don't forget to restart your webserver!

Activate an account manually
------------------------------
In case you need to activate your account manually you have to set the ``activation_hash`` column of the user of the ``_account`` table to "null" in the database.

Poster tool does not show up
------------------------------
You need to fulfill the :ref:`additional requirements <queueing-system>`. Even then the poster tool may not show up in the tool list. Some PHP defaults does not allow to check the directories for the converter and python. Adjust your php settings or copy the template and remove the if-condition of ` https://github.com/Runalyze/Runalyze/blob/master/app/Resources/views/tools/tools_list.html.twig#L76`_

FIT Importer is not working
----------------------------
Perl must be installed on your system and you have to set the corresponding path in the RUNALYZE configuration file.
