.. _configuration:


Configuration
==============

RUNALYZE needs at least database parameters to work. Copying a default
``app/config/default_config.yml`` to ``data/config.yml`` is part of the
:doc:`Installation process <install>`.

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
      database_password:
      secret: please_change_this_secret
      user_can_register: true
      user_cant_login: false
      user_disable_account_activation: false
      garmin_api_key:
      openweathermap_api_key:
      nokia_here_appid:
      nokia_here_token:
      geonames_username:
      perl_path:
      ttbin_path:
      sqlite_mod_spatialite:
      mail_sender:
      mail_name:
      smtp_host:
      smtp_port:
      smtp_security:
      smtp_username:
      smtp_password:

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
user\_can\_register
    Flag if users can register. Set to false to disable registration form.
user\_cant\_login
    Flag if users can login. Set to true to disable login form (e.g. while
    updating your installation).
user\_disable\_account\_activation
    Flag if accounts need to be activated. Set to false to automatically
    activate accounts after registration.
garmin\_api\_key
    Api key for `GarminCommunicator <http://developer.garmin.com/web-device/garmin-communicator-plugin/get-your-site-key/>`_,
    required to directly import activities from a connected Garmin device
openweathermap\_api\_key
    Api key for `openweathermap.org <http://openweathermap.org/api>`_, required
    to load weather data
nokia\_here\_appid
    App id for HERE access, see <https://developer.here.com/>_, required to use
    HERE maps
nokia\_here\_token
    Token for HERE access
geonames\_username
    Username for `geonames.org <http://www.geonames.org/>`_, used for elevation
    correction if no local srtm files are available
perl\_path
    Path to your perl binary, usually ``/usr/bin/perl`` or something like
    ``C:\[...]\xampp\perl\bin\perl`` on Windows.
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
