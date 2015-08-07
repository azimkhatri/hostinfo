# Introduction #
Instead of invoking the command line scripts from within python which has the cost of forking a new process and the hassle of parsing the output this little bit of code lets you access the hostinfo data directly.

I will put this in the code tree at some point; and add more features

# Details #
Obviously you will need to change the path.
You can call it like
```
 getHostinfo('os=linux', environment='uat')
 getHostinfo('os!=linux')
```

```python

#!/usr/bin/env python2.7
import sys
sys.path.append('/var/www/hostinfo/lib/python2.7/site-packages')

from django.core.management import setup_environ
from hostinfo import settings
setup_environ(settings)
from hostinfo.hostinfo.models import getMatches, parseQualifiers
from hostinfo.hostinfo.models import KeyValue, Host

################################################################################
def getHostinfo(*args, **kwargs):
""" Return a dictionary of dictionaries for each hostinfo host that matches the
args/kwargs.
Call like:
getHostinfo(environment='uat')
getHostinfo('os!=linux')
{ 'hostA': { 'keyA': ['val1', 'val2'], 'keyB': ['val2']}, 'hostB': {...}}
"""

args=list(args)
ans={}
for k,v in kwargs.items():
args.append("%s=%s" % (k,v))
qualifiers=parseQualifiers(args)
matches=getMatches(qualifiers)
for hostid in matches:
host={}
hostname=Host.objects.get(id=hostid).hostname
for k in KeyValue.objects.filter(hostid=hostid):
keyname=k.keyid.key
if keyname not in host:
host[keyname]=[]
host[keyname].append(k.value)
ans[hostname]=host
return ans

################################################################################
if __name__=="__main__":
print getHostinfo(environment='uat')
print getHostinfo('environment=uat')

#EOF
```