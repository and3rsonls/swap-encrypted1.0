## Swap Device Encryption Without Hibernation

### Distro
in this case the [Arch Linux](https://wiki.archlinux.org/title/Installation_guide) distro is installed and configured

### Preparations
`# swapoff /dev/sdX`  
umount swap device

### UUID
`# blkid` 
to view device UUID and type

### Setup crypttab
`# vim /etc/crypttab`  
add a new device

~~~bash
# <name>  <device>                          <password>        <options>
swap      UUID=XXX...(UUID type swap)      /dev/urandom      swap,cipher=aes-cbc-essiv:sha256,size=256
~~~

### Setup fstab
`# vim /etc/fstab`  
add a new device

~~~bash
# <file system>                 <dir>       <type>      <options>   <dump> <pass>
# /dev/sdX        
UUID=XXX...(UUID type swap)     none        swap        defaults    0       0
~~~

### Sources
- https://linux.die.net/man/5/crypttab<br>
- https://man.archlinux.org/man/crypttab.5<br>
- https://wiki.archlinux.org/title/Dm-crypt/System_configuration<br>
<br>
Linux® is a registered trademark of Linus Torvalds.<br>
The Arch Linux name and logo are recognized trademarks. Some rights reserved.<br>
Copyright © 2002-2021 Judd Vinet, Aaron Griffin and Levente Polyák.<br>
