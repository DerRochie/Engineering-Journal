Switch configuration
====================


Configuring VLANs
^^^^^^^^^^^^^^^^^

Configuring VLAN's on a switch is easy and allows you to segment your network for better throughput, lower latency and better security.

.. code-block ::

        switch(config)# int g0/0
        switch(config-if)# switchport mode access
        switch(config-if)# switchport access vlan 1


Configuring Trunk ports
^^^^^^^^^^^^^^^^^^^^^^^

Since VLAN's are isolated and cannot communicate with eachother, trunk ports are used to allow data from multiple VLAN's across an interface and can be set up like so.

.. code-block ::

        switch(config)# int g0/0
        switch(config-if)# switchport mode trunk



Security
--------

Security is important in the networking world and this is how you configure a password on your switches to disallow access to people without a password.

In this example you will enable ssh on a switch for 5 users (line vty 0 4 means that there can be a total of 5 active ssh sessions) and sets the password to password.

.. code-block ::

        switch(config)# line vty 0 4
        switch(config-line)# password password
        switch(config-line)# login


auto-MDIX
---------

Enables audo-MDIX. With auto-MDIX enabled, either type of cable can be used to connect to other devices, and the interface automatically adjusts to communicate successfully.

..  code-block :: none
        S1(config-if)# mdix auto



