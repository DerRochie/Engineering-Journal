Troubleshooting Commands
========================
|

ping
----
----

The ping command is used to test connectivity to another device on the network

Usage
^^^^^
The most simple use case is '`ping [ip address]`'

.. code-block :: bash

   ping 192.168.1.1


This command can be used from Linux, Windows and Cisco IOS devices





|
traceroute
----------
----------

The trace command is used to view all the 'hops' a packet makes when being sent to a destination on the network.

.. usage2:

Usage
^^^^^

The most simple use case is '`tracert [ip address]`' for Cisco IOS and Linux devices:

.. code-block :: bash

   traceroute 192.168.1.1

However, this command is also available Windows devices:

.. code-block :: bash

   tracert 192.168.1.1

|
show running-config
-------------------
-------------------

Shows the running configuration of a Cisco IOS device. Really important troubleshooting command especially if you know YAML

Usage
^^^^^
To use this command you must be in Privilaged EXEC mode

.. code-block :: bash

   router# show running-conifg

|
show interface
--------------
--------------

|
show ip interface
-----------------
-----------------


|
show ipv6 interface
-------------------
-------------------


|
show ip route
-------------
-------------


|
show ipv6 route
---------------
---------------


|
show vlan
---------
---------


|
show cdp neighbor
-----------------
-----------------


|

|
show ip ospf database
---------------------
---------------------

|
|
Switch Verification Commands
============================

|
show interfaces
---------------
---------------

Display interface status and configuration. Useful for checking for connectivity issues liek exessive noise on the line

.. code-block :: none

   switch# show interfaces [inteface-id]

|
show flash
----------
----------

Display information about flash file system.

.. code-block :: none

   switch# show flash

|
show version
------------
------------

Display system hardware and software status.

.. code-block :: none

   switch# show version

|
show history
------------
------------

Display history of command entered.

.. code-block :: none

   switch# show history

|
show ip interface
-----------------
-----------------

Display IP information about an interface.

.. code-block :: none

   switch# show ip interface [interface-id]

|
show ipv6 interface
-------------------
-------------------

Display IPv6 information about an interface.

.. code-block :: none

   switch# show ipv6 interface [interface-id]

|
show mac-address-table
----------------------
----------------------

Display the MAC address table.

.. code-block :: none

   switch# show mac-address-table
