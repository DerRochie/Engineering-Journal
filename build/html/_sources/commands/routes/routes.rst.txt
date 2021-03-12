Static and Default Routes
=========================


Static
------

Instructs the router to route remote network traffic to a specific address.

.. code-block :: none

    router(config)# ip route [remote-network] [subnet mask] [remote-address]

Default
-------

Instructs the router to send all unknown traffic to a destination address.

.. code-block :: none

   router(config)# ip route 0.0.0.0 0.0.0.0 [destination-address]

