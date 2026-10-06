# EP2230 -> EP3246 UI upgrade investigation

## Goal

Determine whether a richer EP32xx user interface can be used on the EP2230/10, and whether extra recipes are limited by UI firmware, mainboard firmware/configuration, or both.

## Current evidence

OBSERVED:
- our machine uses an OMNIA UI ENTRY board;
- the mainboard exposes U_TX/U_RX/GND/+5V-labelled pads;
- main and UI PCB identifiers have been recorded.

UPSTREAM:
- EP22xx and EP32xx machines use an 8-pin powered serial connection between mainboard and display;
- model-specific command sets exist;
- EP3246 software integrations can request Americano and Latte;
- an ESP can operate as a MITM between original UI and mainboard.

HYPOTHESIS:
An EP2230 mainboard may implement more recipe primitives than the stock EP2230 UI exposes.

## Decision tree

```text
Does EP2230 accept a known EP3246-only command?
        |
     yes+-------------------no
      |                      |
mainboard has             recipe may be
hidden overlap            absent/blocked or
      |                   packet incompatible
compare EP3246 UI
startup traffic
      |
does donor UI communicate reliably?
      |
   yes -> investigate physical/UI swap
   no  -> ESP-based custom UI remains possible
```

## First target: Americano

Americano is a strategically useful test because the EP2230 already contains the physical subsystems required for coffee and hot water. This makes it a better first cross-model experiment than assuming a recipe that could require unavailable hardware.

## What a successful injected Americano would prove

It would prove that the EP2230 mainboard can execute at least one recipe not exposed by its stock UI when addressed with an appropriate protocol command.

It would NOT yet prove:
- full EP3246 UI compatibility;
- identical firmware;
- support for every EP3246 recipe;
- safe permanent operation with a donor UI.

## Donor UI information needed

Before purchase/install, record:
- complete Philips/Saeco service part number;
- PCB number and revision;
- machine model it came from;
- connector photograph and keying;
- UI software/firmware markings;
- front-panel physical dimensions and mounting points.
