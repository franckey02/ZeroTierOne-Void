ZeroTierOne for Void linux
======

# Install xbps package:
```
#add libs
sudo xbps-install -S openssl libstdc++ glibc libgcc wget
#download and install xbps pkg of zerotierone
wget https://github.com/franckey02/ZeroTierOne-Void/releases/download/1.16.0/zerotierone-1.16.0_1.x86_64.xbps
sudo xbps-rindex -a ./zerotierone-1.16.0_1.x86_64.xbps
sudo xbps-install -R $PWD zerotierone-1.16.0_1
#add service
sudo mkdir /etc/sv/zerotier-one
clear
echo '#!/bin/sh
exec 2>&1
exec /usr/bin/zerotier-one -d' | sudo tee /etc/sv/zerotier-one/run > /dev/null
sudo  chmod +x /etc/sv/zerotier-one/run
sudo ln -s /etc/sv/zerotier-one/ /var/service/
```
or ...

# Build & install:
```
#Download and extract source
wget https://github.com/franckey02/ZeroTierOne-Void/archive/refs/tags/1.16.1.tar.gz
tar -xzvf 1.16.1.tar.gz
#Building
cd ZeroTierOne-Void-1.16.1
sudo xbps-install -S git make gcc  linux-headers openssl-devel libffi-devel rust cargo  openssl libstdc++ glibc libgcc wget
sudo xbps-install -S pkg-config
sudo xbps-install -S openssl-devel
make -j2
#Install
make install
#Add service
sudo mkdir /etc/sv/zerotier-one
clear
echo '#!/bin/sh
exec 2>&1
exec /usr/bin/zerotier-one -d' | sudo tee /etc/sv/zerotier-one/run > /dev/null
sudo  chmod +x /etc/sv/zerotier-one/run
sudo ln -s /etc/sv/zerotier-one/ /var/service/
```

