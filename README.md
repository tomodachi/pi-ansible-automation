# pi-ansible-automation
A set of roles (mostly) tested &amp; optimized towards raspberry PI running Raspberry PI OS (bullseye debian arm64)  

## avahi-discoverable
enables avahi hostname mDNS broadcasting so you can reach host on hostname.local  


**kodi**
installs & configures kodi. 

## pihole
un-attended install of pihole for DNS based ad-blocking 
 
## librespot
Installs & configures reverse engineered spotify-connect compatible client
by default in anonymous mode allowing anyone on your network to stream to your device
  

| Variable name        | Example       | Mandatory  |
| -------------------- |:-------------:| :----------:|
| spotify_connect_name:| my-hifi       | no |


## roc-streaming
Installs the roc sink modules for pulseaudio allowing streaming audio from
any pulseaudio/pipewire sound server giving a apple air-share like streaming experience  
for Linux users (only better) see /roles/roc-streaming/README.MD for more details.  
Currently limited to raspberrypi OS 11 (debian old stable) as the roc modules are compiled  
towards that target  
 
## steamlink-pi
Installs steamlink along with PS3 controller (wireless) support  
 
## unattended-upgrades
Configures scheduled upgrades & reboots  
 
| Variable name        | Example       | Mandatory   |
| -------------------- |:-------------:| :----------:|
| automatic_reboot_time:| "04:00"      | yes         |
| apt_get_update_ndays:| 15            | no          |
| download_upgradeable_packages_ndays:| 16 | no      |
| unattended_upgrade_ndays:  :| 17     | no          |
| apt_get_autoremove_ndays: | 18       | no          |


## dnsmasq-tftp
Configures dnsmasq to annouce tftp server for PXE boot  
 
| Variable name        | Example       | Mandatory   |
| -------------------- |:-------------:| :----------:|
| tftp_server:         | 10.0.5.41     | yes         |


## tftpd-server
Configures tftp server for PXE boot

| Variable name        | Example       | Mandatory   |
| -------------------- |:-------------:| :----------:|
| rootfs_path:        | /mnt/rootfs     | yes        |
| bootfs_path:        | /mnt/bootfs     | yes        |


## nfs-boot-pi
Configures a raspberry pi to boot diskless of a NFS share
| Variable name        | Example       | Mandatory   |
| -------------------- |:-------------:| :----------:|
| rootfs_path:        | /mnt/rootfs     | yes        |
| bootfs_path:        | /mnt/bootfs     | yes        |

## dns-over-tls
DNS over TLS using Cloudflares clourflared for DNS proxying.

| Variable name            | Example       | Mandatory   |
| ------------------------ |:-------------:| :----------:|
| cloudflared_release_ver: |               | yes         |
| doh_dns_1:               | 1.1.1.1       | yes         |
| doh_dns_2:               | 1.0.0.1       | yes         |

## single-nic-firewall
Sets up a single nic NAT:ing Firewall with a DHCP server using VLANs & nftables for firewalling.   
This required that you have a Switch with VLAN capabilities.  

Since it's a single NIC you cannot get full linkspeed in duplex mode.
Excpected raw throughput on different models:   
PI2 model B: ~70 Mbit/s  
PI3 model B: ~70 Mbit/s  
PI4: ~650 Mbit/s 
  
| Variable name            | Example       | Mandatory   |
| ------------------------ |:-------------:| :----------:|
| lan_if:                  | eth0          | yes         |
| lan_ip:                  | 192.168.0.254 | yes         |
| lan_broadcast:           | 192.157.0.255 | yes         |
| lan_broadcast:           | 192.157.0.255 | yes         |
| lan_net:                 | 192.168.0.0/24| yes         |
| lan_vlan:                | 10            | yes         |
| wan_vlan:                | 99            | yes         |
| dns_primary:             | 1.0.0.1       | yes         |
| dns_secondary:           | 1.1.1.1       | yes         |
| dhcp_range:              |   192.168.0.50,192.157.100 yes          |
| dhcp_router:             | 192.168.0.254 | yes         |
| domain:                  | yourhomedomain.local| yes   |

 Example of how static dhcp client would look 
```
static_dhcp_clients:  
  xx:xx:xx:xx:xx:xx: ip1  
  xx:xx:xx:xx:xx:xx: ip2 
```
`
