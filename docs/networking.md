
# Networking

Zones created by :command: `zcage` are setup as an exclusive-IP zone, this 
means that each zone have its distinct IP layer configuration and state
Network virtualization is provided by Crossbow. 
  

## Creating Virtual Network Interfaces

zcage needs a virtual network interface (vnic) per each zone ,these
are created using the **DLADM(1)**  command, for example this will create the vnic
vnic0 using the physical nic e1000g0: 
   
```
# dladm create-vnic -l e1000g0 vnic0
```
Then later vnic0 could be use for **zcage create** when specifying network 
properties.


## Configuring Zone networking
  
The **--net** flag is used to configure networking, values are separated by '|': 
  
vnic name | ip address/netmask (CIDR format) | default gateway 

### IPv4
   
```
# zcage create --alias=test07 --net "vnic0|192.168.1.225/24|192.168.1.1" --ram 2gb
```
### IPv6
    
```
# zcage create --alias=test07 --net "vnic1|0:0:0:0:0:ffff:c0a8:1e1/24|0:0:0:0:0:ffff:c0a8:101" --ram 2gb
```

These examples creates a zone with IP **192.168.1.225/24** and **0:0:0:0:0:ffff:c0a8:1e1/24** using vnics *vnic1* and *vnic0*.
   

# Links

   [Quickstart](https://github.com/cneira/zcage/blob/master/docs/quickstart.md)  
   [Install](https://github.com/cneira/zcage/blob/master/docs/install.md)  
   [Basic usage](https://github.com/cneira/zcage/blob/master/docs/basic-use.md)  
   [Networking](https://github.com/cneira/zcage/blob/master/docs/networking.md)  
   [Brand types](https://github.com/cneira/zcage/blob/master/docs/brand-types.md)  
   [Options available](https://github.com/cneira/zcage/blob/master/docs/Options.md)    

# References
* https://illumos.org/man/5/zones 
* https://wiki.smartos.org/display/DOC/Networking+and+Network+Virtualization
* https://illumos.org/man/1M/dladm


