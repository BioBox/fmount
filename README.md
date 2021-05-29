# fmount
Fuzzy finder Mounting Script for USBs and Android Devices

![](fmount.gif)

This is a collection of two bash scripts that mount and unmount USB and Android devices respectively.

## Dependencies

[fzf](https://github.com/junegunn/fzf) and [jmtpfs](https://github.com/kiorky/jmtpfs) is required. These should be easily installable by your package manager.

## Installation

Send all the files in `/src` to somewhere in your `$PATH`.

## Configeration

There are a couple of enviornment variables that can be used to modify the selection of devices/mountpoints available to you:

* **$FSTAB_ENTRIES**: This is a string that's passed into `grep -v` used to filter out drives that you don't want to be shown, e.g. Your internal drives. Defaults to `/dev/sda`.
* **$USB_FINDOPTS**: This is a string that is passed into `find` to acquire the mountpoints available to you. Defaults to `/mnt /media -maxdepth 3 -type d -empty`

These two can be changed by `export`ing them to your bash profile or bash rc.

## Known Issues

Mounting an Android phone actually requires you to mount it twice. The first time is just to give your computer permission (tap the *allow* button on your phone). Then you may have to unmount it and mount again.

## Special Thanks

Special thanks goes to [Luke Smith](https://lukesmith.xyz/) for coming up with the idea. [Here's](https://www.youtube.com/watch?v=lcmJg4OfKzs&ab_channel=LukeSmithLukeSmithVerified) the video that inspired this project. This is basically just his `dmenumount` script with the following changes:

* `simple-mtpfs` doesn't work for me, so it's been replaced with [jmtpfs](https://github.com/kiorky/jmtpfs).
* This does not use `dmenu` at all; you can run it with any plain-old terminal.
* Allows for more/easier customization with a couple of env variables.
