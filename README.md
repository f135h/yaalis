# arsh
This script is designed to suit my needs, but maybe, it will be useful for you too...

**Warning (1): This script create/delete partitions. Use at your own risks.**

**Warning (2): This script assume that your disk is fresh and wiped.**

# The script
* Configure the partitions (LVM on UEFI system using GPT)
  1. Create GPT partition table
  2. Create bootable EFI System Partition
  3. Create partiton for /boot
  4. Mark remaining partition for LVM
* Install the basic system
  * base
  * base-devel
  * linux
  * linux-firmware
  * efibootmgr
  * btrfs-progs
  * lvm2
  * grub
  * nano
  * sudo
* Modify root password
* Create a standard user

### Steps
1. Boot the [original Arch Linux installation media](https://www.archlinux.org/download/)
2. `wget https://raw.githubusercontent.com/f135h/yaalis/master/yaalis`
3. `sh arsh`
5. Wait...
6. Reboot (remove the [original Arch Linux installation) media](https://www.archlinux.org/download/) from your device
7. Login and `su`
8. Edit the `/etc/sudoers` file with nano, use the command `EDITOR=nano visudo`
9. Logout from root
10. Voilà!

### Variables
* **disk**
  Your disk name, example: `disk=nvme0n1`
* **disk_part_efi**
  efi partition, example: `disk_part_efi=${disk}p1`
* **disk_part_boot**
  boot partition, example: `disk_part_efi=${disk}p2`
* **disk_part_lvm**
  lvm partition, example: `disk_part_efi=${disk}p3`
* **lvm_vg**
  Volume group name
* **lvm_lv_root**
  logical volume name for root, example `lvm_lv_root=arch-root`
* **lvm_lv_root_size**
  root volume size (include option), example `lvm_lv_root_size="-L 15G"`
* **lvm_lv_home**
  logical volume name for home, example `lvm_lv_home=arch-home`
* **lvm_lv_home_size**
  home volume size (include option), example `lvm_lv_home_size="-l 100%FREE"`
* **user_root_pwd**
  root password, example `user_root_pwd=1234`
* **user_user_name**
  standard user login, example `user_user_name=f135h`
* **user_user_pwd**
  standard user password, example `user_user_pwd=xcvb`

# License
Licensed under the WTFPL [license](LICENSE).
