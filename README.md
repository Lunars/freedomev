## Installation - easy way: prepare a USB stick from a Linux desktop system

You need a USB stick to insert into the car - best 16 or 32GB, formatted as ext4.
Download and extract the latest image tarball on it as the root user (so the permissions and special files are correct).
Download here: https://www.freedomev.com/FreedomEV-1.0-usbstickimage-extract-to-an-ext4-filesystem.tgz
If you mounted the stick to /mnt/stick:
```
cd /mnt/stick
tar xvf ~/FreedomEV-1.0-usbstickimage-extract-to-an-ext4-filesystem.tgz --no-same-owner
mv freedomev-1.0-rootfs/* .
mv freedomev-1.0-rootfs/.git .
sync
cd 
umount /mnt/stick
```
It depends on the speed of your USB stick if this will take a while.
Insert the USB stick into the car, it will hopefully be mounted on a subdirectory of /disk/
Go into the chrooted environment:
```
bash /disk/usb.*/freedomevstart
chroot /disk/usb.*/
```
Update to the latest version of FreedomEV (execute in chroot on the stick / directory):
```
git pull 
#webgui for hotspot mode is currently still a git submodule
cd /var/www/html/raspap-webgui
git pull
```

And test it out! (see below)

## Installation instructions - manual installation
We start out from the NVIDIA Ubuntu image
Extract it on a USB stick, use the mounting/chroot script and install extra packages (we don't use them all yet).
Ensure you are connected to WiFi to not pull too much extra data over the Tesla network.
``` 
apt-get install flex bison liblzo2-dev texinfo zlib1g-dev zlib1g ncurses-dev g++ texinfo subversion m4 gettext texi2html liblzo2-2 libacl1 libacl1-dev libglib2.0-dev autoconf automake libtool git libexif-dev notify-osd ruby-notify zenity x11-apps kde-runtime oneko xpenguins xphoon xjokes kaffeine marble libreadline-dev libc-dev libncurses5-dev libreadline-dev libsqlite3-dev libgtk2.0-dev libagg-dev libfribidi-dev nmap wireshark tcpdump firefox i3 fbi imagemagick mplayer hostapd dnsmasq bridge-utils dstat screen tmux chromium-browser mpg123 feh vim qv4l2 qv4l2 kde-style-breeze-qt4 locate links wget festival festvox-kallpc16k festvox-kdlpc16k  festvox-us-slt-hts festvox-don festvox-en1 festvox-rablpc16k  festvox-us1  festvox-us2 festvox-us3 xterm konsole xdotool x11-utils xauth xserver-xephyr
```

On your usb stick you can go to the / filesystem directory and 
```
git clone http://www.github.com/jnuyens/freedomev .
```
For easy access to the applications, adjust your path:
```
echo "export PATH=$PATH:/freedomev/tools" >> ~/.bash_profile
source ~/.bash_profile
```

### Test it out:
```
cid-message "FreedomEV Upgrade Initiated, prepare to be Pan Galactic Gargleblasted!"
```
This should show this message on your central display

### Lets test some more:
```
moonshine.sh
```
This should make the colors on you Instrument Cluster (behind the steering wheel) fade slowly
