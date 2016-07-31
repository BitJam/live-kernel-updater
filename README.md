# live-kernel-updater
Update the kernel on an antiX or MX live-usb

### NOTE for early testers

This program requires the cli-shell-utils.bash library.  We will look
for it in the same directory this script is in and also in a
cli-shell-utils/ directory next to the directory this script is in so
if you clone both repos side-by-side then you should be okay.

We also look for the library in /usr/local/lib/cil-shell-utils/ so if
you install the library to that directory then you should also be
okay.

###  Another NOTE for early testers

This script require the programs vmlinuz-version and
copy-initrd-modules.  They either need be on your path or in the same
directory this script is in.

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
  -D --debug            Pause before cleaning up
  -d --device=<device>  live-usb device to update the kernel on
                        (use "live" to force updating a running live system)
  -f --force=XXXX       Force the options specfied:
                                flock:  ignore missing flock program
                                clear:  remove previous initrd directory
                             compress:  use gzip instead of unknown compression
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
