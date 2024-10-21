# Zabbix template for Palo Alto Networks Next-Generation firewall

## Overview

The template to monitor Palo Alto Networks NGFW PAN-OS by Zabbix v.7.0 using SNMP v2c or SNMPv3. For use with a different Zabbix version please choose corresponding branch.

This template is linked with official zabbix template: [Network Generic Device by SNMP](https://git.zabbix.com/projects/ZBX/repos/zabbix/browse/templates/net/generic_snmp?at=refs%2Fheads%2Frelease%2F7.0).

This template was tested on:

- PAN-OS, version 9.1
- PAN-OS, version 10.0
- PAN-OS, version 10.1
- PAN-OS, version 10.2
- PAN-OS, version 11.0

## Setup

> See [Zabbix templates importing](https://www.zabbix.com/documentation/7.0/en/manual/xml_export_import/templates#importing) for basic instructions on how to import a template.

Create a NGFW host and link this template to it.

## Zabbix configuration

- Set/change the SNMP settings to match your community string (SNMPv2c) or Security name, security level ... (SNMPv3). See [CONFIGURING SNMP MONITORING](https://www.zabbix.com/documentation/current/manual/config/items/itemtypes/snmp#configuring_snmp_monitoring)
- Set SNMP settings on the NGFW and commit. See [Enable SNMP Monitoring] (https://docs.paloaltonetworks.com/pan-os/10-0/pan-os-web-interface-help/device/device-setup-operations/enable-snmp-monitoring.html)

## Interface monitoring

Interfaces monitored by template **Network Generic Device by SNMP**

## Discovery rules

|Name|Description|Type|Key and additional info|
|----|-----------|----|----|
|DISK Discovery |<p>Discovery for disk partitions</p> |SNMP agent |vfs.storage.partitions<p>**Filter**:</p><p>based on `SNMP walk storage table` item, MATCHES_REGEX `.1.3.6.1.2.1.25.2.1.4`</p> |
|FAN Discovery |<p>Discovery for fans</p> |SNMP agent |entPhysicalDescr[FAN]<p>**Filter**:</p><p>{#SNMPVALUE} MATCHES_REGEX `{Fan}`</p> |
|POWER Discovery |<p>Discovery for power supplies</p> |SNMP agent |entPhysicalDescr[POWER]<p>**Filter**:</p><p>{#SNMPVALUE} MATCHES_REGEX `{Power}`</p> |
|TEMPERATURE Discovery |<p>Discovery of temperature sensors</p> |SNMP agent |entPhysicalDescr[TEMPERATURE]<p>**Filter**:</p><p>{#SNMPVALUE} MATCHES_REGEX `{Temperature}`</p> |

## Items collected

|Name|Description|
|----------|--------------|
|App-ID content date |<p>Currently installed application definition release date. If no release date is found, unknown is returned.</p> |
|App-ID Version |<p>Currently installed application definition version. If no application definition is found, 0 is returned.</p> |
|Chassis type |<p>Chassis type for this Palo Alto device.</p> |
|Global Protect Client Version |<p>Currently installed global-protect client package version. If package is not installed, 0.0.0 is returned.</p> |
|GP active tunnels |<p>Number of active tunnels.</p> |
|GP gateway utilization |<p>GlobalProtect Gateway utilization percentage.</p> |
|GP tunnels supported |<p>Max tunnels allowed.</p> |
|HA Mode |<p>Current high-availability mode (disabled, active-passive, or active-active).</p> |
|HA Peer State |<p>Current peer high-availability state.</p> |
|HA State |<p>Current high-availability state.</p> |
|HW Version |<p>Hardware version of the unit.</p> |
|Memory utilization |<p>calculated item </p> |
|PAN-OS Version |<p>Full software version. The first two components of the full version are the major and minor versions. The third component indicates the maintenance release number.</p> |
|Processor 1 Load (mgmt) |<p>The average, over the last minute, of the percentage of time that this processor was not idle. Implementations may approximate this one minute smoothing period if necessary.</p> |
|Processor 2 Load (data) |<p>The average, over the last minute, of the percentage of time that this processor was not idle. Implementations may approximate this one minute smoothing period if necessary.</p> |
|Serial Number |<p>The serial number of the unit. If not available, an empty string is returned.</p> |
|Session table utilization |<p>Session table utilization percentage. Values should be between 0 and 100.</p> |
|SNMP walk storage table |<p>SNMP extract of `HOST-RESOURCES-MIB::hrStorageTable`, used for disk discovery</p> |
|Threat Version |<p>Currently installed threat definition version. If no threat definition is found, 0 is returned.</p> |
|Total active ICMP sessions |<p>Total number of active ICMP sessions.</p> |
|Total active sessions |<p>Total number of active sessions.</p> |
|Total active TCP sessions |<p>Total number of active TCP sessions.</p> |
|Total active UDP sessions |<p>Total number of active UDP sessions.</p> |
|Total Memory |<p>Memory installed in system.</p> |
|Total supported sessions |<p>Total number of sessions supported.</p> |
|URL Filtering Version |<p>Currently installed URL filtering version. If no URL filtering is installed, 0 is returned.</p> |
|Used Memory |<p>Memory actually used by system.</p> |

## Triggers

Appropriate triggers are associated with the items

## Feedback

Please report any issues with the template here in the "Issues" tab.
