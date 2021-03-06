# Volume Management in Dashboard

Objective 1: Scope demo/demo.

```
Create a New Volume:
• Name: demo-vol1
• Description: Database Volume for demo Project
• Volume Source: empty volume
• Type: no volume type
• Size: 1
Start the Instance test-vm1.
Attach the Volume demo-vol1 to Instance test-vm1.
```

Objective 2: Scope demo/demo.
```
Login to Console of Instance test-vm1.
Create ext3 type filesystem on newly attached Volume:
sudo mkfs.ext3 /dev/vdb
Mount the Volume:
sudo mount /dev/vdb /mnt
Create a file with Instance "stamp":
hostname >> /mnt/file.txt
date >> /mnt/file.txt
Verify the file:
pg /mnt/file.txt
Unmount the Volume and Detach from the Instance.
```

Objective 3: Scope: demo/demo.
```
Create a New Snapshot demo-vol1-snap1 of the Volume demo-vol1.
Create a New Volume from the Snapshot:
• Name: demo-vol2
• Volume Source: Snapshot
• Snapshot Source: demo-vol1-snap1
```

Objective 4: Scope lisa/crm-dev.
```
Create a Volume Type lvm-2 to enable Volume scheduling to Backend LVM-2.
```

Objective 5: Scope lisa/crm-dev.
```
Change Storage Quota snapshots to 50 for Project crm-dev.
```

Objective 6:  Scope demo/demo.

```
Create a New Volume from Image:
• Name: boot-vol3
• Description: Boot Volume Created from Image system-3.5
• Volume Source: image
• Use image as source: system-3.5
```
```
Launch a New Instance from Bootable Volume:
• Name: persistent-boot-vol
• Description: Instance Created from Bootable Volume boot-vol3
• Boot Source: Volume
• Flavor: m1.tiny
• Network: private
• Security Groups: default and demo_sg
```
```
Attach a Volume demo-vol2 to Instance persistent-boot-vol and mount it to /mnt.

Create an Instance "stamp" in the file /mnt/file.txt:
hostname >> /mnt/file.txt
date >> /mnt/file.txt
Verify the file:
pg /mnt/file.txt
Copy the file to Instance Volume:
cp /mnt/file.txt ~/history.txt
Unmount the Volume and Detach from the Instance.
Shutdown the Instance.
```

Objective 7: Scope: demo/demo.
```
Create a Volume Transfer for demo-vol2.
Note down Transfer ID and Authorization ID.
```

Objective 8: Scope: lisa/crm-dev.
```
Accept the Volume Transfer, using the Transfer ID and Authorization ID noted in Objective 7.
```
Objective 9: Scope: lisa/crm-dev.

```
Create a Volume Type LUKS-1 to accomodate Volume Encryption.
Create Volume Encryption:
• Provider: nova.volume.encryptors.luks.LuksEncryptor
• Control Location: front-end
• Cipher: aes-xts-plain64
• Key size: 256
Create a New Volume encrypted-vol1 of type LUKS-1 and size 1.
```

Objective 10: Scope demo/demo.
```
Create a Backup of Volume demo-vol1.
```
```
Create a New Empty Volume:
• Name: demo-vol4
• Description: Backup Restore Volume for demo Project
• Volume Source: empty volume
• Type: no volume type
• Size: 1
```
```
Restore Backup of demo-vol1 to demo-vol4.
Start up the test-vm1 Instance, Attach and mount the Volume demo-vol4 in /mnt2 directory.
```
```
Create a file with Instance "stamp":
hostname >> /mnt2/file.txt
date >> /mnt2/file.txt
Verify the file:
pg /mnt2/file.txt
```
```
Detach the Volume demo-vol4 and Shutdown test-vm1 Instance.
```

# Managing Volumes on Command Line

Objective 1 : Scope amy/sales-crm.
```
Create a New Volume:
• Name: sales-vol1
• Description: Database Volume for sales-crm Project
• Volume Source: empty volume
• Type: no volume type
• Size: 1
Start the Instance insta2.
Attach the Volume sales-vol1 to Instance insta2. Check the device name.
```

Objective 2: Scope amy/sales-crm.

```
Login to Instance insta2.
Create ext3 type filesystem on newly attached Volume:

sudo mkfs.ext3 /dev/vdb
Mount the Volume:
sudo mount /dev/vdb /mnt
Create a file with Instance “stamp”:
hostname >> /mnt/file.txt
date >> /mnt/file.txt
Verify the file:
pg /mnt/file.txt
Unmount the Volume and Detach from the Instance.
```

Objective 3: Scope: amy/sales-crm.
```
Create a New Snapshot sales-vol1-snap1 of the Volume sales-vol1.
Create a New Volume from the Snapshot:
• Name: sales-vol2
• Volume Source: Snapshot
• Snapshot Source: sales-vol1-snap1
```

Objective 4: Scope lisa/crm-dev.
```
Create a Volume Type sales-vol-type-2 to enable Volume scheduling to Backend LVM-2.
```


