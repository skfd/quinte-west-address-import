# quinte-west-address-import

The **Quinte West city checkout** of the address-import family — city #4,
scaffolded 2026-08-15 by the breadth-first onboarding loop (engine
`future-work/multi-city/onboarding-queue.md`). Status: **onboarding**. No
proposal published, no uploads made; the config is a first draft for
conflation baseline runs.

The pipeline lives in the engine repo,
[`address-importer-friend`](https://github.com/skfd/address-importer-friend)
(see its README for setup). This repo carries only Quinte West's
`config.toml`, credentials (`.env.*`, gitignored, from the `.example` files),
and — locally, gitignored — `data/` with the OSM extract and
`data/quinte-west/tool.db`.

```bash
cd ../address-importer-friend
python run.py --city-dir ../quinte-west-address-import
```

Source data: City of Quinte West address points via the sibling
[`ontario-address-changes`](https://github.com/skfd/ontario-address-changes)
tracker (`data/quinte-west/quinte-west.db`, 20,290 active rows / 19,096 civic
addresses at snapshot 25, 2026-08-06). The 2026-08-12 portfolio survey put
the gap at 16,315 missing (86.3%).

Entry state probed 2026-08-15 (`onboarding/entry-state-2026-08-15.json`):
**greenfield**, Hamilton's exact shape — 932 of 1,005 sampled elements are
CanVec 6.0 NRCan loose nodes (97% nodes, 3% ways); the 2018 "peak" is Matthew
Darwin's `City of Quinte West => Quinte West` rename retag, not new data;
organic building/address mapping by `CanadianRob` in 2020; no wiki page, no
import tags, no recent activity. An import target. Courtesy contacts before
the first visible changeset: Matthew Darwin (Ontario-wide maintainer, did the
rename sweep) and CanadianRob (mapped Trenton houses by hand in 2020).
Existing convention: `addr:city=Quinte West` (932 vs 17 Frankford/Trenton).

Distinctive traits, all measured 2026-08-15 (details in config comments):
ALL-CAPS street names (title-casing needed before any upload — engine TODO);
no stable source key (synthetic identities); an untrustworthy combined
address column; 342 number-less named-feature rows (dams); tiles subdivide
the 4 former-municipality ward polygons via the declared-field contract
(`mapguide`), after the 81-polygon Planning Districts layer failed its
point-test at 63%.

Before any production upload: wiki proposal page, forum announcement, and
feedback window per the
[OSM Import Guidelines](https://wiki.openstreetmap.org/wiki/Import/Guidelines)
— Toronto's [`IMPORT_PROPOSAL.mediawiki`](https://github.com/skfd/toronto-2-address-import/blob/main/IMPORT_PROPOSAL.mediawiki)
is the template.

MIT licensed.
