EIGRP Routing Protocol
----------------------
----------------------

EIGRP (Enhanced Interior Gateway Routing Protocol)

EIGRP-IPv4
^^^^^^^^^^

.. code-block :: bash

   Router(config) router eigrp [area number]
   Router(config) network [network]

   # Optional - use if there are multiple subnets of the network on the same network
   Router(config) no auto-summary


EIGRP-IPv6
^^^^^^^^^^
