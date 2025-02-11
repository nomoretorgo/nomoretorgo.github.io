---
published: true
---
# With Meraki MX, Segregated wifi network vlan 

## Summary:  You wish to create a wifi network where clients who join are allowed to communicate with each other, but not anyone else on the network.  This is particularly useful for IOT devices which need to communicate with each other, but we are not comfortable with them having access to the rest of the network.


### Step:  Create Vlan
Security & SD-WAN -> Configure -> Addressing & VLANs -> Routing -> Add Vlan

![Add VLAN, Meraki](https://github.com/nomoretorgo/nomoretorgo.github.io/blob/master/_posts/modVLAN.png?raw=true)


### Step:  create a group policy to deny
Network-wide -> configure -> Group Policies -> new policy

Create layer 3 deny rules for any subnet that you are wanting to Not allow visitation.

![meraki, group policy](https://github.com/nomoretorgo/nomoretorgo.github.io/blob/master/_posts/group-policy-deny.png?raw=true)



### Step:  Link VLAN to group policy 
Security & SD-WAN -> Configure -> Addressing & VLANs -> Routing -> select vlan -> assign our group policy

### Step:  Link devices to the group policy 
Lookup client device, scroll down and change the policy 

![device-groupPolicy.jpg](https://github.com/nomoretorgo/nomoretorgo.github.io/blob/master/_posts/_posts/device-groupPolicy.jpg?raw=true)
