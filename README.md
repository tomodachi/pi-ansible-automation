# pi-ansible-automation
A set of roles (mostly) tested &amp; optimized towards raspberry PI running raspbian (Debian)  

## avahi-discoverable
enables avahi hostname mDNS broadcasting so you can reach host on hostname.local  

## kodi
installs & configures kodi  
  
kodi/files/sources.xml with your media shares

## pihole
unattended install of pihole  

## spotifyd
installs & configures spotifyd 
by default in anonymous mode allowing anyone on your network to streap to your device
  
vars:  
extsoundcard=true  # Optional specify to route audio to external soundcard  
spotifyd_release  # Optional set to full url of  .tar.gz of spotifyd release on github  


## steamlink-pi
Installs steamlink along with ps3 controller (wireless) support  


## unattended-upgrades
Configures scheduled upgrades & reboots  

vars:  
apt_get_update_ndays:  # required  
download_upgradeable_packages_ndays: # required  
unattended_upgrade_ndays: # required  
apt_get_autoremove_ndays: # required  

