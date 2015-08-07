## Status Table ##
Need to add the concept of a status table in the core database.

This will have the following fields (with better names):
  * caller
  * status
  * date
  * output string

This will keep the status of all the various automated jobs that run, such as link generators, or auto updaters. The
name of the script gets put into the caller field.

Every script should have consistent return codes:
  * 0 - OK
  * 1 - Warning
  * 2 - Critical
  * 3 - Unknown
The return code goes into the status field

The date the script returned should get put into the date field.

The script should also only print to stdout the status message. This gets put into the output string field

## Reporting ##
Obviously if there is a status table there needs to be some way to report on it

## Cleanup ##
There has to be an automated process that cleans up entries in this table (and others such as the audit tables) after a certain time period. Obviously the status of the cleanup process gets added to the status table.