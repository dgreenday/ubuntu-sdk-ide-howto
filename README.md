# Installing Ubuntu SDK on a fresh Ubuntu Xenial

``` sh
sudo add-apt-repository ppa:ubuntu-sdk-team/ppa
sudo apt-get update
# sudo apt-get upgrade
sudo apt-get install ubuntu-sdk-ide
sudo apt-get install -t xenial-backports lxd

sudo lxd-init
# Answer all questions with default

# Restart session (or machine)

# Install fixed usdk-tools (Fixed lxc.aa_profile -> lxc.apparmor.profile)
dpkg -i ubuntu-sdk-tools_0.6_amd64.deb

# Do not forget to setup SSH keys
# ssh-keygen -t rsa

# No idea why, but without this line IDE's Devices page shows the "Unknown SDK version" error for my device.
echo '{"ubuntu-sdk-15.04": "available"}' > ~/.config/QtProject/qtcreator/ubuntu-sdk/framework-cache.json

# Always run with XDG_CONFIG_HOME properly set due to bug (or feature?) in usdk-tools
XDG_CONFIG_HOME="~/.config" ubuntu-sdk-ide
```
