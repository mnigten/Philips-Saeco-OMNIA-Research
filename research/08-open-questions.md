# Open questions

## Protocol
- Does our EP2230/10 use the same D5 55 framing as documented EP2231?
- Are its stock recipe packets byte-identical to EP2231 or EP2235?
- What checksum algorithm generates the final two bytes?
- Does EP3246 add new button bits inside the same frame or use a different mapping?
- Does the mainboard return different LED/status frame layouts by UI/model?

## Electrical
- What are the measured idle voltages on our UI serial lines?
- Are both directions 3.3 V logic?
- Do the U_TX/U_RX pads connect directly to the 8-pin UI harness?
- What is the function of the noisy/unknown upstream pin?

## Configuration
- Where is model identity stored?
- Does the UI announce its model during startup?
- Does the mainboard reject unsupported UI/model variants?
- Are recipes compiled into mainboard firmware, UI firmware, or parameter/config tables?

## Upgrade
- Does EP2230 accept EP3246 Americano?
- Does it accept Latte?
- Can a complete EP3246 UI boot on the EP2230 mainboard?
- Are additional LEDs/touch electrodes already present on the shared UI PCB?
- Are EP3200 front-panel mechanics interchangeable with EP2230?

## Saeco
- Which Saeco models, if any, use the same OMNIA PCB numbers?
- Are there Saeco service manuals exposing OMNIA naming or firmware variants?
