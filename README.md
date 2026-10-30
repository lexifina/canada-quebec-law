# Quebec: law history in git

The law of Quebec as a git history: one file per provision, one commit per law on the day it took effect, and the law that made each change as the commit's author. `git blame` names the law behind every paragraph; `git log` lists every change; picking a date gives the text in force that day.

It follows the shared design of [lexifina/global-law](https://github.com/lexifina/global-law).

## What this repository holds

**Metadata only, no law text, because the Government of Quebec does not allow its statutes to be reproduced without prior authorisation.** LégisQuébec, the official consolidation, says that its laws and regulations are protected by copyright and that reproducing, downloading or storing them needs the prior authorisation of Publications du Québec and payment of royalties; the government's copyright notice covers "des lois et règlements"; the open-data copy of the consolidated statutes is licensed only for non-commercial use with no derivatives (CC BY-NC-ND 4.0); and Canada's Copyright Act gives provincial statutes no exemption. This repository records which bills received assent and when, and a handful of open facts about the province's legal system. To read a statute, go to [LégisQuébec](https://www.legisquebec.gouv.qc.ca). Text will be added if Quebec grants authorisation.

| Folder | Act | Versions | History |
| --- | --- | ---: | --- |
| `catalogue/` | Catalogue of bills given assent: title, bill number, assent date and chapter only | 252 | 252 assent days from 10 June 2014 to 12 June 2026 (496 bills, 41st to 43rd Legislatures) |
| `legal-system/` | Legal system facts from Wikidata (CC0) | 2 | The province's inception (1 July 1867), then the facts as Wikidata held them on 29 October 2026 |

## Source

The catalogue's bill numbers, French titles, assent (sanction) dates and annual-statute chapters are facts taken from the [Assemblée nationale du Québec](https://www.assnat.qc.ca/fr/travaux-parlementaires/projets-loi/index.html)'s record of each sanctioned bill, from the 1st session of the 41st Legislature (2014) to the 2nd session of the 43rd Legislature; no text of the bills or of those pages is reproduced. The titles are the official French titles (French is the language of record; the English titles are not used). The Wikidata facts are from [Wikidata](https://www.wikidata.org/wiki/Q176) (CC0).

## Dates

A catalogue entry is dated by the day of assent (sanction) the Assembly records, not by commencement (many Quebec Acts come into force on dates set by the government), and is credited to a `catalogue-<date>` entry. Where the Assembly gives one single in-force date it is listed in the entry. Commits are at noon, Quebec time (America/Toronto, with daylight saving time). The Wikidata facts are dated by the province's inception (1 July 1867) and otherwise by the latest revision of the Wikidata items (29 October 2026; retrieved 30 October 2026).

## How it is checked

Every version is read back from git on the day it took effect and on the day before (`tools/check_repo.py`) and must match `corpus.json`; results are in `REPRODUCE.md`.

## What "author" means

The author of a commit is the law (or, for facts, the retrieval) that made the change, with an e-mail address that cannot exist (`<law key>@assnat.qc.ca.invalid`). The committer is always Lexifina.

## Limits

Only bills assented from the 1st session of the 41st Legislature (2014) onward are listed; earlier statutes, and the consolidated chapters of the RLRQ, are not. Entries do not record later amendment or repeal. Nothing here is an official record of the statutes.
