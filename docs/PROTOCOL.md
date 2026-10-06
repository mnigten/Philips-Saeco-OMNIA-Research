# Protocol investigation

## Established upstream facts

Related Philips 2200/3200 projects use two UART interfaces at 115200 baud to sit between display and mainboard. Commands differ between at least some models/revisions.

TillFleisch exposes model profiles:
- EP_2220
- EP_2235
- EP_3243
- EP_3246

Supported logical actions include:
- SELECT/MAKE COFFEE
- SELECT/MAKE ESPRESSO
- SELECT/MAKE HOT WATER
- SELECT/MAKE STEAM
- SELECT/MAKE CAPPUCCINO
- SELECT/MAKE LATTE
- SELECT/MAKE AMERICANO
- BEAN
- SIZE
- MILK
- AQUA CLEAN
- CALC CLEAN
- PLAY/PAUSE

Availability of a logical action in software does not prove our EP2230 mainboard accepts the corresponding EP3246 packet.

## Questions for packet-level extraction

For every model/action record:
1. exact byte sequence;
2. direction;
3. frame length;
4. repeated bytes/counters;
5. checksum/CRC if any;
6. timing/repetition;
7. required machine state;
8. response from mainboard.

## Capture naming

Use:
`captures/<model>/<date>/<state>_<action>_<sequence>.txt`

Example:
`captures/EP2230/2026-10-xx/idle_make_coffee_001.txt`

## Comparison matrix

| Action | EP2220 | EP2235 | EP2230 local | EP3243 | EP3246 |
|---|---|---|---|---|---|
| Espresso | extract | extract | capture | extract | extract |
| Coffee | extract | extract | capture | extract | extract |
| Hot water | extract | extract | capture | extract | extract |
| Cappuccino | n/a or extract | extract | capture | extract | extract |
| Latte | n/a or extract | investigate | n/a UI | extract | extract |
| Americano | n/a or extract | investigate | n/a UI | extract | extract |

Next code-research milestone: fill this table with source-linked packet definitions, not guesses.
