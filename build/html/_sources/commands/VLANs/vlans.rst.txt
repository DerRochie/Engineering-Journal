Configuring VLAN's on a swtich
==============================

All VLAN's are private and their traffic  will not mix with that on other VLAN's.

Therefore, VLAN's can be used to enhance security by deliberately segrigating network traffic.

Creating VLAN's
---------------

Vlans Can be created like This

.. code-block :: none

   Switch(config)# vlan 100

|
Configuring access ports
------------------------

.. code-block :: none

   Switch(config)# interface range f0/1 - 24
   Switch(config-if)# swichport mode access
   Switch(config-if)# switchport access vlan 100



|
Configuring trunk ports
-----------------------

.. code-block :: none

   Switch(config)# interface f0/1
   Switch(config-if)#swichport mode trunk
   Switch(config-if)# switchport trunk native vlan vlan-id

Use the no switchport trunk allowed vlan and the no switchport trunk native vlan commands to remove the allowed VLANs and reset the native VLAN of the trunk. When it is reset to the default state, the trunk allows all VLANs and uses VLAN 1 as the native VLAN. The example shows the commands used to reset all trunking characteristics of a trunking interface to the default settings.

.. code-block :: none

   S1(config-if)# no switchport trunk allowed vlan
   S1(config-if)# no switchport trunk native vlan


|
Dynamic Trunking Protocol
-------------------------

Some Cisco switches have a proprietary protocol that lets them automatically negotiate trunking with a neighboring device. This protocol is called Dynamic Trunking Protocol (DTP). DTP can speed up the configuration process for a network administrator. Ethernet trunk interfaces support different trunking modes. An interface can be set to trunking or nontrunking, or to negotiate trunking with the neighbor interface. Trunk negotiation is managed by DTP, which operates on a point-to-point basis only, between network devices.

.. code-block :: none

   S1(config-if)# switchport mode trunk
   S1(config-if)# switchport nonegotiate
   S1(config-if)# switchport mode dynamic auto

|
Negotiated Interface Modes
--------------------------

.. code-block :: none

   Switch(config-if)# switchport mode { access | dynamic { auto | desirable } | trunk }

access
^^^^^^

    Puts the interface (access port) into permanent nontrunking mode and negotiates to convert the link into a nontrunk link.
    The interface becomes a nontrunk interface, regardless of whether the neighboring interface is a trunk interface.

dynamic auto
^^^^^^^^^^^^

    Makes the interface able to convert the link to a trunk link.
    The interface becomes a trunk interface if the neighboring interface is set to trunk or desirable mode.
    The default switchport mode for all Ethernet interfaces is dynamic auto.

dynamic desirable
^^^^^^^^^^^^^^^^^

    Makes the interface actively attempt to convert the link to a trunk link.
    The interface becomes a trunk interface if the neighboring interface is set to trunk, desirable, or dynamic auto mode.


trunk
^^^^^

    Puts the interface into permanent trunking mode and negotiates to convert the neighboring link into a trunk link.
    The interface becomes a trunk interface even if the neighboring interface is not a trunk interface.


|
Configuring VOIP VLAN
---------------------

.. code-block :: none

   S3(config)# vlan 20
   S3(config-vlan)# name student
   S3(config-vlan)# vlan 150
   S3(config-vlan)# name VOICE
   S3(config-vlan)# exit
   S3(config)# interface fa0/18
   S3(config-if)# switchport mode access
   S3(config-if)# switchport access vlan 20
   S3(config-if)# mls qos trust cos
   S3(config-if)# switchport voice vlan 150
   S3(config-if)# end

