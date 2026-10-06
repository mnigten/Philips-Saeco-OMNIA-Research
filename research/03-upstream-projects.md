# Upstream project research

## SmartPhilips2200
https://github.com/chris7topher/SmartPhilips2200

Historical Philips 2200 ESP8266/MQTT work. Uses serial interception and 115200 baud in source. Later projects explicitly note that its command values differ from some other revisions. Keep as a protocol-family reference, not a universal packet map.

## TillFleisch/ESPHome-Philips-Smart-Coffee
https://github.com/TillFleisch/ESPHome-Philips-Smart-Coffee

Central modern reference for 2200/3200. Explicit model profiles include EP2220, EP2235, EP3243 and EP3246. The project warns that display commands can differ by revision/model. Contributors added EP3243 and EP3246 support.

## thiesgerken/esphome-philips-ep2231
https://github.com/thiesgerken/esphome-philips-ep2231

Very relevant EP2231 LatteGo adaptation. Includes protocol.md with concrete D5 55 packets, button mapping and LED-state interpretation. This is currently our closest documented sibling to EP2230/10.

## sendorm/ESPHome-Philips-EP3200
https://github.com/sendorm/ESPHome-Philips-EP3200

3200-series derivative useful for cross-checking protocol evolution and wiring.

## quack3d/ESPHome-Philips-Smart-Coffee-3200-Series
https://github.com/quack3d/ESPHome-Philips-Smart-Coffee-3200-Series

EP3243-oriented work and useful reference for reversible ESP32 MITM installations.

## mkorenko/esp-phillips-3200
https://github.com/mkorenko/esp-phillips-3200

Independent Philips 3200 ESP32/ESP8266 control library. Useful for recipe semantics and cross-checking Americano-related implementation.

## flashmandv/phillips-3246-smart
https://github.com/flashmandv/phillips-3246-smart

EP3246-focused fork/reference. Primary target for extracting EP3246-only recipe behaviour.

## markobel/Philips-EP5400-ESPHome
https://github.com/markobel/Philips-EP5400-ESPHome

Important cautionary example. A later 5400 firmware revision required fresh sniffing, strict timing and dual-counter synchronization. This demonstrates why packets from one revision must not be assumed portable.

## OpHaCo/smart_coffee_machine
https://github.com/OpHaCo/smart_coffee_machine

Saeco Intelia research. Unlike OMNIA, this older machine's front daughterboard has no MCU and the project sniffs/control-signals including SPI/LCD behaviour. Valuable lineage/methodology reference, but not an OMNIA protocol source.

## Non-Philips comparative research

prototux/delonghi-re is useful only as a comparative reverse-engineering reference. Its goal includes backporting segmented recipes and investigating UART control. It is not evidence about Philips/Saeco packet formats.
