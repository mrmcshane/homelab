# RAID

Brief guide on configuring a 6 disk server in software RAID 5.

Install software for managing RAID:
```
yum install mdadm -y
```

Check there is no superblock (filesystem info):
```
mdadm -E /dev/sd[a-f]1
```

Create RAID5 from the 6 disks:
```
mdadm --create /dev/md5 --level=5 --raid-devices=6 /dev/sd[a-f]1
```

Check status of RAID:
```
mdadm -D /dev/md5
```

Create ext4 filesystem on RAID device:
```
mkfs.ext4 /dev/md5
```

Create mount directory:
```
mkdir /data
```

Add mount details to `/etc/fstab`:
```
/dev/md5 /data ext4 defaults 0 0
```

Mount all devices:
```
mount -a
```