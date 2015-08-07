# Introduction #

Configuring apache to use mod\_wsgi and hostinfo


# Details #
The [Django docs](https://docs.djangoproject.com/en/1.5/howto/deployment/wsgi/modwsgi/) are a useful reference.

Putting this in `/etc/httpd/conf.d/hostinfo` works:

This is obviously if you want it on port 82 and if you have installed it
in `/var/www/hostinfo`

```
Listen 82
WSGIPythonPath /var/www/hostinfo/lib/python2.7/site-packages:/var/www/hostinfo/lib/python2.7/site-packages/hostinfo
<VirtualHost *:82>
    WSGIDaemonProcess hostinfo user=nobody group=nobody threads=5
    WSGIScriptAlias / /var/www/hostinfo/lib/python2.7/site-packages/hostinfo/wsgi.py
    <Directory /var/www/hostinfo>
        WSGIProcessGroup hostinfo
        WSGIApplicationGroup %{GLOBAL}
        Order deny,allow
        Allow from all
    </Directory>
    Alias /static/ /var/www/hostinfo/lib/python2.7/site-packages/django/contrib/admin/static/
</VirtualHost>
```

The `/static` alias is so that the admin interface has all its CSS and images, etc.