auto-suspend
============

N.B., This is a sunken ship. While the init script is useful, it will not
autostart because you need an active X session. I figured out how to suspend as
a non-root user using udev, upower, and policykit. I updated my
[xinitrc](https://github.com/CrashenX/xmonad/blob/master/config/xinitrc) to use
this solution.

Simple daemon for auto suspending and locking a system without a desktop
environment. This daemon uses xautolock, xscreensaver, and pm-utils. The init
script uses LSB headers and has only been tested and validated to work on
Debian Sid.

To install:

     cd build             # as user
     cmake ..             # as user
     make install         # as root
     insserv auto-suspend # as root

The default install prefix is `/usr/local/`. If you wish to change it to
`/usr/`, instead run:

     cmake -DCMAKE_INSTALL_PREFIX=/usr/ ..

Control the daemon (as root) with:

     /etc/init.d/auto-suspend start
     /etc/init.d/auto-suspend stop
     /etc/init.d/auto-suspend restart

Check the status of the daemon:

     /etc/init.d/auto-suspend status

To manually lock your screen and suspend your system:

     lock # as root
