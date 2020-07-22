# Ubuntu Setup 

Specific steps to init a typical ubuntu env.

## Basic Installation

```
echo "install basic utilities"
sudo -s
apt update
apt install curl git nodejs npm net-tools openssh-server
apt autoremove


echo "install snaps"
snap install chromium
snap install aria2c
snap  install code --classic
snap  install eclipse --classic
snap install youtube-dl
snap install docker


echo "install sdkman"
curl -s "https://get.sdkman.io" | bash
source "$HOME/.sdkman/bin/sdkman-init.sh"
sdk install 11.0.7.fx-librca
sdk install maven
sdk install visualvm
```

# Post Init

* host name change
* SSH server setup: add pub key, disable password login 

