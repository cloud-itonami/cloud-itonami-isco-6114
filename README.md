# cloud-itonami-isco-6114

Open Occupation Blueprint for **ISCO-08 6114**: Mixed Crop Growers.

This repository designs a forkable OSS business for an independent smallholder mixed-crop grower: a field robot performs sowing, weeding and harvest-support work across diverse crop plots under a governor-gated actor, so the grower keeps their own operating records instead of renting a closed farm-management SaaS.

## Robotics premise

All cloud-itonami verticals are designed on the premise that a **robot performs
the physical domain work**. Here a field robot performs sowing, weeding and targeted harvest support across mixed crop plots under an actor that proposes
actions and an independent **Mixed Crop Governor** that gates them. The governor never
dispatches hardware itself; `:high`/`:safety-critical` actions (such as
operating near buyers/visitors on-site, or applying treatments near water sources) require human sign-off.

A live sample of the operator console (robotics safety console, shared template) is rendered in [docs/samples/operator-console.html](docs/samples/operator-console.html) — pure-data HTML output of `kotoba.robotics.ui`.

## Core Contract

```text
planting plan + crop mix + market order
        |
        v
Crop Advisor -> Mixed Crop Governor -> tend/harvest, or human sign-off
        |
        v
robot actions (gated) + operating records + audit ledger
```

No automated advice can dispatch a robot action the governor refuses, suppress
an operating record, or disclose sensitive data without governor approval and
audit evidence.

## Capability layer

Resolves via [`kotoba-lang/occupation`](https://github.com/kotoba-lang/occupation)
(ISCO-08 `6114`). Required capabilities:

- :robotics
- :telemetry
- :optimization
- :dmn
- :bpmn
- :audit-ledger
- :forms

See [`docs/business-model.md`](docs/business-model.md) and
[`docs/operator-guide.md`](docs/operator-guide.md).

## License

AGPL-3.0-or-later.
