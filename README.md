# CompanyNews

**Digital signage for Ignition 8.3.** Put company news, safety counters and shift information on the
TVs around your plant, managed from inside Perspective — and interrupt all of them the moment a tag
says there is an emergency.

Built by [Central Valley Ignition](https://www.centralvalleyignition.com).

---

## What it does

- **Slides** — upload an image, choose which departments see it, set how long it stays up and how it
  arrives. Schedule it with a start and end date, daily, weekly or monthly.
- **Emergency slides** — held out of the normal rotation and shown on every screen the instant a
  gateway tag goes true. No button, no script, nobody who has to notice. Bad tag quality counts as
  *not* firing, so a PLC dropping off the network cannot evacuate your building.
- **View slides** — point a slide at a Perspective view you built. Charts, tables, gauges, live tag
  values, your own styling.
- **Ticker** — a scrolling bar along the bottom, scoped per department, with live tag values written
  inline: `Line 3 running at {[default]Line3/Rate} units/hr`.
- **Clock** — optional corner clock, date and time, formatted how you like.

Screens sharing a department stay **in step with each other** — slide position comes from the wall
clock, not a per-browser counter, so a TV that reboots rejoins the rotation where the others already
are instead of starting the loop again out of sync.

Media is stored on the gateway filesystem **outside** the Ignition data directory, so uploads never
bloat a `.gwbk`, and is served with cache headers rather than round-tripped through a database as
base64.

---

## Requirements

| | |
|---|---|
| Ignition | 8.3.0 or later |
| Modules | Perspective |
| Screens | Anything with a modern browser — smart TV, Chromebox, Raspberry Pi, thin client |

No database. No internet connection. No cloud account. Licensing is validated entirely on your
gateway, so it works on an air-gapped network.

---

## Install

1. Download `CompanyNews-<version>.modl` from [Releases](../../releases).
2. Gateway web interface → **Config → Modules** → **Install or Upgrade a Module**.
3. Accept the certificate if prompted — the module is signed by Central Valley Ignition.

It starts immediately; no gateway restart. Then drop the two components onto Perspective views and
point a TV at one.

**Full walkthrough: [docs/INSTALL.md](docs/INSTALL.md)** — wiring a TV to a department, emergency
trigger tags, ticker tag values, backups, redundancy, and a troubleshooting table.

---

## Licensing

Without a key, CompanyNews plays the **first 2 slides of your library in total** — not 2 per
department — followed by a Central Valley Ignition slide. A department whose slides are not among
those first 2 shows only that slide. Nothing is deleted and nothing stops working: every slide you
configured starts playing the moment a key is entered.

To license a gateway: **Config → Services → CompanyNews**, copy the Gateway ID shown there, and send
it with your order. Paste the key you receive into the same page.

Keys are validated **offline**. The module never contacts us, sends no telemetry, and needs no
internet access. An expired key drops back to the unlicensed behaviour above — **it never blanks a
screen**.

---

## Before you deploy an emergency slide

Read section 0 of [LICENSE.txt](LICENSE.txt).

The emergency slide is a way to put information on a screen quickly. **It is not a fire alarm and
not an emergency notification system.** It is not listed or certified to UL 864, UL 2572 or NFPA 72,
and it depends on your gateway, your network, your PLCs and the browser on each TV — any of which can
fail without warning. Emergency notification must come from systems designed, listed and maintained
for that purpose. Anything CompanyNews shows is supplementary.

---

## Support

**Support@CentralValleyIgnition.com**

Include your Gateway ID (Config → Services → CompanyNews) and the module version from Config →
Modules.

---

## Changelog

See [CHANGELOG.md](CHANGELOG.md).

## License

Commercial. See [LICENSE.txt](LICENSE.txt).
