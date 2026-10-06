# UI upgrade investigation

## Original question

Can a Philips EP2230/10 use a richer EP3200-series user interface, particularly an EP3246-style panel, to expose additional drinks/functions?

## Evidence supporting feasibility

1. EP22xx and EP32xx share the OMNIA-era serial UI/mainboard architecture.
2. Multiple projects support both 2200 and 3200 variants using closely related software architecture.
3. Our EP2230 UI is explicitly marked OMNIA UI ENTRY.
4. Our mainboard has U_TX/U_RX-labelled test points.
5. EP3246 support exists in upstream MITM projects, so its UI actions can be studied without initially purchasing a donor UI.

## Evidence against assuming plug-and-play

1. Upstream authors explicitly report command differences between revisions/models.
2. Complete UI assemblies may contain model-specific software even where bare PCB families overlap.
3. Later Philips research demonstrates that firmware revisions can alter timing/counters enough to break earlier integrations.
4. Physical fit and front-overlay touch/button mapping still need comparison.

## Better experiment order

1. Capture our EP2230 protocol.
2. Match its stock commands against EP2231/EP2235.
3. Extract EP3246 Americano/Latte packets.
4. Prove injection using an ordinary EP2230 command.
5. Test one EP3246-only command.
6. Only then test/buy a donor EP3246 UI.

## Why Americano first

The reference EP2230 already has coffee brewing and hot-water hardware. Americano is therefore a strong candidate for a software-segmented recipe. This is still a hypothesis until the EP2230 mainboard accepts the relevant command.

## Alternative outcome

Even if a donor EP3246 UI is incompatible, a custom ESP32 interface could expose extra supported recipes while retaining the stock EP2230 panel.
