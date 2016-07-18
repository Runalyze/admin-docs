
==========================
Frequently Asked Questions
==========================

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

.. note:: We recommend PHP 5.6!


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

PHP Fatal error: Class 'RunalyzePluginPanel_Schuhe' not found
-------------------------------------------------------------
The following error may appear after updating from v2.1 to v2.2 when opening the plugin's configuration::

    PHP Fatal error: Class 'RunalyzePluginPanel_Schuhe' not found in /runalyze/inc/plugin/class.PluginFactory.php on line 149

**Answer:**
You probably copied the new version into your existing runalyze-directory without removing the old files.
You can just delete the folder ``/plugin/RunalyzePluginPanel_Schuhe/``.

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

Import/Export is not working
----------------------------
Check that the following directories exist and are writable::

        /data/backup-tool/
        /data/cache/
        /data/import/
        /data/log/

The public activity view is not working
---------------------------------------
All shared views require ``mod_rewrite``. RUNALYZE comes with a pre-configured ``.htaccess`` file in its root directory. Make sure that the file is there and that ``mod_rewrite`` is enabled.
If the public activity view is still not working you may need to set the ``RewriteBase``::

     RewriteBase /

You may need to set a special base if your RUNALYZE installation is located in a subdirectory of your domain.
If you access RUNALYZE via yourdomain.com/runalyze/ you may need to use::

	 RewriteBase /runalyze

My RUNALYZE version is only in english
--------------------------------------
*On Linux (Ubuntu/Debian):*

Maybe you are missing the gettext PHP package. Please install the package ``php-gettext``. Don't forget to restart your webserver!

Cannot activate my account (no activation mail)
------------------------------------------------
Usually the account should be activated automatically when you host your RUNALYZE installaton locally. If this fails you have to remove the hash from the ``activation_hash`` colum of the user of the ``_account`` table in the database. 


