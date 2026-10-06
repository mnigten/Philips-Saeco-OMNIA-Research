# Hardware notes

## Reference machine

OBSERVED from the EP2230/10 reference machine:

| Component | Marking |
|---|---|
| Machine | Philips EP2230/10 |
| Main PCB | 1.9.30.330.00 V10 |
| Main PCB service label | 421941311941/04 |
| UI PCB | OMNIA UI ENTRY 1.9.30.332.00 V05 |
| UI service label | 421941311861/03 |
| Mainboard pads | U_TX, U_RX, GND, +5V |

These markings should be photographed and retained because PCB revision may explain protocol differences.

## Upstream 8-pin interface

UPSTREAM documentation for related EP22xx/EP32xx machines identifies:
- 5 V supply
- two ground conductors
- two serial conductors
- one unused conductor
- one unknown/noisy conductor
- a second 5 V conductor

Do not map this table blindly to the exposed U_TX/U_RX test pads. Verify continuity while unplugged.

## Candidate test hardware

Preferred direction for a reversible test rig:
- ESP32 S2 Mini or similar ESP32 with two usable hardware UARTs
- spare matching 8-pin Picoflex cable/connectors
- logic analyzer for initial passive measurement
- suitable level shifting/protection if measurements show it is required

The ESP32 must not be connected to an unknown 5 V UART signal until logic levels have been measured.

## Why ESP32 S2 Mini is currently preferred

EP3246 community reports show cases where an ESP8266 D1 Mini caused unreliable operation while an ESP32 S2 Mini worked correctly. This does not prove the D1 Mini is fundamentally incompatible, but it makes ESP32 S2 Mini a sensible starting platform for the 3200-style MITM path.

## Reversibility requirement

No factory cable should be cut for the first prototype. The goal is:

```text
mainboard -> adapter harness -> ESP/sniffer -> adapter harness -> original UI
```

Removing the adapter should restore the machine to factory wiring.
