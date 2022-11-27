# pi-ansible-automation
A set of roles (mostly) tested &amp; optimized towards raspberry PI running raspbian bullseye (debian arm64)  

## avahi-discoverable
enables avahi hostname mDNS broadcasting so you can reach host on hostname.local  

## kodi
installs & configures kodi. Currently this role reconfigures pulseaudio to run in system wide mode
which might not be what you want.
  
kodi/files/sources.xml with your media shares

## pihole
un-attended install of pihole for DNS based ad-blocking 
 
## librespot
installs & configures reverse engineered spotify-connect compatible client
by default in anonymous mode allowing anyone on your network to stream to your device
  
__optional variables:__  
extsoundcard=true  # route audio to external soundcard  
 
## steamlink-pi (currently not working on 64 bit arm debian)
Installs steamlink along with ps3 controller (wireless) support  
 
## unattended-upgrades
Configures scheduled upgrades & reboots  
 
__mandatory variables:__  
apt_get_update_ndays:  
download_upgradeable_packages_ndays:  
unattended_upgrade_ndays:  
apt_get_autoremove_ndays:  

## dnsmasq-tftp
Configures dnsmasq to annouce tftp server for PXE boot  
__mandatory variables:__  
tftp_server:  ip  

## tftpd-server
Configures tftp server for PXE boot
__mandatory variables:__  
rootfs_path:   
bootfs_path  
 
## single-nic-firewall
Sets up a single nic NAT:ing Firewall with a DHCP server using VLANs & nftables for firewalling.   
This required that you have a Switch with VLAN capabilities.  

LAN interface will use VLAN ID 10   
WAN interface will use VLAN ID 99  
 
Excpected raw throughput on different models:   
PI2 model B: ~70 Mbit/s  
PI3 model B: ~70 Mbit/s  
PI4: ~320 Mbit/s  ( I'm hitting ISP throttling as I'm paying for 250/250 Internet)
  
__mandatory variables:__  
lan_if: eth0  
lan_ip: lan_ip_of_firewall  
lan_broadcast: lan_broadcast   
lan_net: lan_network  
lan_vlan: 10  
lan_wlan: 99  
 
dns_primary: ip1  
dns_secondary: ip2  
 
dhcp_range: start_ip,stop_ip  
dhcp_router: ip  
domain: yourhomedomain.local  
  
__optional variables:__  
static_dhcp_clients:  
  xx:xx:xx:xx:xx:xx: ip1  
  xx:xx:xx:xx:xx:xx: ip2 
