
==========================
Checkout
==========================

RUNALYZE is hosted on `GitHub <https://github.com/Runalyze/Runalyze>`_.
If you want to contribute to RUNALYZE or want to be up to date and use our current dev version you need to maintain a local checkout of our git repository.
GitHub offers a good tutorial `How to set up Git <https://help.github.com/articles/set-up-git/>`_.

Required tools
--------------
Whereas our official release contains all required dependencies, developers and users of our dev version need to install them themselves.

* `composer <https://getcomposer.org/doc/00-intro.md#system-requirements>`_
* `npm <https://nodejs.org/download/>`_
* `bower <http://bower.io/>`_: ``sudo npm install -g bower``
* `grunt <http://gruntjs.com/>`_: ``sudo npm install -g grunt-cli``

Clone our repository
--------------------
Having installed all required tools you can clone our repository.
Open a terminal, switch to the directory where your copy of RUNALYZE should be located and type the following::

    git clone https://github.com/Runalyze/Runalyze.git

This creates a new directory ``Runalyze`` with all contents from our repository.

Installation of dependencies
----------------------------
To install all current dependencies, open a terminal, switch to your RUNALYZE directory and type the following::

    composer install
    bower install
    npm install
    grunt dev

Installation of RUNALYZE
------------------------
Now you can continue with the default installation of RUNALYZE.
You need to create your own ``config.php`` containing your database credentials and setup the database structure from ``inc/install/structure.sql``.
