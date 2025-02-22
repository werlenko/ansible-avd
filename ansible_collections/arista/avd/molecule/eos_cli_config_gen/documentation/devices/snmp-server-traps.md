# snmp-server-traps
# Table of Contents
<!-- toc -->

- [Management](#management)
  - [Management Interfaces](#management-interfaces)
- [Authentication](#authentication)
- [Monitoring](#monitoring)
  - [SNMP](#snmp)
- [Internal VLAN Allocation Policy](#internal-vlan-allocation-policy)
  - [Internal VLAN Allocation Policy Summary](#internal-vlan-allocation-policy-summary)
- [Interfaces](#interfaces)
- [Routing](#routing)
  - [IP Routing](#ip-routing)
  - [IPv6 Routing](#ipv6-routing)
- [Multicast](#multicast)
- [Filters](#filters)
- [ACL](#acl)
- [Quality Of Service](#quality-of-service)

<!-- toc -->
# Management

## Management Interfaces

### Management Interfaces Summary

#### IPv4

| Management Interface | description | Type | VRF | IP Address | Gateway |
| -------------------- | ----------- | ---- | --- | ---------- | ------- |
| Management1 | oob_management | oob | MGMT | 10.73.255.122/24 | 10.73.255.2 |

#### IPv6

| Management Interface | description | Type | VRF | IPv6 Address | IPv6 Gateway |
| -------------------- | ----------- | ---- | --- | ------------ | ------------ |
| Management1 | oob_management | oob | MGMT | -  | - |

### Management Interfaces Device Configuration

```eos
!
interface Management1
   description oob_management
   vrf MGMT
   ip address 10.73.255.122/24
```

# Authentication

# Monitoring

## SNMP

### SNMP Configuration Summary

| Contact | Location | SNMP Traps | State |
| ------- | -------- | ---------- | ----- |
| DC1_OPS | DC1 | All | Disabled |
| DC1_OPS | DC1 | bgp, bridge, lldp, mpls, msdp backward-transition, msdp established, snmp link-down, snmpConfigManEvent | Enabled |
| DC1_OPS | DC1 | bgp arista-backward-transition, bridge arista-mac-age | Disabled |

### SNMP VRF Status

| VRF | Status |
| --- | ------ |
| default |  Disabled  |
| MGMT |  Enabled  |

### SNMP Device Configuration

```eos
!
snmp-server contact DC1_OPS
snmp-server location DC1
snmp-server enable traps bgp
no snmp-server enable traps bgp arista-backward-transition
snmp-server enable traps bridge
no snmp-server enable traps bridge arista-mac-age
snmp-server enable traps lldp
snmp-server enable traps mpls
snmp-server enable traps msdp backward-transition
snmp-server enable traps msdp established
snmp-server enable traps snmp link-down
snmp-server enable traps snmpConfigManEvent
no snmp-server vrf default
snmp-server vrf MGMT
```

# Internal VLAN Allocation Policy

## Internal VLAN Allocation Policy Summary

**Default Allocation Policy**

| Policy Allocation | Range Beginning | Range Ending |
| ------------------| --------------- | ------------ |
| ascending | 1006 | 4094 |

# Interfaces

# Routing

## IP Routing

### IP Routing Summary

| VRF | Routing Enabled |
| --- | --------------- |
| default | false|
### IP Routing Device Configuration

```eos
```
## IPv6 Routing

### IPv6 Routing Summary

| VRF | Routing Enabled |
| --- | --------------- |
| default | false |

# Multicast

# Filters

# ACL

# Quality Of Service
