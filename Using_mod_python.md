# Introduction #

If you are using mod\_python you should probably look at [Using\_mod\_wsgi](Using_mod_wsgi.md) as mod\_python is fairly old and deprecated.

# Details #

Add the following to your apache config:
```
<Location "/hostinfo">
  SetHandler python-program
  PythonHandler django.core.handlers.modpython
  SetEnv DJANGO_SETTINGS_MODULE hostinfo.settings
  PythonPath "['/usr/local/lib/python', '/usr/local/lib/python/site-packages/'] + sys.path"
</Location>

<Location "/hostinfo-admin">
  SetHandler python-program
  PythonHandler django.core.handlers.modpython
  SetEnv DJANGO_SETTINGS_MODULE hostinfo.settings
  PythonPath "['/usr/local/lib/python', '/usr/local/lib/python/site-packages/'] + sys.path"
</Location>
```
Substitute the appropriate library path for `/usr/local/lib/python` if you have the hostinfo libs installed in another location.