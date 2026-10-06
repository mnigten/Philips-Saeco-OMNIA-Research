# EP2230/10 test plan

## Phase 0: document while unplugged
Photograph both PCBs, connector keying, wire colours/pin order and test pads. Perform continuity checks only with mains disconnected.

## Phase 1: electrical characterization
Before connecting an ESP32:
1. establish ground;
2. measure connector supply;
3. measure idle levels on candidate TX/RX;
4. determine 3.3 V vs 5 V logic;
5. confirm baud/framing using a high-impedance logic analyzer or oscilloscope.

Related projects point to UART and commonly 115200 baud, but the reference EP2230/10 must be measured rather than assumed.

## Phase 2: passive capture
Start receive-only. Capture power-on, idle, espresso, coffee, cappuccino, hot water, strength changes, quantity changes, start/stop and safely reproducible warning states. Keep untouched raw captures.

## Phase 3: compare
Compare EP2230 captures with EP2235 and EP3246 implementations. Identify frame length, headers, counters, checksum/CRC, action fields, state fields and timing.

## Phase 4: controlled injection
First inject a command already available on EP2230. Only after that works, test an EP3246-only recipe such as Americano. Keep a physical power disconnect available.

## Phase 5: donor UI
Only after protocol compatibility is characterized, compare an EP3246 UI connector/pinout and voltage levels, then test it without modifying the original EP2230 parts.
