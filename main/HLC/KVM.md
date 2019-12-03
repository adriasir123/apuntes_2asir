-Crea el fichero del disco 

qemu-img create -f qcow2 hd1.qcow2 10G

-Info sobre el fichero

qemu-img info hd1.qcow2


-Creación de la máquina

kvm -m 512 -hda hd1.qcow2 -cdrom debian-10.1.0-amd64-netinst.iso




Crear disco teniendo una imagen base común (el -b, backing file)

qemu-img create -b h1.qcow2 -f qcow2 buster1.qcow2
qemu-img create -b h1.qcow2 -f qcow2 buster2.qcow2

A esto se le llama aprovisionamiento ligero, el hecho de partir de una imagen base, y que en las que salgan de ahí, se guarden las modificaciones con respecto a la imagen base.


22/11/19

Libvirt tiene
-qemu://session (con privilegios de usuario)
-qemu://system (con privilegios de root)

virsh -c (se utilizan los permisos de root)


EJ: 2 MVs con debian buster, aprovision. lig
-1 con red interna NAT (10.10.10.0/24) 
-1 con red externa tipo bridge



27/11/19

EJERCICIO HECHO POR ALBERTO
Se pueden crear por:
-virmanager
-virsh

/etc/libvirt (muchas cosas importantes)

cat /proc/sys/kernel/random/uuid (genera un uid random)

virsh -c qemu:///system define debian10.xml

En /etc/libvirt


vol-resize voll 80G

    









<!--stackedit_data:
eyJoaXN0b3J5IjpbLTYyNDM3NDkyN119
-->