# Protocol findings

## Closest concrete packet set: EP2231

UPSTREAM from thiesgerken/esphome-philips-ep2231.

Display-to-mainboard messages are documented as 12 bytes. They begin with:
`D5 55`

Known examples:

| Function | EP2231 packet |
|---|---|
| Status request | D5 55 00 01 02 00 02 00 00 00 11 36 |
| Start/Pause | D5 55 00 01 02 00 02 00 00 01 19 32 |
| Espresso | D5 55 00 01 02 00 02 02 00 00 09 2D |
| Hot Water | D5 55 00 01 02 00 02 04 00 00 21 01 |
| Coffee | D5 55 00 01 02 00 02 08 00 00 39 1C |
| Cappuccino | D5 55 00 01 02 00 02 10 00 00 09 26 |
| Beans | D5 55 00 01 02 00 02 00 02 00 09 2F |
| Size | D5 55 00 01 02 00 02 00 04 00 20 05 |
| Aqua Clean | D5 55 00 01 02 00 02 00 10 00 0D 36 |
| Calc Clean | D5 55 00 01 02 00 02 00 20 00 28 37 |

Documented power-on variants:
- D5 55 0A 01 02 00 02 00 00 00 0E 12: beep, no full power-on
- D5 55 01 01 02 00 02 00 00 00 25 27: power-on without cleaning
- D5 55 02 01 02 00 02 00 00 00 38 15: power-on including cleaning

Power-off:
`D5 55 00 01 02 00 02 01 00 00 1D 3B`

## Mainboard-to-display

EP2231 documentation describes 19-byte frames, also beginning D5 55, carrying LED states. Examples include espresso, hot water, coffee, cappuccino, bean/size groups, water-empty, waste/warning and play/pause indicators.

## Checksum uncertainty

The EP2231 researcher did not derive the checksum algorithm. Do not synthesize arbitrary button combinations until checksum behaviour is understood or valid captured packets are replayed.

## What remains to extract

We still need source-linked packet maps for:
- EP2220
- EP2235
- EP3243
- EP3246
- SmartPhilips2200 revision

Then compare them byte-by-byte against a local EP2230 capture.

## Critical rule

A packet documented here is evidence for its source model only. It becomes EP2230-compatible only after a passive match or controlled test.
