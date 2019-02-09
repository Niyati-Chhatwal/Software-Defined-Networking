# Software-Defined-Networking

SDN OpenFlow Virtaul Switches
Mininet, RYU, OpenFlow v1.3

Experiments
1. Use Mininet to create the following topology: (4 Hosts, 4 OVSes ) with a remote controller
2. Use RYU to implement the controller (you can use other controller such as BEACON, POX, etc...)

<img width="1024" alt="screen shot 2019-02-09 at 11 06 39 am" src="https://user-images.githubusercontent.com/45272824/52523949-515ed800-2c65-11e9-95f2-5e38d3b671e6.png">


Enforce these policies:
1.Everything follows shortest path
2.When there are two shortest paths available
      -ICMP and TCP packets take the upper/right path
              S1-S2-S3 and S2-S3-S4
      -UDP packets take the lower/left path
            S1-S4-S3 and S2-S1-S4
      -H1 and H3 cannot have HTTP traffic (TCP with port:80)
             -New connections are dropped with a TCP RST sent back to H1 or H3
             -To be more specific, when the first TCP packet (SYN) arrives S1 or S3, forwarded it to controller, controller then create a RST packet and send it back to the host.
      -H2 and H3 cannot have UDP traffic
              simply drop packets at switches


