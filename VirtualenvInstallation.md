# Introduction #

[Virtualenv](https://pypi.python.org/pypi/virtualenv) is a great way to install python software so that it is independent of other python installations.


# Details #
```
$ cd /var/www
$ virtualenv hostinfo
$ cd hostinfo && source bin/activate
$ pip install Django
$ pip install http://hostinfo.googlecode.com/files/hostinfo-1.30.tar.gz
--- Either ---
$ pip install psycopg2
--- or ---
$ pip install mysql-python
```

Edit `./lib/python/site-packages/hostinfo/settings.py` as per instructions in [Django Settings](django_settings.md)

I also found that when using mod\_wsgi I needed to modify `lib/python2.7/site-packages/hostinfo/wsgi.py` and add the following lines near the top:
```
import site
site.addsitedir('/var/www/hostinfo/lib/python2.7/site-packages')
```
Obviously change the path to where you installed hostinfo.

Once you have the database access set up
```
django-admin.py syncdb --settings hostinfo.settings
```