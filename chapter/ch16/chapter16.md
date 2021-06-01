## Chapter 16 - Unix Networking

<small>Philipp Moritzer - 21170004</small>
<hr/>

### TCP/IP Protocol

- TCP: Layer 4 of Internet Protocols
- IP: Layer 3 of Internet Protocols
- ICMP: Internet Control Message Protocol (ping, traceroute)
- UDP: Layer 4 Protocol
- ARP: Adress Resolution Protocol (arp -a)
- HTTP: Hypertext Transfer Protocol
- FTP: File Transfer Protocol
- Telnet: Remote Acesss
- SMTP: Simple Mail Transport Protocol
- RIP: Routing Information Protocol
- DNS: Name Server (Resoulves domain name and IP Adress)
- DHCP: Dynamic host configuration protocol

### IP Setup
```bash
$ ifconfig -a # shows network interfaces (name, ip, netmask, etc.)
$ ifconfig e1000g0 plumb # automatically sets the ip to the interface
$ ifconfig e1000g0 10.0.2.5 netmask 255.255.255.0 broadcast 10.0.2.255 # sets ip address, subnetmask and broadcast address for network interface e1000g0
$ ifconfig e1000g0 up # starts the e1000g0 interface
$ route add net default 10.0.2.2 # adds 10.0.2.2 (router) as default route
$ ping 10.10.54.75 # icmp message returns if successful
```  

### Network Configuration Files
- /etc/hostname.e1000g0
- /etc/hosts
- /etc/netmasks
- /etc/defaultrouter
- /etc/resolv.conf
- /etc/nsswitch.conf

### /etc/hostname.e1000g0
- The interface name can be different depending on the system
- Sol300
  - IP addresss is located unter /etc/hosts
- 10.0.2.5 - can bes specified directly

### /etc/hosts
Contains internal IP Adresses
```file
127.0.0.1   localhost
10.0.2.5    sol300 sol300.snut.ac.kr loghost
```

### /etc/netmasks
Network address and subnetting netmask is specified
```file
10.0.2.0    255.255.255.0
```

### /etc/defaultrouter
Router Adress is specified
```file
10.0.2.2
```

### /etc/nsswtich.conf
```file
hosts: files dns
```

- If the system is note able to find an ip address of a domain name at the /etc/hosts file ist will send the query request to the DNS Server which is specified in /etc/resolv.conf

### Network commands

```bash
$ arp -a # shows IP address / Mac Adress caching table
$ ping 10.0.2.2 # sends ICMP-Message and receives one if the target is alive
$ traceroute 10.10.54.75 # check route to target and see all the routers on the way
$ nslookup www.snut.ac.kr # Domain name and IP Adress resolution
$ ftp 10.10.54.75 # starts FTP Session to 10.10.54.75
$ telnet 10.10.54.75 # starts Telnet Session to 10.10.54.75
$ telnet www.snu.ac.kr 80 # web page access
```

### netstat
- Show network status
- -i: status of the interface
- -r: routing table