# Saeco research track

## Why Saeco matters

Philips and Saeco coffee-machine development has significant historical overlap, so Saeco projects, service information and PCB identifiers are worth searching alongside Philips.

## Important distinction

Brand relationship does not imply protocol identity.

The documented Saeco Intelia project by OpHaCo uses a different front-panel architecture: its research reports no MCU on the front daughterboard and relies on sniffing lower-level display/control signals including SPI. That differs materially from the MCU-equipped OMNIA UI in our EP2230.

Therefore:
- Saeco Intelia is useful methodology/history.
- Intelia packets/signals must not be imported into OMNIA assumptions.
- Saeco models using identical OMNIA PCB identifiers would be much stronger evidence.

## Search keys

Continue searching Saeco sources for:
- OMNIA
- 1.9.30.330
- 1.9.30.332
- 421941311941
- 421941311861
- EP22xx/EP32xx equivalent chassis
- matching 8-pin Picoflex UI harness
- matching MCU/PCB photographs

## Desired result

Find a Saeco-branded machine with an identical mainboard or UI PCB and document its model, part numbers and available recipes. That would help separate platform capability from Philips product segmentation.
