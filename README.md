# accel-ppp-deb

This repository contains binary packages for accel-ppp and dkms packages for ipoe and vlan_mon drivers. It supports LTS versions of Debian and Ubuntu supported by Ubuntu team (free period) and Debian/Debian LTS team.

## Step 1. Add Public GPG key

```shell
wget -O - https://github.com/svlobanov/accel-ppp-deb/raw/main/accel-ppp-deb.gpg.key | sudo apt-key add -
```

## Step 2. Add APT Repository

```shell
echo deb https://raw.githubusercontent.com/svlobanov/accel-ppp-deb/main `lsb_release -cs` nightly  | sudo tee -a /etc/apt/sources.list

sudo apt update
```

## Step 3. (Optional) install kernel modules

If you need ipoe or vlan_mon drivers, install `accel-ppp-ipoe-dkms` or `accel-ppp-vlan-mon-dkms` package. DKMS system requires linux headers. If your system is not up to date, then apt package manager may install newer linux headers than currently launched kernel, in this case, DKMS will not be able to build a driver. To avoid this issue please update your system and reboot the host:

```shell
sudo apt update && sudo apt upgrade && sudo reboot
```

If you don't like this approach, then manually install linux headers the same version as currently launched kernel.

To install ipoe/vlan_mon drivers:

```shell
sudo apt install accel-ppp-ipoe-dkms
sudo apt install accel-ppp-vlan-mon-dkms
```

## Step 4. Install accel-ppp

```shell
sudo apt install accel-ppp
```

Use accel-ppp manuals to configure the service.
