VPN configuration
=================

What is?
^^^^^^^^

Configuration
^^^^^^^^^^^^^

For this example image you have two autonomous system's running EIGRP ()

Setting up GRE Tunnel
---------------------

Setting up GRE Tunnel

.. code-block :: none

    router(config)# interface tunnel 0
    router(config-if)# ip address [ip address] [subnet mask]
    router(config-if)# tunnel source g0/1
    router(config-if)# tunnel destination [Device 2 edge interface]
    router(config-if)# exit
    router(config)# access-list 101 permit gre host [device ip] host [destination ip]


After this advertise the gre tunnel in your routing protocol. This could be RIP, OSPF, BGP or EIGRP.

Repeat these two steps for each device then test connectivity between them


Setting up VPN
--------------

.. code-block :: none

    router(config)# crypto isakmp enable
    router(config)# crypto isakmp policy 1
    router(config)# authentication pre-share
    router(config)# encryption des
    router(config)# hash md5
    router(config)# group 1
    router(config)# lifetime
    router(config)# exit
    router(config)# crypto isakmp key [pre-shared key] address [ip of network]
    router(config)# crypto ipsec transform-set [transform set name] esp-3des esp-sha-hmac
    router(config)# crypto map [crypto map name] 1 ipsec-isakmp
    router(config)# match address [access list number]
    router(config)# set peer [ip of external network edge router]
    router(config)# set transform-set [transfrom set name]
    router(config)# set pfs group2
    router(config)# set security-association lifetime seconds 44000
    router(config)# exit


Testing
-------

.. code-block :: none

    show crypto isakmp sa
    show crypto ipsec sa
