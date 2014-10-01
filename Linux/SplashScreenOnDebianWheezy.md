Spalsh Screen On Debian Wheezy
==============================


#Step 1: Install Plymouth

> ### Core
sudo aptitude install plymouth
### Themes
sudo aptitude install plymouth-drm


#Step 2: Configure

##step a

Edit the file **/etc/initramfs-tools/modules** using your favorite text editor and add the modesetting for what best fits you:

### Intel
> intel_agp
drm
i915 modeset=1

### Nouveau (nVidia)
> drm
> nouveau modeset=1


### ATI
>  drm
radeon modeset=1


##step b

Now we have to configure Grub2 for whatever resolution best fits your needs.

> vim /etc/default/grub

You will also need to change this line


> GRUB_CMDLINE_LINUX_DEFAULT="quiet"

 to

> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

##step c and the final one of the step 2

Update grub by taping this commmand:

> sudo update-grub2

#Step 3: Choose a Theme

To view all thems run this:

> sudo /usr/sbin/plymouth-set-default-theme --list

To set a theme run this:

> sudo /usr/sbin/plymouth-set-default-theme spacefun

note that **spacefun** here one of the themes installed

Now you have to save the change and to do that you have just to run this command:

> sudo update-initramfs -u

##Step 4: Reboot

You must reboot your computer for the changes to take effect
