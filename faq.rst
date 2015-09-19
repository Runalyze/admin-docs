
==========================
Frequently Asked Questions
==========================

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

My RUNALYZE version is only in english
--------------------------------------
*On Linux (Ubuntu/Debian):*

Maybe you are missing the gettext PHP package. Please install the package ``php-gettext``. Don't forget to restart your webserver!
