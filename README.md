# Gratisfaction · Tuesday Topic Lab

Pre-show topic prep + auto-ordered timeline generator for the Gratisfaction podcast.

**Live at:** [gratisfaction.inkwellandiron.com](https://gratisfaction.inkwellandiron.com)

---

## What this is

A static web tool that:

1. Pulls current events from RSS feeds across News, Tech, Culture/Pop, and Politics/Money
2. Scores each topic against the show's voice (calibrated from Episode 1 + 2 transcripts)
3. Lets all 3 hosts drag picks into a shared pool
4. Generates a coherent run-of-show timeline with the 🎬 **Build Timeline** button — auto-ordered by the show's natural arc (cold open → hot take → parent beat → crude humor capped → deep dive → closer)

No backend. No tracking. State persists in your browser. Imports/exports JSON to share picks between hosts.

## Files

| File | Purpose |
|---|---|
| `index.html` | The dashboard — open in any browser, works on iPhone |
| `TUESDAY_WORKFLOW.md` | The 15-minute Tuesday ritual — what each host does, what the compiler does |

## How to use

1. Open the live URL on any device
2. Tap **Refresh Feeds** to pull the latest news
3. Drag interesting topics from the columns into the **Pick Pool**
4. When it's time to lock the docket, hit **🎬 Build Timeline**
5. Drag to reorder, drop topics that don't fit, save others for next week
6. Export the timeline as markdown

Full workflow detail in [TUESDAY_WORKFLOW.md](./TUESDAY_WORKFLOW.md).

## Tech

- Static HTML + CSS + vanilla JS
- No build step, no dependencies
- No tracking, no analytics
- Works offline once loaded (RSS refresh requires connection)

## License

Private project. Not for redistribution.

## Hosting

- **Host:** Cloudflare Pages (free tier)
- **Domain:** subdomain of `inkwellandiron.com` (DNS at GoDaddy, CNAME → Cloudflare Pages)
- **Auto-deploy:** every push to `main` triggers a new deploy (~30 sec)
