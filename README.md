# Philips / Saeco OMNIA Research

Reverse-engineering notes for Philips and Saeco OMNIA coffee machines, initially focused on understanding and upgrading a Philips EP2230/10.

## Reference machine
- Philips EP2230/10
- Main PCB: 1.9.30.330.00 V10
- Main PCB label observed: 421941311941/04
- UI PCB: OMNIA UI ENTRY 1.9.30.332.00 V05
- UI label observed: 421941311861/03
- Visible test pads: U_TX, U_RX, GND, +5V

## Goals
1. Document the OMNIA mainboard/UI architecture.
2. Compare EP22xx and EP32xx serial traffic and UI variants.
3. Test whether EP3246-only recipes can be invoked on EP2230 hardware.
4. Investigate an EP3246 UI swap.
5. Map related Saeco hardware/research.
6. Build a safe read-only sniffer before command injection.

See docs/SOURCES.md, docs/RESEARCH.md and docs/TEST_PLAN.md.

> Safety: coffee machines contain mains voltage, heaters, pumps and moving parts. Never assume UART voltage levels from labels alone. Measure before connecting an ESP32.
