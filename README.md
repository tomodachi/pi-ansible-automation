# pi-ansible-automation
A set of roles (mostly) tested &amp; optimized towards raspberry PI running raspbian bullseue (debian arm64)  

## avahi-discoverable
enables avahi hostname mDNS broadcasting so you can reach host on hostname.local  

## kodi
installs & configures kodi. Currently this role reconfigures pulseaudio to run in system wide mode
which might not be what you want.
  
kodi/files/sources.xml with your media shares

## pihole
un-attended install of pihole  

## librespot
installs & configures reverse engineered spotify-connect compatible client
by default in anonymous mode allowing anyone on your network to streap to your device
  
vars:  
extsoundcard=true  # Optional specify to route audio to external soundcard  

## steamlink-pi (currently not working on 64 bit arm debian)
Installs steamlink along with ps3 controller (wireless) support  

## unattended-upgrades
Configures scheduled upgrades & reboots  

vars:  
apt_get_update_ndays:  # required  
download_upgradeable_packages_ndays: # required  
unattended_upgrade_ndays: # required  
apt_get_autoremove_ndays: # required  

