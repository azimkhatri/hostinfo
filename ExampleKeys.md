A lot of the power of hostinfo comes from deciding what should be put into keys. The decision to put data into a key shouldn't be taken lightly, as each key effectively has a cost associated with it - which is the effort required to maintain the data in the key. Having a key that is only accurate 1 in 10 times is probably not worth it as no one will trust it.

The following is a list of example keys that have been created. Not all of these will be useful to everyone.

| **key** | **meaning**  | **examples** |
|:--------|:-------------|:-------------|
| alias   | What other names does the server have| ...          |
| apps    | what apps have been installed | apache, mysql |
| arch    | architecture of the cpu | i86pc, sun4u |
| bu\_policy| the backup policy for this server |              |
| class   | what class of host this is | prod, dev, test |
| console | How to get onto the console | ...          |
| cpuspeed | How fast the CPUs are on this server | 550\_mhz     |
| explorerdate | Date that the last explorer was taken of this host| 2011-01-17   |
| fscapacity | Filesystem capacity | 233          |
| fsused  | Filesystem actually used| 231          |
| hardware | the hardware model | sun\_v210    |
| hweosl  | End of service life for this hardware | 2009-5-31    |
| hwsupport | Hardware support vendor | Interactive, HP |
| hwsupport\_expiry | When does the hardware support run out | 2011-12-31   |
| ismailhost | Is this a mailhost? | True         |
| issuesfound | What issues have been found with the server | disk\_harderrors, fma\_critical |
| lastping | last day that the server was pinged. | 2009-05-29   |
| localfs | List of local filesystems | /, /var, /usr/local |
| logical\_location | Where in the network the server is | dmz, internal, loadbal |
| nics    | What NICs are in use| eth0, hme2   |
| numcpu  | how many cpus this device has | 1, 2, 4      |
| oracle\_sids | What Oracle database SIDs are active on this server | ...          |
| os      | the operating system |  solaris, linux, windows |
| osrev   | the revision of the OS |  5.10, 2.6.4 |
| patchdate | the date this system was last patched | 2011-01-18   |
| purpose | what is the primary purpose of this server | oracle, web  |
| python  | version of python installed | 2.7          |
| rack    | the rack which the server is installed in | sun10a       |
| rackpos | What position within the rack is the server | 34           |
| ram     | the amount of ram the host has | 2048         |
| satellite\_channel | Name of the base channel for redhat satellite | rhel5.5\_x64 |
| serial  | Serial number of the server| ....         |
| site    | which site the server is installed on  | 1060westaddison |
| status  | Status of server | active, beingbuilt, decommissioned |
| technologies | Unusual technologies in use | cluster, zfs, zfsroot, vxvm |
| type    | what sort of device this is | server, virtual, tape |
| uname   | the full uname -a output | ...          |
| vlan    | What vlans the server is on | ...          |
| virtualmaster | if this is a virtual server, what is the physical server that it lives on | ...          |
| vmtype  | what sort of virtual machine this is, if it is one | vmware, ldom, zone |
| wwn     | List of world wide numbers (WWN) on server | ...          |