# hostinfo\_addvalue #

Add a new value to the hostinfo database
```
 % hostinfo_addvalue [opts] <key>=<value> <host> [<host>...]
  Opts: --update or --append
```

  * If you specify _--update_ it will replace an existing value; otherwise it will return an error if there is already a value for that key specified
  * If you specify _--append_ it will add a new value to an existing key that is defined as having multiple values
  * You cannot add values to a host that doesn't exist in the database yet (use [hostinfo\_addhost](hostinfo_addhost.md) to add new hosts to the database)
  * You should try to avoid having spaces in values as the make using hostinfo from the command line more difficult.
  * Everything will get converted to lowercase.
  * If you need to add a new key then look at [hostinfo\_addkey](hostinfo_addkey.md)
  * If you are doing a lot of these, especially from a script, then add _--origin=_

&lt;scriptname&gt;

