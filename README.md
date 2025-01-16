# Загрузка системы
## Задание
1. Включить отображение меню Grub.
2. Попасть в систему без пароля несколькими способами.
3. Установить систему с LVM, после чего переименовать VG.  
-------------------
1. Включить отображение меню Grub.
```
user@user:~$ sudo -i
[sudo] password for user:
root@user:~# nano /etc/default/grub
root@user:~# update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.15.0-130-generic
Found initrd image: /boot/initrd.img-5.15.0-130-generic
Warning: os-prober will not be executed to detect other bootable partitions.
Systems on them will not be added to the GRUB boot configuration.
Check GRUB_DISABLE_OS_PROBER documentation entry.
done
root@user:~# reboot
```
![изображение](https://github.com/user-attachments/assets/1fa0f9e4-a1bf-43d3-956e-a4fe1928cabb)
---------------------------
2. Попасть в систему без пароля несколькими способами.  
Способ 1. init=/bin/bash
Меняем параметры загрузки
![изображение](https://github.com/user-attachments/assets/f770a1fe-da56-4a7c-8fe4-39cbabacfc33)  
Перемонтируем / в режим Read-Write
![изображение](https://github.com/user-attachments/assets/6e9dfea0-b879-4e24-bd85-7e653b5ad58e)  
Способ 2. Recovery mode  
![изображение](https://github.com/user-attachments/assets/c866b571-e2b9-4f43-9760-8c0559d6b73a)  
![изображение](https://github.com/user-attachments/assets/59898d8b-7988-4057-b953-941d537a4047)  
-------------------
3. Установить систему с LVM, после чего переименовать VG.
```
root@user:~# vgs
  VG        #PV #LV #SN Attr   VSize  VFree
  ubuntu-vg   1   1   0 wz--n- 18.22g 8.22g
root@user:~# vgrename ubuntu-vg ubuntu-otus
  Volume group "ubuntu-vg" successfully renamed to "ubuntu-otus"
root@user:~# nano /boot/grub/grub.cfg
root@user:~# shutdown -r now
```
![изображение](https://github.com/user-attachments/assets/a58dd485-b781-46a8-930f-9ba62ca887d8)


