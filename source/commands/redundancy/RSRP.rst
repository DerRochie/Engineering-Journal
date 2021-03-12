Configuring Router redundancy with HSRP
=======================================


To configure HSRP on a network there must be at least two edge routers facing the WAN. It is also advised that all ip addresses are assined to network devices to avoid error.

R1 configuration - Primary router

.. code-block :: none

    R1(config)# int g0/0
    R1(config-if)# standby 1 ip 192.168.1.1

Configuring priority:

.. code-block :: none

    R1(config-if)# standby 1 priority 150
    R1(config-if)# standby 1 preempt

R2 configuration - Backup routers

.. code-block :: none

    R2(config)# int g0/0
    R2(config-if)# standby 1 ip 192.168.1.1
