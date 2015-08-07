Follow these simple steps to install hostinfo

## Pre-installation ##
Firstly you need to satisfy a number of [Prerequisites](Prerequisites.md) the most obvious being python, django and a database (e.g. MySQL)

## Installation ##

  * Unpack the tarball
  * `% gzip -cd hostinfo-1.20.tar.gz | tar -xf -`
  * Run the supplied setup script (you may need to be root if you are installing in the system area)
  * `% cd hostinfo-1.20`
  * `# python ./setup.py install`

## Configuration ##
Go to where python installs new packages. E.g. `/usr/local/lib/python/dist-packages` and rename the `settings_dist.py` file to `settings.py` and edit it as required:

There are a number of configurable options here, see [Django Settings](django_settings.md) for more details

## Database creation ##
First you need to create the database that you will be using and set up the appropriate permissions and then create the schema.

See [MySQL\_Setup](MySQL_Setup.md) or [Postgresql\_Setup](Postgresql_Setup.md)

## Web Server Configuration ##
### Apache ###
To get the web interface working through Apache, you will need to install mod\_wsgi or mod\_python.
  * See [Using\_mod\_wsgi](Using_mod_wsgi.md)
  * Deprecated [Using\_mod\_python](Using_mod_python.md)