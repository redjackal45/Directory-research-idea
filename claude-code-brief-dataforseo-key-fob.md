# Claude Code brief — DataForSEO verification: car key / key fob (TOP PICK)

## Your job
Run the DataForSEO API research below on this computer, using the local DataForSEO credentials (login + API password from the dashboard at app.dataforseo.com/api-access, or from the local .env — do NOT paste credentials into any file you return, and do NOT commit them).

This REPLACES the original 10-niche screen in claude-code-brief-dataforseo-directory-niches.md. Focus on ONE niche first: car key / key fob by vehicle. Muse cannot call the DataForSEO API directly — it needs a login+password pair and Muse's connector only deposits one secret. So you are the API runner. Muse will do the ranking/analysis from your output file.

Note: webdesign.so was checked 2026-11-22 and has NO keyword-research tool — DataForSEO there is not exposed. This Claude Code run is the only verification route.

## The niche to verify
Car key / key fob by vehicle — a year/make/model → key-type database answering: what key/fob does my specific car take, what's the fob part number / FCC ID, can I program it myself, what should it cost.

Keywords Everywhere (KWE) interim, 2026-11-22 — UNVERIFIED, bucketed volumes, do NOT treat as confirmed:
- "car key replacement near me" 33,100/mo, "key fob programming" 6,600/mo — dedup cluster 39,700/mo, in the 20k–100k band
- Top SERP in KWE run was all local locksmith pages (ziplocksmith.com, citadellocksmith.com, greystonelocksmith.com) — no database found, Bay Area-localised SERP
- Score 8/10 in KWE screen, strongest payer (locksmith lead gen, $180–$550 jobs)
- Caveat: 39,700 is a floor from just 2 keywords; the long tail ("what key does my [year make model] take") returns 0 in KWE and is unmeasurable there

## What DataForSEO must settle (in this order)
1. Exact cluster volume (non-bucketed): Labs keyword ideas / related keywords / suggestions for "car key replacement near me", "key fob programming", "car key replacement", "key fob replacement", "what key does my car take", "key fob FCC ID", "program key fob myself" + close variants. Then Keywords Data search_volume (location_code 2840 = US, language en) to total the cluster. Is it really 20k–100k? How big is the long tail?
2. Real DR for the top 10: SERP API Google organic US, keyword = "car key replacement near me", location_code 2840, language_code en, depth 10. Record top 10 domains. Then Backlinks bulk_ranks for all top-10 domains. Flag any DR 50+ site in the top 5.
3. National (not localised) top 10: confirm whether a national key/fob database exists that the localised "near me" SERP did not surface (e.g. a key-blank catalogue site ranking nationally). Search also: "key fob replacement by car", "car key fob lookup", "what key fob do I need".
4. Keyword difficulty: Labs bulk keyword difficulty for the head terms, as a second check.

## DataForSEO endpoints (api.dataforseo.com/v3, POST, Basic Auth, body is a JSON array)
- Labs: `POST /dataforseo_labs/google/keyword_ideas/live`, `related_keywords/live`, `keyword_suggestions/live`
- Keywords Data: `POST /keywords_data/google_ads/search_volume/live` (location_code 2840, language en)
- SERP: `POST /serp/google/organic/live/regular` (or `/live/advanced`), depth 10
- Backlinks: `POST /backlinks/bulk_ranks/live` with `targets` = all top-10 domains (one call)
- Record the exact field name/value for the backlink rank metric — do not relabel it as Ahrefs DR unless it is.

## Cost guardrail
DataForSEO balance was $45.17 on 2026-11-22 (was $51.00 Nov 20). Keep total spend well under that. Use bulk endpoints, depth 10 only. This is ONE niche — do not burn calls on the other niches unless the key-fob check finishes well under budget, in which case (and only then) also verify, in order: (2) lawn mower / small-engine parts, (3) u-pick farms.

## Also evaluate for key fob
- Data sourcing: where would listing data come from? Key-blank catalogues (Ilco/Silca), public FCC ID database, dealer parts lists, locksmith price surveys. Rate build/refresh difficulty: easy / medium / hard.
- Page scale: how many pages programmatically (year × make × model, key-type, FCC-ID pages)?
- Monetization: locksmith lead gen, featured locksmith listings per city, aftermarket fob affiliate — who would actually pay, and at what ticket?
- Search intent: confirm searchers want to find / solve / compare, not just read information.

## Output — save TWO files in this same repo
1. `dataforseo-key-fob-results.json` — raw numbers: head term, full keyword cluster with per-keyword volume + endpoint, cluster total, top-10 SERP domains with rank/DR field + endpoint, keyword difficulty, competitor URL + UX faults observed, data source, page-scale estimate, monetization, intent, score 1–10.
2. `dataforseo-key-fob-results.md` — same data in readable form, with a verdict: does key fob CONFIRM as a GAP / WEAK / CLOSED, and why. Every number must cite its DataForSEO endpoint.

## Rules
- Do NOT guess or estimate any volume or DR number. If a call fails or returns nothing, say so plainly instead of inventing a figure.
- Do NOT include any API login, API password, or credential in either output file.
- Do NOT register, buy, or build anything. Research only.
