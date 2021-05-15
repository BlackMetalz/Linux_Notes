-- Clone a disk using dd
dd if=/dev/vdc of=/dev/vdb bs=100M conv=sync,noerror status=progress

-- Clone a partition using dd
dd if=/dev/vdc1 of=/dev/vdb1 bs=100M conv=sync,noerror status=progress
