# Virtual Box

## Export and Import VirtualBox VM images?

### Export

Open VirtualBox and enter into the `File` option to choice `Export Appliance...`

![](https://i.stack.imgur.com/WIJ98.png)

You will then get an assistance window to help you generating the image.

1. Select the VM to export
2. Enter the output file path and name

![](https://i.stack.imgur.com/lNrXD.png)

You can choice a format, which I always leave the default OVF 1.

3. Finally you can write metadata like Version and Description

Now you have an OVA file that you can carry to whatever machine to use it.

### Import

Open VirtualBox and enter into the `File` option to choice `Import`

You will then get an assistance window to help you loading the image.

1. Enter the path to the file that you have previously exported

![](https://i.stack.imgur.com/XHgG7.png)

2. Then you can modify the settings of the VM like RAM size, CPU, etc.

![](https://i.stack.imgur.com/kXQv6.png)

My recommendation on this is to enable the *Reinitialize the MAC address of all the network cards* option

3. Press `Import` and done!

Now you have cloned the VM from the host machine into another one

Reference: [https://askubuntu.com/questions/588426/how-to-export-and-import-virtualbox-vm-images](https://askubuntu.com/questions/588426/how-to-export-and-import-virtualbox-vm-images)

## Install Guest Additions

Guest Additions installs on the guest system and includes device drivers and system applications that optimize performance of the machine.  Launch the guest OS in VirtualBox and click on Devices and Install Guest Additions.

![](https://www.howtogeek.com/wp-content/uploads/2009/07/1menu.png)

The AutoPlay window opens on the guest OS and click on the Run VBox Windows Additions executable.

![](https://www.howtogeek.com/wp-content/uploads/2009/07/2autoplay.png)

Click yes when the UAC screen comes up.

![](https://www.howtogeek.com/wp-content/uploads/2009/07/3UAC.png)

Now simply follow through the installation wizard.

![](https://www.howtogeek.com/wp-content/uploads/2009/07/4installWizard.png)

During the installation wizard you can choose the Direct3D acceleration if you would like it.  Remember this is going to take up more of your Host OS’s resources and is still experimental possibly making the guest unstable.

![](https://www.howtogeek.com/wp-content/uploads/2009/07/5install3dsupport.png)

When the installation starts you will need to allow the Sun display adapters to be installed.

![](https://www.howtogeek.com/wp-content/uploads/2009/07/6confirm.png)

After everything has completed a reboot is required.

![](https://www.howtogeek.com/wp-content/uploads/2009/07/7rebootrequired.png)

Reference: [https://www.howtogeek.com/howto/2845/install-guest-additions-to-windows-and-linux-vms-in-virtualbox/](https://www.howtogeek.com/howto/2845/install-guest-additions-to-windows-and-linux-vms-in-virtualbox/)
