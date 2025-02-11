## Steganography


To extract hidden data from an image
```
steghide extract -sf secret.bmp
```

To read a message on QR code
```
zbarimg secret.png
```

To check metadata
```
exiftool secret.png
```
To analyze hidden layers
```
zsteg secret.png
```
To extract hidden files
```
binwalk --dd='.*' secret.png 
```