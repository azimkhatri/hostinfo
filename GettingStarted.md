Once you have hostinfo installed and running then what do you do with it?

You should have a think about the things that you want to be able
to ask about your servers. The most obvious questions are:

  * Where are the servers?
  * What are they (hardware wise)?
  * Operating system details (uname output)
  * What do they do?

For each of these questions you need to create keys that allow the
answer to be stored. These will be different for each person. For
example if you only have one data centre you don't need to record
which site a server is at; if you have lots of data centres you may
need to store what state or even country that they are in.

As most location information is inherently single valued (a server
can't be in multiple locations at the same time) create the location
keys as single valued.

For example:
```
hostinfo_addkey rack single What rack the server is in
```

One of the important things to remember when creating keys and
populating them is that hostinfo only is useful if you are consistent
in the values that you use. For example if you put the hardware of
a server as 'v240' and someone else uses 'sun\_v240' then a human
can tell that these probably refer to the same thing, but hostinfo
can't. Define a standard and stick to it. You can always change it
later (with the use of hostinfo\_replacevalue) but it is going to
be less effort to get it right the first time.

You can also use restricted value keys to make sure that people
stick to the standard.  So if you have come up with a list of
hardware types that you want to stick to:

```
hostinfo_addkey --restricted hardware single What sort of hardware is it
```
then for every hardware type that you know about:

```
hostinfo_addrestrictedvalue hardware=sun_v240
```

Restricted value keys are about stopping inconsistencies through
typos or other issues. They are not about stopping people doing
what they need to do. That is why it is really easy to add new
allowed values to a restricted key.

Once you have a basic set of keys created - you can always create
more as you need them - it is time to start adding hosts and data
about those hosts. For hosts that have multiple names, I recommend
that you use the 'uname -n' output without any domain information,
and use aliases to add the other names.

```
hostinfo_addhost hostA
hostinfo_addalias hostA webserv01
```

Then add details that you know about that host
```
hostinfo_addvalue hardware=sun_v240 hostA
```

Most of the details that come out of uname (for unix servers) should
probably have keys associated with them. This also makes it easy
to automate the population of hostinfo. Suggested keys:
  * os - operating system (uname -s)
  * osrev - revision of operating system (uname -r)
  * arch - architecture of machines (uname -m) - useful if you have OS's that run on different architectures (e.g. solaris on sun4u/i86pc; linux on pretty much everything)