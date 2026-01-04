### Disk Image


Unzip the disk image
```
gzip -d example.dd.gz
```

Mount the disk image
```
sudo mount -o loop example.dd /mnt
```

Check the file type
```
file example.dd
```

Check the partition
```
fdisk -l example.dd
```

Check the directory
```
ls /mnt
```
  
Move into the dirctory
```
cd /mnt/bin
```

Search for a flag
```
sudo grep -R "Flag{" /mnt 2>/dev/null
```

#### [Multiple Partitions](#partitions)
Reference: Pico DISKO 2

If `fdisk` shows a disk image has multiple partitions 

```
sudo fdisk -l disko-2.dd
Disk disko-2.dd: 100 MiB, 104857600 bytes, 204800 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x8ef8eaee

Device      Boot Start    End Sectors Size Id Type
disko-2.dd1       2048  53247   51200  25M 83 Linux
disko-2.dd2      53248 118783   65536  32M  b W95 FAT32
```
```
offset = start_sector * sector_size
```
```
disko-2.dd1 = 2048 * 512
disko-2.dd2 = 53248 * 512
```
```
sudo mkdir -p /mnt2
sudo mount -o loop,offset=1048576 disko-2.dd /mnt2
```
```
sudo mkdir -p /mnt3
sudo mount -o loop,offset=27262976 -t vfat disko-2.dd /mnt3
```

To search all file in a particion
```
sudo find /mnt2 -type f -exec strings -a {} + | grep flag{

```

To search a temporary file for the first partition
```
sudo dd if=disko-2.dd of=disko-2-part1.dd bs=512 skip=2048 count=51200
sudo strings -a -o disko-2.dd | tail -c +1048577 | grep "flag{"
```

To search for a flag directly a disk image file (Go to [partitions](#partitions))
```
sudo strings -a -o example.dd | tail -c +1048577 | grep "flag{"
```
Reference: Pico DISKO 3

