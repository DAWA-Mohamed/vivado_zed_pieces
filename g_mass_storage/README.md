You may read about this
http://www.wiki.xilinx.com/Zynq+Linux+USB+Device+Driver

Here is a working example w/ petalinux 2014.4(linux 3.17):
 - Use config under subsystems/linux/configs/kernel as your kernel config(*1)
 - patch your device tre with devicetree.patch(*2)

With your new kernel and system.dtb, 
 - modprobe usb_f_mass_storage
 - insmod g_mass_storage.ko file=/dev/mmcblk0
 - attach ZedBoard OTG port to PC, DONE.

1) You don't need 
    <M> USB functions configurable through configfs
2) Actually, you only need
usb_phy0: phy0 {
    compatible = "usb-nop-xceive";
    #phy-cells = <0>;
}



