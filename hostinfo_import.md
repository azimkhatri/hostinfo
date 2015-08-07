# hostinfo\_import #

Import a hostinfo XML file
```
 hostinfo_import -[vk] file.xml
```
  * Specify _-v_ for verbose output
  * Specify _-k_ to not actually do anything - note that this will generally fail as it will look up keys that haven't actually been created yet.

To generate an appropriate XML file of all hosts:
```
  % hostinfo --xml --origin --showall > file.xml
```

You can also do a subset with all the normal options, such as _os=solaris_