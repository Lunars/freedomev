# freedomev
FreedomEV repository. Unlocking the full potential of Linux on your EV!

### Disclaimer
This is not made by Tesla, nor officially endorsed (just yet?). We take no responsability whatsoever for damage, costs, injury or even death caused by this to you or third parties. In certain territories, it might violate local regulations, we don't know about that, and we don't care. We hope FreedomEV will enjoy your car even more.
I am open to my Tesla Service Center about what we are doing here. But when I let my car being services, I disable all strange stuff so they might not become too confused (unless they ask for it). Tesla car service people have instructions to remove all visible USB attached stuff to not interfere with possible updates, keep that in mind. Also, I don't claim warranty on stuff I broke myself, Tesla was very reasonable with respect to that. 
We hope Tesla will provide - in a not too distant future - a legitimate way for owners to get root on your own car. For example by allowing owners to request a secret ssh token through their web account or car app. But nothing is certain until Elon Musk tweets about it ;)
We also hope other electric car manufacturers will be inspired, and allow the community to grow beyond what we currently imagine.

## Prerequisites
You need root access on the Central Instrument Display of your Tesla.
Currently only tested on my Model X. I suppose it will also work on the Model S.
The latest generation of Model S/X and the Model 3 might be more problematic 
_for now_ as they use an Intel based board instead of the ARM based Linux system. If someone has root to such a Tesla, we might get FreedomEV working relative easily.

## Installation - easy way: prepare a USB stick from a Linux desktop system
You need a USB stick to insert into the car - best 16 or 32GB, formatted as ext4.
Download and extract the latest image tarball on it as the root user (so the permissions and special files are correct).
If you mounted the stick to /mnt/stick:
```
cd /mnt/stick
tar xvf ~/Downloads/freedomev-1.0.xz
sync
cd 
umount /mnt/stick
```
It depends on the speed of your USB stick if this will take a while.
Insert the USB stick into the car, it will hopefully be mounted on a subdirectory of /disk/
Go into the chrooted environment:
```
bash /disk/*/freedomev/chroot
```
And test it out! (see below)

## Installation instructions - manual installation
We start out from the NVIDIA Ubuntu image
Extract it on a USB stick, use the mounting/chroot script and install extra packages (we don't use them all yet).
Ensure you are connected to WiFi to not pull too much extra data over the Tesla network.
``` 
apt-get install flex bison liblzo2-dev texinfo zlib1g-dev zlib1g ncurses-dev build-essential g++ texinfo subversion m4 gettext texi2html liblzo2-2 libacl1 libacl1-dev libglib2.0-dev autoconf automake libtool git libexif-dev notify-osd ruby-notify zenity x11-apps razorqt kde-runtime  qtstalker qt3-examples kaptain oneko xpenguins xphoon xjokes kaffeine marble libreadline-dev libc-dev libncurses5-dev libreadline-dev libsqlite3-dev libgtk2.0-dev libagg-dev libfribidi-dev lidssl-dev nmap wireshark tcpdump firefox i3 fbi imagemagick mplayer ncurses hostapd dnsmasq bridge-utils dstat screen tmux build-esssential chromium-browser mpg123 feh vim qv4l2 qv4l2 kde-style-breeze-qt4 locate links wget festival festvox-kallpc16k festvox-kdlpc16k  festvox-us-slt-hts festvox-don festvox-en1 festvox-rablpc16k  festvox-us1  festvox-us2 festvox-us3 xterm konsole xdotool x11-utils xauth Xephyr
```

On your usb stick you can go to the / filesystem directory and 
```
git clone http://www.github.com/jnuyens/freedomev
```
For easy access to the applications, adjust your path:
```
echo "export PATH=$PATH:/freedomev" >> ~/.bash_profile
source ~/.bash_profile
```

### Test it out:
```
say "FreedomEV Upgrade Initiated, prepare to be Pan Galactic Gargleblasted!"
```
This should show this message on your central display

### Lets test some more:
```
moonshine.sh
```
This should make the colors on you Instrument Cluster (behind the steering wheel) fade slowly


## How to contribute:
```
git pull 
```
This gets the latest changes from the server and merges them with your changes
```
commit -m "My first addition to FreedomEV"
```
This marks your changes into a commit ready to be pushed to github
```
git push 
```
This actually sends your changes to this project. 

Have fun!

