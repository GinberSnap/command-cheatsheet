## Wireshark

* To open a file with Wireshark `wireshark -r example.pcapng`
* **Client** is the source.
* **Server** is the destination.


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

To find what software is sending the HTTP requests.
```
tshark -r BasicTraining.pcapng -Y "http.request" -T fields -e http.user_agent
```
To count the number of the 



```
tshark -r talktome.pcap -T fields -e usb.iso.data | tr -d '\n' | xxd -r -p > audio.raw
```

* `tr -d '\n'`   Removes line breaks
* `xxd -r -p > audio.raw`  `xxd` to create a hex dump or reverse a hex dump back to binary form. `-r` to reverse the process, converting a hex hump back into binary form. `-p` to use a plain hex dump format, where only the hex bytes are processed. 
