

Access Control Lists
====================

Standard
--------

Standard ACL's have a id number of 1-99

.. code-block :: none

   router(config)# access-list 1 deny [destination-address] [wildcard-mask]
   router(config)# access-list 1 permit any
   router(config)# interface [interface]
   router(config-if)# ip access-group 1 [out/in]
   

Extended 
--------

Extended ACL's have a id number of 100-199 and are more precise with what is filtered - right down to the protocl level

.. code-block :: none

   router(config)#  access-list 101 deny icmp <[desination-address] [wildcard mask] | any> <[source-address] [wildcard mask] | any> 
   router(config)#  access-list 101 deny icmp 192.168.20.0 0.0.0.255 any 
   router(config)#  access-list 101 deny icmp 192.168.30.0 0.0.0.255 any 
   router(config)#  access-list 101 permit ip any any 

Then apply the access list to an interface with:

.. code-block :: none

   router(config)# interface [interface]
   router(config-if)# ip access-group 1 [out/in]

|
|
Network Address Translation(NAT) with Port Address Translation(PAT)
===================================================================

NAT allows a private inside address to hide behind a public one and PAT takes this a stage further by attaching port numbers to conversations meaning that many private inside addresses can hide behind a single public address.  NAT can be implemented either dynamically if it’s operating from inside-to-out or statically from outside-to-in for server access. 


In a situation were we have two networks with a server and a host on each connected via a WAN connection. NAT/PAT is setup like this

.. code-block :: none

   router(config)# ip nat inside source static [private-ip-address] [nat-address]
   router(config)# access-list 1 permit any
   router(config)# ip nat inside source list 1 interface g0/0 overload

Then on the edge router, on the interface facing the internet, use the following command.

.. code-block :: none

   router(config)# interface [interface name]
   router(config-if)# ip nat outside

Then configure internal interfaces as so - including virtual interfaces.

.. code-block :: none

   router(config)# interface [interface name]
   router(config-if)# ip nat inside
   