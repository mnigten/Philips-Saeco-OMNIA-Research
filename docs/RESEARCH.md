# Research notes

## Working architecture
Public reverse-engineering projects support a serial link between UI and mainboard:

```text
OMNIA UI <---- serial/UART ----> OMNIA mainboard
 buttons/LEDs/recipes             grinder/pump/heater/valves/brew group
```

Several upstream projects place an ESP between both boards to observe and inject traffic.

## Reference EP2230/10
| Item | Identification |
|---|---|
| Machine | Philips EP2230/10 |
| Main PCB | 1.9.30.330.00 V10 |
| Main label | 421941311941/04 |
| UI PCB | OMNIA UI ENTRY 1.9.30.332.00 V05 |
| UI label | 421941311861/03 |
| Visible pads | U_TX, U_RX, GND, +5V |

The TX/RX markings are consistent with upstream serial research, but do not prove the voltage, baud rate or exact protocol on those pads.

## EP22xx vs EP32xx
TillFleisch maintains separate model definitions for EP2220, EP2235, EP3243 and EP3246. This supports a shared protocol family with model/revision-specific mappings.

Working hypothesis: shared OMNIA hardware architecture + UI firmware/model profile + possible mainboard configuration determines recipes and behaviour.

## Upgrade question
Can the EP2230/10 mainboard accept a known EP3246 recipe command not exposed by the EP2230 UI?

Americano is a useful first candidate because EP2230 hardware already supports coffee and hot-water delivery. A positive result would demonstrate hidden functional overlap, but would not by itself prove an EP3246 UI is plug-and-play.

## UI swap questions
1. Are connector pinouts identical?
2. Are supply and UART logic levels identical?
3. Does the mainboard identify a UI variant?
4. Are recipes controlled by UI firmware, mainboard firmware/configuration, or both?
5. Does an EP3246 UI boot and remain synchronized on the EP2230 mainboard?

## Saeco track
Search by platform and PCB identifiers, not only product names:
OMNIA, 1.9.30.330, 1.9.30.332, 421941311941, 421941311861.

Older Saeco UART research is useful context but packet compatibility must never be assumed.

## Protocol table backlog
| Model | Direction | Action | Packet | Evidence |
|---|---|---|---|---|
| EP2230 | UI -> main | Espresso | TBD local capture | pending |
| EP2230 | UI -> main | Coffee | TBD local capture | pending |
| EP2230 | UI -> main | Cappuccino | TBD local capture | pending |
| EP3246 | UI -> main | Americano | extract from upstream | pending review |
| EP3246 | UI -> main | Latte | extract from upstream | pending review |

Before transmitting upstream packets, understand framing, counters/checksums, state requirements and timing.
