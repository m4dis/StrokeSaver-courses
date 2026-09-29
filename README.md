# Stroke Saver courses

Static course packages served to the Stroke Saver app.

Data: Ortofoto ja kõrgusmudel © Maa- ja Ruumiamet (avaandmed); rajad © OpenStreetMap contributors (ODbL); skoorikaardid klubidelt.

Entry point: catalog.json

## `courses/<id>/pins.json`

Optional, per course, published separately from the package (not listed in that course's
manifest.json — it changes daily, the package underneath it doesn't). When present, `date` in the
file must equal your local today or you must ignore it entirely and fall back to that hole's
`green.center` in holeNN.json — a missing file and a stale `date` mean exactly the same thing.
Each entry under `holes` gives a hole's pin both in the course's own hole frame (`x`/`y`, meters)
and in WGS84 (`lat`/`lon`), so a consumer can use whichever it already has. See
`docs/course-package.md` v1.9 in the main repo for the full field list and `source` values.
