## DIR ##
Top directory of hostinfo source
<dl>
<dt>MANIFEST.in</dt><dd>Details which files to include in the python package</dd>
<dt>README</dt><dd>Read it</dd>
<dt>setup.py</dt><dd>Python setup file used to install the code and build packages</dd>
</dl>

### DIR/bin ###
Directory for all the scripts that are the command line interface to hostinfo

### DIR/contrib ###
Contributed code that will not apply to all organisations but that may be useful to adapt for specific requirements.

<dl>
<dt>hostinfo.php</dt> <dd> </dd>
<dt>ListExpander.php</dt> <dd> </dd>
</dl>

#### DIR/contrib/dataload ####
Contribution code on importing large amounts of data from other sources
<dl>
<dt>csv2hostinfo.py</dt> <dd> </dd>
<dt>newhost.py</dt> <dd> </dd>
<dt>referential_integrity.py</dt> <dd> </dd>
<dt>wikiImport.py</dt> <dd>Maintain a wiki page per host in hostinfo</dd>
<dt>wikiImport.template</dt> <dd>Template for wikiImport.py</dd>
<dt>xls2hostinfo.py</dt> <dd> </dd>
</dl>

### DIR/docs ###
Documentation

### DIR/hostinfo ###
Python code

<dl>
<dt>manage.py</dt> <dd> </dd>
<dt>settings.py.dist</dt> <dd>Configuration file - See <a href='django_settings.md'>Django Settings</a> for more details about the settings</dd>
<dt>urls.py</dt> <dd> Directs urls into the hostinfo code base - allows the same web itnerface to run multiple django applications</dd>
</dl>

#### DIR/hostinfo/backends ####
Different methods to authenticate users on the web interface live here
<dl>
<dt>ActiveDirectoryBackend.py</dt> <dd>Authenticate against Active Directory </dd>
<dt>ldapBackend.py</dt> <dd>Authenticate against LDAP </dd>
</dl>

#### DIR/hostinfo/hostinfo ####
<dl>
<dt>admin.py</dt> <dd> Django definitions allowing the underlying database to be modified using the Django admin interface (<a href='http://*/hostinfo-admin'>http://*/hostinfo-admin</a>)</dd>
<dt>audit.py</dt> <dd> Code that updates the audit trails on changes, taken from <a href='http://code.djangoproject.com/wiki/AuditTrail'>http://code.djangoproject.com/wiki/AuditTrail</a> </dd>
<dt>forms.py</dt> <dd> Code to handle forms for the web interface</dd>
<dt>links</dt> <dd> </dd>
<dt>models.py</dt> <dd><a href='DjangoModels.md'>Django / Database model definitions</a> and shared methods</dd>
<dt>urls.py</dt> <dd>django code to map the URL in the web interface to the code in the views.py to execute </dd>
<dt>views.py</dt> <dd>Code that does most of the web and some of the wiki interface</dd>
</dl>

##### DIR/hostinfo/hostinfo/autoupdaters #####
Where the scripts that will automatically update details of hosts should
live. These should certainly be in the contrib area as they will change
from organisation to organisation.

##### DIR/hostinfo/hostinfo/converters #####
Where the scripts that convert the various keys for excel importing
live. These should be in the contrib area as they will change from
organisation to organisation.

##### DIR/hostinfo/hostinfo/links #####
Where the scripts that generate the links live. These should be in the
contrib area as they will change from organisation to organisation.

##### DIR/hostinfo/hostinfo/reports #####
Where report scripts go. These should be in the contrib area.

##### DIR/hostinfo/hostinfo/templates #####
Where the wiki and web interface templates go

##### DIR/hostinfo/hostinfo/templatetags #####
Extensions to Django tags that are used in the templates

### DIR/reports ###
Should be removed