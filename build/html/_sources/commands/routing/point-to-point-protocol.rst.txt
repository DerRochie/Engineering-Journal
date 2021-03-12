Point To Point Protocol
=======================

Point-to-Point Protocol (PPP) is a data link layer (layer 2) communication protocol between two routers directly without any host or any other networking in between. It can provide connection authentication, transmission encryption, and data compression. 


Configuring CHAP
----------------

For this configuration imagine that you have a pair of networks with a router and a host connected via a serial connection. For this configuration we will be securing a serial connection between the two routers using point to point running on interfaces s0/0/0. For this instance we will be using the CHAP variation

R1 
^^^

.. code-block :: none

    R1(config)# username R1 password password

this sets up a local user database entry for the "R1" router with a password of “password”

.. code-block :: none

    R1(config)# interface s0/0/0
    R1(config-if)# encapsulation ppp
    R1(config-if)# ppp authentication chap

R2 
^^^

.. code-block :: none

    R2(config)# username R2 password password

this sets up a local user database entry for the "R2" router with a password of “password”

.. code-block :: none

    R2(config)# interface s0/0/0
    R2(config-if)# encapsulation ppp
    R2(config-if)# ppp authentication chap


|

Configuring PAP
---------------

For this configuration imagine that you have a pair of networks with a router and a host connected via a serial connection. For this configuration we will be securing a serial connection between the two routers using point to point running on interfaces s0/0/0. For this instance we will be using the PAP variation

R1 
^^^

.. code-block :: none

    R1(config)# username R1 password password

this sets up a local user database entry for the "R1" router with a password of “password”

.. code-block :: none

    R1(config)# interface s0/0/0
    R1(config-if)# encapsulation ppp
    R1(config-if)# ppp authentication pap
    R1(config-if)# ppp pap sent-username R1 password password

R2 
^^^

.. code-block :: none

    R2(config)# username R2 password password

this sets up a local user database entry for the "R2" router with a password of “password”

.. code-block ::  none

    R2(config)# interface s0/0/0
    R2(config-if)# encapsulation ppp
    R2(config-if)# ppp authentication pap
    R2(config-if)# ppp pap sent-username R2 password password

