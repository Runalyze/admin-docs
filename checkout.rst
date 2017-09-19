
==========================
Checkout
==========================

RUNALYZE is hosted on `GitHub <https://github.com/Runalyze/Runalyze>`_.
If you want to contribute to RUNALYZE or want to be up to date and use our
current dev version you need to maintain a local checkout of our git repository.
GitHub offers a good tutorial `How to set up Git <https://help.github.com/articles/set-up-git/>`_.

Required tools
--------------
Whereas our official release contains all required dependencies, developers and
users of our dev version need to install them themselves.

* `composer <https://getcomposer.org/doc/00-intro.md#system-requirements>`_
* `npm <https://nodejs.org/download/>`_
* `bower <http://bower.io/>`_: *will be installed via npm*
* `gulp <https://github.com/gulpjs/gulp/blob/master/docs/getting-started.md>`_:
  *will be installed via npm*

Clone our repository
--------------------
Having installed all required tools you can clone our repository.
Open a terminal, switch to the directory where your copy of RUNALYZE should be
located and type the following::

    git clone https://github.com/Runalyze/Runalyze.git

This creates a new directory ``runalyze`` with all contents from our repository.
If you want to contribute to RUNALYZE you should fork our repository.
In that case you'll have to clone RUNALYZE via::

    git clone https://github.com/<your-github-name>/Runalyze.git

Installation of dependencies
----------------------------
To install all current dependencies, open a terminal, switch to your RUNALYZE
directory and type the following::

    composer install --prefer-dist
    npm install
    gulp

You may need to install ``gulp-cli`` globally: ``npm install -g gulpjs/gulp-cli``

Installation of RUNALYZE
------------------------
You can now continue with the default installation of RUNALYZE, see :doc:`installation/4.x`.

Stay up to date
---------------
You can use ``git pull`` to pull recent changes from our master branch to your
local checkout. You may need to run ``composer update``, ``npm update`` and
``gulp`` to update all dependencies and clearing the cache (everything within
``var/cache/`` is always a good idea).

Database changes will be handled by `doctrine migrations <http://symfony.com/doc/current/bundles/DoctrineMigrationsBundle/index.html>`_
from v3.0 on. To update your database, simply run::

    php bin/console doctrine:migrations:migrate

Further hints
-------------
* Adjust ``web/.htaccess`` to use ``web/app_dev.php`` instead of ``web/app.php``
  if you want to use the dev environment.
* You may need to adjust ``web/app_dev.php`` if some *You are not allowed to
  access this file.* message appears.
* Clear ``var/cache/prod/`` (or ``var/cache/dev/``) and ``var/cache/doctrine``
  to clear the cache.
