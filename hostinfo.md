# hostinfo #

The hostinfo command is the command to get output from the hostinfo database.
## hostinfo expressions ##

### Summary ###

| **Type** | **Expression** | **Alternative Form** | **Example** | **Meaning** |
|:---------|:---------------|:---------------------|:------------|:------------|
| Equality | key=value      | key.eq.value         | use=apache  | Used for apache |
| Inequality | key!=value     | key.ne.value         | os!=solaris | OS isn't Solaris |
| Less than | key<value      | key.lt.value         | warrantydate<2009-01-01 | Warranty ends before the start of 2009 |
| Greater than | key>value      | key.gt.value         | patchdate>2007-01-01 | System has been patched since the start of 2007 |
| Contains | key~value      | key.ss.value         | serial~123  | Serial number has '123' somewhere in it |
| Not contains | key%value      | key.ns.value         | serial%456  | Serial number doesn't have '456' somewhere in it |
| Defined  |                | key.defined          | hardware.defined | The hardware is known |
| Undefined |                |key.undef             | buvers.undefined | No idea what the backup version is |
| Host like |                | name.hostre          | oleweb.hostre | All hosts that have 'oleweb' in their name |
| Host is  |                | name                 | hawk        | The single host called 'hawk' |

#### Equality ####
_key=value_ or _key.eq.value_

Match all hosts that have _key_ set to _value_.

```
% hostinfo os=solaris
```

  * If a key is a list of values, then if any of them match the host will be considered a match

#### Inequality ####
_key!=value_ or _key.ne.value_

Match all hosts that have _key_ not equal to _value_

```
% hostinfo os!=solaris
```

  * If a key is a list of values, then if any of them match the host will be considered not a match
  * If a host has no associated key then it will be considered a match

#### Less than ####
_key<value_ or _key.lt.value_

Match all hosts that have _key_ less than (or equal to) _value_

```
% hostinfo instdate.lt.2007-01-30
```

  * Most values don't evaluate to anything useful - dates are the large exception

#### Greater than ####
_key>value_ or _key.gt.value_

Match all hosts that have _key_ greater than (or equal to) _value_

> ` % hostinfo instdate.gt.2007-12-31`

  * Most values don't evaluate to anything useful - dates are the large exception
  * This is actually >=

#### Contains (or substring) ####
_key~value_ or _key.ss.value_

Match all hosts where _value_ is a substring, or is contained by the hosts value for _key_.

```
% hostinfo serial~421
```

#### Undefined ####
_key.undef_

Match all hosts that don't have a value set for the _key_

```
% hostinfo buver.undef
```

#### Defined ####
_key.def_

Match all hosts that have a value set for _key_

```
% hostinfo zones.def
```

#### hostname ####
_hostname_

#### Hostname contains ####
_name.hostre_
Match hosts that have _name_ as part of their hostnames
```
% hostinfo opsdbc.hostre
```

#### Hostname ####
_hostname_
Match the host that is _hostname_

```
% hostinfo hawk
```

  * You can only specify one host
  * Matches the one host that matches the name exactly

#### AND Conditions ####
```
% hostinfo os=solaris rev!=5.10
```

  * Just add the conditions and it will take the AND of all of the expressions

#### OR Conditions ####

```
% hostinfo rev=5.9; hostinfo rev=5.10
```

  * Not explicitly supported, you need to run hostinfo multiple times

## hostinfo output ##
By default hostinfo just outputs the names of the matching hosts, one per line.

You can get more information out if you require it. Each of these methods can be joined with the expressions above.

  * Values of explicit keys: _-p < key >_

```
 % hostinfo -p site -p rack
 ...
 cordb16904p site=300exhibition rack=1/u3/r8
 cordb26901s site=1822dandenong rack=cm26/r02
 ...
```

  * Can have multiples
  * If the matching host doesn't have that key, it will output _< key >=_

### specifying the separator ###
By default items in a list are separated with a comma. Occasionally this is not the desired option. If you want to use a different separator you can with the _--sep <sep str>_ option.

Note that the separator specified can be more than a single character if you desire

### showall ###
You can get hostinfo to show everything that it knows about the hosts that match the conditions.
```
 % hostinfo --showall hawk
 hawk
  buserver: sunbak03
  buver: 7.1.2.build.325
  hardware: v880
  os: solaris
  rack: 1/ay21/r2
  rev: 5.8
  serial: 12345678
  site: 300exhibition
  type: server
```

  * If you add a _--origin_ to the showall it will also tell you where the data (both host and keys) came from. This only works in the long showall output, not in the CSV formatted output.
  * If you add a _--times_ to the showall it will tell you creation and modification times for the data. This only works in the long showall output, not in the CSV formatted output.

### Output in CSV or XML formats ###
```
 % hostinfo --csv -p hardware -p rev os=solaris
 hostname,hardware,rev
 acrobat2-syd_inst01,v20z,
 acrobat5-syd_inst01,v20z,5.9
 ...
```

  * If there is no value for a key then it will be left blank
  * If there are multiple values for a key then they will be comma separated within quotes.

  * Output in CSV format without the header line

```
 % hostinfo --noheader --csv -p hardware -p rev os=solaris
 acrobat2-syd_inst01,v20z,
 acrobat5-syd_inst01,v20z,5.9
 ...
```
  * These can be combined to report everything about everything

```
 % hostinfo --csv --showall
 hostname,use,rev,console,asset,os,support,apps,site,rack,hardware,...
 ...
 corapp26201s,,,t1-con-01 2021,105904,,interactive,,1822dandenong,cm26/r04,v440,...
 ...
```
  * You can use all the same options by using _--xml_ instead of _--csv_.

### valuereport output ###
If you put a _--valuereport < key >_ in the option list, followed by the normal list of conditions you will get the breakdown of the values for the key specified for all the hosts matching the condition:
```
 % hostinfo --valuereport <key> <cond> <cond>
```

E.g.
```
 % hostinfo --valuereport hardware os=solaris site=300exhibition arch.ns.sun4
 hardware set: 131 100.00%
 hardware unset: 0 0.00%

 ibm_x345 1 0.76%
 ibm_x346 3 2.29%
 …
 sun_x4100 77 58.78%
 sun_x4600 26 19.85%
```