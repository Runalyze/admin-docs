
==========================
Frequently Asked Questions
==========================

Error messages
**************

 „out of memory“ or „Maximum execution“
 --------------------------------------




I got an PHP Parse error: syntax error, unexpected '['
------------------------------------------------------
Error when try to view an activity::

    PHP Parse error: syntax error, unexpected '[' in /runalyze/inc/core/View/Activity/Plot/Series/Pace.php on line 210

**Answer:**

Your PHP version is too old. For RUNALYZE 2.1 you need at least PHP 5.4.

.. note:: We recommend PHP 5.6!


PHP Warning: Missing date.timezone setting
-------------------------------------------
Error message in the error log of the webserver::

    PHP Warning:  date(): It is not safe to rely on the system's timezone settings. You are *required* to use the date.timezone setting or the date_default_timezone_set() function.

**Answer::**
Set the right date.timezone in your ``php.ini`` file. E.g. for Germany::

    date.timezone = "Europe/Berlin"

Internal Server Error 500
-------------------------
This is a very inprecise description. Sometimes the .htacces could be corrupt.

The best way to debug such an error is to look into the server-log.
If you have this problem you should attach the log file to your post.

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
Add the following line to your .htaccess file::

     RewriteBase /

My RUNALYZE version is only in english
--------------------------------------
*On Linux (Ubuntu/Debian):*

Maybe you are missing the gettext PHP package. Please install the package ``php-gettext``. Don't forget to restart your webserver!
