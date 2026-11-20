# Claude Code brief — Directory niches with DataForSEO

## Your job
Run the DataForSEO API research below on this computer, using the local DataForSEO credentials (login + API password from the dashboard at app.dataforseo.com/api-access, or from the local .env — do NOT paste credentials into any file you return, and do NOT commit them).

Muse cannot call the DataForSEO API directly — it needs a login+password pair and Muse's connector only deposits one secret. So you are the API runner. Muse will do the ranking/analysis from your output file.

## Goal
Find 10 directory-website niches where a well-built directory could win organic traffic because existing options are weak, thin, or hard to use.

## Hard criteria — a niche must meet ALL of these
1. Search demand: core keyword cluster (head term + close variations + "near me" terms + location modifiers) totals 20,000–100,000 US searches/month.
2. Weak authority: sites ranking top 10 for the head term mostly have Domain Rating (DR) ≤ 20. Flag any DR 50+ site in the top 5 — that usually means the niche is out.
3. Thin competition: at most ONE dedicated directory/database already serving the niche. Zero is fine.
4. Bad UX if a competitor exists: no filters/search, outdated listings, no map, missing prices/hours, cluttered with ads, slow, not mobile friendly, or data buried in PDFs/long lists.

## EXCLUDE
- Niches dominated by Yelp, Google Maps, Zillow, Indeed, or other giant platforms.
- Medical, legal, and financial YMYL niches unless the data is purely factual and public.

## Candidate niches to screen first (do not limit yourself to these if a better one shows up — but screen these first)
These are starting ideas only. Verify or reject each one with real data; do not keep one that fails the criteria.
1. Dog daycare / dog boarding directories — "dog daycare near me"
2. Self-storage facilities by city — "self storage near me"
3. RV parks / campgrounds — "rv parks near me"
4. Food trucks for catering / events — "food trucks near me"
5. Mobile home parks — "mobile home parks near me"
6. Farmers markets — "farmers market near me"
7. Pickleball courts — "pickleball courts near me"
8. Dog parks — "dog parks near me"
9. Public boat launches / marinas — "boat launch near me"
10. Community gardens / allotments — "community garden near me"
11. Skate parks — "skate parks near me"
12. Disc golf courses — "disc golf courses near me"
13. Hot springs — "hot springs near me"
14. U-pick farms / pumpkin patches — "u-pick farms near me"
15. Escape rooms — "escape rooms near me"

## DataForSEO endpoints to use (api.dataforseo.com/v3, POST, Basic Auth, body is a JSON array)
- Keyword cluster: Labs — `POST /dataforseo_labs/google/keyword_ideas/live` and/or `related_keywords/live`, `keyword_suggestions/live` for the head term. Then Keywords Data — `POST /keywords_data/google_ads/search_volume/live` (location_code 2840 = US, language en) to total the cluster volume.
- SERP: `POST /serp/google/organic/live/regular` (or `/live/advanced`), keyword = head term, location_code 2840, language_code en, depth 10. Record top 10 domains.
- Authority: Backlinks — `POST /backlinks/bulk_ranks/live` with `targets` = all top-10 domains (one call). Record rank / DR-equivalent for each. Note: DataForSEO returns its own rank metric — record the exact field name and value, do not relabel it as Ahrefs DR unless it is.
- Difficulty second check: Labs — bulk keyword difficulty if available for the head terms.

## Cost guardrail
Account balance was $51.00 on 2026-11-20. Keep total API spend well under that. Use bulk endpoints, depth 10 only, and stop a niche early if its head-term volume alone is far outside 20k–100k or its top 5 is full of DR 50+ giants — do not burn calls finishing a dead niche.

## Also evaluate for each surviving niche
- Data sourcing: where would listing data come from? Public government datasets, open APIs, scrapable sources, or manual collection. Rate build/refresh difficulty: easy / medium / hard.
- Page scale: how many pages could the directory generate programmatically (by city, state, category, attribute)?
- Monetization: lead gen, featured listings, affiliate, ads, or sponsorships — and who would actually pay.
- Search intent: confirm searchers want to find / compare / locate something, not just read information. Check this from the SERP (directories, maps, listings ranking = transactional/locational; articles/guides ranking = informational).

## Output — save TWO files in this same folder
1. `dataforseo-directory-niches-results.json` — raw numbers per niche: head term, full keyword cluster with per-keyword volume + endpoint, cluster total, top-10 SERP domains with rank/DR field + endpoint, competitor URL + UX faults observed, data source, page-scale estimate, monetization, intent, score 1–10.
2. `dataforseo-directory-niches-results.md` — same data in readable form, one section per niche, ranked best to worst, with a top pick + why it beats the others. Every number must cite its DataForSEO endpoint.

## Rules
- Do NOT guess or estimate any volume or DR number. If a call fails or returns nothing, say so plainly for that niche instead of inventing a figure.
- Do NOT include any API login, API password, or credential in either output file.
- Do NOT register, buy, or build anything. Research only.
