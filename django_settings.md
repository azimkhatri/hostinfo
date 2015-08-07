These are all defined in settings.py.

See http://docs.djangoproject.com/en/dev/ref/settings/ for the full list and all their meanings.

Here are the ones that you will almost certainly want to change:

| **ADMINS** | A tuple containing the name of the person to received error messages | `ADMINS = ( ('Ann', 'ann@example.com'), ('Brian', 'brian@example.com') )` |
|:-----------|:---------------------------------------------------------------------|:--------------------------------------------------------------------------|
| **SECRET\_KEY** | A string of characters that is used for encrypting session information | `SECRET_KEY='ex-)...pjk98'`                                               |
| **TEMPLATE\_DIRS** | The directories that the web interface will look for templates       | `TEMPLATE_DIRS = ("/app/hostinfo/templates")`                             |
| **DEBUG**  | Should be set to False for all production or semi-production uses    | DEBUG = False                                                             |
| **DATABASES** | See below                                                            |

Also the DATABASES dictionary has a number of fields that will need to be changed.
| **ENGINE** | The type of database software to store the data in | `ENGINE='django.db.backends.mysql'` |
|:-----------|:---------------------------------------------------|:------------------------------------|
| **NAME**   | The name of the database that will be used         | `NAME='hostinfo'`                   |
| **USER**   | The name of the user within the database software that the hostinfo scripts will connect to the database as. This is not an operating system user | `USER='hostinfo_user'`              |
| **PASSWORD** | The database password for the '''USER'''           | `PASSWORD='django_secret'`          |