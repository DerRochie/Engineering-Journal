DHCPv4
======

First of all, log into global configuration mode on the device and configure it as such:

.. code-block :: none
    
    Router(config) ip dhcp excluded-excluded address [ip address]
    Router(config) ip dhcp [pool name]
    Router(config) network [ip address] [subnet mask]
    Router(config) default-router [gateway ip address]

Optionally, you can also use '`ip dhcp excluded-excluded address [ip address] [ip address]`' for a range of addresses

DHCP clients are on a different network to the DHCP Server
----------------------------------------------------------

The usage of the "`ip helper-address`" command is used to specify a remote dhcp server

.. code-block :: none
    
    Router(config) interface g0/0/0
    Router(config-if) ip helper-address   

   