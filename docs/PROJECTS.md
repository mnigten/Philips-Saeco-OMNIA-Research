# Related project survey

This page records what each upstream project contributes to the EP2230/EP3246 UI-upgrade investigation.

## chris7topher/SmartPhilips2200
https://github.com/chris7topher/SmartPhilips2200

Early Philips 2200 ESP8266/MQTT reverse engineering. Source code uses 115200 baud serial communication. Important historical baseline, but later projects explicitly report different command bytes on some revisions.

## TillFleisch/ESPHome-Philips-Smart-Coffee
https://github.com/TillFleisch/ESPHome-Philips-Smart-Coffee

Current central reference. Explicitly supports EP2220, EP2235, EP3243 and EP3246 model profiles. Documents an 8-pin Picoflex connection between mainboard and display, with two serial data lines. Supports actions including Coffee, Espresso, Hot Water, Steam, Cappuccino, Latte and Americano, depending on model profile.

Documented connector functions in this project:
| Pin | Mainboard label/function |
|---|---|
| 0 | 5 V |
| 1 | GND |
| 2 | GND |
| 3 | unused |
| 4 | mainboard -> display serial |
| 5 | display -> mainboard serial |
| 6 | unknown/noisy |
| 7 | 5 V |

The project configuration uses 115200 baud for both UART directions.

## sendorm/ESPHome-Philips-EP3200
https://github.com/sendorm/ESPHome-Philips-EP3200

3200-series work derived from TillFleisch. Useful corroboration for the 8-pin bus and model/revision-dependent command sets.

## quack3d/ESPHome-Philips-Smart-Coffee-3200-Series
https://github.com/quack3d/ESPHome-Philips-Smart-Coffee-3200-Series

Developed on EP3243 with ESP32 S2 Mini. Demonstrates a reversible MITM installation using an extra cable/connector rather than cutting the factory harness. This is attractive for our eventual EP2230 test rig.

A 2025 upstream discussion reports EP3246 users having unreliable behaviour with a D1 Mini and successful operation after moving to ESP32 S2 Mini. Treat this as implementation experience, not a universal electrical requirement.

## thiesgerken/esphome-philips-ep2231
https://github.com/thiesgerken/esphome-philips-ep2231

EP2231-specific fork with LatteGo adaptation. Particularly relevant because EP2231 is close to our EP2230/10 target and may provide useful packet comparisons.

## mkorenko/esp-phillips-3200
https://github.com/mkorenko/esp-phillips-3200

Independent/control-library angle for ESP32/ESP8266 and Philips 3200. Contains recipe/control logic including Americano-related material. MIT licensed.

## flashmandv/phillips-3246-smart
https://github.com/flashmandv/phillips-3246-smart

EP3246-focused fork of mkorenko. Useful target for extracting EP3246 command semantics.

## markobel/Philips-EP5400-ESPHome
https://github.com/markobel/Philips-EP5400-ESPHome

Later Philips generation. Useful for comparing design concepts, packet timing and MITM architecture. Do not assume 5400 packets are compatible with OMNIA 2200/3200.

## OpHaCo/smart_coffee_machine
https://github.com/OpHaCo/smart_coffee_machine

Older Saeco Intelia UART reverse engineering. Useful evidence that UI/mainboard serial reverse engineering has precedent in Saeco machines. It is not evidence that Intelia and OMNIA use the same packets.

## Key conclusion

There is enough independent evidence to treat the UI/mainboard serial link as established for the 2200/3200 family. The unresolved question is not whether serial communication exists, but how our exact EP2230/10 revision maps commands and whether its mainboard accepts EP3246-only recipe requests.
