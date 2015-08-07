# Introduction #

How to setup PostgreSQL database before use


# Details #

```
psql:
 postgres=# create database <DATABASE_NAME>;
 postgres=# create role <DATABASE_USER> with password '<DATABASE_PASSWORD>' superuser login;
 postgres=# grant all privileges on database <DATABASE_NAME> to <DATABASE_USER>;

```

If you are going to run hostinfo on more than one server with a common database (recommended) then you also need to let those other servers have access by editing the pg\_hba.conf file.

See [PostgreSQL Documentation](http://www.postgresql.org/docs/9.0/static/auth-pg-hba-conf.html) if you get an error like "OperationalError: FATAL:  Peer authentication failed for user DATABASE\_USER"

For example:
```
 postgres=# create database hostinfo;
 postgres=# create role hostinfo_user with password 'sekrit' superuser login;
 postgres=# grant all privileges on database hostinfo to hostinfo_user;
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