# How this repository was made (Quebec)

This file is written by the build on 2026-10-30, the day the source data was retrieved.

## Sources

| Source | Address | Retrieved | Licence |
| --- | --- | --- | --- |
| Assemblée nationale du Québec: bills (projets de loi), per session, and each sanctioned bill's record | <https://www.assnat.qc.ca/fr/travaux-parlementaires/projets-loi/index.html> | 2026-10-30 | Facts only (bill number, title, assent date, annual-statute chapter); no text of the bills or of the Assembly's pages is reproduced |
| Wikidata | <https://www.wikidata.org/wiki/Q176> | 2026-10-30 | CC0 1.0 |

Every word of law in this repository comes from these sources. Lexifina reads them and records each act's dated versions, and the laws that made each change, in one corpus file. This repository is built from that file.

## What is in it

| Act | Title | Versions | Span |
| --- | --- | ---: | --- |
| `catalogue` | Catalogue of Quebec bills given assent (title, bill number, assent date and chapter only) | 252 | 2014-06-10 to 2026-06-12 |
| `legal-system` | Quebec: legal system facts (Wikidata) | 2 | 1867-07-01 to 2026-10-29 |

The build made 254 commits:

| Commits | Kind |
| ---: | --- |
| 2 | first version of an act |
| 252 | one law on its in-force day |
| 0 | changes no amendment note explains, credited to the publisher |

Other counts:
- 0 commits on the branch `future`: laws not yet in force on 2026-10-30.
- 1 commits dated 1 January 1970: in force before 1970, with the real day in their `In-force` trailer.
- 253 laws in the record.
- 506 tags.

## Dates

Each commit is dated at noon (America/Toronto) on the day the change took effect. The other dates, enacted and published, are trailers.

When a law gives no date of its own, the default rule applies: Catalogue entries are dated by the day of assent (sanction) recorded by the National Assembly; they describe bills and are not law text. https://www.assnat.qc.ca/fr/travaux-parlementaires/projets-loi/index.html

## How the history is built

`tools/build.py` turns the corpus into this history in one pass: one commit per law, on the day it took effect. The same corpus always gives the same commit hashes. `tools/check_repo.py` reads every version back from git and compares it with the corpus. `tools/on.py` shows the law as it stood on any date. The corpus format is described in `tools/SCHEMA.md`.

- Corpus: sha256 `79baba3c07030247fa92726dd283110342cf5f546b47d43e66bda7dc9a45797c` (420066 bytes).
- Builder blob hashes (`git hash-object`): `build.py` `a4faa25af85facb64b956b372f6b528aafdd7ec1`, `check.py` `3e59cb6f05eccb94a9ec14431a7f6781221e83ef`, `on.py` `644a6c0857fbcc72562032b58d57aa113fee0641`.
- Python 3.12.10; git version 2.46.0.windows.1.

## Checks

254 versions of 2 acts read back from git on the day each took effect and on the day before: 0 mismatches. Trailers: 0 commits whose trailers git cannot parse. Health: 0 merge commits on main, 0 commit dates that go backwards, 0 commits dated after the build.

A second build from the same corpus into an empty folder gave identical hashes for all 254 history commits and 506 tags (history tip `0ec4c4edac28688afcb9a0c941319001e5757ab3`).

## Decisions made by hand

- No law text is published. LegisQuebec, the official consolidation, requires prior authorisation from Publications du Québec, and payment of royalties, to reproduce, download or store its contents (its "Droits d'auteur" page); the Government of Quebec's copyright notice covers "des lois et règlements"; the XML dataset on Données Québec is CC BY-NC-ND 4.0; and the Copyright Act (Canada) gives provincial statutes no exemption. Nothing was taken from LegisQuebec.
- The catalogue holds facts only: bill number, the French title, the assent (sanction) date and the chapter in the annual statutes, as the National Assembly's record of each sanctioned bill gives them. An in-force date is added only where the record gives one single date.
- Coverage: every bill marked sanctioned in the 41st Legislature, 1st session (from May 2014) to the 43rd Legislature, 2nd session (to 2026-06-12): 496 bills on 252 assent days; 409 with a chapter number, 254 with a single in-force date. Earlier sessions are not included.
- Wikidata facts (CC0) form the "legal-system" act: the province's inception (1 July 1867) is day-precision, so it is the oldest version; the other facts are dated by the latest revision of the Wikidata items before retrieval (2026-10-29; retrieved 2026-10-30), so no commit lies after the build.
- Not built: treaty actions (Quebec's international ententes are not treaties in the UN Treaty Collection).

## What AI did and did not do

The scripts that read the sources and build this repository were written by Claude Code running Claude Opus 5.5 (`claude-opus-5-5`) under Lexifina's direction.

No model wrote, translated or corrected legal text. No model runs at build time. Every word of law in this repository comes from the official sources above.

The commit messages are written by `build.py` from the source data.

Model use at data-build time:
- Claude Code with Claude Opus 5.5 wrote Lexifina's code and chose the sources; it did not write or alter any legal text. The code is deterministic and runs no model.
