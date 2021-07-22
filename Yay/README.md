# libalpm error

## Description

`libalpm.so.12: cannot open shared object file ( Installed pacman without yay rebuild) #1519`

## Solution

`cd /tmp && git clone 'https://aur.archlinux.org/yay.git' && cd /tmp/yay && makepkg -si && cd ~ && rm -rf /tmp/yay/`
