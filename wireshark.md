## Wireshark

* To open a file with Wireshark `wireshark -r example.pcapng`
* **Client** is the source.
* **Server** is the destination.

* To filter a specific frame number `frame.number == 100`
* To filger a specific frame number that contain banana in the info field ` frame contains "banana"`


#### USB

* `usb.data_len == 9`  Filter keyboard events in USB packet
* `usb.data_len == 4`  Filter mouse events in USB packet


## Tshark

To display the source (client) and destination (server) IP address 
```
tshark -r example.pcap -T fields -e ip.src -e ip.dst
```

To find the hostname of the first website the client visited
```
tshark -r example.pcapng -Y "http.request" -T fields -e http.host | head -n 1
```
To find the third website the client visited
```
tshark -r example.pcapng -Y "http.request" -T fields -e http.host | sed -n '3p'
```

To find what software is sending the HTTP requests.
```
tshark -r example.pcapng -Y "http.request" -T fields -e http.user_agent
```
To list the frame numbers of the ping originating from the source 127.0.0.1
```
tshark -r example.pcapng -Y "icmp.type == 8 && ip.src == 127.0.0.1" -T fields -e frame.number
```
To count the number of pings from the source 127.0.0.1
```
tshark -r example.pcapng -Y "icmp.type == 8 && ip.src == 127.0.0.1" -T fields -e frame.number | wc -l
```
To find the frame number that contains ARP request. 
```
tshark -r example.pcapng -Y "arp.opcode == 1" -T fields -e frame.number
```
To find the domain queried in a nameserver (NS) lookup.
```
tshark -r example.pcapng -Y "dns.qry.type == 2" -T fields -e dns.qry.name
```
* Type 2 = Nameserver (NS)
* Type 1 = A. IPv4 address
* Type 28 = AAAA. IPv6 address
* 
To find the frame number that may contain Chromecast
```
tshark -r example.pcapng -Y "mdns" -T fields -e frame.number
```

#### Extracting data using Tshark
To extract raw data from USB iso.data field, removing the line breaks, then reversing to binary data. Then finally save as audio.raw.
```
tshark -r example.pcap -T fields -e usb.iso.data | tr -d '\n' | xxd -r -p > audio.raw
```

* `tr -d '\n'`   Removes line breaks
* `xxd -r -p > audio.raw`  `xxd` to create a hex dump or reverse a hex dump back to binary form. `-r` to reverse the process, converting a hex hump back into binary form. `-p` to use a plain hex dump format, where only the hex bytes are processed. 
