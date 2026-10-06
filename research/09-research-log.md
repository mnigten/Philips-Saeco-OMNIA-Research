# Research log

## 2026-10-06

### Hardware identification
Recorded the reference EP2230/10 mainboard and UI PCB markings:
- main 1.9.30.330.00 V10 / 421941311941/04;
- UI OMNIA UI ENTRY 1.9.30.332.00 V05 / 421941311861/03;
- visible U_TX/U_RX/GND/+5V test pads.

### Initial UI-upgrade hypothesis
Investigated whether richer EP3200-series UI hardware could be fitted. Shared OMNIA architecture and overlapping service-part families made the idea plausible, but model-specific software/configuration remains an unresolved dependency.

### GitHub research
Identified SmartPhilips2200, TillFleisch ESPHome Philips Smart Coffee, EP2231 LatteGo fork, EP3200/EP3246 projects, EP5400 work and Saeco Intelia research.

### Major protocol finding
The EP2231 fork contains a detailed protocol document with concrete D5 55 packets for power, status, coffee, espresso, hot water, cappuccino and settings. This becomes the closest documented baseline for our EP2230.

### Strategy change
Instead of buying a donor EP3246 UI first, the preferred path is:
1. passive local capture;
2. compare with upstream;
3. controlled replay of a native command;
4. controlled EP3246-only recipe test;
5. donor UI test only after protocol compatibility is understood.

### Saeco conclusion
Saeco remains in scope, but older Intelia research uses a materially different front-panel architecture. Future Saeco work should prioritize identical OMNIA PCB/service identifiers rather than brand similarity alone.
