# Installation d'ArchLinux (avec archinstall)


## Prérequis

- Le secure boot doit être désactivé
- Installation des OS en UEFI
- Activer os-prober

```sh
# Installer les packages
pacman -S grub efibootmgr os-prober
#Trouver le disque avec Windows et noter le chemin de la partition EFI
fdisk -l
# Monter le volume EFI dans /mnt et on vérifie ce qu'il y a dedans
mount /dev/sda2 /mnt/ && ls -l /mnt/
# On lance os-prober
os-prober
# On sauvegarde la configuration de grub
cp /boot/grub/grub.cfg /boot/grub/grub.cfg-origin
# On lance la configuration du grub, vérifiez si le bootmgr de Windows est bien présent
grub-mkconfig -o /boot/grub/grub.cfg
# On redemarre la machine
```

J'ai trouvé cette ligne de commande à savoir ce qu'elle fait: ``grub-install --target=x86_64-efi --efi-directory=/efi --bootloader-id=GRUB``

# Resources

- https://dev.to/setevoy/arch-linux-installing-with-efi-and-windows-dual-boot-1eoh

- https://www.linuxtechi.com/dual-boot-arch-linux-windows-10/
- https://unix.stackexchange.com/questions/405472/cannot-find-efi-directory-issue-with-grub-install
- https://unix.stackexchange.com/questions/593748/os-prober-doesnt-detect-windows-10-in-archlinux
- https://bbs.archlinux.org/viewtopic.php?id=240117
- https://vitux.com/display-drives-on-linux/
- https://ubuntuforums.org/showthread.php?t=1529799
- https://www.omgubuntu.co.uk/2021/12/grub-doesnt-detect-windows-linux-distros-fix
- https://unix.stackexchange.com/questions/350079/how-to-use-os-prober-to-find-ms-windows-boot-data
- https://linuxhint.com/update_grub_arch_linux/
- https://medium.com/swlh/dual-boot-arch-linux-and-windows-the-right-way-7f59969f7525
- https://bbs.archlinux.org/viewtopic.php?id=221442
- 