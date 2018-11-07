# Idrac-cheat-sheet
Useful commands for Idrac configuration

Replace values with yours :
* $IPADDRESSIDRAC = IP address of idrac card
* $USERIDRAC = User to connect to idrac card
* $PWDIDRAC = User password

```bash
# Change hostname on remote host
$ racadm -r $IPADDRESSIDRAC -u $USERIDRAC -p $PWDIDRAC config -g ifcRacManagedNodeOs -o ifcRacMnOsHostname $NEWNAME

# Change DNS Idrac name
$ racadm -r $IPADDRESSIDRAC -u $USERIDRAC -p $PWDIDRAC set iDRAC.NIC.DNSRacName $NEWNAME

# Reset Idrac card
$ racadm -r $IPADDRESSIDRAC -u $USERIDRAC -p $PWDIDRAC racreset

# Get info
$ racadm -r $IPADDRESSIDRAC -u $USERIDRAC -p $PWDIDRAC getsysinfo

# Set timezone
$ racadm -r $IPADDRESSIDRAC -u $USERIDRAC -p $PWDIDRAC set iDRAC.TIME.Timezone Europe/Paris

# Set NTP address
$ racadm -r $IPADDRESSIDRAC -u $USERIDRAC -p $PWDIDRAC set iDRAC.NTPConfigGroup.NTP1 $IPaddress

# Enable NTP
$ racadm -r $IPADDRESSIDRAC -u $USERIDRAC -p $PWDIDRAC set iDRAC.NTPConfigGroup.NTPEnable Enabled

# Set static IP Address
$ racadm -r $IPADDRESSIDRAC -u $USERIDRAC -p $PWDIDRAC setniccfg -s $IP $Netmask $IPGateway

# Enabled remote syslog
$ racadm -r $IPADDRESSIDRAC -u $USERIDRAC -p $PWDIDRAC set iDRAC.SysLog.SysLogEnable Enabled

# Set remote syslog1 to syslog.example.com
$ racadm -r $IPADDRESSIDRAC -u $USERIDRAC -p $PWDIDRAC set iDRAC.SysLog.Server=syslog.example.com
```
