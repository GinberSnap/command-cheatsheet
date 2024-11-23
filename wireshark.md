## Wireshark

* `usb.data_len == 9`  Filter keyboard events in USB packet
* `usb.data_len == 4`  Filter mouse events in USB packet


## Tshark

```
tshark -r talktome.pcap -T fields -e usb.iso.data | tr -d '\n' | xxd -r -p > audio.raw
```

* `tr -d '\n'`   Removes line breaks
* `xxd -r -p > audio.raw`  `xxd` to create a hex dump or reverse a hex dump back to binary form. `-r` to reverse the process, converting a hex hump back into binary form. `-p` to use a plain hex dump format, where only the hex bytes are processed. 
