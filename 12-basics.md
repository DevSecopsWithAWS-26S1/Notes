# AWS EBS Volume – Attach, Partition and Mount in RHEL 9

Example scenario:

- Existing root disk: `/dev/nvme0n1`
- New EBS volume: 20 GB
- New disk device: `/dev/nvme1n1`
- Partition: `/dev/nvme1n1p1`
- Mount directory: `/data`
- Filesystem: XFS

## Step 1. Create EBS volume in AWS

1. Open AWS Console.
2. Go to EC2 → Elastic Block Store → Volumes.
3. Click Create volume.
4. Select:
   - Volume type: gp3
   - Size: 20 GiB
   - Availability Zone: Same AZ as your EC2 instance.
5. Click Create volume.

## Step 2. Attach EBS volume

1. Select the newly created volume.
2. Click Actions → Attach volume.
3. Select your RHEL EC2 instance.
4. Device name:

```
/dev/sdf
```

5\. Click Attach volume.

On Nitro-based EC2 instances, Linux may identify this volume as `/dev/nvme1n1`.

## Step 3. Verify the new disk in RHEL

Connect to your RHEL server:

```
lsblk
```

Example:

```
NAME          SIZE TYPE MOUNTPOINT
nvme0n1        10G disk
├─nvme0n1p2   200M part /boot/efi
├─nvme0n1p3   960M part /boot
└─nvme0n1p4   8.8G part /
nvme1n1        20G disk
```

Confirm that `/dev/nvme1n1` is your newly attached, empty EBS volume.

## Step 4. Create a partition

```
sudo fdisk /dev/nvme1n1
```

Inside fdisk, enter:

| Command | Purpose              |
| ------- | -------------------- |
| `n`     | New partition        |
| `p`     | Primary partition    |
| `1`     | Partition number     |
| Enter   | Default first sector |
| Enter   | Default last sector  |
| `p`     | Verify partition     |
| `w`     | Save changes         |

Partition created

## Step 5. Verify partition

```
sudo partprobe /dev/nvme1n1
lsblk
```

Expected:

```
nvme1n1       20G disk
└─nvme1n1p1   20G part
```

## Step 6. Format partition

Create an XFS filesystem:

```
sudo mkfs.xfs /dev/nvme1n1p1
```

## Step 7. Create mount directory

```
sudo mkdir -p /data
```

## Step 8. Mount the partition

```
sudo mount /dev/nvme1n1p1 /data
```

## Step 9. Verify storage

```
df -h
```

Expected:

```
Filesystem         Size  Used Avail Use%
/dev/nvme1n1p1      20G  175M   20G   1%
```

## Step 10. Make the mount permanent

First, get the UUID:

```
sudo blkid /dev/nvme1n1p1
```

Copy the UUID and edit:

```
sudo vi /etc/fstab
```

Add:

```
UUID=<your-uuid>  /data  xfs  defaults,nofail  0  2
```

Save and test:

```
sudo mount -a
```

Verify:

```
df -h
```

## Complete command reference

For quick revision:

```
# 1. Check disks
lsblk

# 2. Create partition
sudo fdisk /dev/nvme1n1

# 3. Refresh partition table
sudo partprobe /dev/nvme1n1

# 4. Verify partition
lsblk

# 5. Format
sudo mkfs.xfs /dev/nvme1n1p1

# 6. Create directory
sudo mkdir -p /data

# 7. Mount
sudo mount /dev/nvme1n1p1 /data

# 8. Verify
df -h

# 9. Get UUID
sudo blkid /dev/nvme1n1p1

# 10. Permanent mount
sudo vi /etc/fstab

# 11. Test
sudo mount -a
```

Important precautions

- Never format `/dev/nvme0n1` or your existing root partition.
- Use `p` (primary), not `e` (extended), for this new disk.
- Ensure the EBS volume and EC2 instance are in the same Availability Zone.
- Test `/etc/fstab` with `mount -a` before rebooting.


To delete a partition in RHEL 9, use `fdisk`.

### Step 1. Identify the disk and partition

```
lsblk
```

Example:

```
nvme1n1       20G disk
└─nvme1n1p1   20G part /data
```

### Step 2. Unmount the partition

If mounted:

```
sudo umount /data
```

### Step 3. Open fdisk

```
sudo fdisk /dev/nvme1n1
```

### Step 4. Delete the partition

Inside fdisk:

```
p       # Print partition table
d       # Delete partition
1       # Select partition number
p       # Verify partition deletion
w       # Save changes
```

### Step 5. Refresh and verify

```
sudo partprobe /dev/nvme1n1
lsblk
```

Partition deleted

Important:

- `d` deletes the partition entry, not the entire EBS volume.
- Data on that partition becomes inaccessible.
- Remove its `/etc/fstab` entry if you previously configured a permanent mount.
- Make sure you're operating on the new disk `/dev/nvme1n1`, never your root disk `/dev/nvme0n1`.

If you want to reuse the disk, you can create a new partition and format it again.
