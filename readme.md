# urob's Kinesis Advantage 360 pro demo config

This replicates the official Advantage 360 pro configuration, streamlining the config a little bit.

The main differences are:

- move board definition from the user-repo to the ZMK branch
- improved matrix transform that removes unused keys and moves the thumb cluster to the
  bottom of the layout
- a bit of cleaning up of the keymap
- replace custom make script with standard ZMK build routine
- dropped custom LED code for better compatibility with standard ZMK

