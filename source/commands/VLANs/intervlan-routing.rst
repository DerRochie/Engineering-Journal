Configuring Inter-vlan routing
==============================


Dot1q encapsulation
-------------------

Switch configuration
^^^^^^^^^^^^^^^^^^^^

.. code-block :: bash

   Router(config) interface range f0/0 - 6
   Router(config) swichport mode access
   Router(config) switchport access vlan 100
   Router(config) interface range f0/7 - 14
   Router(config) swichport mode access
   Router(config) switchport access vlan 200
   Router(config) interface range f0/14 - 21
   Router(config) swichport mode access
   Router(config) switchport access vlan 300
   


Router configuration
^^^^^^^^^^^^^^^^^^^^

.. code-block :: bash

   Router(config) interface g0/0.100
   Router(config) encapsulation dot1q 100
   Router(config) ip address 192.168.1.1 255.255.255.0
   Router(config) interface g0/0.200
   Router(config) encapsulation dot1q 200
   Router(config) ip address 192.168.2.1 255.255.255.0
   Router(config) interface g0/0.300
   Router(config) encapsulation dot1q 300
   Router(config) ip address 192.168.3.1 255.255.255.0