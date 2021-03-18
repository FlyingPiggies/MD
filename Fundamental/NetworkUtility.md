# Network Utility

## Ping

***

Ping is a basic networking utility that comes with your operating system. You can use it to check whether an IP address can be reached.

Ping does two main things. First, it checks whether there's a connection between the machine you're ping from and another machine(or more specifically, another IP address) on the network. Second, it looks at the speed of the connection, also known as the latency time. The latency time is the round-trip time, or the time a packet takes to reach the other IP address and return, measured in the milliseconds.

## Tracert

***

Tracert, also known as traceroute, is another basic networking utility.

Tracert is useful in a similar way to ping, in that it looks at the connection between the sender and the destination. Unlike the ping, however, tracert provides details on all the "hops" the packet went through to get to the destination, including switches and routes, along with the IP address and DNS information of each. It then breaks down the information of each hop to show the latency between points.

## ARP

***

ARP stands for "Address Resolution Protocol". It's used to determine the MAC address associated withe a particular IP address. You can use the ARP network utility to display the ARP table, which shows the mapping between IP and MAC address.

## Netstat

***

Netstat, short for "network statistics", allows you to display the network connections for TCP (Transmission Control Protocol) and UDP (User Datagram Protocol). Essentically, it lets you check whether the connections exist, and provides statistics to show how the connections is performing.

## Nbtstat

***

Nbtstat is a primarily diagnostic network utility. It uses NetBIOS over TCP/IP, a protocol for allowing old NetBIOS applications to be run on a TCP/IP network.

## Nslookup

*** 

Nslookup, which stands for "name server lookup", is used to query the domain name system (DNS) for domain name or IP address mapping, or to obtain other kinds of DNS records.

## IPconfig

IPconfig is an application run on the console used for displaying information on TCP/IP configuration and information pertaining to the DNS and DHCP (Dynamic Host Configuration Protocol).


