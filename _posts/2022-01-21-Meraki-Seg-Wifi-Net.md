---
published: false
---
# With Meraki MX, Segregated wifi network vlan 

## Summary:  You wish to create a wifi network where clients who join are allowed to communicate with each other, but not anyone else on the network.  This is particularly useful for IOT devices which need to communicate with each other, but we are not comfortable with them having access to the rest of the network.


### Step:  Create Vlan
Security & SD-WAN -> Configure -> Addressing & VLANs -> Routing -> Add Vlan

![Add VLAN, Meraki]({{site.baseurl}}/_posts/modVLAN.png)


### Step:  create a group policy to deny
Network-wide -> configure -> Group Policies -> new policy

Create layer 3 deny rules for any subnet that you are wanting to Not allow visitation.

![meraki, group policy]({{site.baseurl}}/_posts/group-policy-deny.png)


### Step:  Link group policy 
Security & SD-WAN -> Configure -> Addressing & VLANs -> Routing -> select vlan -> assign our group policy

