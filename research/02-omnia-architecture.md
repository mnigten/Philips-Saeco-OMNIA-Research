# OMNIA architecture

## Current model

CORROBORATED by several Philips 2200/3200 projects:

```text
             serial link
+----------+ <===========> +----------------+
| UI board |               | main/power PCB |
+----------+               +----------------+
 buttons                     pump
 LEDs                        heater
 recipes                     grinder
 user I/O                    brew group
                             valves/sensors
```

The display/UI sends user actions and repeatedly requests/status-polls the machine. The mainboard performs the physical machine control and returns UI/LED state.

## Upstream bus characteristics

Related EP22xx/EP32xx projects use an 8-pin Picoflex cable. Published implementations use two UART channels in a man-in-the-middle ESP arrangement and 115200 baud.

Important: these are upstream findings. Our exact EP2230/10 electrical levels and framing still require local measurement.

## EP2231 protocol description

The thiesgerken EP2231 project documents fixed-length display-to-mainboard messages beginning with D5 55. It describes button presses as bit/byte changes and mainboard-to-display messages as longer LED-state frames. It also states that the final two bytes behave as a checksum whose algorithm was not determined there.

This is exceptionally relevant because EP2231 is close to our EP2230 LatteGo target.

## Implication

The UI is not simply a passive switch panel. It contains an MCU and participates in a structured serial protocol. Therefore a richer UI can fail even when mechanically/electrically connected if its command map, startup handshake or expected status format differs.
