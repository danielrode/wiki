# Check if NOCOW attribute is set on a file

	lsattr FILE  # Capital 'C' is NOCOW flag

# Replace failed/disconnected drive in volume

TODO

# Add empty disk or partition to BTRFS volume

	sudo parted /dev/sdX mklabel gpt
	sudo parted /dev/sdX mkpart PART-LABEL btrfs 0% 100%
	sudo btrfs device add /dev/sdX1 /mnt/point

Can add whole drive instead, but using partitions is recommended so other tools like `lsblk` know what is going on with the drive.

# Convert volume to RAID1 that stores 3 copies

	sudo btrfs balance start -dconvert=raid1c3 -mconvert=raid1c3 /mnt/point
	sudo btrfs balance status /mnt/point  # To show conversion progress

# Verify block checksum (data integrity)

	sudo btrfs scrub start /mnt/point
	sudo btrfs scrub status /mnt/point  # To see progress

# Balancing

TODO

see info about -dsoft -msoft in https://unix.stackexchange.com/questions/196490/what-can-i-do-with-btrfs-profiles

see https://wiki.tnonline.net/w/Btrfs/Balance

# Diff two snapshots

	sudo btrfs send --no-data -p path/to/@snapshotA path/to/@snapshotB | btrfs receive --dump | grep '^update_extent'
