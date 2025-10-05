create additional strorage in the sata

boot vm and execute commans

//

sudo -s

fdisk -l

pvdisplay

vgdisplay

Lvdisplay


//create pythsical volume

pvcreate /dev/sdb


vgcreate demo-vg /dev/sdb


lvcreate -L 10G -n demo-lv demo-vg


//crrate file system and mount

mkfs.ext4 /dev/demo-vg/demo-lv



mkdir /mnt/lvm-demo

mount /dev/demo-vg/demo-lv /mnt/lvm-demo




//resize logical volume

lvresize --size +12G ubuntu-vg/ubuntu-lv  

/check current strogae

df -h

//resize filsessytem

resize2fs /dev/mapper/ubuntu-vg-ubuntu-lv


//verify the extension


df -h

