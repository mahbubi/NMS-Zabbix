Step-Step:
```
# apt install snmp-mibs-downloader
```
Enabling MIB files
On RedHat-based systems the mib files should be enabled by default. On Debian-based systems you have to edit file /etc/snmp/snmp.conf and comment out the line that says mibs :

```
# As the snmp packages come without MIB files due to license reasons, loading
# of MIBs is disabled by default. If you added the MIBs you can reenable
# loading them by commenting out the following line.
#mibs :
```

Testing MIB files
Testing snmp MIBs can be done using snmpwalk utility. If you don't have it installed, use the following instructions.

On Debian-based systems:
```
# apt install snmp
# snmpwalk -v 2c -c public <NETWORK DEVICE IP> ifInOctets
```
Used options:
-v 2c	use SNMP protocol version 2c
-c public	specify SNMP community - “public”

Using custom MIB files
There are standard MIB files coming with every GNU/Linux distribution. But some device vendors provide their own.
```
# cp /path/to/file.mib /usr/share/snmp/mibs/file.mib
# service snmp restart
```
to search OID root
```
# snmptranslate -m Name module -Tz | egrep '"1\.3\.6\.1\.4\.1\.[0-9]+"'
or
# snmptranslate -m /usr/share/snmp/mibs/file.mib -Tz | egrep '"1\.3\.6\.1\.4\.1\.[0-9]+"'
```
install perl
```
# apt-get install perl*
```
copy source code
```
link : https://github.com/Akint/mib2template/blob/master/mib2template.pl
```
install prerequisites on Ubuntu: 
```
# apt-get install perl libxml-simple-perl libsnmp-perl
and install any required perl module
```
to change permission
```
# chmod +x ~/bin/mib2template.pl
```
command to run script
```
# ./mib2template.pl --module NAME_MODULE --root 1.3.6.1.4.1.12356 --group template > mibForti.xml
or
./mib2template.pl --module /usr/share/snmp/mibs/file.mib --root 1.3.6.1.4.1.12356 --group template > mibForti.xml
```
