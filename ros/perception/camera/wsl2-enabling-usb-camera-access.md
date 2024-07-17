# \[WSL2] Enabling USB Camera Access



1\) Get usbipd

{% embed url="https://learn.microsoft.com/en-us/windows/wsl/connect-usb" %}

2\) Follow the video

{% embed url="https://www.youtube.com/watch?v=t_YnACEPmrM" %}

Check your kernel version.

<figure><img src="../../../.gitbook/assets/image (31).png" alt=""><figcaption></figcaption></figure>

[https://github.com/microsoft/WSL2-Linux-Kernel/tree/linux-msft-wsl-5.15.y](https://github.com/microsoft/WSL2-Linux-Kernel/tree/linux-msft-wsl-5.15.y)

```
sudo apt update && sudo apt upgrade -y && sudo apt install -y build-essential flex bison libgtk2.0-dev libelf-dev libncurses-dev autoconf libudev-dev libtool zip unzip v4l-utils libssl-dev python3-pip cmake git iputils-ping net-tools dwarves bc
sudo mkdir /usr/src
cd /usr/src

VERSION=5.15.153.1
sudo git clone -b linux-msft-wsl-${VERSION} https://github.com/microsoft/WSL2-Linux-Kernel.git ${VERSION}-microsoft-standard && cd ${VERSION}-microsoft-standard

sudo cp /proc/config.gz config.gz
sudo gunzip config.gz
sudo mv config .config
sudo make menuconfig
sudo make -j$(nproc)
sudo make modules_install -j$(nproc)
sudo make install -j$(nproc)
sudo cp -rf vmlinux /mnt/c/Sources/

######################
# Record video in WSL
######################
sudo apt install v4l-utils guvcview
sudo guvcview
```
