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

`pins.json` can also carry three competition fields (v1.10): `competition` (bool, default false),
`eventName` (optional string), and `validUntil` (ISO-8601, defaults to the end of `date`'s local
Estonian day). A pin applies when `date` is today **and** the current time is at or before
`validUntil` — useful for a tournament pin sheet that should stop applying once that day's round is
over, even though `date` is still today. See `docs/course-package.md` v1.10 in the main repo.

## Course rating / slope rating (v1.13)

`course.json`'s `scorecardTees` entries carry an optional `courseRating`/`slopeRating` per tee
(and, where the source gives separate figures, per gender — see `docs/course-package.md` v1.13 in
the main repo for the exact field shape). Values are sourced per course, each from that club's own
site unless noted otherwise; a missing row means no rating was found publicly anywhere, not a 0:

| course | found? | source |
|---|---|---|
| EGCC Sea Course | yes | [egcc.ee scorecard](https://egcc.ee/en/sea-course-scorecard/) + [slope table](https://egcc.ee/sea-course-slope-tabel/) (official, cross-checked) |
| Niitvälja Golf | yes | [niitvaljagolf.ee Slope-2023.pdf](https://niitvaljagolf.ee/wp-content/uploads/2022/11/Slope-2023.pdf) (official) |
| Otepää Golf | yes | [otepaagolf.com Slope Tables MEN](https://otepaagolf.com/wp-content/uploads/2022/04/Slope-Tables-MEN.pdf)/[WOMEN](https://otepaagolf.com/wp-content/uploads/2022/04/Slope-Tables-WOMEN.pdf) (official) |
| Rae Golf | yes | [raegolf.ee Slope Mehed](https://raegolf.ee/static/Rae-Golf-Slope_Mehed_2022.pdf)/[Naised](https://raegolf.ee/static/Rae-Golf-Slope_Naised_2022.pdf) (official) |
| Pärnu Bay Golf Links | yes | [GolfPass](https://www.golfpass.com/travel-advisor/courses/24825-parnu-bay-golf-links-championship-course) -- **aggregator, not first-party**: the official scorecard and parnubay.com don't publish CR/Slope |
| Rõuge Golf | **no** | not published anywhere found; the club's own scorecard already notes "no stroke index published" |
| Saaremaa Golf & Country Club | yes | [saaregolf.ee scorecard](https://saaregolf.ee/wp-content/uploads/2025/12/SGGC_score_card2024_210x1483.pdf) (official -- printed directly in the tee-color header) |
| Pivarootsi (Uus-Meremäe) | **no** | newly opened course, not yet rated |
| White Beach Golf | yes | [wbg.ee Slope Mens](https://www.wbg.ee/wp-content/uploads/2022/04/WBG-Slope-Mens-2022.pdf)/[Ladies](https://www.wbg.ee/wp-content/uploads/2022/04/WBG-Slope-Ladies-2022.pdf) (official) |
