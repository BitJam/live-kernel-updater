# live-kernel-updater
Update the kernel on an antiX or MX live-usb or a running live system.

### Quick Start

    sudo apt-get update       # if needed
    sudo apt-get install git  # if needed
    git clone https://github.com/BitJam/live-kernel-updater
    git clone https://github.com/BitJam/cli-shell-utils
    cd live-kernel-updater
    sudo ./live-kernel-updater

## Synopsis


This program is CLI only for now.  We try to avoid making your
live-usb unbootable so you need to install a new kernel and then
do a remaster before we will attempt to update the live kernel.
We do this by always looking for new kernels inside of the linuxfs
file so we know for sure it will be available when you next boot.

It can update a running live system or a live-usb that you plug
into any system.  You will be prompted with choices if you don't
specify what you want to do with command line options.

The log file is at `/var/log/live-kernel-updater.log`.


## Usage

```
Usage: live-kernel-updater [options] [command]

Update the kernel on a running antiX/MX live-usb or on an antiX/MX live-usb
that is plugged into another system.  The new kernel must already be installed.
You will be prompted for info that is needed but not given in command line
arguments.

Commands:
   all         All commands below
   unpack      Unpack the old initrd
   copy        Copy kernel modules into initrd
   repack      Repack the new initrd
   install     Copy new initrd and vmlinuz to the live boot directory

Options:
  -a --auto             Non-interactive.  Always assume the safe answer
     --color=<xxx>      Set color scheme to off|low|high
  -D --debug            Pause before cleaning up
  -d --device=<device>  live-usb device to update the kernel on
                        (use "live" to force updating a running live system)
  -F --force=XXXX       Force the options specfied:
                             flock:  ignore missing flock program
                               usb:  Allow non-usb devices (dangerous!)
                             clear:  remove previous initrd directory
  -h --help             Show this usage
  -i --initrd=<name>    Name of initrd file (initrd.gz)
  -I --ignore-config    Ignore the config file
  -k --kernel=<kernel>  The version (uname -r) of the new kernel
  -K --keep-old         Keep the old module directory in the initrd
  -p --pretend          Don't run the install commands
     --pause=<list>     Pause after certain stages of processing:
                            mount
                            unpack
                            copy
                            repack
                            install

  -q --quiet            Print less
  -v --verbose          Print more, show commands when run
  -W --write-config     Write a new config file

Notes:
  - short options stack. Example: -pq instead of -p -q
  - options can be intermingled with commands and parameters
```
