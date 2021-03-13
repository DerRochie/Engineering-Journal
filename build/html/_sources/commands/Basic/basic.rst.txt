Configuring Virtual interfaces
==============================

Virtual interfaces are a great way to connect trunk ports to a single interface of a router.

.. code-block ::

    router(config)# int g0/0.10
    router(config-if)# encapsulation dot1q 10
    router(config-if)# ip address 192.168.1.1 255.255.255.0