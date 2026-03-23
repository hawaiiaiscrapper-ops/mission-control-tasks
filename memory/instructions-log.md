# Instructions Log — All Directives from Karthik

_This file tracks every instruction/request Karthik has given, in chronological order. Updated each session._

---

## 2026-03-23

### Session 1 (05:55 – 12:11 CDT)

| # | Time | Instruction | Action Taken | Status |
|---|------|-------------|-------------|--------|
| 1 | 05:56 | "right now I have not setup any cron schedules so scrape and log only when I request so, Add this listing but don't setup any schedule. Not right now. Yes" | Noted: no cron schedules for Trekker. Manual scraping only. | ✅ |
| 2 | 06:14 | "do you have all that's needed" | Confirmed system state — auth, gateway, Trekker, Mission Control all set up. | ✅ |
| 3 | 06:14 | "continue working on trekker bot and add it to Mission Control" | Added Trekker project to Mission Control (tasks.json + projects.json). Created 3 tasks: overview (permanent), scrape demo (backlog), refresh sheet (backlog). | ✅ |
| 4 | 06:18 | "I don't see trekker in mission control" | Discovered tasks.json wasn't pushed to GitHub. Committed and pushed. | ✅ |
| 5 | 06:20 | "what do I not see trekker in office and Team" | Explained: Team view pulls from Gateway API (live sessions), Office is a pixel art canvas. Neither shows projects — those are on the Task Board. | ✅ |
| 6 | 06:23 | "1. Yes 2. No 3. No" (re: project filters visible?) | Discovered projects.json was a separate file with different data. Updated it with Trekker project and pushed. | ✅ |
| 7 | 06:25 | "give me link to this" | Provided: https://hawaiiaiscrapper-ops.github.io/mission-control-tasks/ | ✅ |
| 8 | 06:30 | "looks like GitHub is not able to connect" | Guided through Settings: GitHub Token, Owner, Repo fields. | ✅ |
| 9 | 06:36 | "I get: ❌ Network error: Load failed" | Investigated — crons.json was missing from GitHub repo (404). | ✅ |
| 10 | 06:39 | "I get this error: Failed to load resource: the server responded with a status of 404" | Committed and pushed crons.json to GitHub. | ✅ |
| 11 | 06:41 | "I get no errors but I still see tasks with errors" | Continued debugging. | ✅ |
| 12 | 06:43 | "I still get the same error" (re: gateway) | Checked gateway status — running on localhost:18789. CORS issue from GitHub Pages is expected. | ✅ |
| 13 | 06:45 | "I think openclaw gateway is not connected" | Verified gateway is running and webhook works (tested with curl). | ✅ |
| 14 | 06:46 | "check if gateway is connected to mission control" | Confirmed webhook config exists, transform script present, tested successfully. | ✅ |
| 15 | 06:47 | "still see errors" | Asked for more details. | ✅ |
| 16 | 06:53 | Pointed to: `https://api.github.com/repos/.../data/crons.json?ref=main` returning 404 | crons.json was missing from repo. Committed and pushed it. | ✅ |
| 17 | 06:56 | "I get no errors but I still see tasks with errors" | Investigated further. | ✅ |
| 18 | 06:57 | "swap to opus 4-6" | Switched model to anthropic/claude-opus-4-6. | ✅ |
| 19 | 06:58 | "I see undefined tasks" | Root cause: `atob()` can't decode UTF-8/emoji characters. Fixed with `TextDecoder`. Pushed fix. | ✅ |
| 20 | 07:01 | "I still see same error" | Browser cache issue. Suggested incognito window to verify. | ✅ |
| 21 | 11:57 | "Yes it looks good in incognito" | Confirmed fix works. Cache issue in normal browser window. | ✅ |
| 22 | 11:57 | "But how do I make sure this issues does not repeat" | Added cache-busting: version.json + auto-reload check every 2 minutes. Pushed. | ✅ |
| 23 | 11:59 | "Also add the zip code you want to track in a google sheet as well and track only the zip codes in the sheet to get started only track 96761" | Created "Zip Codes" tab in existing sheet. Added 96761 (Lahaina, HI). Updated Trekker config. | ✅ |
| 24 | 12:04 | "rename this sheet as zip code listings, also create another sheet with preferred listings and create a tab with the listings and another with their metadata" | Renamed sheet → "Zip Code Listings". Created new "Preferred Listings" sheet with Listings + Metadata tabs. Updated config. | ✅ |
| 25 | 12:08 | "Make sure you don't forget this use case" | Updated MEMORY.md with full Trekker use case, both sheets, workflow. | ✅ |
| 26 | 12:09 | "Make sure you are logging every input given by me also" | Added chronological instruction log to daily notes. | ✅ |
| 27 | 12:11 | "Also I want you to also document all the instructions given so far as well for reference" | Created this file (instructions-log.md). | ✅ |

---

## Standing Instructions (always active)
- **No cron schedules for Trekker** — scrape only on manual request
- **Log every instruction** from Karthik in daily notes + this file
- **Track zip codes from Google Sheet** — only scrape what's in the Zip Codes tab
- **No name** — don't suggest names, don't ask for one
- **No onboarding** — skip all intro/setup conversations, get straight to work
- **Direct communication** — no fluff, no "Great question!" filler
