
==========================
Frequently Asked Questions
==========================

Error messages
**************

 „out of memory“ or „Maximum execution“
 --------------------------------------




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

Common problems
***************

Import/Export is not working
----------------------------
Check if the following folders are existing and that they have writing permissions::

        /log/
        /inc/export/files/
        /inc/import/files/
        /plugin/RunalyzePluginTool_DbBackup/backup/
        /plugin/RunalyzePluginTool_DbBackup/import/

The public activity view is not working
---------------------------------------
Add the following line to your ``.htaccess`` file::

     RewriteBase /

My RUNALYZE version is only in english
--------------------------------------
*On Linux (Ubuntu/Debian):*

Maybe you are missing the gettext PHP package. Please install the package ``php-gettext``. Don't forget to restart your webserver!
