.. _configuration:


Configuration
==============

RUNALYZE needs at least database parameters to work. Copying a default
``app/config/default_config.yml`` to ``data/config.yml`` is part of the
:doc:`Installation process <installation/4.x>`.

All parameters are optional. If they are not in your custom ``data/config.yml``
default values from ``app/config/default_config.yml`` will be used. Still, we
recommend to include all parameters in your custom configuration.

.. note::
    You need to clear your cache (``var/cache/prod/`` in general) for the
    changes to take effect.

.. warning::
    Strings containing special characters must be enclosed in quotes, see `these docs <http://symfony.com/doc/current/components/yaml/yaml_format.html#strings>`_.

Examplary configuration
-----------------------
::

    parameters:
      locale: en
      database_host: 127.0.0.1
      database_prefix: runalyze_
      database_port: 3306
      database_name: runalyze
      database_user: root
      database_password: "My$3cr3tP4$$w0rd!"
      secret: "please_change_this_secret"
      update_disabled: no
      user_can_register: true
      user_disable_account_activation: false
      maintenance: false
      garmin_api_key:
      openweathermap_api_key:
      darksky_api_key:
      nokia_here_appid:
      nokia_here_token:
      thunderforest_api_key:
      mapbox_api_key:
      geonames_username:
      perl_path: /usr/bin/perl
      python3_path: /usr/bin/python3
      rsvg_path: /usr/bin/rsvg-convert
      inkscape_path: /usr/bin/inkscape
      ttbin_path: ../call/perl/ttbincnv
      sqlite_mod_spatialite: libspatialite.so.5
      mail_sender: example@example.com
      mail_name: Example sender name
      smtp_host: smtp.gmail.com
      smtp_port: 587
      smtp_security: tls
      smtp_username: example@googlemail.com
      smtp_password: <password>
      backup_storage_period: 5
      poster_storage_period: 5
      router.request_context.host: runalyze.com
      router.request_context.scheme: https
      router.request_context.base_url:

Configuration variables
-----------------------
locale
    Default language, see ``data_config_lang.php`` for available languages
database\_host
    Host name of your database, ``localhost`` or ``127.0.0.1`` for local
    installations, otherwise specific to your hoster
database\_prefix
    Prefix for all RUNALYZE tables in your database, by default ``runalyze_``.
    Changing this value is only needed if you want to keep multiple
    installations in one database.
database\_port
    Port number for database connection, defaults to ``3306``
database\_name
    Name of your database, you need to creat it if it does not already exist
database\_user
    Username for database connection
database\_password
    Password for database connection
secret
    Installation specific secret that is used for hashing. Just use your own
    string.
update\_disabled
    Setting this parameter to ``yes`` will disable all pages for installing and
    updating RUNALYZE to protect public installations. Updates via console are
    still possible. This parameter defaults to ``no`` such that the installation
    is possible.
user\_can\_register
    Flag if users can register. Set to false to disable registration form.
user\_disable\_account\_activation
    Flag if accounts need to be activated. Set to false to automatically
    activate accounts after registration.
maintenance
    Set to `True` to enable maintenance mode. Only updater and installer will work during maintenance mode.
garmin\_api\_key
    Api key for `GarminCommunicator <https://my.garmin.com/api/communicator/key-generator.jsp/>`_,
    required to directly import activities from a connected Garmin device
openweathermap\_api\_key
    Api key for `openweathermap.org <http://openweathermap.org/api>`_, required
    to load weather data. `Free key <http://openweathermap.org/price>`_ does only have access to current weather
darksky\_api\_key
    Api key for `darksky.net <http://darksky.net/dev>`_, required
    to load weather data. `Free key <https://darksky.net/dev/>`_ includes current and historical weather information. (1000 requests per day are free)
nokia\_here\_appid
    App id for HERE access, see `developer.here.com <https://developer.here.com/>`_, required to use
    HERE maps
nokia\_here\_token
    Token for HERE access
thunderforest\_api\_key
    Api key for thunderforest layers (for activity maps), see `thunderforest.com <https://www.thunderforest.com/docs/apikeys/>`_
mapbox\_api\_key
    Api key for mapbox outdoor layer (for activity maps), see `mapbox.com <https://www.mapbox.com/help/create-api-access-token/>`_
geonames\_username
    Username for `geonames.org <http://www.geonames.org/>`_, used for elevation
    correction if no local srtm files are available
perl\_path
    Path to your perl binary, usually ``/usr/bin/perl`` or something like
    ``C:\[...]\xampp\perl\bin\perl`` on Windows.
python3\_path
    Path to your python binary (v3+), usually ``/usr/bin/python3``.
rsvg\_path
    Path to your rsvg-convert binary, usually ``/usr/bin/rsvg-convert``.
inkscape\_path
    Path to your inkscape binary, usually ``/usr/bin/inkscape``.
ttbin\_path
    Path to ttbin converter that is required for reading binary ttbin files.
    A compiled version is located under ``call/perl/ttbincnv`` but you may need
    to compile it for your os manually, see `ryanbinns/ttwach <https://github.com/ryanbinns/ttwatch>`_
sqlite\_mod\_spatialite
    Name of SQLite spatialite extension, usually ``libspatialite.so.5``.
    This extension is required if you want to use ``data/timezone.sqlite`` for
    time zone lookups of activities based on their coordinates.
mail\_sender
    Mail adress that will be used as sender for outgoing mails,
    ``mail@runalyze.com`` will be used if this value is empty.
mail\_name
    Name that will be used as sender for outgoing mails
smtp\_host
    Host for smtp server
smtp\_port
    Port for smtp server
smtp\_security
    Security setting, set to ``ssl`` or ``tls`` if you wish to use the encryption
smtp\_username
    Password for smtp server
smtp\_password
    Password for smtp server
backup\_storage\_period
    Default storage period for backups (in days)
poster\_storage\_period
    Default storage period for poster (in days)
router.request_context.host
    Needed for correct urls in mails. Set your domain name here.
router.request_context.scheme
    Needed for correct urls in mails. Set to ``https`` or ``http``
router.request_context.base_url
    Needed for correct urls in mails. Set it to e.g. ``/runalyze`` if you are using subdirectories (you should not do that)
