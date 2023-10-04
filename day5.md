
https://kyubot.tistory.com/138

wget http://archive.ubuntu.com/ubuntu/pool/universe/b/backport-iwlwifi-dkms/backport-iwlwifi-dkms_9858-0ubuntu3_all.deb

sudo dpkg -i backport-iwlwifi-dkms_9858-0ubuntu3_all.deb


https://h30434.www3.hp.com/t5/Notebook-Boot-and-Lockup/HP-Omen-17-New-install-Ubuntu-20-04-doesn-t-boot-after-apt/td-p/8842563

On a new HP Omen 017 (Nvidia RTX 4090) installed the Ubuntu 20.04.2 I had handy. Dual boot with W11.

First thing after login

 

sudo apt update
sudo apt install dkpm
sudo ubuntu-drivers autoinstall
sudo apt update
sudo apt upgrade



ubuntu-drivers devices

현재 사용중인 그래픽카드 확인

lshw -numeric -C display

lspci | grep -i nvidia

sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
 

sudo apt install nvidia-driver-465 nvidia-settings

 sudo reboot now 

Restart will not boot.

 

Updated the BIOS to latest.
