# Introduction #

How to setup MySQL database before use

# Details #

```
 # mysqladmin create <DATABASE_NAME>
 mysql> grant usage on *.* to '<DATABASE_USER>'@ 'localhost' identified by '<DATABASE_PASSWORD>';
 mysql> grant all on <DATABASE_NAME>.* to '<DATABASE_USER>'@'localhost';
```

If you are going to run hostinfo on more than one server with a common database (recommended) then you also need to let those other servers have access.
```
 mysql> grant all on <DATABASE_NAME>.* to '<DATABASE_USER>'@'%';
```

For example:
```
 # mysqladmin create django
 mysql> grant usage on *.* to 'django_script'@'localhost' identified by 'django_secret';
 mysql> grant all on django.* to 'django_script'@'localhost';
```
Then you need to tell django to create the schema
```
% django-admin syncdb --settings hostinfo.settings
```

If you have installed somewhere other than the default location, you will need to update PYTHONPATH to ensure that this works
```
 % export PYTHONPATH=$PYTHONPATH:/path/to/hostinfodb/lib
 % django-admin syncdb --settings hostinfo.settings
```
It may also ask for a username/password which is for the django admin interface.