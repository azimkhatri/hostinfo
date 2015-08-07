These scripts get called by AutoUpdaters and live in the updaters path specified in the settings file.

The output needs to be in a specific format:

```
hostname key=value[,value]
```
which will update the key with the specified values for hostname

Lines beginning with a # are ignored as are blank lines

The origin of all changes made will be the name of the updater script