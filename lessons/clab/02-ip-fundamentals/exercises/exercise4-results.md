# Deliverables

## Diagnostic commands and applied fix

```bash
# Interface is manually disabled
A:srl1# show interface brief
+---------------------+------------------------+------------------------+------------------------+------------------------+------------------------+
|        Port         |      Admin State       |       Oper State       |         Speed          |          Type          |      Description       |
+=====================+========================+========================+========================+========================+========================+
| ethernet-1/1        | disable                | down                   | 25G                    |                        |                        |
| ethernet-1/2        | enable                 | up                     | 25G                    |                        |                        |

# Bring it back up and validate it state
A:srl1# enter candidate
--{ + candidate shared default }--[  ]--
A:srl1# set / interface ethernet-1/1 admin-state enable
--{ +* candidate shared default }--[  ]--
A:srl1# commit now
All changes have been committed. Leaving candidate mode.
--{ + running }--[  ]--
A:srl1# show interface brief
+---------------------+------------------------+------------------------+------------------------+------------------------+------------------------+
|        Port         |      Admin State       |       Oper State       |         Speed          |          Type          |      Description       |
+=====================+========================+========================+========================+========================+========================+
| ethernet-1/1        | enable                 | up                     | 25G                    |                        |                        |
| ethernet-1/2        | enable                 | up                     | 25G                    |                        |                        |

# Verification
~/repositories/github/maor-klir/network-fundamentals/lessons/clab/02-ip-fundamentals main*​ 9m20s
❯ docker exec clab-ip-fundamentals-host1 ping -c 3 10.1.1.1
PING 10.1.1.1 (10.1.1.1): 56 data bytes
64 bytes from 10.1.1.1: seq=0 ttl=64 time=64.278 ms
64 bytes from 10.1.1.1: seq=1 ttl=64 time=2.139 ms
64 bytes from 10.1.1.1: seq=2 ttl=64 time=2.103 ms

--- 10.1.1.1 ping statistics ---
3 packets transmitted, 3 packets received, 0% packet loss
round-trip min/avg/max = 2.103/22.840/64.278 ms
```
