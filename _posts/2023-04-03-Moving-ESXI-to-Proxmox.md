---
    title: Moving ESXI (6.5) Virtual Machines to Proxmox
    date: 03-04-2023
    categories: [tutorials]
    tags: [esxi, proxmox]
---
<!-- Post Image -->
<style>
    .center {
  display: block;
  margin-left: auto;
  margin-right: auto;
  width: 50%;
}
    </style>
<img src="https://i.imgur.com/sm6Y2Jv.jpg" alt= “python” width="400rem" height="value" class="center">
<br/><br/>
<!-- End Post Image -->
# Moving ESXI (6.5) Virtual Machines to Proxmox

## Steps to achieve migration (TL;DR)
* Export Existing VM’s from ESXI
* Convert vmdk files to qcow2 
    *  https://cloudbase.it/qemu-img-windows/
    * Unzip to directory
    * Make sure vmdk is in same directory as qemu-img.exe (for ease of conversion)
    * Use this command to convert vmdk to qcow2
        * qemu-img.exe convert -f vmdk -O qcow2 “YOURVMDKNAME.vmdk” YOURVMDKNAME.qcow2
* Decommission ESXI Server and install Proxmox
    * https://www.proxmox.com/en/downloads/category/iso-images-pve
* Import qcow2 images
    * https://getlabsdone.com/how-to-import-qcow2-into-proxmox-server-step-by-step/
* Setup Proxmox VM for migration
* Configuring Proxmox VM for the imported qcow2 image
* Test VMs making sure everything works (including connection to SAN)
<br /><br />

## Export Existing VM’s from ESXI (6.5)
* Login to ESXI

* Go to Virtual Machines on the left

* Find your VM you are exporting

* Right click the VM select Power > Power Off

* Right click on the VM again and select Export

* Select Export on the Export screen that pops up

* This will Download the vmdk, ovf and mf files to your machine

* Be patient this will take some time for larger VMs
<br /><br />

## Convert vmdk files to qcow2
* I completed the conversion to qcow2 on Windows (it’s probably easier to do this on Linux)

* Got to this address and download qemu-img.zip (https://cloudbase.it/qemu-img-windows/):

* Unzip this folder to your Desktop

* Copy your vmdk into this folder (so that the qemu-img.exe is in the same folder as your vmdk)

* Open the Command Line and navigate to the folder we just unzipped (or type cmd into the address bar in * explorer (and hit Enter) – this will open CMD prompt to that directory)

* Use this command to convert the vmdk to qcow2:

    > qemu-img.exe convert -f vmdk -O qcow2 “YOURVMDKNAME.vmdk” YOURVMDKNAME.qcow2

**NOTE 1: You can download the vmdk from the ESXI storage datastore too (go to storage and then to your datastore, then “Datastore Browser”.). Downloading it this way you will need to convert using the raw switch (since this downloads a raw vmdk file).**

> qemu-img.exe convert -f raw -O qcow2 “YOURVMDKNAME-flat.vmdk” YOURVMDKNAME.qcow2

**NOTE 2: You can check what format a vmdk is by using the following command:**

> qemu-img.exe info YOURVMDKNAME.vmdk

<br /><br />

## Decommission ESXI Server and install Proxmox
If you are using the same server hardware you can now decommission ESXI and install Proxmox. I use the latest Proxmox ISO to install to my lab server.

Here is the link to the latest Proxmox distros: https://www.proxmox.com/en/downloads/category/iso-images-pve
<br /><br />

## Import qcow2 images
First thing we want to do is make a folder to hold the migrated qcow2 files temporarily. Login to your Proxmox server and access the shell. Use this command to make directory to copy to: mkdir /var/lib/vz/template/qemu (note: You don’t have to use sudo here because you are logged in as root)

I use Powershell with the scp (Secure Copy) command to move the qcow2 files to the Proxmox server. Use this command to copy using scp:

> scp YOURVMDKNAME.qcow2 root@PROXMOX_IP_ADDRESS:/var/lib/vz/template/qemu

[How to Import QCOW2 into Proxmox Server? | Step by Step.](https://getlabsdone.com/how-to-import-qcow2-into-proxmox-server-step-by-step/)
<br /><br />

## Testing VMs, making sure everything works (including connection to SAN)
I am using a SAN so I had to make sure connections works afterword’s. I tested by installing Proxmox onto my ESXI as a VM and followed all the steps above. After I completed all the steps I booted the VM in Proxmox. I thought I was doing something wrong with Proxmox because I could not get the VM to communicate with the network (only able to ping the host (Proxmox) and not my gateway). It turns out since I was using nested vitalization I had to turn on Promiscuous mode on the VM Network in ESXI. After fixing this I was able to fully test the migrated qcow2 VM. Everything worked! I exported/converted all my VMs and decommissioned ESXI, installed Proxmox and followed the same steps again. I am now fully migrated to Proxmox. 