# Ubuntu Setup 

Specific steps to init a typical ubuntu env.

## Basic Installation

```
echo "install basic utilities"
sudo -s
apt update
apt upgrade
apt install curl git nodejs npm net-tools openssh-server fswatch open-vm-tools
apt autoremove


echo "install snaps"
snap install chromium aria2c
snap  install code --classic
snap  install eclipse --classic
snap install youtube-dl
snap install docker
snap install ffmpeg


echo "install sdkman"
curl -s "https://get.sdkman.io" | bash
source "$HOME/.sdkman/bin/sdkman-init.sh"
sdk install 11.0.7.fx-librca
sdk install maven
sdk install visualvm
```

## Post Init

* host name change
* SSH server setup: add pub key, disable password login 

## Notes
* At least on the latest 20.04.1 LTS, VMWare is recommendinig using open-vm-tools instead of its own vmware tools. 