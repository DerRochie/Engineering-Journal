OSPF Routing Protocol
=====================

OSPF (Open Shortest Path First) is a routing protocol used to allow internetwork communication between two or more routers.

OSPFv2
------

OSPFv2 is the IPv4 version of the OSPF routing protocol and is configured as followed.


Single Area OSPF
^^^^^^^^^^^^^^^^

.. code-block :: none

   router(config)# router ospf 1
   router(config-router)# network [network-id] [wildcard mask] area [ospf-area-number]

Remember to add all adjacent networks using the `network [network-id] [wildcard mask] area [ospf-area-number]` command. 

Static and Default Routes
^^^^^^^^^^^^^^^^^^^^^^^^^

If there are default or static routes that need to be advertised use this command:

.. code-block :: none

   ## For default routes
   router(config-router)# default-information originate

   ## For static Routes
   router(config-router)# redistribute static
   or
   router(config-router)# redistribute static subnets


First, log onto the router and enter global configuration mode

OSPF Authentication
^^^^^^^^^^^^^^^^^^^

OSPF can be configured to authenticate every OSPF message. This is usually done to prevent a rogue router from injecting false routing information and therefore causing a Denial-of-Service attack.

Two types of authentication can be used:
   1.  clear text authentication – clear text passwords are used
   2.  MD5 authentication – MD5 authentication is used. This type of authentication is more secure because the password doesn’t go in clear-text over the network.


.. code-block :: none

   R1(config)# router ospf 1
   R1(config-router)# area 0 authentication message-digest
   R1(config-router)# exit
   R1(config)# int [interface]
   R1(config-if)# ip ospf message-digest-key 1 md5 [password]

   R2(config)# router ospf 1
   R2(config-router)# area 0 authentication message-digest
   R2(config-router)# exit
   R2(config)# int [interface]
   R2(config-if)# ip ospf message-digest-key 1 md5 [password]




OSPFv3
------