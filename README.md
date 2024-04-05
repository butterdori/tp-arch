# tp-arch
Arch Linux installation and configuration for Thinkpad T14s AMD Gen 3

## Installation
Process

## After installation
### Keyboard
**keyd**

https://github.com/rvaiya/keyd
```
git clone https://github.com/rvaiya/keyd
cd keyd
make && sudo make install
sudo systemctl enable keyd && sudo systemctl start keyd
```
Install and start keyd `sudo systemctl enable keyd`

Config file in `/etc/keyd/default.conf`

```
[ids]
#Exception for NINJA keyboard
-258a:004c
*
[main]
#Escape when presesd, control when held
capslock = overload(control, esc)
#Remap esc to capslock
esc = capslock
pagedown = macro(leftalt+right)
pageup = macro(leftalt+left)
rightcontrol=layer(fn)
[fn]
pageup = macro(pageup)
pagedown = macro(pagedown)

```
