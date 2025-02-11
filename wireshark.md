
## Wireshark

* [Nameserver Lookup](#nameserver)
* [PTR](#ptr)
* [ICMP](#icmp)
* [Extracting data](#extracting-data)
* [FTP](#ftp)


Open a pcap file 
```
wireshark -r filename.pcap
```

To find a channel
```
wlan.fc.type_subtype == 0x08

```
To find the organization operates the DNS resolver using command line
```
whois 127.10.10.10
```
To filter deauthenticated packets
```
wlan.fc.type_subtype == 0x0c

```
To filter out the packets that contain "deauthentication"
```
wlan.fc.type_subtype != 0x0c

```
To filter out the packets that contain "deauthentication" and data packets
```
!(wlan.fc.type_subtype == 0x0c) and !(wlan.fc.type == 2)
```
To filter out the packets that contain "deauthentication", data packets, and "authentication"
```
!(wlan.fc.type_subtype == 0x0c) and !(wlan.fc.type == 2) and !(wlan.fc.type_subtype == 0x0b)

```
To filter out the packets that contain "deauthentication", data packets, "authentication", and "acknowledgement"
```
!(wlan.fc.type_subtype == 0x0c) and !(wlan.fc.type == 2) and !(wlan.fc.type_subtype == 0x0b) and !(wlan.fc.type_subtype == 0x1d)
```



* To open a file with Wireshark `wireshark -r example.pcapng`
* **Client** is the source.
* **Server** is the destination.

* To filter a specific frame number `frame.number == 100`
* To filger a specific frame number that contain banana in the info field ` frame contains "banana"`


#### USB

* `usb.data_len == 9`  Filter keyboard events in USB packet
* `usb.data_len == 4`  Filter mouse events in USB packet


## Tshark

To find a packet that contains "flag" using Wireshark filter
```
frame contains "flag"
```
To find a packet that contains "flag" using Tshark
```
tshark -r example.pcap -Y 'frame contains "flag"'
```
To display the packets that has 127.0.0.1 as the source
```
ip.src == 127.0.0.1
```
To count how many unique destination IPs and frequency that have the source IP of 127.0.0.1. 
```
tshark -r example.pcap -Y "ip.src == 127.0.0.1" -T fields -e ip.dst | sort | uniq -c
```
To list the top 20 most frequent destination IP addresses.
```
tshark -r Exfil.pcap -Y "ip.src == 192.168.64.137" -T fields -e ip.dst | sort | uniq -c | sort -rn | head -20
```
To exclude DNS and ICMP protocoles on Wireshark
```
not dns and not icmp
```
To list all protocols used in a pcap
```
tshark -r example.pcap -T fields -e _ws.col.Protocol | sort | uniq -c
```
To list all source IPs in a pcap
```
tshark -r example.pcap -T fields -e ip.src | sort | uniq
```
To display the source (client) and destination (server) IP address 
```
tshark -r example.pcap -T fields -e ip.src -e ip.dst
```
To find the **IPv4** address responsible for www.example.com

```
tshark -r example.pcap -Y "dns.qry.name == \"www.example.com\" && dns.flags.response == 1" -T fields -e dns.a
```
```
(WireShark Filter) dns.qry.name == "\www.example.com\" && dns.flags.response == 1
```
TO find the **IPv6** address responsible for www.example.com
```
tshark -r example.pcap -Y "dns.qry.name == \"www.example.com\" && dns.aaaa" -T fields -e dns.aaaa
```


To find the **hostname** of the first website the client visited
```
tshark -r example.pcapng -Y "http.request" -T fields -e http.host | head -n 1
```
To find the third website the client visited
```
tshark -r example.pcapng -Y "http.request" -T fields -e http.host | sed -n '3p'
```

To find what **software** is sending the HTTP requests.
```
tshark -r example.pcapng -Y "http.request" -T fields -e http.user_agent
```
To list the **frame numbers** of the ping originating from the source 127.0.0.1
```
tshark -r example.pcapng -Y "icmp.type == 8 && ip.src == 127.0.0.1" -T fields -e frame.number
```
To count the number of **pings** 
```
tshark -r example.pcapng -Y "icmp.type == 8" -T fields -e frame.number | wc -l
```

To count the number of **pings** from the source 127.0.0.1
```
tshark -r example.pcapng -Y "icmp.type == 8 && ip.src == 127.0.0.1" -T fields -e frame.number | wc -l
```
To find the frame number that contains ARP request. 
```
tshark -r example.pcapng -Y "arp.opcode == 1" -T fields -e frame.number
```
To find a DNS query. 
```
(Wireshark filter) dns.qry.type == 15
```

### Nameserver
To find the domain queried in a **nameserver (NS) lookup**.
```
tshark -r example.pcapng -Y "dns.qry.type == 2" -T fields -e dns.qry.name
```

* Type 0 = Echo Response (Ping response)
* Type 1 = A. IPv4 address
* Type 2 = Nameserver (NS)
* Type 8 = Echo Request (Ping)
* Type 15 = MX. Mail Server
* Type 12 = PTR **Reverse DNS** queries
* Type 18 = ICMP
* Type 28 = AAAA. IPv6 address
* Type 33 = SVR
* 

### PTR

 To find PTR (Reverse DNS) packet
 ```
tshark -r example.pcap -Y "dns.qry.type == 12" -T fields -e ip.src -e dns.qry.name -e frame.number
```
If output is 10.10.172.192.in-addr.arpa, then queried IP address is 192.172.10.10. [More info on Reverse DNS lookup](https://www.cloudflare.com/learning/dns/glossary/reverse-dns/#:~:text=A%20reverse%20DNS%20lookup%20takes,DNS%20Glossary)

To find SVR records (Type 33).
```
tshark -r example.pcap -Y "dns.qry.type == 33" -T fields -e dns.qry.name -e dns.srv.target -e dns.srv.priority -e dns.srv.weight -e dns.srv.port
```
* The one with the next lowest priority (after the primary) is the backup server.

### ICMP

To find the IP address of the device making ICMP requests
```
tshark -r example.pcap -Y "icmp.type == 8" -T fields -e ip.src | sort | uniq -c | sort -nr
```
To find the IP address of the device responding to the ICMP requests.
```
tshark -r example.pcap -Y "icmp.type == 0" -T fields -e ip.src | sort | uniq -c | sort -nr
```

### FTP

Banner is a welcome message that can be found in the first packets with 220 response code
```
(Wireshark filter) ftp.response.code == 220
```

To find the frame number that may contain Chromecast
```
tshark -r example.pcapng -Y "mdns" -T fields -e frame.number
```

### Extracting data

**⚠️⚠️ PING can send message or a file!! Check for Hex data !!**

To extract raw data from USB iso.data field, removing the line breaks, then reversing to binary data. Then finally save as audio.raw.
```
tshark -r example.pcap -T fields -e usb.iso.data | tr -d '\n' | xxd -r -p > audio.raw
```

* `tr -d '\n'`   Removes line breaks
* `xxd -r -p > audio.raw`  `xxd` to create a hex dump or reverse a hex dump back to binary form. `-r` to reverse the process, converting a hex hump back into binary form. `-p` to use a plain hex dump format, where only the hex bytes are processed.


To extract checksums and remove `0x` and add space to each binary
```
tshark -r example.pcap -T fields -e tcp.checksum | tr -d '\n' | sed 's/0x//g' | sed 's/../& /g' > result.txt
```

To extract checksums and remove line breaks. No spaces between each binary. 
```
tshark -r example.pcap -T fields -e tcp.checksum | tr -d '\n' > result.txt
```
To extract the Encrypted Application Data from the destination IP 127.0.0.1. Remove line breaks and add a space between each binary. 
```
tshark -r example.pcap -Y "ip.dst == 127.0.0.1" -T fields -e tls.app_data | tr -d '\n' | sed 's/0x//g' | sed 's/../& /g' > result.txt
```


