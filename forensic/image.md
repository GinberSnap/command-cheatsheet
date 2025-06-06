## Examine an image file

First, get partition info

```
fdisk -l image_file.img
```

Mount image file

```
sudo mkdir /mnt/usb
sudo mount -o loop,offset=$((128 * 512)) image_file.img /mnt/usb
```

Check if it acutally mounted
```
ls -lah /mnt/usb
```
Search inside the folder
```
ls -lah /mnt/usb/flag
```
To view image files in a directory
```
ristretto /mnt/usb/Flag/image*.*
```
To read text file
```
nano "/mnt/usb/Flag/secret.txt"
```

To identify the file type
```
file /mnt/usb/Flag/*
```