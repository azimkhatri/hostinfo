There are a number of command line tools that allow unix admins and their scripts to read and write to the hostinfo database.

These commands are designed to be embedded into scripts - they will never ask for more input - everything is done on the command line.

# Commands #

  * [hostinfo](hostinfo.md) - access information in the database

## Host based commands ##
  * [hostinfo\_addhost](hostinfo_addhost.md) - add a new host to the database
  * [hostinfo\_renamehost](hostinfo_renamehost.md) - change the name of a host
  * [hostinfo\_mergehost](hostinfo_mergehost.md) - merge two hosts together into one
  * [hostinfo\_deletehost](hostinfo_deletehost.md) - remove a host from the database

## Value based commands ##
  * [hostinfo\_addvalue](hostinfo_addvalue.md) - add a new value to the database
  * [hostinfo\_deletevalue](hostinfo_deletevalue.md) - remove a value from the database
  * [hostinfo\_replacevalue](hostinfo_replacevalue.md) - replace an existing value with a new one

## Key based commands ##
  * [hostinfo\_addkey](hostinfo_addkey.md) - add a new key
  * [hostinfo\_showkey](hostinfo_showkey.md) - show the keys and their details

## Restricted value commands ##
  * [hostinfo\_addrestrictedvalue](hostinfo_addrestrictedvalue.md) - Add a new possible value to a restricted value key
  * [hostinfo\_deleterestrictedvalue](hostinfo_deleterestrictedvalue.md) - Remove a possible value from a restricted value key
  * [hostinfo\_listrestrictedvalue](hostinfo_listrestrictedvalue.md) - List all the possible values for a restricted value key

## Alias commands ##
  * [hostinfo\_addalias](hostinfo_addalias.md) - Add a new alias to an existing host
  * [hostinfo\_deletealias](hostinfo_deletealias.md) - Delete an alias from a host
  * [hostinfo\_listalias](hostinfo_listalias.md) - List the aliases that a host has

## Misc commands ##
  * [hostinfo\_undolog](hostinfo_undolog.md) - access the undo log if you made a mistake
  * [hostinfo\_history](hostinfo_history.md) - show the changes that have been made to a host
  * [link\_generator](link_generator.md) - generate links to other data sources
  * [hostinfo\_import](hostinfo_import.md) - import a previously exported XML dump of hostinfo