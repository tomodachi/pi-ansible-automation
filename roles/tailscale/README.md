# Tailscale

This role install the official tailscale APT repository then installs tailscale and starts it as service (tailscaled)
It also registers the tailscale node with the headscale server. The Node registration is done non-interactively
The role will connect to the headscale management server to fetch a pre-auth key used in the node registration process.

This requires the host running this playbook to be connected to the live VPN to generate that key from the management server.
If the host you wish to enroll is on a different VPN than the Live vpn you will need to be connected to that at the same time.
Given the conflicting routing information given between live and test vpn you might need to create a host-route to explicitly route traffic to the management server over the right vpn tunnel


Role Variables
--------------

## Configurable & Default variables
````yaml
tailscale_headscale_host: management.tailscale.live.btcx.nu    <- The reachable ssh hostname of headscale/management server
headscale_fqdn: management.btcx.live                           <- Declared and imported from headscale role vars. Server for node to register with
````


## Common Operations & tags
````bash
ansible-playbook pb-yourplay.yml -D -K -b  # Install tailscale
````


## Known Issues
- Currently it's not possible to run tailscale on LXC containers as the tun module / interface is not accessible. I believe it needs to be enabled on the Proxmox host

## Manually installing tailscale

Pick the right version for your operating system of choice from here: https://tailscale.com/download
if on Linux run:
```bash
tailscale up --login-server https://management.tailscale.live.bt.cx
```

You will be given a url paste it in a browser. You will see a tailscale command as output to this action
give it to your headscale admin person (whoever has permissions to the server) to execute on the headscale cli.
Please note that the user who's laptop you want to enroll has to be created as a user in headscale firstly.
Since the enroll command requires a user that exists for enrollment.

To create the given user:
```bash
# on management server
docker exec -ti headscale headscale users create mail@bt.bt.cx
```

Example command of how the register / enrollment command looks like:
```bash
docker exec -it headscale headscale nodes register --user CHANGEME --key XXXXXXX
```
where CHANGEME is the username you just created

Once executed the new node will have been enrolled.

If you are on some other OS and or have a gui tailscale client,  you need to find where to specify/add your own login server 
as described above to auth the new node.

## Backup & State storage considerations

Any node can be easily re-enrolled using the tailscale playbook so no need to manage or backup any state
