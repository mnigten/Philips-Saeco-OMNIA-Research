# Web and community research

Research pass covering public websites and community discussions outside the core GitHub reverse-engineering projects.

Last research pass: 2026-10-06.

## Philips official documentation

Philips maintains a combined 1200/2200/3200 user-manual family on the EP2230/10 support page. This is useful supporting evidence that these ranges share substantial operating/service concepts, but a common user manual does not prove identical electronics or firmware.

Reference:
https://www.philips.nl/c-p/EP2230_10/series-2200-volautomatische-espressomachines/ondersteuning

Philips' EP2230/10 product description identifies the stock beverages as espresso, coffee and cappuccino, with LatteGo milk functionality.

Reference:
https://www.philips.nl/c-p/EP2230_10/series-2200-volautomatische-espressomachines

## Service-parts evidence

PartsNL lists UI/control PCB 421941311861 for multiple machines, including EP2224 and EP3243-family applications. A dedicated EP3241/50 listing explicitly warns that the part is **version dependent** and should be checked against the machine type number.

This is important evidence for the upgrade investigation:

- shared PCB/service-part family: supported;
- arbitrary donor-board plug-and-play compatibility: NOT supported;
- software/configuration/revision dependency: explicitly plausible.

References:
https://www.partsnl.nl/print-421941311861
https://www.partsnl.nl/philips-onderdelen/philips-series-3200-ep324150-2159947/print-421941311861

## Reddit research

Searches were run for EP2230, EP3246, Philips 2200/3200 UART/ESP32/modification topics and related superautomatic discussions.

### What was found

Reddit has a substantial Philips 2200/3200 owner community, especially in r/superautomatic. Most discussions concern reliability, calibration, drink quality, maintenance and model selection rather than electronics reverse engineering.

One useful recurring observation is that owners discuss closely related EP2230/EP2231/EP2235 variants together. This is community-level context only and is not enough to establish electronic equivalence.

A 2023 r/superautomatic discussion specifically compares EP2230/10, EP2235/47 and EP2231/40 as 2200 LatteGo variants. A commenter describes their differences primarily in product presentation/colour. Treat this as anecdotal, not service evidence.

Reference:
https://www.reddit.com/r/superautomatic/comments/188xrzm/

A separate EP2230/14 owner report discusses normal pre-infusion behaviour. This is not directly useful for the UART/UI upgrade but is retained as model-behaviour reference.

Reference:
https://www.reddit.com/r/superautomatic/comments/18pqql8/

### Negative finding

This search pass did **not** uncover a Reddit thread with a documented EP2230-to-EP3246 UI conversion, firmware flash, PCB reprogramming procedure or packet-level UART reverse engineering.

That negative result is useful: at present, GitHub remains substantially stronger than Reddit for the technical protocol investigation.

## External protocol corroboration

The strongest publicly indexed packet-level source remains the EP2231 reverse-engineering document. It documents D5 55 framed commands, including status, power, espresso, hot water, coffee, cappuccino, bean strength and size.

Reference:
https://github.com/thiesgerken/esphome-philips-ep2231/blob/main/protocol.md

This remains upstream evidence for EP2231 only until compared with a capture from our EP2230/10.

## Search terms used

Examples:
- EP2230 UART
- EP2231 UART
- EP3246 UART
- Philips 2200 ESPHome
- Philips 3200 UART
- EP3246 ESP32
- OMNIA UI Philips
- 421941311941
- 421941311861
- 421945017912
- 421945017932
- D5 55 Philips coffee machine
- Saeco OMNIA PCB
- Reddit Philips EP2230 modification
- Reddit Philips 3200 UART

## Current conclusion

The broader web search strengthens three parts of the working model:

1. Philips treats 1200/2200/3200 as a closely related operating family in its documentation.
2. At least one UI PCB service number spans parts of the 2200/3200 family, but suppliers explicitly warn about version dependency.
3. Community discussion does not currently provide evidence of a completed EP2230 -> EP3246 UI conversion.

The highest-value next external research targets are therefore service manuals, exploded views, service-programming documents, firmware/update packages, archived technician forums and exact PCB-number matches rather than general owner forums.
