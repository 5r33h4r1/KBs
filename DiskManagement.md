# Disk Management
 
### Partitioning the disk

	1. use `sudo fdisk -l` to list the disks.
 	2. Use the below `fdisk` to create one more of Linux LVM partition
     `fdisk /dev/sdx`
      and follow the instructions (chose 8e for Linux LVM Partition)
     . sdx is the name of the drive that you would like to partition.
     . Now you may have partitions like `/dev/sdx1` 
    3. Now run the below command to format the partition
    	`sudo mkfs -t ext4 /dev/sdc1`
    4. Now the file can be mounted to any directory
    	- Create a new directory `sudo mkdir /mnt/drive`
    	- mount the new volume to the directory using the below command
    	  `sudo mount /dev/sdx1 /mnt/drive`
    	  Note: This is only an one time mount. Will not persist after restart
    5. For persistent mount the entry needs to be added to `/etc/fstab`
    	- run `sudo blkid` to find the UUID of the newly created partition
    	- edit `/etc/fstab`
    	`UUID=<UID-of-new-partition-as-per-blkid>  /mnt/drive   ext4   defaults,nofail   1   2`
    6. Reboot the system
    7. Now you should see the drive in /mnt/drive directory
    8. To get the write permissions follow the below steps
    	- Change Group ownership to adm group
    		`sudo chgrp adm /mnt/data/`
    	- Give write permissions to the group
    		`sudo chmod -R g+w /mnt/data/`



