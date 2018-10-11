# Idrac-cheat-sheet
Useful commands for remote Idrac configuration (tested Integrated Dell Remote Access Controller 8/7 Version 2.60.60.60)

To configure local Idrac, remove -r


Replace values with yours :
* $IPADDRESSIDRAC = IP address of idrac card
* $USERIDRAC = User to connect to idrac card
* $PWDIDRAC = User password

```bash
# Change hostname on remote host
$ racadm -r $IPADDRESSIDRAC -u $USERIDRAC -p $PWDIDRAC config -g ifcRacManagedNodeOs -o ifcRacMnOsHostname $NEWNAME

# Change DNS Idrac name
$ racadm -r $IPADDRESSIDRAC -u $USERIDRAC -p $PWDIDRAC set iDRAC.NIC.DNSRacName $NEWNAME

# Change DNS IP Address
$ racadm -r $IPADDRESSIDRAC -u $USERIDRAC -p $PWDIDRAC set iDRAC.IPv4.DNS1 192.168.0.5
$ racadm -r $IPADDRESSIDRAC -u $USERIDRAC -p $PWDIDRAC set iDRAC.IPv4.DNS2 192.168.0.6

# Set DNS domain
$ racadm -r $IPADDRESSIDRAC -u $USERIDRAC -p $PWDIDRAC set iDRAC.Nic.DNSDomainName $DOMAIN

# Reset Idrac card
$ racadm -r $IPADDRESSIDRAC -u $USERIDRAC -p $PWDIDRAC racreset

# Clear all job queue
$ racadm -r $IPADDRESSIDRAC -u $USERIDRAC -p $PWDIDRAC jobqueue delete --all

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

# Enable global alerts
$ racadm -r $IPADDRESSIDRAC -u $USERIDRAC -p $PWDIDRAC set iDRAC.IPMILan.AlertEnable 1

# Enable email alerts slot 1
$ racadm -r $IPADDRESSIDRAC -u $USERIDRAC -p $PWDIDRAC set iDRAC.EmailAlert.Enable.1 1

# Set email address to receive alerts
$ racadm -r $IPADDRESSIDRAC -u $USERIDRAC -p $PWDIDRAC set iDRAC.EmailAlert.Address.1 mail@example.com

# Configure SMTP email server address settings
$ racadm -r $IPADDRESSIDRAC -u $USERIDRAC -p $PWDIDRAC set iDRAC.RemoteHosts.SMTPServerIPAddress 127.0.0.1

# Test sending email alert slot 1
$ racadm -r $IPADDRESSIDRAC -u $USERIDRAC -p $PWDIDRAC testemail -i 1

# List all alerts
$ racadm -r $IPADDRESSIDRAC -u $USERIDRAC -p $PWDIDRAC eventfilters get -c idrac.alert.all

# Enable all available sending alert method for config critical severity
$ racadm -r $IPADDRESSIDRAC -u $USERIDRAC -p $PWDIDRAC eventfilters set -c idrac.alert.config.critical -a none -n email,snmp,ws-events,redfish-events,remotesyslog,oslog

# Enable all available sending alert method for system critical severity
$ racadm -r $IPADDRESSIDRAC -u $USERIDRAC -p $PWDIDRAC eventfilters set -c idrac.alert.system.critical -a none -n email,snmp,ws-events,redfish-events,remotesyslog,oslog

# Enable all available sending alert method for audit critical severity
# Will show Few alert settings have failed, but it's ok since Audit - Software Change can't be set
$ racadm -r $IPADDRESSIDRAC -u $USERIDRAC -p $PWDIDRAC eventfilters set -c idrac.alert.audit.critical -a none -n email,snmp,ws-events,redfish-events,remotesyslog,oslog

# Enable all available sending alert method for storage critical severity
$ racadm -r $IPADDRESSIDRAC -u $USERIDRAC -p $PWDIDRAC eventfilters set -c idrac.alert.storage.critical -a none -n email,snmp,ws-events,redfish-events,remotesyslog,oslog

```
