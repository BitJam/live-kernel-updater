# live-kernel-updater
Update the kernel on an antiX or MX live-usb or a running live system.

#### Quick Start

    sudo apt-get update       # if needed
    sudo apt-get install git  # if needed
    git clone https://github.com/BitJam/live-kernel-updater
    git clone https://github.com/BitJam/cli-shell-utils
    cd live-kernel-updater
    sudo ./live-kernel-updater

# Usage

```
Usage: live-kernel-updater [options] [command]
Update the kernel on a running antiX or MX live-usb.  The new
kernel must already be installed.  If the name (uname -r) of the new
kernel is not give then you will be prompted for it from a menu.

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

Notes:
  - short options stack. Example: -pq instead of -p -q
  - options can be intermingled with commands and parameters
```
