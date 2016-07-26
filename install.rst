.. _install:


Installation instructions for v3.x
==================================

The following instructions are valid only for official `RUNALYZE releases starting from version 3.0 <https://github.com/Runalyze/Runalyze/releases>`_.
If you want to use our current development version, have a look at our :doc:`checkout instructions <checkout>`.

In general, RUNALYZE requires at least PHP 5.5.9+ and MySQL 5.0.0+. We encourage you to use the latest MySQL versions for future releases (5.7).

General
-------
Since version 3.0 the ``web`` directory is the public web directory. We strongly
recommend you to use a specific (sub)domain for your RUNALYZE installation.
Otherwise, it's your responsibility to secure your configuration files and we
cannot guarantee that all parts of RUNALYZE will work as expected.

To install an official release, download the respective \*.zip or \*.tar.gz file and unpack the archive.

Copy ``app/config/default_config.yml`` to ``data/config.yml`` and adjust at least the following settings::

    database_host: 127.0.0.1     # database hostname or ip  (e.g. localhost, 127.0.0.1 ...)
    database_prefix: runalyze_   # table prefix of the new RUNALYZE installation
    database_port: 3306          # port of the database server (normally 3306)
    database_name: runalyze      # database name
    database_user: root          # database username  
    database_password: xxx       # database password


Afterwards open ``/install`` in your browser and follow the instructions. This will work only the database settings are correct.


Ubuntu/Debian distributions
---------------------------

Packages: php-gettext libxml2 gettext 

You may need to install the corresponding locales to get the translations running:
Have a look in ``less /usr/share/i18n/SUPPORTED`` whether the locale is already installed.
If not you have to install the locales on the system(the following example is for the german language)::

    sudo locale-gen de_DE.UTF-8
    sudo service apache2 restart
    
Windows
-------

.. warning:: We encourage you to use a unix system. We cannot guarantee that RUNALYZE will always be compatible with a Windows system. You will get the best experience with a unix system. 

.. warning:: The `ttbin`-Importer will only work with a unix system.

Running RUNALYZE on Apache
--------------------------

.. warning:: Required Apache modules - You need to enable ``mod_rewrite`` for Apache. On Debian-based systems you can do this by ``a2enmod rewrite``

Create a new virtual host:

.. todo:: Add example configuration


Running RUNALYZE on NGINX
-------------------------

.. todo:: Add example configuration
