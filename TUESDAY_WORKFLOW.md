# Tuesday Topic Lab — Workflow

**The tool:** `GratisfactionFeed.html` — open in any browser (works on iPhone too).

**The point:** Every Tuesday before recording, all 3 of us pick what we want to riff on. The tool scores topics against the show's actual voice, then auto-orders the picks into a coherent run-of-show.

**Anti-goal:** This is NOT a chemistry-grading tool. It doesn't analyze you mid-conversation. It just helps you walk into Thursday's recording knowing what's on the docket.

---

## The 15-minute Tuesday ritual

### Each host (5 min, on your own)

1. Open the dashboard in your browser
2. Tap **Refresh Feeds** — pulls current events across News + Tech + Culture/Pop + Politics/Money
3. Scroll the columns. Topics already sorted by brand-fit score (S/A/B/C tier).
4. Drag 3–5 topics into **your bucket** (Pogi / Vanilla / Rob)
5. If something feels like "we should ALL riff on this," drag into the **Episode Group** bucket
6. Add anything missing manually — scoring runs on whatever you type
7. Click **Export My Picks** → download a JSON file → drop it in the group chat

### Compiler (Pogi, 5 min)

1. Open dashboard
2. Click **Import Picks** → load Justin's JSON → load Bobbye's JSON. Picks merge into the right buckets.
3. Click **🎬 Build Run-of-Show**
4. Modal pops with auto-ordered episode (Cold Open → Hot Take → Parent Beat → Crude → Deep Dive → Closer)
5. Drop anything that doesn't fit (✕). Move stuff to "save for next week" (↓). Hit **↻ Rebuild** if you want a different order.
6. Click **Export Run-of-Show** → markdown file → drop in chat as the docket

### Group sync (5 min, optional)

- Quick voice or text confirmation in chat: anyone need to swap? Anything missing?
- Lock the docket. Done.

---

## How the auto-order works (so you can trust or fight it)

The button uses the show's actual arc patterns from Eps 1+2:

| Slot | Logic | Target time |
|---|---|---|
| **Cold Open** | Era reference / running-bit potential / S-tier hot energy | ~4 min |
| **Hot Take Pivot** | Politics / hot-take / money topic, A-tier+ | ~15 min |
| **Parent / Friendship Beat** | Parent-life or friendship-dynamics topic | ~15 min |
| **Crude Humor (capped)** | One main pick — Ep 1 ran 25 min on this, so it's capped | ~10 min |
| **Deep Dive** | Space / sci-fi / conspiracy — Pogi+Rob lane | ~15 min |
| **Cultural Beat** | Heritage / identity if any survived the picks | ~10 min |
| **Closer / Picks** | Lighter — food, sci-fi recs, whatever — "Lowkey Heat" energy | ~8 min |
| **FLEX** | Stragglers up to 8 total topics | ~8 min |

**Why crude is capped at 1:** Ep 1 had a 25-min foot/body humor stretch. Funny in the room, but for clips, returns diminish past clip 2-3 from the same vein. The auto-order spreads it.

**Why deep dive is at the end:** Ep 2 closed strong on NASA/conspiracy/sci-fi. That's where the chemistry breathes after the energy peaks.

**You can override anything.** The button is a starting point, not a verdict.

---

## Multi-host workflow (current state)

Right now this works via **JSON file pass**:

```
Justin picks → exports JSON → drops in chat
   ↓
Bobbye picks → exports JSON → drops in chat
   ↓
Pogi imports both JSONs → his picks already in → runs Build RoS
   ↓
Pogi exports RoS markdown → drops in chat as the docket
```

It's clunky. **Future v2 (when we know this is worth investing in):** real shared state via Supabase. One link, all three of you edit the same dashboard live, no JSON shuffling. Until then — JSON pass works.

---

## What this dashboard is, and isn't

**It is:**
- A topic-prep tool that runs on Tuesdays
- A scoring system that surfaces topics that fit YOUR voice (calibrated from real Ep 1+2 transcripts)
- A run-of-show generator that uses your show's natural arc
- Local-only state — your picks live in your browser, not on a server

**It is not:**
- A performance tracker
- A tool that grades your chemistry
- A KPI dashboard
- Anything you should be looking at during recording

If it ever feels like surveillance, you tell me and I kill the feature. The chemistry is the moat. The tool just feeds you better topic prep.

— filed in `podcast_system/` · open `GratisfactionFeed.html` to use
