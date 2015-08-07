# hostinfo\_undolog #

Print out a list of commands to undo actions taken
```
 hostinfo_undolog [opts]
  --days=<numdays
  --user=<username>
  --week
```

  * By default will do your commands for a day
  * Specifying _--week_ will make it go back seven days
  * Specifying _--days=< numdays >_ will make it go back that number of days
  * Specifying _--user=< username >_ will print out another users undolog
  * Don't blindly execute the commands, review them before acting on them