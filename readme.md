# Demo config for Kinesis Advantage 360 pro

This is a variation of the [official ZMK
configuration](https://github.com/KinesisCorporation/Adv360-Pro-ZMK) for the Advantage
360 pro. It is intended to be a starting point for further customization.

To build upon this configuration, simply fork [this
repo](https://github.com/urob/adv360-demo-config) to your Github Account. The firmware
will then be automatically (re-)build by Github whenever you make changes to the
configuration, and can be downloaded from the Github Actions tab.

The main differences of this repo compared to the official Kinesis configuration are as
follows:

## Latest ZMK firmware with various experimental features

The firmware in this repo is configured to be compiled using my [adv360
branch](https://github.com/urob/zmk/tree/adv360) of the ZMK firmware. Compared to the
branch used by the official Kinesis repo, it features the following enhancements:
- ZMK updated to latest ZMK firmware
- includes board files and optional alternate matrix-transform (see below)
- supports experimental mouse usage (PR #778)
- supports tri-state (aka swapper) behavior (PR #1366)
- supports global-quick-tap-ms configuration for hold-taps and combos (PR #1387)
- supports positional-hold-tap-on-release option for home-row mods (PR #1423)
- supports smart-layers and numword (PR #1451)

## Alternate matrix-transform

The board definition in the official repo includes several "dead" keys, which require
placing several `&none` into the layout. This repo uses an alternate matrix transform
that eliminates all unused keys, making the layout easier to read. 

In addition, it also moves the thumb cluster below the rest of the layout to further
simplify the configuration. 

Specifically, the revised layout looks as follows:
```
 ╭────────────────────────────┬────────────────────────────╮
 │  0   1   2   3   4   5   6 │  7   8   9  10  11  12  13 │
 │ 14  15  16  17  18  19  20 │ 21  22  23  24  25  26  27 │
 │ 28  29  30  31  32  33  34 │ 35  36  37  38  39  40  41 │
 │ 42  43  44  45  46  47 ╭───┴───╮ 48  49  50  51  52  53 │
 │ 54  55  56  57  58╭────╯       ╰────╮59  60  61  62  63 │
 ╰───────────────────┼────────┬────────┼───────────────────╯
                 ╭───╯ 64  65 │ 66  67 ╰───╮
                 │ 68  69  70 │ 71  72  73 │
                 ╰───────╮ 74 │ 75 ╭───────╯
                         ╰────┴────╯
```

See the
[keymap file](https://github.com/urob/adv360-demo-config/blob/main/config/adv360pro.keymap)
for configuration examples.

## Standard ZMK build routine

I have replaced the custom make script used by Kinesis with a more standard ZMK build
routine. In other words, this configuration now behaves exactly like any other ZMK
configuration. While not necessarily better, this makes it a bit easier to use the
excellent [ZMK documentation](https://zmk.dev/docs/user-setup) and get help from the
wonderful [ZMK community](https://discord.gg/XnBTxwHmfT).

## LED status indicators

LED status indicators are currently not officially supported by ZMK. To increase
compatibility with standard ZMK, I therefore dropped support for the LED status
indicators from the main branch of this repo.

The [led branch](https://github.com/urob/adv360-demo-config/tree/led) of this repo
includes experimental LED support by building against a version of ZMK that has been
patched with experimental code developed by Kinesis. Note that this code is highly
customized and is *not* compatible with most other ZMK keyboards. It is therefore
unlikely that the ZMK community will be able to help troubleshooting.

## Cleaned up user config

Finally, I have implemented a few tweaks to the keymap.

Moreover, in an attempt to declutter the user repo, I have also moved the board
definition files to the ZMK branch.

