DHCPv6
======

Server to client DHCPv6 messages use UDP destination port 546 while client to server DHCPv6 messages use UDP destination port 547.

Steps for DHCPv6 operations:

1. The client sends an RS (Router Solicitation) message to all IPv6-enabled routers.
2. The router receives the RS and responds with an RA indicating that the client is to initiate communication with a DHCPv6 server.
3. The client, now a DHCPv6 client, needs to locate a DHCPv6 server and sends a DHCPv6 SOLICIT message to the reserved IPv6 multicast all-DHCPv6-servers address of ff02::1:2. This multicast address has link-local scope, which means routers do not forward the messages to other networks.
4. One or more DHCPv6 servers respond with a DHCPv6 ADVERTISE unicast message. The ADVERTISE message informs the DHCPv6 client that the server is available for DHCPv6 service.
5. The host responds to the DHCPv6 server.
    * Stateless DHCPv6 client - The client creates an IPv6 address using the prefix in the RA message and a self-generated Interface ID. The client then sends a DHCPv6 INFORMATION-REQUEST message to the DHCPv6 server requesting additional configuration parameters (e.g., DNS server address).
    * Stateful DHCPv6 client - The client sends a DHCPv6 REQUEST message to the DHCPv6 server to obtain all necessary IPv6 configuration parameters.
6. The server sends a DHCPv6 REPLY unicast message to the client. The content of the message varies depending on if it is replying to a REQUEST or INFORMATION-REQUEST message. (Note: The client will use the source IPv6 Link-local address of the RA as its default gateway address. A DHCPv6 server does not provide this information.)

Enable Stateless DHCPv6 on an Interface
---------------------------------------

.. code-block :: none

    R1(config-if)# ipv6 nd other-config-flag


Enable Stateful DHCPv6 on an Interface
--------------------------------------

.. code-block :: none

    R1(config-if)# ipv6 nd managed-config-flag
    R1(config-if)# ipv6 nd prefix default no-autoconfig