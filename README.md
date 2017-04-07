### lab.stuff
created by Rikard Hjelm 2017
updated as needed by my lab tasks
This is stuff I use in my lab to build topologies. Mainly based on EVPN/MPLS / EVPN/VXLAN on Juniper's MX and QFX device.

First update hosts.ini with the host names and the IP for each host
Now create a creds.yml file with username/password for the devices. Same for all devices.
Examples of the above are provided
[todo] You can use the play-books "pb.add.host_vars.yml" and "pb.add.group_vars" to create vars files based on your hosts.ini

[pb.make.configs.yml]
Now create config files by using the "pb.make.configs.yml" -e hosts=<single or comma-separated hosts/groups>
Of course this file may be edited for the roles you need, add tags or other conditionals.

[pb.upload.configs.yml]
You can upload configs to devices using play-book "pb.upload.configs.yml" -e hosts=<single or comma-separated hosts/groups>
The configuration will use junos "commit confirmed 5" by default. No avoid this add "--skip-tags no-commit-confirmed"
Please note that the "configs" directory contains staged configurations files per host. These will be deleted after successful upload to avoid re-using an old config file.


Files you needs to tweak:

[topology.yml]
Used to create layer 3 links between routers.

[evpn-tenants.yml]
Add layer 2 and layer3 VRFs

[host_vars/]
Unique variables per device

[group_vars/]
Unique variables per group of devices defined in "hosts.ini"

[hosts.ini]
List devices with name, IP and group

[creds.yml]
Username and password for devices.
