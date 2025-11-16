## Table des matières  
- [Liste des commandes](#liste-des-commandes)
  - [Commandes de changement de Mode](#commandes-de-changement-de-mode)
  - [Commandes de configuration de base](#commandes-de-configuration-de-base)
  - [Commandes de dépannage](#commandes-de-dépannage)
  - [Commandes de routage et VLAN](#commandes-de-routage-et-vlan)
  - [Commandes de DHCP](#commandes-de-dhcp)
  - [Commandes de sécurité](#commandes-de-sécurité)
  - [Commandes de Sécurité Supplémentaires](#commandes-de-sécurité-supplémentaires)
  - [Commandes de surveillance et journalisation](#commandes-de-surveillance-et-journalisation)
- [Liens externes](#liens-externes)

### Quick Snippets & Scripts
  - [Intialize](#intialize)
  - [Basic Config](#basic-config)
  - [Assign Static IP to Interface](#assign-static-ip-to-interface)
  - [Snippet: Enable Router DHCP Server](#snippet-enable-router-dhcp-server)
  - [Snippet: Enable Switch DHCP Server](#snippet-enable-switch-dhcp-server)
  - [Nuking (ROMMON, Password Recovery, etc)](#nuking-rommon-password-recovery-etc)
  - [Howto: File Transfer Over Console (linux / xmodem)](#file-transfer-over-console-linux--xmodem)
  - [Access Console over USB on Linux](#access-console-over-usb-on-linux)

  

### General Sections
  * [Basic Networking](#basic-networking)
    + [Basic Setup](#setup)
    + [Interfaces](#interfaces)
    + [DHCP](#dhcp)
  * [Intermediate Networking](#intermediate-networking)
    + [VLANs](#vlans)
    + [Trunks](#trunks)
    + [Etherchannel](#etherchannel)
    + [Dynamic Trunking Protocol (DTP)](#dtp-dynamic-trunking-protocol)
    + [Routing](#routing)
    + [Spanning Tree Protocol](#spaning-tree-protocol)
  * [Advanced Networking](#advanced-networking)
    + [OSPFv2](#ospfv2)
  * [How To's](#how-tos)
    + [FTP Server Usage](#ftp-server-usage)
    + [Access Console over USB on Linux](#access-console-over-usb-on-linux)
  * [Tools](#tools)

## Full Navigation

- [Table des matières](#table-des-matières)
  - [Quick Snippets \& Scripts](#quick-snippets--scripts)
  - [General Sections](#general-sections)
- [Full Navigation](#full-navigation)
- [Basic Networking](#basic-networking)
  - [Setup](#setup)
    - [Intialize](#intialize)
    - [Basic Switch Config](#basic-switch-config)
    - [Basic Router Config](#basic-router-config)
    - [Basic Config with Password Security](#basic-config-with-password-security)
    - [Basic Security](#basic-security)
    - [Configure SSH](#configure-ssh)
    - [Set Clock](#set-clock)
    - [Basic Hardening (Work Needed)](#basic-hardening-work-needed)
    - [Backup config over FTP](#backup-config-over-ftp)
    - [Backup config over console](#backup-config-over-console)
    - [Restore Config](#restore-config)
    - [Nuking (ROMMON, Password Recovery, etc)](#nuking-rommon-password-recovery-etc)
  - [Interfaces](#interfaces)
    - [Interface Selection](#interface-selection)
    - [Assign Static IP to Interface](#assign-static-ip-to-interface)
    - [Interface Ranges](#interface-ranges)
  - [Interface Verification](#interface-verification)
    - [Remove IP Addresses](#remove-ip-addresses)
  - [Console Port](#console-port)
    - [Change Console Baudrate](#change-console-baudrate)
  - [DHCP](#dhcp)
    - [Snippet: Enable Router DHCP Server](#snippet-enable-router-dhcp-server)
    - [Snippet: Enable Switch DHCP Server](#snippet-enable-switch-dhcp-server)
    - [Create DHCP Pool](#create-dhcp-pool)
    - [DHCP Verification](#dhcp-verification)
    - [Disable DHCP](#disable-dhcp)
    - [Re-enabled DHCP](#re-enabled-dhcp)
    - [Create VLAN DHCP](#create-vlan-dhcp)
    - [Verify DHCP Pool](#verify-dhcp-pool)
    - [Delete DHCP Pool](#delete-dhcp-pool)
- [Intermediate Networking](#intermediate-networking)
  - [VLANs](#vlans)
    - [VLAN Creation](#vlan-creation)
    - [Port Assignment](#port-assignment)
    - [IP Assignemnt](#ip-assignemnt)
    - [Verification](#verification)
    - [Voice and Data VLAN](#voice-and-data-vlan)
    - [Management VLAN](#management-vlan)
    - [Delete VLANS on file](#delete-vlans-on-file)
    - [Delete VLANS in memory](#delete-vlans-in-memory)
    - [Inter-VLAN Routing](#inter-vlan-routing)
  - [Trunks](#trunks)
    - [Create multi-switch vlan trunk](#create-multi-switch-vlan-trunk)
    - [Trunk Verification](#trunk-verification)
  - [EtherChannel](#etherchannel)
    - [Configure EtherChannel](#configure-etherchannel)
    - [Verify EtherChannel](#verify-etherchannel)
  - [DTP (Dynamic Trunking Protocol)](#dtp-dynamic-trunking-protocol)
    - [Configure DTP](#configure-dtp)
    - [Disable DTP](#disable-dtp)
    - [Verify DTP](#verify-dtp)
- [Advanced Networking](#advanced-networking)
  - [OSPFv2](#ospfv2)
    - [OSPF Router IDs](#ospf-router-ids)
      - [All Commands](#all-commands)
      - [Enable router OSPF process](#enable-router-ospf-process)
      - [Configure Loopback](#configure-loopback)
      - [Configure OSPF Router ID](#configure-ospf-router-id)
      - [Modify OSPF router ID](#modify-ospf-router-id)
    - [OSPF - Point-to-Point Networks](#ospf---point-to-point-networks)
      - [Network Command Syntax](#network-command-syntax)
      - [Configure OSPF With Network Command](#configure-ospf-with-network-command)
      - [Use Entire Gigabit Interfaces](#use-entire-gigabit-interfaces)
      - [Configure OSPF with `ip ospf`](#configure-ospf-with-ip-ospf)
      - [OSPF Passive Interfaces](#ospf-passive-interfaces)
      - [Find Designated Router and Backup](#find-designated-router-and-backup)
      - [Change OSPF from Broadcast to Point-to-Point](#change-ospf-from-broadcast-to-point-to-point)
      - [Loopback and P2P Networks](#loopback-and-p2p-networks)
    - [Multiaccess OSPF Networks](#multiaccess-ospf-networks)
      - [Configure OSPF Priority](#configure-ospf-priority)
    - [Modifying Single Area OSPF](#modifying-single-area-ospf)
      - [Adjusting Reference Bandwidth](#adjusting-reference-bandwidth)
      - [Manually Set OSPF Link Cost](#manually-set-ospf-link-cost)
      - [Show OSPF Hello Packet Intervals](#show-ospf-hello-packet-intervals)
      - [Set OSPF Hello Packet Intervals](#set-ospf-hello-packet-intervals)
      - [Set OSPF Dead Interval](#set-ospf-dead-interval)
    - [OSPF Default Routes](#ospf-default-routes)
      - [Propogate Default Route](#propogate-default-route)
      - [Verify Propogated Default Route](#verify-propogated-default-route)
    - [Verify Single-Area OSPF](#verify-single-area-ospf)
      - [Verify OSPF Neighbors](#verify-ospf-neighbors)
      - [Verify OSPF Protocols](#verify-ospf-protocols)
      - [Verify OSPF Process Info](#verify-ospf-process-info)
      - [Verify OSPF Interface Setting](#verify-ospf-interface-setting)
- [Liste des commandes](#liste-des-commandes)
  - [Commandes de changement de Mode](#commandes-de-changement-de-mode)
  - [Commandes de configuration de base](#commandes-de-configuration-de-base)
  - [Commandes de dépannage](#commandes-de-dépannage)
  - [Commandes de routage et VLAN](#commandes-de-routage-et-vlan)
  - [Commandes de DHCP](#commandes-de-dhcp)
  - [Commandes de sécurité](#commandes-de-sécurité)
  - [Commandes de Sécurité Supplémentaires](#commandes-de-sécurité-supplémentaires)
  - [Commandes de surveillance et journalisation](#commandes-de-surveillance-et-journalisation)
- [Liens externes](#liens-externes)

## Basic Networking

### Setup
---

#### Intialize

These commands wipe all config and reboot the device

```
erase startup-config
delete vlan.dat
reload
```

**Note:** Remeber to say "no" to saving running config on reload. If you say yes, running config will be saved and you wont be working with fresh config on reload.

#### Basic Switch Config

```
configure terminal
no ip domain-lookup
hostname S1
line console 0
logging synchronous
exit
banner motd $ Authorized Access Only! And Godzilla will beat Kong any day $
exit
copy running-config startup-config
```

#### Basic Router Config

```
configure terminal
no ip domain-lookup
hostname R1
line console 0
logging synchronous
exit
banner motd $ Authorized Access Only! And Godzilla will beat Kong any day $
exit
copy running-config startup-config
```

#### Basic Config with Password Security

_pastable_

```
configure terminal
no ip domain-lookup
hostname R1
line console 0
logging synchronous
exit
banner motd $ Authorized Access Only! And Godzilla will beat Kong any day $
exit
copy running-config startup-config
conf t
enable secret class
line console 0
password cisco
login
exit
line vty 0 4
password cisco
login
exit
service password-encryption
end
copy running-config startup-config
```

#### Basic Security

```
conf t
enable secret class
line console 0
password cisco
login
exit
line vty 0 4
password cisco
login
exit
service password-encryption
end
```

#### Configure SSH

```
show ip ssh
conf t
ip domain-name cisco.com
crypto key generate rsa

username admin secret ccna
line vty 0 15
transport input ssh
login local
exit
ip ssh version 2
exit
```

#### Set Clock

*Show Clock*

```
show clock
```

*Sets clock to eastern US time*

```
clock timezone EST -5
```

*Revert to Default Timezone*

```
no clock timezone
```

#### Basic Hardening (Work Needed)

```
conf t
! Logout timer
!
line con 0
 exec-timeout 5
line vty 0 4
 exec-timeout 5
 
exit

ip ssh time-out 60
ip ssh authentication-retries 3
end
```

#### Backup config over FTP

*Using included [FTP server](#ftp-server-usage)*

```
copy running-config startup-config
copy startup-config ftp://192.168.1.10/config.txt
```

#### Backup config over console

_coming soon_

#### Restore Config
```
copy ftp://192.168.1.10/config.txt running-config
```

#### Nuking (ROMMON, Password Recovery, etc)

*Perform a Boot Interupt to Recover a lost or unknown password*

**WARNING**: This operation will delete all current config on the device

1. Ensure Console Cable is connected at 9600 Baudrate
2. Backup config if you need
3. Unplug Power
4. Wait for a few seconds
5. Re-insert the power cord to the switch
6. Within 15 seconds, hold the `Mode` button until the green flashing light flashes amber and then returns to flashing green. Release the `Mode` button.
7. Something like the following should display:

    ```
    initialize the flash file system, and finish loading the operating system software#
    
    flash_init
    load_helper
    boot
    ```
8. Run `flash_init`
9. Run `copy flash:config.text flash:config.text.old`
10. Run `boot`

    The device should now boot with no config and grant you access to it.


### Interfaces
---


#### Interface Selection

*Assign and IP address to a port*
```
conf t
int f0/1
ip addr 192.168.10.11 255.255.255.0
end
```

#### Assign Static IP to Interface

```
cont t
int g0/0
ip addr 10.0.0.10 255.255.255.0
```

#### Interface Ranges

*Assign and IP address to a port*
```
conf t
int f0/1
ip addr 192.168.10.11 255.255.255.0
end
```

*Select Single Range and Assign to a VLAN*
```
conf t
int range f0/1-12
switchport mode access
switch access vlan 10
end
```

```
conf t
int range f0/13-24
switchport mode access
switchport access vlan 20
end
```

*Select Multiple Interface Ranges and Move to a VLAN*
```
conf t
int range f0/1-4,g0/1,f0/16-20
switchport mode access
switchport access vlan 10
end
```

### Interface Verification

```
show ip interface brief
```

*or*

```
show ip int br
```

#### Remove IP Addresses

```
conf t
int f0/1
no ip addr
end
```

### Console Port

#### Change Console Baudrate

```
conf t
line con 0
speed 115200
end
```

```
conf t
line con 0
speed 9600
end
```

### DHCP
---

#### Snippet: Enable Router DHCP Server

This snippet configures a DHCP Server on R1 and will hand out
IPs on the `10.0.0.1/24` network. Great for using an [FTP Server](#ftp-server-usage) with.

```
conf t
ip domain name cisco.com
ip dhcp excluded-address 10.0.0.1
ip dhcp pool test
network 10.0.0.0 255.255.255.0
default-router 10.0.0.1
end
```

#### Snippet: Enable Switch DHCP Server

```
ip dhcp pool test
network 10.0.0.0 255.255.255.0
domain-name cisco.com
default-router 10.0.0.1
dns-server 10.0.0.1
lease 4
ip dhcp snooping
ip dhcp-server 10.0.0.3
interface vlan 1
ip address 10.0.0.3
```

#### Create DHCP Pool

*Workaround for CCNA labs at Liberty University since we can't change the LAB IP addresses*

```
conf t
ip domain name cisco.com
ip dhcp excluded-address 10.0.0.1
ip dhcp pool managementpool
network 10.0.0.1 255.255.255.0
default-router 10.0.0.1
end
```

```
conf t
ip dhcp excluded-address 192.168.10.1
ip dhcp excluded-address 192.168.10.254
ip dhcp pool office-pool-1
network 192.168.10.0 255.255.255.0
default-router 192.168.10.1
dns-server 192.168.5.5
domain-name linux.org
end
```

#### DHCP Verification

```
show running-config | section dhcp
show ip dhcp binding
show ip dhcp server statistics
```

#### Disable DHCP

```
conf t
no service dhcp
end
```

#### Re-enabled DHCP

```
conf t
service dhcp
end
```

#### Create VLAN DHCP

*Creates a Seperate DHCP Pool for each VLAN*

*Create VLANS*
```
conf t
vlan 10
name Management
vlan 20
name Sales
vlan 30
name Operations
end
```

*Configure SVI's and IP Address*

| VLAN | IP Address     | Gateway      |
| ---- | -------------- | ------------ |
| 10   | 192.168.10.254 | 192.168.10.1 |
| 20   | 192.168.20.254 | 192.168.20.1 |
| 30   | 192.168.30.254 | 192.168.30.1 |

```
conf t
int vlan 10
ip address 192.168.10.254 255.255.255.0
ip default-gateway 192.168.10.1
no shut

int vlan 20
ip address 192.168.20.254 255.255.255.0
ip default-gateway 192.168.20.1
no shut

int vlan 30
ip address 192.168.30.254 255.255.255.0
ip default-gateway 192.168.30.1
no shut
end
```

*Add interfaces to VLANS, 8 ports per vlan*

```
conf t
int range f0/1-7
switchport mode access
switchport access vlan 10

int range f0/8-15
switchport mode access
switchport access vlan 20

int range f0/16-24
switchport mode access
switchport access vlan 30
end
```

*Create DHCP Pools for each vlan*

```
conf t
ip domain name cisco.com
ip dhcp excluded-address 192.168.10.1
ip dhcp pool vlan10pool
network 192.168.10.0 255.255.255.0
default-router 192.168.10.1
import all


ip dhcp excluded-address 192.168.20.1
ip dhcp pool vlan20pool
network 192.168.20.0 255.255.255.0
default-router 192.168.20.1
import all

ip dhcp excluded-address 192.168.30.1
ip dhcp pool vlan30pool
network 192.168.30.0 255.255.255.0
default-router 192.168.30.1
import all
end
```

Now when a device plugs into a port `f0/4` for instance and performs a DHCP request, it should get an IP like `192.168.10.3` because it is plugged into the ports assigned to VLAN 10

#### Verify DHCP Pool

```
show ip dhcp pool
```

#### Delete DHCP Pool

```
conf t
no ip dhcp pool managementpool
end
```

## Intermediate Networking

### VLANs
---

#### VLAN Creation

```
conf t
vlan 10
name Faculty
exit
```

```
conf t
vlan 20
name Students
exit
```

#### Port Assignment

```
conf t
interface range Fa0/1-12
switchport mode access
switchport access vlan 10
end
```

```
conf t interface range Fa0/13-24
switchport mode access
switchport access vlan 20
end
```

```
conf t
interface Gi0/1
switchport mode access
switchport access vlan 99
end
```

#### IP Assignemnt

```
cont t
int vlan 99
ip address 10.0.0.1 255.255.255.0
end
```

#### Verification

```
show vlan brief
```

#### Voice and Data VLAN

*Assuming Data on VLAN 10, Voice on VLAN 20*

```
conf t
int Fa0/4
switchport mode access
switchport access vlan 10
switchport voice vlan 20
end
```

#### Management VLAN

```
conf t
vlan 99
name Management
exit
interface Fa0/24
switchport mode access
switchport access vlan 99
exit
int vlan 99
ip addr 10.0.0.1 255.255.255.0
end
```

#### Delete VLANS on file

```
delete vlan.dat
```

#### Delete VLANS in memory
*Warning: Make sure you move ports to another vlan or the will be unsable*

```
conf t
no vlan 10
no vlan 20
end
```

#### Inter-VLAN Routing

*Creates multiple sub-interfaces on a router port to enable inter-vlan routing.*

*Note: `encapsulation dot1q` must be called on a sub interface before an IP can be assigned to it.*

```
conf t
interface G0/0/1.10
description Default Gateway for VLAN 10
encapsulation dot1Q 10
ip add 192.168.10.1 255.255.255.0
exit

interface G0/0/1.20
description Default Gateway for VLAN 20
encapsulation dot1Q 20
ip addr 192.168.20.1 255.255.255.0
exit

interface G0/0/1.99
description Default Gateway for VLAN 99
encapsulation dot1Q 99
ip addr 192.168.99.1 255.255.255.0
exit

interface G0/0/1
description Trunk link to S1
no shut
end
```

### Trunks
---

#### Create multi-switch vlan trunk

*S1*

```
conf t
interface Gi0/1
description Trunk Line to S2 Gi0/1
switchport mode trunk
switchport trunk native vlan 99
switchport trunk allowed vlan 99
end
```

*Note: Remember to set the native vlan (to 99 for instance) on each switch in the trunk so you don't get a native vlan mismatch warning*

#### Trunk Verification

```
show interface trunk
show interface g0/1 switchport
```

### EtherChannel
---

Etherchannel protocols LACP and PAgP configure multiple physical interfaces and links to act as one logical one. You can configure up to 8 ports to act as a single link. This increases bandwidth and improves redundancy.


*Note: `mode active` sets the etherchannel group to use the LACP protocol*

#### Configure EtherChannel

*Configure etherchannel between two switches connected with two ethernet cables.*
```
conf t
int range f0/1-2
channel-group 1 mode active
exit
int port-channel 1
switchport mode trunk
switchport trunk allowed vlan 1,2,20
```


#### Verify EtherChannel

```
show interfaces trunk
show etherchannel summary
```

### DTP (Dynamic Trunking Protocol)
---

#### Configure DTP

```
conf t
int gi0/1
switchport mode dynamic auto
end
```

**or**

```
conf t
int gi0/1
switchport mode dynamic desirable
end
```


#### Disable DTP

*Usefull for connecting to devices that don't support Cisco propietary DTP or creating a static trunk*

```
conf t
int gi0/1
switchport mode trunk
switchport nonegotiate
end
```

#### Verify DTP

```
show dtp interface gi0/1
```

## Advanced Networking

### OSPFv2

#### OSPF Router IDs

##### All Commands

```
show ip ospf neighbor
show ip ospf database 
```

##### Enable router OSPF process

Starting Mode: Global, Non-enabled

```
enable
conf t
router ospf 10
```

##### Configure Loopback

```
enable
conf t
interface Loopback 1
ip addr 1.1.1.1 255.255.255.255
end
```

##### Configure OSPF Router ID

_replace `1.1.1.1` with desired id_
```
conf t
router ospf 10
router-id 1.1.1.1
end
```

##### Modify OSPF router ID

_Prompt confirmation with 'y' needed_

```
conf t
router ospf 10
router-id 1.1.1.2
end
clear ip ospf process
```

_Verify_

```
show ip proto | include Router ID
```
#### OSPF - Point-to-Point Networks

##### Network Command Syntax

`Router(config-router)# network network-address wildcard-mask area area-id`

##### Configure OSPF With Network Command

The following configures a trianngle of 3 routers connected to
each other as an OSPF point to point network.

```
conf t
router ospf 10
network 10.10.1.0 0.0.0.255 area 0
network 10.10.1.4 0.0.0.3 area 0
network 10.10.1.12 0.0.0.3 area 0
end
```

##### Use Entire Gigabit Interfaces

```
conf t
router ospf 10
network 10.10.1.1 0.0.0.0 area 0
network 10.10.1.5 0.0.0.0 area 0
network 10.10.1.14 0.0.0.0 area 0
end
```

##### Configure OSPF with `ip ospf`

Configure OSPF directly on the interfaces rather with with the network
command.

Syntax: `Router(config-if)# ip ospf <process-id> area <area-id>`

```
R1(config)# router ospf 10
R1(config-router)# no network 10.10.1.1 0.0.0.0 area 0
R1(config-router)# no network 10.1.1.5 0.0.0.0 area 0
R1(config-router)# no network 10.1.1.14 0.0.0.0 area 0
R1(config-router)# interface GigabitEthernet 0/0/0
R1(config-if)# ip ospf 10 area 0
R1(config-if)# interface GigabitEthernet 0/0/1 
R1(config-if)# ip ospf 10 area 0
R1(config-if)# interface Loopback 0
R1(config-if)# ip ospf 10 area 0
R1(config-if)#
```

##### OSPF Passive Interfaces

```
conf t
router ospf 10
passive-interface loopback 0
end
```

```
conf t
router ospf 10
passive-interface Gi0/0/0
end
```

##### Find Designated Router and Backup

```
show ip ospf interface GigabitEthernet 0/0/0
```

##### Change OSPF from Broadcast to Point-to-Point

```
conf t
interface GigabitEthernet 0/0/0
ip ospf network point-to-point
```

##### Loopback and P2P Networks

Loobacks can be used to simulate real LAN networks

```
conf t
interface Loopback 0
ip ospf network point-to-point
```

```
show ip route | include 10.10.1
```

#### Multiaccess OSPF Networks

##### Configure OSPF Priority

```
conf t
int g0/0/1
ip ospf priority 255
end
```

Where `255` can be values from `0` to `255` with higher numbers making the router to be elected `DR`.

#### Modifying Single Area OSPF

##### Adjusting Reference Bandwidth

```
Router# router ospf 10
Router(config-router) auto-cost reference bandwidth 1000
```

_Where 1000 is the speed of the link in Mpbs_
Common Values: 10, 100, 1000

##### Manually Set OSPF Link Cost

```
conf t
int g0/0/1
ip ospf cost 25
interface l0
ip ospf cost 15
end
```

##### Show OSPF Hello Packet Intervals

```
show ip ospf int g0/0/1
```

##### Set OSPF Hello Packet Intervals

```
Router(config-if)# ip ospf hello-interval <seconds>
```

```
conf t
int g0/0/1
ip ospf hello-interval 30
end
```

Note: dead-interval automatically gets set as `hello-interval * 4`


##### Set OSPF Dead Interval

#### OSPF Default Routes

##### Propogate Default Route

```
conf t
ip route 0.0.0.0 0.0.0.0 loopback 1
router ospf 10
default-information originate
```

##### Verify Propogated Default Route

```
show ip route | begin Gateway
```

#### Verify Single-Area OSPF

##### Verify OSPF Neighbors

```
show ip ospf neighbor
```

##### Verify OSPF Protocols

```
show ip protocols
```

##### Verify OSPF Process Info

```
show ip ospf
```

##### Verify OSPF Interface Setting

```
show ip ospf int g0/0/1
show ip ospf int brief
```

Where `g0/0/1` is the interface you was to see OSPF information on.

```
conf t
int g0/0/1
ip ospf dead-interval 100
end
```




## Liste des commandes

### Commandes de changement de Mode

| **Commande**                        | **Description**                                                                                                                                        |
| ----------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **enable**                          | Déplace un utilisateur du mode User EXEC vers le mode Privileged EXEC. Le mode Privileged EXEC est indiqué par le symbole # dans l'invite de commande. |
| **configure terminal**              | Connecte l'utilisateur au mode de configuration globale.                                                                                               |
| **interface** _fastethernet/number_ | Entre dans le mode de configuration de l'interface pour l'interface Fast Ethernet spécifiée.                                                           |


### Commandes de configuration de base

| **Commande**                                              | **Description**                                                                                                                     |
| --------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| **reload**                                                | Redémarre le commutateur ou routeur Cisco.                                                                                          |
| **hostname** _name_                                       | Définit un nom d'hôte pour le périphérique réseau Cisco actuel.                                                                     |
| **copy** _from-location to-location_                      | Copie des fichiers d'un emplacement à un autre.                                                                                     |
| **copy running-config startup-config**                    | Remplace la configuration de démarrage par la configuration active lors de l'initialisation du périphérique réseau Cisco.           |
| **copy startup-config running-config**                    | Fusionne la configuration de démarrage avec la configuration actuellement active en RAM.                                            |
| **write memory**                                          | Sauvegarde la configuration en cours                                                                                                |
| **write erase**  <br>**erase startup-config**             | Supprime la configuration de démarrage.                                                                                             |
| **ip address** _ip-address mask_                          | Assigne l'adresse IP et le masque de sous-réseau spécifiés.                                                                         |
| **shutdown**  <br>**no shutdown**                         | Arrête l'interface (shutdown) ou la réactive (no shutdown).                                                                         |
| **ip default-gateway** _ip_address_                       | Définit la passerelle par défaut sur le périphérique Cisco.                                                                         |
| **show running-config**                                   | Affiche la configuration actuelle du périphérique.                                                                                  |
| **show startup-config**                                   | Affiche la configuration sauvegardée dans la NVRAM du périphérique, qui sera chargée au démarrage.                                  |
| **description** _string_                                  | Assigne la description spécifiée à une interface.                                                                                   |
| **show running-config interface** _interface slot/number_ | Affiche la configuration active pour l'interface spécifiée.                                                                         |
| **show ip interface** _[type number]_                     | Affiche l'état d'une interface réseau ainsi qu'une liste détaillée de ses configurations IP et caractéristiques associées.          |
| **show ip interface brief**                               | Affiche un résumé de l'état et de la configuration des interfaces IP, y compris leur statut (up ou down).                           |
| **ip name-server** _serverip-1 serverip-2_                | Définit l'adresse IP d'un ou plusieurs serveurs DNS que le périphérique peut utiliser pour résoudre des noms d'hôte en adresses IP. |


### Commandes de dépannage  

| **Commande**                                                    | **Description**                                                                                                                                                             |
| --------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **ping** _{hostname \| system-address} [source source-address]_ | Utilisé pour diagnostiquer la connectivité réseau de base.                                                                                                                  |
| **speed** _{10 \| 100 \| 1000 \| auto}_                         | Configure la vitesse de transmission d'une interface réseau à la valeur spécifiée en mégabits par seconde (Mbps), ou active la détection automatique de la vitesse du port. |
| **duplex** _{auto \| full \| half}_                             | Définit le duplex en mode semi, complet ou automatique.                                                                                                                     |
| **cdp run**  <br>**no cdp run**                                 | Active ou désactive le Cisco Discovery Protocol (CDP) pour le périphérique.                                                                                                 |
| **show mac address-table**                                      | Affiche la table des adresses MAC.                                                                                                                                          |
| **show cdp**                                                    | Indique si le CDP est activé globalement.                                                                                                                                   |
| **show cdp neighbors**_[detail]_                                | Liste les informations résumées (ou détaillées) sur chaque voisin connecté au périphérique.                                                                                 |
| **show interfaces**                                             | Affiche des informations détaillées sur l'état, les paramètres et les compteurs de l'interface.                                                                             |
| **show interface status**                                       | Affiche l'état de la ligne de l'interface.                                                                                                                                  |
| **show interfaces switchport**                                  | Affiche de nombreux paramètres de configuration et l'état opérationnel actuel, y compris les détails du VLAN trunking.                                                      |
| **show interfaces trunk**                                       | Affiche des informations sur les trunks opérationnels et les VLANs pris en charge par ces trunks.                                                                           |
| **show vlan**  <br>**show vlan brief**                          | Liste chaque VLAN et toutes les interfaces assignées à ce VLAN, sans inclure les trunks.                                                                                    |
| **show vtp status**                                             | Affiche l'état actuel du VLAN Trunk Protocol (VTP), y compris le mode actuel.                                                                                               |


### Commandes de routage et VLAN  

| **Commande**                                                                                              | **Description**                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| --------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **show ip route**                                                                                         | Affiche l'état actuel du routage IP de toutes les routes connues, qu'elles soient configurées statiquement ou apprises dynamiquement via un protocole de routage.                                                                                                                                                                                                                                                                                  |
| **ip route** _network-number network-mask {ip-address \| interface}_                                      | Définit une route statique dans la table de routage IP.                                                                                                                                                                                                                                                                                                                                                                                            |
| **router rip**                                                                                            | Active un processus de routage RIP (Routing Information Protocol), ce qui place l'utilisateur en mode de configuration de routeur.                                                                                                                                                                                                                                                                                                                 |
| **network** _ip-address_                                                                                  | Associe un réseau à un processus de routage RIP.                                                                                                                                                                                                                                                                                                                                                                                                   |
| **version 2**                                                                                             | Configure le logiciel pour recevoir et envoyer uniquement des paquets RIP version 2.                                                                                                                                                                                                                                                                                                                                                               |
| **no auto-summary**                                                                                       | Désactive le résumé automatique.                                                                                                                                                                                                                                                                                                                                                                                                                   |
| **default-information originate**                                                                         | Génère une route par défaut dans RIP.                                                                                                                                                                                                                                                                                                                                                                                                              |
| **passive-interface** _interface_                                                                         | Met l'interface spécifiée en mode passif RIP, ce qui signifie que les mises à jour de routage RIP sont acceptées par l'interface mais ne sont pas envoyées.                                                                                                                                                                                                                                                                                        |
| **show ip rip database**                                                                                  | Affiche le contenu de la base de données de routage RIP.                                                                                                                                                                                                                                                                                                                                                                                           |
| **ip nat** _[inside \| outside]_                                                                          | Configure le Network Address Translation (NAT), qui permet aux adresses IP privées d'un réseau local d'être traduites en adresses IP publiques avant d'être envoyées sur Internet.                                                                                                                                                                                                                                                                 |
| **ip nat inside source** _{list{access-list-number \| access-list-name}} interface type number[overload]_ | Établit une traduction dynamique des sources. L'utilisation du mot-clé "list" permet d'utiliser une ACL pour identifier le trafic soumis au NAT. L'option "overload" permet au routeur d'utiliser une adresse globale pour plusieurs adresses locales.                                                                                                                                                                                             |
| **ip nat inside source static** _local-ip global-ip_                                                      | Établit une traduction statique entre une adresse locale et une adresse globale.                                                                                                                                                                                                                                                                                                                                                                   |
| **vlan**                                                                                                  | Crée un VLAN et entre en mode de configuration VLAN pour des définitions supplémentaires.                                                                                                                                                                                                                                                                                                                                                          |
| **switchport access vlan**                                                                                | Définit le VLAN auquel l'interface appartient.                                                                                                                                                                                                                                                                                                                                                                                                     |
| **switchport trunk encapsulation dot1q**                                                                  | Spécifie l'encapsulation 802.1Q sur le lien trunk.                                                                                                                                                                                                                                                                                                                                                                                                 |
| **switchport access**                                                                                     | Configure un port Ethernet spécifique d'un commutateur pour fonctionner en mode access afin d'accommoder un périphérique final tel qu'un ordinateur, un serveur ou une imprimante. Le port doit ensuite être assigné à un seul VLAN.                                                                                                                                                                                                               |
| **vlan vlan-id** _[name vlan-name]_                                                                       | Configure un nom VLAN spécifique (1 à 32 caractères).                                                                                                                                                                                                                                                                                                                                                                                              |
| **switchport mode** _{ access \| trunk }_                                                                 | Configure le mode d'adhésion VLAN d'un port. Le port access est configuré en mode access de manière inconditionnelle et fonctionne comme une interface VLAN unique non trunkée qui envoie et reçoit des trames non encapsulées (non taguées). Un port trunk envoie et reçoit des trames encapsulées (taguées) qui identifient le VLAN d'origine. Un trunk est un lien point à point entre deux commutateurs ou entre un commutateur et un routeur. |
| **switchport trunk** _{encapsulation { dot1q }}_                                                          | Définit les caractéristiques du trunk lorsque l'interface est en mode trunking. Dans ce mode, le commutateur prend en charge simultanément le trafic tagué et non tagué sur un port.                                                                                                                                                                                                                                                               |
| **encapsulation dot1q vlan-id**                                                                           | Définit les critères de correspondance pour mapper les trames 802.1Q reçues sur une interface au service approprié.                                                                                                                                                                                                                                                                                                                                |
| **show spanning-tree**                                                                                    | Fournit des informations détaillées sur le protocole Spanning Tree pour tous les VLANs.                                                                                                                                                                                                                                                                                                                                                            |


### Commandes de DHCP  
| **Commande**                                                | **Description**                                                                                                                             |
| ----------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- |
| **ip address dhcp**                                         | Acquiert une adresse IP sur une interface via DHCP.                                                                                         |
| **ip dhcp pool name**                                       | Utilisé pour configurer un pool d'adresses DHCP sur un serveur DHCP et entrer en mode de configuration du pool DHCP.                        |
| **domain-name** _domain_                                    | Spécifie le nom de domaine pour un client DHCP.                                                                                             |
| **network** _network-number [mask]_                         | Configure le numéro de réseau et le masque pour un pool d'adresses DHCP, sous-réseau principal ou secondaire sur un serveur DHCP Cisco IOS. |
| **ip dhcp excluded-address** _ip-address [last-ip-address]_ | Spécifie les adresses IP qu'un serveur DHCP ne doit pas attribuer aux clients DHCP.                                                         |
| **ip helper-address** _address_                             | Active le transfert des diffusions UDP, y compris BOOTP, reçues sur une interface.                                                          |
| **default-router** _address [address2 ... address8]_        | Spécifie une ou plusieurs adresses de routeur à attribuer aux clients DHCP.                                                                 |
| **dns-server** _address [address2 ... address8]_            | Spécifie une ou plusieurs adresses de serveur DNS à attribuer aux clients DHCP.                                                             |
| **lease** _{days hours minutes \| infinite}_                | Spécifie la durée pendant laquelle une adresse IP est allouée à un client DHCP.                                                             |
| **show ip dhcp binding**                                    | Affiche des informations sur les adresses IP attribuées dynamiquement à l'aide du protocole DHCP et leur durée de bail.                     |
| **show ip dhcp pool**                                       | Affiche l'état d'un pool DHCP.                                                                                                              |
| **show ip dhcp conflict**                                   | Affiche les adresses IP en conflit détectées par un routeur Cisco.                                                                          |
| **clear ip dhcp conflict**                                  | Efface les informations de conflit DHCP enregistrées sur un routeur.                                                                        |


### Commandes de sécurité  

| **Commande**                                                                         | **Description**                                                                                                                                                                                               |
| ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **password** _pass-value_                                                            | Liste le mot de passe requis si la commande login (sans autres paramètres) est configurée.                                                                                                                    |
| **username** _name_ **password** _pass-value_                                        | Définit un ou plusieurs noms d'utilisateur et mots de passe associés utilisés pour l'authentification des utilisateurs. Utilisé lorsque la commande de configuration de ligne **login local** a été utilisée. |
| **enable password** _pass-value_                                                     | Définit le mot de passe requis lors de l'utilisation de la commande **enable**.                                                                                                                               |
| **enable secret** _pass-value_                                                       | Définit le mot de passe requis pour qu'un utilisateur puisse entrer en mode enable.                                                                                                                           |
| **service password-encryption**                                                      | Oriente le logiciel Cisco IOS à chiffrer les mots de passe, les secrets CHAP et d'autres données similaires enregistrées dans son fichier de configuration.                                                   |
| **ip domain-name** _name_                                                            | Configure un nom de domaine DNS.                                                                                                                                                                              |
| **crypto key generate rsa**                                                          | Crée et stocke (dans un emplacement caché de la mémoire flash) les clés requises par SSH.                                                                                                                     |
| **transport input** _{telnet \| ssh}_                                                | Définit si l'accès Telnet ou SSH est autorisé sur ce commutateur. Les deux valeurs peuvent être spécifiées dans une seule commande pour permettre l'accès Telnet et SSH (paramètres par défaut).              |
| **access-list** _access-list-number {deny \| permit} source [source-wildcard] [log]_ | Définit une liste de contrôle d'accès IP standard.                                                                                                                                                            |
| **access-class**                                                                     | Restreint les connexions entrantes et sortantes entre un VTY particulier (vers un appareil Cisco de base) et les adresses d'une liste de contrôle d'accès.                                                    |
| **ip access-list** _{standard \| extended} {access-list-name \| access-list-number}_ | Définit une liste de contrôle d'accès IP par nom ou par numéro.                                                                                                                                               |
| **permit source** _[source-wildcard]_                                                | Autorise un paquet à passer une ACL IP nommée. Pour supprimer une condition de permission d'une ACL, utilisez la forme “no” de cette commande.                                                                |
| **deny source** _[source-wildcard]_                                                  | Utilisé pour définir des conditions dans une ACL IP nommée qui refusera des paquets. Pour supprimer une condition de refus d'une ACL, utilisez la forme “no” de cette commande.                               |
| **ntp peer** _<ip-address>_                                                          | Configure l'horloge logicielle pour synchroniser un pair ou être synchronisé par un pair.                                                                                                                     |
| **switchport port-security**                                                         | Active la sécurité des ports sur l'interface.                                                                                                                                                                 |
| **switchport port-security maximum maximum**                                         | Définit le nombre maximum d'adresses MAC sécurisées sur le port.                                                                                                                                              |
| **switchport port-security mac-address** _{mac-addr \| {sticky [mac-addr]}}_         | Ajoute une adresse MAC à la liste des adresses MAC sécurisées. L'option “sticky” configure les adresses MAC comme collantes sur l'interface.                                                                  |
| **switchport port-security violation** _{shutdown \| restrict \| protect}_           | Définit l'action à prendre lorsqu'une violation de sécurité est détectée.                                                                                                                                     |
| **show port security** _[interface interface-id]_                                    | Affiche les informations sur les options de sécurité configurées sur l'interface.                                                                                                                             |


### Commandes de Sécurité Supplémentaires

| **Commande**                               | **Description**                                                                                                                            |
| ------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------ |
| **enable secret 2** _pass-value_           | Définit un mot de passe d'activation de niveau supérieur qui est chiffré en utilisant un algorithme plus sécurisé que **enable password**. |
| **login local**                            | Utilise une base de données d'utilisateurs locaux pour l'authentification des utilisateurs sur les lignes VTY ou consoles.                 |
| **line vty 0 4**                           | Accède à la configuration des lignes VTY, où tu peux définir des paramètres pour les sessions Telnet/SSH.                                  |
| **exec-timeout** _minutes _seconds_        | Définit le délai d'expiration d'inactivité pour une session sur les lignes VTY.                                                            |
| **transport output** _{telnet \| ssh}_     | Définit le protocole utilisé pour les connexions sortantes sur le commutateur.                                                             |
| **show users**                             | Affiche les utilisateurs actuellement connectés à l'appareil.                                                                              |
| **show access-lists**                      | Affiche la liste d'accès IP configurée sur l'appareil, y compris les conditions de filtrage définies.                                      |
| **clear access-list** _access-list-number_ | Supprime une liste d'accès spécifique, ce qui peut être utile pour réinitialiser les règles de filtrage.                                   |


### Commandes de surveillance et journalisation  

| **Commande**             | **Description**                                                                                                                                                                                          |
| ------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **logging** _ip address_ | Configure l'adresse IP de l'hôte qui recevra les messages de journalisation du système (syslog).                                                                                                         |
| **logging trap level**   | Utilisé pour limiter les messages qui sont enregistrés sur les serveurs syslog en fonction de leur gravité. Spécifiez le numéro ou le nom du niveau de gravité souhaité pour les messages à enregistrer. |
| **show logging**         | Affiche l'état de la journalisation du système (syslog) et le contenu du tampon de journalisation standard du système.                                                                                   |
| **terminal monitor**     | Envoie une copie de tous les messages syslog, y compris les messages de débogage, à l'utilisateur Telnet ou SSH qui exécute cette commande.                                                              |


## Liens externes  


https://www.netwrix.com/cisco_commands_cheat_sheet.html

https://github.com/grplyler/cisco-cheatsheet