.. _templates:


Templates
==============

RUNALYZE is (from v3.0 onwards) based on `Symfony <http://symfony.com/>`_ and
uses `Twig <http://twig.sensiolabs.org/>`_ as template engine. All app-specific
templates are located under ``app/Resources/views``.

Using your own templates
------------------------
There are situations where you may want to adjust some of the templates, e.g.
to provide additional information on the login page. To achieve this you can
put your own template into ``data/views``. The app will preferably uses
templates from this directory.

.. note::
    ``data`` does only contain installation specific files such as your
    configuration and must not be emptied/replaced when updating RUNALYZE to
    keep your settings.
