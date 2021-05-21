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

Security is important in the networking world and this is how you configure a password on your switches to disallow access to people without a password. Many types of authentication can be performed on networking devices, and each method offers varying levels of security. The simplest method of remote access authentication is to configure a login and password combination on console, vty lines, and aux ports, as shown in the vty lines in the following example. This method is the easiest to implement, but it is also the weakest and least secure. This method provides no accountability and the password is sent in plaintext. Anyone with the password can gain entry to the device.

SSH is a more secure form of remote access:

. It requires a username and a password, both of which are encrypted during transmission.
. The username and password can be authenticated by the local database method.
. It provides more accountability because the username is recorded when a user logs in.

The following example illustrates SSH and local database methods of remote access.

.. code-block :: none

        switch(config)# ip domain-name example.com
        switch(config)# crypto key generate rsa general-keys modulus 2048
        switch(config)# username Admin secret Str0ng3rPa55w0rd
        switch(config)# ssh version 2
        switch(config)# line vty 0 4
        switch(config-line)# transport input ssh
        switch(config-line)# login local


auto-MDIX
---------

Enables audo-MDIX. With auto-MDIX enabled, either type of cable can be used to connect to other devices, and the interface automatically adjusts to communicate successfully.

..  code-block :: none
        S1(config-if)# mdix auto



