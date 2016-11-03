# OpenITG

OpenITG - an open-source rhythm dancing game which is a fork of StepMania 3.95
with the goal of adding arcade-like ITG-style behavior and serving as a drop-in
replacement for the ITG binary on arcade cabinents.

Project homepage: https://github.com/openitg/openitg/wiki
Project bug tracker: https://github.com/openitg/openitg/issues
Project IRC channel: #openitg on irc.badnik.com
Project source code: https://github.com/openitg/openitg

See original project to contribute if you want, this is my personal abomination

# Building 
I'm Not currently bothering with packaging assets, this is just to generate the
openitg binary.

To configure (for fresh build)
    ./autogen.sh
    ./configure --with-x --with-gnu-ld
    make clean

To build just
    make
    strip --strip-unneeded src/openitg
    cp src/openitg $OPENITG/openitg

# Details on my personal setup

I have Fedora 24 installed with openitg running from within my home directory.

Using the assets gotten when downloading zip home version and coping binary
over.

Not using signatures for profile data

Changed systemd getty service to auto login to tty's

Boot process is 

* Machine boots

* Autologin to tty1

* bash_profile starts up a dropbox service and starts x (exec startx)

* .xinitrc just exec ~/openitg/openitg. Have set the dimentions correctly in
Static.ini so this works seamlessly.

## Other things I needed to do

Install pmount, this was an annoying issue. Usb's dont work without it.

Installing lua5.1. Ended up just installing
from an archived rpm and then symlinking liblua.so -> liblua.so.5.1 
Thankfully this didn't break anything. 

Installing the rest of libaries that openitg requires, the linker errors make
knowing which other ones you need easy.

