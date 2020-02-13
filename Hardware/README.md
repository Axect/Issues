# WIFI module not loaded

## Machine Specification & OS

* Nvidia graphic card
* Arch linux

## Solution

* Maybe there is a problem for `nvidia` graphic card.
* Install `arch-prime-git`
	* `nvidia`
	* `xf86-video-intel`
	* `bbswitch-dkms`
* Change graphic card to nvidia
	```sh
	sudo prime-select boot nvidia
	```
* Reboot
