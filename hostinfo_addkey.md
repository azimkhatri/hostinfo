# hostinfo\_addkey #

Add a new key to the hostinfo database
```
 % hostinfo_addkey [--restricted] [--readonly] [--noaudit] <keyname> [<keytype> [<desc>]]
```

  * Keytype should be one of
    * single
    * list
    * date
  * Think carefully before adding a new key, and make sure that there isn't already a key that does the same thing under a different name
  * If you specify _--restricted_ then you can only assign values to this key that have been authorised by the use of [hostinfo\_addrestrictedvalue](hostinfo_addrestrictedvalue.md)
  * If you specify _--readonly_ then the you will not be able to change the value without specifying another argument to [hostinfo\_addvalue](hostinfo_addvalue.md).
  * If you specify _--noaudit_ then no audit trail will be kept of changes to this key. This is useful for keys that change often and where a history isn't very useful - for example a key containing the last day the host was pinged.
  * After creating a new key you should document in your own operational documents what the key is for, how it gets provisioned, etc.