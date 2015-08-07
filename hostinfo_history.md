# hostinfo\_history #

Show the history of changes made to a host
{{
> % /app/hostinfo/bin/hostinfo\_history [opts](opts.md) host
}}
Options are:
  * _--origin_ will reveal the origin of the change
  * _--actor_ will reveal what program (or actor) made the change
  * When a host is deleted all the history around its keys will be deleted
  * This will not track certain changes such as aliases