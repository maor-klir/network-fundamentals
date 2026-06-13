# Deliverables

## Explanation of black hole routing

Black hole routing is when a router has a valid-looking route in its routing table, but traffic sent along that route is silently dropped.  
No error is returned to the sender, the packet simply disapperars.  
In our case, the route exists and is selected for forwarding the packet, but the next hop IP is unreachable.  
No device owns that IP, so ARP resolution fails (00:00:00:00:00:00). srl1 cannot build a valid Ethernet frame, so it drops the packet.

## ARP output showing failed resolution for 10.1.3.99

```sh
❯ docker exec -it clab-routing-basics-srl1 sr_cli -c "show arpnd arp-entries"
+-------------+-------------+----------------+-------------+--------------------------+--------------------------------------------------+
|  Interface  | Subinterfac |    Neighbor    |   Origin    |    Link layer address    |                      Expiry                      |
|             |      e      |                |             |                          |                                                  |
+=============+=============+================+=============+==========================+==================================================+
| ethernet-   |           0 |       10.1.1.2 |     dynamic | AA:C1:AB:B1:88:91        | 3 hours from now                                 |
| 1/1         |             |                |             |                          |                                                  |
| ethernet-   |           0 |       10.1.2.2 |     dynamic | 1A:48:04:FF:00:01        | an hour from now                                 |
| 1/2         |             |                |             |                          |                                                  |
| ethernet-   |           0 |      10.1.3.99 |     dynamic | 00:00:00:00:00:00        | a second from now                                |
| 1/3         |             |                |             |                          |                                                  |
| mgmt0       |           0 |    172.20.20.1 |     dynamic | 4A:B8:9C:31:72:E3        | an hour from now                                 |
+-------------+-------------+----------------+-------------+--------------------------+--------------------------------------------------+
--------------------------------------------------------------------------------------------------------------------------------------------
  Total entries : 4 (0 static, 4 dynamic)
--------------------------------------------------------------------------------------------------------------------------------------------
```
