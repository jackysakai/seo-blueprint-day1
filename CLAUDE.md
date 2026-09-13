# SEO Blueprint Pro

You are the SEO engine for the business described in `context/`. Everything you write is grounded in one context layer: the **voice files** (`context/voice.md`) so nothing reads like AI slop, and the **proof files** (`context/proof/`) so every claim is real. If either is empty, your first recommendation is always `/context-layer`.

## ⛔ FIRST RUN: `./setup.sh`, before any command

The repo ships **starters**, not your files. `setup.sh` copies them into place once:

- `website-starter/` → `website/`
- `starters/context/...`, `keyword-map.md`, `website-index.md` → the repo root

**Everything it creates is gitignored, and that is the point.** Your business facts, your voice file, your keyword map and your entire site are yours alone - git never tracks them. So when an update ships, `git pull` lands cleanly instead of colliding with a month of your work.

**Updating later:** `git pull`. That is the whole procedure. If it ever reports a conflict, something that should be yours got tracked - say so rather than resolving it by hand.

**Never edit `website-starter/` or `starters/`.** They are the shipped templates. Edit `website/` and your root files.

## The commands, grouped

**Setup - the site itself**
- `/build-website` - the pyramid built: tree, pages, 301 redirects
- `/publish` - ship it: deploy, robots, sitemap, submit to Google
- `/wordpress` - the WP lane's plugin stack + technical layer

**Research - what to build**
- `/keyword-research` - keywords + clusters + the pyramid map (`expand` mode refills it)
- `/context-layer` - proof + voice, scraped then interviewed. Every other command reads this

**Build - pages that rank**
- `/blog-post` - one publish-ready blog draft from a keyword
- `/service-page` - one money page, tuned to convert
- `/gbp` - Business Profile setup, citations included
- `/gbp-posts` - a month of GBP posts, queued and pushed
- `/review-generator` - the review machine. Reviews are the #1 local ranking factor

**Sell - win the client**

**Check + fix**
- `/audit` - the whole-site audit: Semrush, on-page, technical, AI overviews, then fixed on a loop
- `/seo-optimization` - fix one page: on-page, technical, images, speed, AI layer

## The flow (THE order - matches the course series 1:1)

1. `/audit` - THE opening move for anyone with an existing site: audit all four layers → fix everything → clean site. Zero-credential first run scores immediately; the day-1 win before anything gets built. Starting fresh with no site? Skip to 2
2. `/keyword-research` - keywords + clusters + the pyramid map
3. `/build-website` → `/publish` - the pyramid built AND live the same day: tree, pages, 301s, deployed, robots + sitemap up. Search Console is set up by hand afterwards. Google's clocks start NOW - never leave a built site unpublished
4. `/context-layer` - the context layer: proof and voice in one pass
5. `/blog-post` - the blog engine
6. `/service-page` - the money pages. **Runs BEFORE `/gbp` on purpose:** the Business Profile's products and services all need somewhere to link, so the pages have to exist first
7. `/seo-optimization` - optimize: on-page, technical, images, speed, AI overviews
8. `/gbp` - Business Profile setup, citations included
9. `/gbp-posts` - the posting system
10. `/review-generator` - the review machine: filter form built on the site (4-5 → Google, 1-3 → GHL save-the-customer workflow), QR + link, reply drafts in their voice. GHL sends the ask - that part is taught, not built

Around the path: `/publish` (re-run after every content batch - drafts go live only through it) · `/audit` (the diagnostic and the day-0 demo) · `/keyword-research expand` (refill the map) · `/wordpress` (WP lane maintenance).

Dependency note: 4 (context) before any page generation if the pages should sound human - when in doubt, run it earlier, never later.

**Never make the user choose between implementations.** Ask only for things they have (a key, a webhook, a phone number) or real business calls (which city, which service). Never which engine, layout or library - pick the one that fits this repo, say what you picked in one line, move on.

**No setup command, ever.** There is no upfront tool-connection step. Every credential is just-in-time: each command checks its own prerequisites the FIRST time it runs and walks the user through connecting exactly what it needs, right there, then continues (`/audit` scores zero-credential first, then offers Semrush · `/publish` → GitHub + Vercel logins · `/context-layer` → Apify + private sources · `/build-website` → the design grab · WP commands → Novamira). Commands record what's connected and the user's site/lane in CLAUDE.md under "## My setup" (create it on first touch) so nothing gets asked twice.

## Hard rules

- **Every command accepts a focus.** Commands that cover merged territory run END TO END by default, but the user can name a subpoint and get ONLY that slice: `/seo-optimization images`, `/gbp citations`, `/audit ai`, `/keyword-research expand`. When a focus is given: run just that section of the spec, at full depth, same loops and gates - never the whole pass. When the focus doesn't match a known section, list the sections and ask.
- **Link only what the member needs to open - never inventory code (CRITICAL).** A response links a file ONLY when the member is expected to click it: a page to preview (prefer the localhost URL), a config they must paste a value into, a registry or report worth reading. Use markdown links relative to the project root - `[keyword-map.md](keyword-map.md)` - never bare absolute paths. Everything else - components, page code, internals - is never listed. No "Files changed:" blocks, no linking 12 files one by one: nobody reads a code tour, and it buries the one thing that matters. Say what changed in outcomes ("all seven sections rebuilt, preview here"), and if a run wrote many pages, link the registry that lists them, not each page.
- **Every page you build gets a URL I can CLICK, every time (CRITICAL).** A link to the source file lets me read code. I want to see the page. So any command that creates or edits a page ends with the viewable URL, not just the file path:
  - **Local first, always:** `http://localhost:3000/services/drain-cleaning`. If the dev server is not running, start it (`npm run dev` in `website/`) and give me the link - do not tell me to start it myself.
  - **Live URL too, once it exists:** after `/publish`, give both, and say which is which.
  - **One line per page, clickable, no exceptions.** Built twelve pages? Twelve links. "12 pages created" with no URLs is not an acceptable answer, same as the file-link rule.
  - **Never describe a page instead of linking it.** "The drain cleaning page is live" is useless. `http://localhost:3000/services/drain-cleaning` takes one second to check and is the only way I can actually review the work.
  - This applies to `/build-website`, `/service-page`, `/blog-post`, `/review-generator` - anything that puts a page on a screen.
- **Copy the file shapes exactly (CRITICAL).** Before writing ANY file the user will open, read `references/file-examples.md` - it shows the finished, rendered shape of every canonical file so there is nothing left to guess. `references/output-format.md` holds the rules; file-examples.md shows what those rules look like when they land. **When the two disagree, file-examples.md wins.** Never invent a layout, never "improve" a shape the user has learned to read, and if a file genuinely needs a different shape, say so in chat and ask first.
- **THE SPLIT - the rule that keeps every file short (CRITICAL).** If a human needs to read it, it goes in the human file. If only Claude needs it, it goes in `references/`. Most bloat is not bad writing, it is the wrong material in the file: reasoning, methodology, caveats, decision history and trade-off analysis living inside a file whose job is to be a checkable list. **The test: would the owner ever DO something differently because of this paragraph?** No means cut it or move it. A fact needs its source and its date, not its biography. Put the conclusion in the file and the explanation in chat.
- **EVERY markdown file. No exceptions. No "this one is internal" (CRITICAL).** The legibility rules below apply to every `.md` file this repo writes or edits - `context/business.md`, `proof-inventory.md`, the voice files, audit reports, queues, registries, drafts, notes, everything. There is no such thing as a file the owner will not open, and a file that is hard to read is a file that does not get checked, which is how wrong facts survive.

  **Before finishing ANY command, re-read every file you wrote and fix it if it fails these:**
  - **Could a busy non-technical business owner read this on a phone and know what to do in 10 seconds?** If not, it is not done.
  - **No tables. Period.** Not "where a list works" - EVER, in any file a member opens. A markdown table is a spreadsheet in disguise: pipes and alignment that collapse the moment one cell runs long, unreadable on a phone, unreadable in a plain editor. Use a `##` block per item with bold field labels, or a plain bullet list. Data that genuinely only works as a grid belongs in `code/` for scripts, never in a deliverable. (Tables rendered on WEB PAGES - a pricing table on a service page - are HTML on the site and stay.)
  - **No raw payloads as deliverables.** No YAML blocks, JSON, CSV, ISO timestamps, field names, IDs or API shapes in a file a human opens. Machine formats get built at send time and cached under `code/`.
  - **No bare numbers.** `(37)` is meaningless. Label it or drop it.
  - **No walls.** No paragraph of `·`-separated items, no list past 10 items without a `+ 23 more`, no block of unbroken text longer than about four lines. Whitespace and headings do the grouping.
  - **Dates in words.** "Tuesday 18 August", never `2026-08-18T00:00:00-07:00`.
  - **Plain words, not jargon.** "Update", not `"Call to action"`. "Button: Book", not `cta_action: BOOK`.
  - **Three lines at the top:** what it is, when it was made, the ONE next action.
  - **Decision before data.** What to do first, then the full list.

  When in doubt, open `references/file-examples.md`. It is 150 lines holding the only five shapes this repo writes - a build list, a registry, a queue, a findings report, a fact file. Find the job, copy the shape. That file is the bar, and it is the only one.

- **Everything stays legible (CRITICAL).** Before writing ANY file the user will open, read `references/output-format.md` and follow it exactly - it defines the nine formatting rules, the house shape, and the canonical layout for `keyword-map.md` and audit files. The short version: three lines at the top, then blockers, then a `##` block per item with bold field labels, long lists collapse to a top 50, no paragraphs inside data files, no tables anywhere, and NEVER a CSV, JSON dump, or raw data blob as a deliverable. The test: could a non-technical business owner open the file and know what to do within 10 seconds? If not, rewrite it. If a file genuinely needs to break a rule, ask first - never change a file's shape silently.
- **Built is not published.** Approved batches go live on the next deploy - there is no queue in this lane. Service and location pages take the earliest slots, blogs drip at 2-3/week. WordPress schedules natively; static sites get a dated frontmatter field plus a daily GitHub Actions cron. `code/publish_due.py` runs daily from launchd, publishes only what's due, and marks it Live. Rules and cron setup in `references/publishing-cadence.md`. Never bulk-publish a batch of blog content.
- **Never delete anything (CRITICAL).** No command removes images, videos, embeds, sections, paragraphs, pages, plugins or scripts - not a thin page, not an orphan, not an oversized image. Every one has a fix that isn't deletion: compress and convert, lazy-load, defer, improve, canonicalize, link to it. Deleting a URL loses its links and rankings permanently. When removal genuinely is right, it goes in the report as a RECOMMENDATION - what it is, why, what it costs to keep, what breaks if it goes, plus any redirect needed - grouped under "Needs your approval to remove", and it waits for an explicit yes. Consolidations and 301 merges count as deletions. Never bundle a removal into a batch of fixes.
- **Never invent proof.** No number, review, credential, or claim goes on any page unless it exists in `context/proof/proof-inventory.md`. If proof is missing, say so and ask - never pad.
- **The context layer must AGREE with itself (CRITICAL).** `context/business.md`, `context/proof/proof-inventory.md` and `context/voice.md` are written at different times and corrected at different times, so they drift - and a stale line at the top of one file is indistinguishable from a current one. This has already cost a full keyword map: `proof-inventory.md` correctly recorded a new offer while `business.md` still led with the retired one, and the next command believed the wrong file.
  - **Before acting on anything from `context/`, cross-check it.** What `business.md` says is sold must match what `proof-inventory.md` has proof for and what the live site shows. Different answers = stop and ask which is current.
  - **The later resolution always beats the earlier summary.** A note dated last week that says "RESOLVED: actually it's X" wins over a paragraph at the top of the file written a month ago. Never believe the headline just because it comes first.
  - **When a contradiction is resolved, FIX the file** so the top reflects the answer and the stale version is marked superseded. Leaving it in place means the next command trips over the same thing.
  - **Every context file carries the date its facts were last verified.** A fact with no date is a fact nobody can trust.
  - **Watch for proof that does not cover the offer.** A business selling SEO with only automation results in its proof file cannot claim SEO outcomes on a page. That is not a contradiction, it is a gap - name it, and say which pages it blocks.
- **If you can't find it, ASK. Never guess, never leave it blank (CRITICAL).** Some things genuinely cannot be looked up from here: which attributes a category exposes (Google publishes no per-category list - only the dashboard knows), whether the owner is family-owned or veteran-owned, their licence number, their average job value, whether they actually serve a city. When you hit one of these, stop and ask a direct question. Three failure modes, all banned:
  - **Guessing** - a plausible number or a likely-sounding attribute presented as fact. This is inventing proof wearing a different hat.
  - **Leaving it empty** - `identity: []` with no note is indistinguishable from a step nobody ran. An empty value is only valid once it records that it was asked and the answer was no.
  - **Quietly skipping it** - the section silently shrinks and nobody notices what's missing.

  Ask one question at a time, in plain words, and say why you need it. If the answer has to come from somewhere the user has to go look (their GBP dashboard, their licensing board, their accountant), tell them exactly where to click. Every unanswered item ends up in the report as an open question, never as a blank.
- **Label confidence on anything not documented.** When a recommendation rests on practitioner convention rather than official guidance or published testing, say so in the file: "this is practitioner consensus, not documented Google behaviour." Never present a widely-repeated SEO claim as fact - most of them have never been tested, and members will act on whatever tone you use.
- **Empty context = say so BEFORE writing, and stamp it on the file (CRITICAL).** Every command that writes customer-facing words - `/gbp`, `/gbp-posts`, `/blog-post`, `/service-page`, `/review-generator` - checks `context/voice.md` and `context/proof/proof-inventory.md` first. If either is empty or still template:
  1. **Say it up front, before generating:** "Your voice files are empty, so anything I write now will read generic. Run `/context-layer` first (about 20 minutes) and it comes out sounding like you. Want to do that, or shall I draft generic and you re-run later?"
  2. **Never block on it.** If they say keep going, keep going - a generic draft they can react to beats a blank page, and some people only understand what voice work buys them once they have seen the flat version.
  3. **Stamp the warning at the TOP of every file produced**, in the header, not buried at the bottom: `> Written before /context-layer ran, so this reads generic. Run /context-layer and re-run this command to get it in your voice.` The person who opens that file in three weeks is not the person who saw the chat message.
  4. **Re-running after `/context-layer` removes the stamp.** The banner going away is the signal it worked.

  This is the single most common way a member ships something that sounds like AI: not because the command is bad, but because they ran it before the voice layer existed and never knew.
- **Never rewrite the copy (CRITICAL).** Audits and fix passes change the mechanical layer only: title tags, meta descriptions, alt text, heading TAGS, schema, canonicals, link anchors, image files, slugs, broken markup. They do NOT touch body sentences - not for flow, not for clarity, not for readability, not for keyword density - and never the stories, jokes, asides or turns of phrase. The test before every edit: mechanical SEO problem, or me writing? If it's the second, stop. Pages that genuinely need new content route to `/blog-post` or `/service-page` where the voice files load and the user approves the draft. If a sentence truly must change, make the smallest possible insertion, keep every other word, and show before/after for a veto. Report the count of body sentences altered after any fix pass - zero is the expected answer.
- **One primary keyword per page, ever.** Check `keyword-map.md` before writing. If a keyword is taken, flag it - never write a second page against the same primary (cannibalization).
- **Update the registries.** Every page you draft appends a row to `website-index.md` and updates its keyword's Status in `keyword-map.md`. No orphan drafts.
- **Platform parity.** Every build works two ways: static/Next.js (deploy via Vercel) or WordPress (via the **Novamira** plugin + MCP connection - it exposes the site's abilities so pages, posts, meta, and settings can be created and edited directly). Ask the lane once (the first command that touches the site), record it in "## My setup". On WordPress: content commands create pages/posts as DRAFTS through Novamira (never publish directly), on-page and speed fixes apply through it, and the SEO plugin owns sitemap/robots. Novamira not connected yet? The first WP command walks them through installing + connecting it right there, then continues - nothing else works on the WP lane without it.

## The GHL link - use it EVERY time GoHighLevel comes up

**Claim link:** https://www.skool.com/automatable/classroom/32447943?md=47d1df7d71c449baa5ab88c94340718c

GoHighLevel is **$1/month** through the community perk, and it is the default answer for a lot of this repo: the review ask and the unhappy-customer save workflow (`/review-generator`), the business phone number, call recording and Voice AI for 24/7 hours (`/gbp`), the booking calendar behind the profile's Book button, speed-to-lead on form fills, and the CRM behind your client work.

**Never mention GHL, GoHighLevel, the CRM, the $1 plan, a business phone number, a booking calendar or Voice AI without pasting that link right there.** Not "claim it in the community", not "see the classroom" - the actual URL, every time, in every command and every generated file. Somebody reading a file three weeks from now cannot click a sentence that describes a link.

Already have GHL? Confirm it, record it in "## My setup", and skip the link from then on.

## Two rules that override everything else

**Test before you respond.** After any code change, run the thing - start the dev server, run the build, execute the script - and check for errors BEFORE replying. **Never say "done" if it's untested.** Keep testing until it actually works. A green build you didn't run is not a green build.

**The 9 out of 10 quality gate.** Nothing gets published to a live site until it scores 9 out of 10 or higher. That covers every page, blog post, meta description and GBP post.

Rate it honestly and neutrally. **Never inflate a score to move things along.** If it isn't a 9, say exactly what's wrong and fix it before going any further. A 10 only exists after the data comes back - never award one in advance.

Score on: hook strength (specificity, numbers, tension), body structure (does it follow the winning formula), originality (would someone screenshot this?), and CTA clarity. Be direct about what's dragging the score down. "It's fine" is not a score.

## ⛔ A PROOF MUST RUN THROUGH THE PRODUCTION PATH. Doing it by hand proves nothing.

This has failed twice in the same way, so it is a rule now rather than a note.

**The failure:** a skill needs to demonstrate that something works unattended. It cannot get the timing right, or the wait is awkward, so it does the thing manually instead - fires the workflow itself with `gh workflow run`, or `curl`s the webhook straight from the terminal. It then reports success. **The report is true and worthless:** it proved a command works, not that the machine runs without a human.

**The rule: if the thing is supposed to happen automatically, the proof must go through the automatic path.**

- Pages publish via `.github/workflows/daily-rebuild.yml` → the proof is a workflow run, triggered from the GitHub Actions page.
- Business Profile posts publish via `.github/workflows/gbp-posts.yml` running `code/publish_due_gbp_posts.py` → the proof is a workflow run, **never a `curl` from this machine.** A terminal `curl` tests the webhook. It does not test the queue, the cron, the caps, the `sent/` move, or the secret - which is where every real failure lives.
- Anything else on a cron: same. The demonstration is the production path or there is no demonstration.

**And a queue is not queued until the artefact exists.** Writing "scheduled for Wednesday" into a markdown file schedules nothing. For GBP that means a dated `.yml` in `gbp-queue/`; for pages it means `publishDate` in the page and the commit pushed. **Verify the artefact on disk and say you did** - `ls gbp-queue/*.yml` returning nothing while a report says 7 posts are scheduled is the exact failure this catches.

**Secrets are part of the path.** An Action that will fail on `MAKE_WEBHOOK_URL` not being set is not wired. Check with `gh secret list` before claiming a queue will drain.

## ⛔ EVERY command opens with a ROADMAP. No exceptions.

**Before doing anything - before the first gate, the first file read, the first tool call - print the plan and stop for one beat.** A command that starts working immediately looks like it is doing random things, because from the outside that is exactly what it looks like. The roadmap is what turns twenty minutes of tool calls into something a person can follow.

Four parts, always, in this order:

```
── /service-page · here's the plan ─────────────────────

WHAT HAPPENS          6 steps
  1. Confirm your two template pages          ~instant
  2. Pull the next 3 rows, check they're unbuilt
  3. Research + write each page               ~10 min
  4. Optimize to 100%, similarity check       ~5 min
  5. Wire internal links
  6. Schedule, push, prove it went live       ~5 min

HOW LONG              about 20 minutes, mostly step 3

I NEED FROM YOU       3 stops - I'll wait at each
  · confirm the templates (one word)
  · approve the batch before it schedules
  · click one link at the end to watch a page go live

WHAT MIGHT GO WRONG
  · city pages get HELD if there's no real local
    material for them - that's the gate working
  · first run only: I build the date wiring, +5 min
────────────────────────────────────────────────────────
```

**The rules for it:**

- **Real numbers, not "a few minutes".** If you do not know, say the range and what drives it ("10-25 min depending on how many pages need research").
- **Every stop where you will wait for me goes in "I NEED FROM YOU"**, with what I actually have to do. A stop I did not know was coming feels like the command hanging.
- **"WHAT MIGHT GO WRONG" is the honest one.** Name the things that genuinely fail on real runs - a gate that holds pages, a credential you might not have, a step that only happens the first time. Not a disclaimer, a heads-up.
- **Adapt it to the actual run.** A `/blog-post` on a keyword already researched skips the research step, so that line comes out. Never print a generic roadmap that does not match what is about to happen.
- **Then start.** Do not ask "shall I begin?" - the roadmap is information, not a gate. The approval stops are inside the run where they belong.
- **Short commands get a short roadmap.** `/publish` on a single page needs two lines, not a box. Scale it to the work.

## How to respond

Explain everything like you're talking to a 15 year old with no coding background.

**Writing style (hard rule): never use em-dashes.** Not in files, not in page copy, not in ad copy, not in these chat replies. Use a regular hyphen (-) instead, always. Em-dashes read as AI-written.

Every response covers:
- **What I just did** - plain English, no jargon
- **What you need to do** - step by step, assume they've never seen this before
- **Why** - one sentence on what it does or why it matters
- **Next step** - one clear action
- **Errors** - if something broke, explain it simply and say exactly how to fix it

When a task involves a tool a non-coder wouldn't know (Search Console, Vercel, Google Ads settings, Novamira, an API key):
- Walk through exactly where to find it: "go to your Search Console dashboard, then Settings, then Users and permissions"
- Describe what each key or setting does in one plain sentence
- If there's a config or folder to create by hand, explain what it is and why it exists
- Be as concise as possible. Do not ramble. Less is more.

## File map

**The context layer - the business, filled once, read by everything**
- `context/business.md` - what the business does, where, what it does NOT do, plus the packages, terms and scope boundary you price from
- `context/proof/` - proof inventory, images library, reviews. The E-E-A-T twin
- `context/voice.md` - Part 1 is the house style and the entertainment spec (blogs write to the standup bar); Part 2 is their material
- `context/buyers.md` - the buyer segments the intent clusters produce

**What the run produces**
- `keyword-map.md` - **THE keyword file.** Root + cluster, volume, difficulty, build order, all in one
- `website-index.md` - registry of every page: written → linked → scheduled → published
- `audit-report.md` - the live audit checklist written by `/audit`, worked through item by item, keeps its history across runs
- `website/` - the Next.js site: chassis plus every standard page already built (thank-you, services, about, contact, quote, reviews, pricing, legal, 404, sitemap, robots, llms.txt). `/build-website` fills it in and adds the pyramid. Verified: installs + builds clean

**How every file must look**
- `references/file-examples.md` - **the rendered shape of every file the user opens. Match it exactly**
- `references/output-format.md` - the nine formatting rules and the house shape behind those pictures
- `references/examples/` - the full worked version of every file a command produces, on a fictional plumbing business. `file-examples.md` shows the shape at a glance; these show a whole finished file. Start at [references/examples/README.md](references/examples/README.md), which says which example matches which command. Never copy their content into real files

**The specs commands execute**
- `references/on-page-seo.md` - the 80-check spec. Generation reads it BEFORE writing, audits grade against it AFTER
- `references/geo.md` - the 38-check GEO spec (get cited by AI). `/audit ai` grades against it, `/seo-optimization ai-layer` fixes to it
- `references/meta-info.md` - high-CTR titles + meta descriptions, the swipe set
- `references/search-intent.md` - **the intent rule: search the term, classify the top 10, 6 of one type decides it.** Informational to a blog, transactional to a money page
- `references/keyword-clusters.md` - cluster + hub-and-spoke rules
- `references/keyword-strategy.md` - **the evidence layer under all of it.** What the metrics really measure, which thresholds are convention, what predicts a new site ranking, and the myths
- `references/pyramid-structure.md` - the canonical site tree (3 layers max, blog flat, cities = Layer 3). `/build-website` builds to it, `/audit` grades against it
- `references/standard-pages.md` - **the pages every site needs:** /thank-you (tracking fires here), the 6 sitelink targets, legal, 404, robots, llms.txt
- `references/blog-post-template.md` - THE locked blog skeleton. Every `/blog-post` writes into it; improve the template, never deviate per-post
- `references/service-page-template.md` - THE locked money-page skeleton (hero-proof-first, 5+ proof touches, anti-clone city rule)
- `references/cro-cheatsheet.md` - the 7-point conversion checklist `/service-page` walks the user through item by item
- `references/gbp-setup.md` - the complete GBP setup spec (research → 12-section paste-ready file). `/gbp` executes it
- `references/gbp-posts.md` - GBP post creation rules + Make.com webhook contract. `/gbp-posts` executes it
- `references/citations.md` - the 5-tier citation directory list + NAP rules. Feeds `/gbp`'s citation campaign

**The WordPress lane**
- `references/wordpress-plugins.md` - the plugin stack: one plugin per function, settings, conflicts. `/wordpress` installs to it
- `references/wordpress-audit.md` - the WP audit-fix methodology (#1 rule: fix where the page actually RENDERS) + the living stack profile
- `references/wordpress-pages.md` - the WP page-build playbook (custom PHP / Gutenberg / Elementor via Novamira). `/build-website`'s WP lane

**Design**
- `design/sites/` - the pre-built site designs by vertical. Every visual build reads it

## My setup

- **Business:** Belicleenair (ベリクリーンエア) - sells industrial/commercial VOC and organic-solvent air purifiers, based in Osaka (Kita-ku), serves Japan nationally. Site: www.belicleenair.com
- **Business type:** National brand (B2B industrial equipment). No city axis on the keyword map.
- **Market / search country:** Japan. Semrush database `jp`. Content language: Japanese.
- **Semrush:** connected and working (MCP tools). `keyword-map.md` rebuilt on REAL `jp` data 30 August 2026 - 23 pages. Key finding: product terms (発散防止抑制措置, 有機溶剤対策, VOC対策) get 0-140 searches/mo; the volume is all in the regulations (局所排気装置 3,600, 化学物質管理者 9,900, 有機則 とは 480, 作業環境測定 管理区分 390). Money pages convert blog-hub traffic, they don't rank for volume themselves. Ceiling KD 30 (belicleenair.com = 8 ranking keywords, no measurable Authority Score - re-confirmed 9 Sep 2026). **All 23 pyramid pages have real Japanese content (finished 6 Sep 2026).**
  - **Expand run 1 (9 Sep 2026):** pages 24-30 added (濃度基準値・保護具着用管理責任者・SDS・管理濃度・プッシュプル型換気・補助金・悪臭防止法), volumes ESTIMATE. All written + published to staging.
  - **Expand run 2 (9 Sep 2026, REAL `jp` data):** only 2 pages survived - **31 化管法/PRTR** (KD24, pairs with hub 17) and **32 有機溶剤作業の防毒マスク** (KD14, honest bridge to money pages). Dust/集塵/粉じん pulled (~110 kw) and CUT: 集塵 SERP = power tools + consumer purifiers; 粉じん則 = courses + asbestos + じん肺; the activated-carbon+HEPA unit can't serve 粉じん則 dust. 換気量計算 = building HVAC. 検知管 = detector-tube purchase + school science. **The niche's meaningful demand is now largely mapped** - big terms (PRTR 4,400, 防毒マスク 8,100, じん肺 5,400) sit in "saved for later" behind the KD-30 ceiling.
  - **Both 31 and 32 written 9 Sep 2026 (`/blog-post`), gated, in `# Written`. `# To build` = 0.** Not yet `/publish`ed (site is noindex). Routes: `/blog/chemical-management-law-prtr`, `/blog/organic-solvent-respirator`.
  - Next content: let the site age (authority score / domain age), then re-run `/keyword-research expand` in a few months for the parked head terms. Still open: re-derive `context/buyers.md` from the map.
  - **Dev-server note reinforced:** `check_page_done` on this OneDrive box throws transient `0` (connection refused) on a random nav link each run - `next dev` can't serve ~25 sequential requests. Fix: warm every route with a curl sweep first, then run the gate immediately while warm. Not a real dead link - every target renders 200 individually and `next build` passes.
- **Site lane:** Static / Next.js (deploy via Vercel). Chosen 30 August 2026 - the repo ships a full Next.js scaffold, no WordPress signal, owner on Salesforce. `SITE_STYLE = calm` (picked 30 Aug 2026 - B2B compliance product, credential-led). Calm promoted to root, picker saved as `website/app/_picker.tsx.bak`.
- **Legacy site captured + rebuilt (31 August 2026):** crawled www.belicleenair.com (no sitemap/robots) - 35 URLs. Real content saved to `context/proof/legacy-site-content.md` (6 anonymised case studies + technical FAQ). Owner said YES to all 3 open decisions, so these are now REAL pages: `/products` index + 7 model pages `/products/{ba100s,ba400s,ba400t,ba500s,ba500t,ba800l,ba900pvc}` (data in `lib/products.ts`, shared render in `app/products/_ProductPage.tsx`), `/faq` (24 Q&As grouped), `/movie` (topic list + YouTube channel link), `/news` (~14 entries, NDA partner names stripped), `/recruit` (full 募集要項). Shared chrome for these: `app/_chrome.tsx` (SiteHeader/SiteFooter). Header nav now 6 items (added 製品ラインナップ). Footer rebuilt site-wide to link all new pages + real privacy/site-policy links. `website/vercel.json` trimmed to 26 redirects (product/faq/movie/news/recruit no longer redirected). sitemap.ts lists all live pages incl. 7 models. The live site's stale copy (115V, "厚労省認定", "申請中", 2024年3月許可, 150台, nail-salon as target) was NOT carried over - `lib/products.ts` and `/faq` use the corrected facts (100V, 大阪労働局天満署 / 株式会社ベリカ名義, EU製・日本アセンブリ, 160台).
- **Dev server note:** the project lives in a OneDrive-synced folder; `next dev` is slow and intermittently 500s with `.next` ENOENT chunk errors, and stale-caches shared components (`_chrome.tsx`, `_ProductPage.tsx`, `lib/*`) - `touch` the file or `rm -rf website/.next` + restart. Not a code problem - gates pass on a clean restart; `next build` is unaffected.
- **Images + logo done (31 August 2026):** the owner sent the full legacy-site export (`context/proof/images/【重要】HPデータ...zip` -> `_hp/x/`). Real product photos, home hero, case diagrams, filter photos and the logo are wired in (compressed to webp in `website/public/images/`). Brand blue retuned to the logo's exact navy **#082088**. Header shows the logo. Security-swept (no secrets, no NDA names, no banned claims) and pushed.
- **Website git repo:** `website/` is its OWN git repo (nested inside the gitignored subdir; the parent repo ignores it). Remote: `https://github.com/jackysakai/Claude-code-belicleenair.co.jp` (the owner's personal GitHub `jackysakai`), branch `main`. Local git identity in `website/.git`: jackysakai / jacky@belica.co.jp. Push works with `GCM_INTERACTIVE=never git push` (the interactive credential dialog hangs the non-interactive shell). Connected to Vercel (auto-deploy on push). Vercel project `jacky-sakai/claude-code-belicleenair-co-jp`; staging site is **https://claude-code-belicleenair-co-jp.vercel.app**. Give this URL + the page path after every push.
- **⛔ Canonical domain = www.belicleenair.co.jp (swapped 6 September 2026).** Owner controls belicleenair.co.jp, .com, .jp, .net (all on お名前.com / GMO). Site code, `lib/site.config.ts` url, sitemap, robots, all JSON-LD point at **https://www.belicleenair.co.jp**. **NOW LIVE (verified 9 Sep 2026):** both domains added to the Vercel project, DNS records in place at お名前.com (dnsv.jp), `https://www.belicleenair.co.jp` serves the new site with valid SSL, `belicleenair.co.jp` apex 308-redirects to www. **Indexable since the 10 Sep launch.** NS stayed on GMO's `0X.dnsv.jp` (external-DNS mode, not Vercel nameservers) - Vercel's `domains inspect` shows ☓ on the NS row, that is expected for external DNS and not an error. The old www.belicleenair.com still serves the OLD legacy site on GMO hosting (gmoserver.jp) - the .com→.co.jp 301 is wired in vercel.json but dormant until the owner adds the .com domains to Vercel + repoints .com DNS (see the launch note below).
- **Analytics: GA4 tracking fully fixed and conversion tracking wired, 12 Sep 2026.** The original measurement ID `G-7SDSW80XRZ` was broken on Google's own side (its `gtag/js` script returned a genuine 404 from Google's server, confirmed via curl outside the browser too - not a code bug, not an ad-blocker) despite GA4's admin UI showing it as the correct, active ID. Fix: created a fresh data stream in the same `Belicleenair1` property, pointed at `www.belicleenair.co.jp` → new working ID **`G-MTFEPQFQJ9`**, now live in `site.config.ts` `ga4`. gtag.js loads site-wide from `app/layout.tsx` head. `/thank-you` + `/catalog/downloads` fire a `generate_lead` event (`app/_analytics.tsx` `<LeadConversion/>`) - confirmed firing correctly in GA4 Realtime. `generate_lead` imported into Google Ads as a conversion action ("Submit lead form" category, primary, live on both campaigns) - Ads account `948-985-8762 BELICLEENAIR` under manager account `473-714-7603` (JACKY SAKAI). Checked disapproved assets 12 Sep 2026: none found, that earlier concern is stale/resolved. `site.config.ts` `adsConversion` stays null (GA4 import covers it; no separate direct Ads snippet needed).
- **Chatbot - in-house Claude bot is LIVE (switched on 8 Sep 2026); Elfsight removed.** `app/_chatbot.tsx` (on-brand widget) → `app/api/chat/route.ts` (Anthropic Messages API, `claude-haiku-4-5-20251001`, per-IP rate limit 25/hr, no SDK dep) → `lib/chatbot-knowledge.ts` (system prompt + fact-checked knowledge + full banned-claims list). Gated on `site.config.ts` `chatbot.enabled: true`; `elfsightAppId: null`. `ANTHROPIC_API_KEY` is in the Vercel project env (never committed). Layout renders one OR the other, never both. Knowledge source of truth: `context/proof/chatbot-knowledge/faq-corrected.md` (keep `lib/chatbot-knowledge.ts` in sync). The old Elfsight widget `70166970-fd14-40e7-a8d4-eb0fbd56566b` is disconnected but still emails the owner about past chats and had bad data (wrong phone 7734, 厚労省認定, ジクロロメタン対応可, etc. - `context/proof/chatbot-knowledge/elfsight-export-errors.md`).
  - **Transcript email (added + wired 9 Sep 2026):** `app/api/chat/log/route.ts` - the widget beacons the full conversation once per session (on close / tab-away / page leave), the route formats a plain-text email and POSTs `{ to, subject, text, messages, ... }` to env `CHAT_LOG_WEBHOOK`. LIVE: `CHAT_LOG_WEBHOOK` is set in Vercel to a Google Apps Script web app (project "belicleenair chat log" in jacky@belica.co.jp's account, deployed as Web app / execute as Me / access = Anyone; `doPost` does `MailApp.sendEmail`). Emails go to **jacky@belica.co.jp + y.otaki@belica.co.jp** (the `to:` string in route.ts - change there, not the script). Note: Make.com and a domain-locked Apps Script deploy both failed first (Workspace blocks "Anyone with a Google account" web apps for anonymous callers - the deploy MUST be access = 全員/Anyone, giving a `script.google.com/macros/s/.../exec` URL with no `/a/macros/`). Unset webhook = no email, chat still works (route returns 204). Payload carries approx. location (Vercel geo headers), IP, referrer and the `_ga` client id for GA4 cross-ref; visitor name/company/email only if they type it. **Decision: do NOT gate the chat behind a name/email form** - kills top-of-funnel influence for a high-consideration B2B buy; capture at intent via the existing /quote /contact /rental forms instead.
- **✅ LAUNCHED 10 September 2026** (owner said "launch", overriding the planned 2-4 week trial - trial ran 4 days). `lib/site.config.ts` `indexable: true`. Every content page is now indexable; `/thank-you`, `/catalog/downloads`, `/catalog/request`, `/privacy-policy`, `/terms` keep their own `robots:{index:false}`, and `/quote` was set noindex + pulled from the sitemap at launch (bare lead form; `/contact` stays in, it carries the NAP). Verified live: www.belicleenair.co.jp/ has no robots meta, sitemap.xml 200 with 62 URLs, robots.txt allows all + AI crawlers.
  - **✅ .com→.co.jp 301 IS LIVE (10 Sep 2026).** Owner added both .com domains to the Vercel project (set to 308-redirect), then at お名前.com: re-added the MX + google-site-verification TXT to the お名前 DNS zone, and switched belicleenair.com's nameservers from `ns-rs1/ns-rs2.gmoserver.jp` to お名前's `01-04.dnsv.jp`. Verified: `https://www.belicleenair.com/` → 308 → `https://www.belicleenair.co.jp/`; deep old paths chain through vercel.json's path rules (`/company` → `/about`, 2 hops); email MX intact. **The bare apex `belicleenair.com` was still serving the old GMO nginx from a stale local DNS cache at check time - authoritative DNS is correct (A → 76.76.21.21) and the Vercel apex redirect is configured, so it follows within ~1h.** The vercel.json host-match rules are a belt-and-suspenders backup to Vercel's dashboard "Redirect to" setting.
  - **Still owner-side:** Search Console - verify www.belicleenair.co.jp, submit sitemap, URL-inspect the top pages; add www.belicleenair.com as a property (the google-site-verification TXT was preserved so it should re-verify) and file Change of Address (.com → .co.jp) - now unblocked.
- **GBP: `/gbp` run 10 September 2026 → `gbp-belicleenair.md` (repo root, gitignored).** Full 12-section paste-ready file, adapted for a national B2B manufacturer (no service-area city list, no review-gen push, ~40 real services not a padded 70, 7 BA models + 4 support items as products all linking to live pages). Owner answers 10 Sep: initially said no listing existed, then a screenshot showed **a GBP for 株式会社ベリクリーンエア ALREADY EXISTS, is verified, and the owner manages it.** Already populated: name, address (correct), **phone 06-6352-7754 (correct - not Belica's 7734)**, category 産業用機器製造業者, website, partial hours, ~12 photos (incl. ad banners - owner must audit for 国産/特化則/Donaldson-BOFA-label wording), a description with muddled "特許出願中認可済み" + risky "上場企業を含む大企業様" phrasing. 0 reviews. No cover photo / logo. **So `gbp-belicleenair.md` is an OVERHAUL checklist, not fresh setup - verification is already done.** **(2) 株式会社ベリカ HAS its own GBP at the same アヴァロンビル 5F** - but since Belicleenair is already verified with the correct distinct phone, near-term suspension risk is low; keep phone/category/description/photos distinct from Belica. **(3) Someone is at 天満 weekdays 9-17.**
  - Chosen primary category: **換気設備メーカー** (Ventilating equipment manufacturer) - JP GBP has no 空気清浄機 category; secondaries lead with エアフィルター製造卸売業者 + 産業用機器製造業者. Opening date to enter: **2021** (BA100S/BA400S on sale), NOT the 2012 entity date.
  - Identity attributes = 該当なし (proof-inventory bans family/veteran-owned). Attributes section left OPEN pending the owner reading their dashboard back (can't be researched from outside).
  - Already listed on イプロス + 製品ナビ (incom.co.jp) under old names - citation campaign updates those to 株式会社ベリクリーンエア. Citation list is JP-specific (Yahoo!プレイス, iタウンページ, J-GoodTech, Metoree, アペルザ, NC-Network) - references/citations.md is US-centric, not used verbatim.
  - **Owner applied most of the file 10-11 Sep:** identity attr set (女性オーナーではない), hours, 敬老の日 closed, サービスオプション, description/category/services/products worked through. Website field: the `belicleenair.com` the owner kept seeing is the ORGANIC result (not a GBP field) - self-heals via the .com→.co.jp 301; the GBP ウェブサイト button is the one to keep on .co.jp.
  - Still open, no rush: audit the ~12 existing photos for 国産/特化則/厚労省認定/Donaldson-BOFA-label wording + add cover/logo; FAQ seeds (section ⑪) into `/faq` (Claude can do); update イプロス + 製品ナビ from old names + register Yahoo!プレイス/iタウンページ (section ⑫). NEVER SAY list applies - gbp-belicleenair.md is clean.
- **`/gbp-posts` webhook setup, 11 Sep 2026.** `MAKE_WEBHOOK_URL: https://hook.eu1.make.com/yix62bjpke6p98b8b2chwegv6rpn4yf1` (Make scenario `eu1.make.com/2713760`). `DEFAULT_CTA_URL: https://www.belicleenair.co.jp`.
  - **⛔ Root project repo moved.** `automatable-skool/seo-blueprint-day1` (the course template) is NOT owned by the user - `gh` CLI isn't installed in this environment either, and `git push`/`git remote set-url` are both blocked by the sandbox's auto-mode classifier for Claude, so this had to be done by the user in their own PowerShell window. **Fixed 11 Sep 2026: forked to `jackysakai/seo-blueprint-day1`, local `origin` now points there, pushed clean.** Also removed `gbp-queue/` from `.gitignore` (was in the "never track the member's work" block, correct for the shared template but wrong for the member's own fork - without this the scheduler can't persist which posts were already sent) - committed as `a8f2f8b`. **All future git pushes for this project go to `jackysakai/seo-blueprint-day1`, not the course repo.** The website (`website/`) is a separate nested repo at `jackysakai/Claude-code-belicleenair.co.jp`, unaffected by this.
  - **✅ Make scenario fully built and tested working end-to-end, 11 Sep 2026.** Webhook → Router (`post_type`) → 3 branches, each a Google Business Profile "Create a Post" + a Webhook Response returning `{"published": true, "post": "{{N.title}}"}`. Connected to the ベリクリーンエア location (account `酒井全福`, not Belica's). Test post confirmed live on the real profile, then deleted.
  - **Two real Make gotchas hit and fixed, worth knowing if this scenario is ever rebuilt:**
    1. **Media items** needs "Array of objects", not a bare URL string. Fix: turn its "Map" toggle OFF, click "+ Add item" once, leave Media format = Photo, map only the Source URL sub-field to `{{1.media_items[1]}}`. Applies to all 3 branches.
    2. **Action type (the CTA button) can't be both mapped AND keep its paired URL field.** Make only shows/sends the "URL" field when Action type is a FIXED dropdown pick - the moment Action type is set to `{{1.cta_action}}` (mapped), Make hides AND drops the URL parameter entirely, so `callToAction.url` silently goes missing at send time even if URL was filled in earlier. **Fix shipped: module 4 (Call to action branch) has Action type locked to a fixed "Learn more"**, not mapped - so every "Call to action" post uses a Learn More button pointing at `{{1.cta_url}}`. `cta_action` in the payload is effectively unused now; don't bother varying it per post.
  - **PowerShell test note:** `Invoke-RestMethod -Body $body` mangles Japanese text (mojibake) because it doesn't send UTF-8 by default - saw this on the test post, harmless since it was deleted. The real production path (`code/publish_due_gbp_posts.py`, Python's `json.dumps().encode()`) is UTF-8-safe and unaffected - this only bit the manual PowerShell test.
  - Owner-side effort spent: ~2 hours across Make scenario building (GBP OAuth connection, 3 branches, Media items fix, Action-type/URL fix), forking the course repo, and adding the GitHub secret. All done, nothing left to build - `/gbp-posts` can now generate and schedule a real month of content whenever run.
  - **⛔ Found + fixed 13 Sep 2026: the first real batch never actually went out.** `gbp-queue/` had been written 11 Sep but stayed untracked (local-only) and a `check_gbp_payload.py` validator fix (media_items must be a YAML list, not a string) was also uncommitted - so the Mon/Wed/Fri Action had nothing to run against. GitHub's own API confirmed 0 total runs ever for `gbp-posts.yml` despite it showing "active" since creation. Both are now committed and pushed (`de1f6e0`). Post 1 (due 11 Sep) was sent by hand through the real `publish_due_gbp_posts.py` script 13 Sep, confirmed 200/published, moved to `gbp-queue/sent/`, pushed (`b102e11`) - owner to confirm it's visible on the live profile. Posts 2-8 now drip for real on their Mon/Wed/Fri dates. **Lesson for future `/gbp-posts` runs: after writing to `gbp-queue/`, always `git status` to confirm the files aren't sitting untracked/ignored before telling the owner anything is scheduled.**
  - **RESOLVED 13 Sep:** a real Apify API token had been pasted into `.env.example` (a committed, public template) by mistake. Moved to `.env` (gitignored, confirmed via `git check-ignore`), `.env.example` blanked back out and pushed clean (`5c18789`).
- **⛔ Run `npx next build` in `website/` before every push.** `next dev` + the two gate scripts do NOT type-check; `next build` does, and Vercel fails the deploy on any type error. First Vercel deploy (commit 5c70df6) failed on two: (1) the new inline footer had a duplicate `font`/`color` key in one style object across all 31 pages - fixed; (2) `content/proposals/*.ts` (starter example data) imported `@/components/proposal/types` which does not exist in this scaffold - removed. Build passes clean at commit f4ba49d (54 static pages, `/api/lead` dynamic). **The OneDrive read-after-write race breaks `next build` for deep/new routes** - it "✓ Compiled successfully" then fails prerender with `PageNotFoundError: Cannot find module for page: /x` (repeatably, on the newest/deepest route). `rm -rf .next` + retry does NOT reliably fix it. **The fix that works: put `.next` on local disk** - `rm -rf website/.next && cmd //c "mklink /J \"website\\.next\" \"C:\\Users\\jacky\\AppData\\Local\\Temp\\belic-next\""` once, then builds are fast (~1 min) and clean. `.next` is gitignored so the junction is invisible to git. Vercel builds in its own clean env and never hits this - a local build is only for catching type errors. **`next start` serves stale content if an old server is still up** - `taskkill //F //IM node.exe` before every `next start`, and verify the served `<main>` matches the new build.
- **`/build-website` run 1 (31 August 2026) + all pages filled (6 September 2026):** 8 core pages + the full 23-page pyramid are now real Japanese content (service + blog rows all in `keyword-map.md` "# Written", `publishDate: 2026-09-08`). English slugs (e.g. `/services/organic-solvent-without-local-exhaust`). No English stubs remain. `/service-page` and `/blog-post` have nothing left to build until `/keyword-research expand` adds rows. Accent blue retuned to a deeper corporate ramp (--blue-700 #0d539e). Both exit gates pass. Contact email on site = y.otaki@belica.co.jp. Photos: NONE placed - no PEXELS key, Openverse unusable, real photos sit in Drive `BELICLEENAIR空気清浄機` (need pulling into `context/proof/images/`). Lead form: wired to `/api/lead` -> `/thank-you`, but `leadWebhook` is null (route 503s) - user will supply a webhook URL (test -> email jacky@belica.co.jp, launch -> Salesforce Web-to-Lead). 3 small i18n fixes made to `code/check_site_complete.py` + `code/check_css_integrity.py` (UTF-8 read, non-Latin keyword-map row -> branch-index check, サービス/製品 accepted in services H1, .next excluded from CSS scan, bare Tailwind utils allowlisted).
- **CRM:** Salesforce (adopted 1 July 2026, run with 株式会社シテラス). Not GoHighLevel - do not push GHL. Accounting: freee.
- **Context layer:** built from the live site, owner answers, and a Google Drive + Gmail sweep on 30 August 2026 (`/context-layer` run 3x). Solid. Remaining open questions in `context/business.md` and `context/proof/proof-inventory.md` - the 特化則 wording and clearing NDA customers are the load-bearing ones.
- **Connectors:** claude.ai Google Drive, Gmail, Calendar and Semrush all CONNECTED and their tools now load. Semrush available for `/keyword-research` re-validation.
- **Drive source of truth:** one folder, `BELICLEENAIR空気清浄機` (id `1Ve_pm18Fv9y9AN9AeiyxXstu8h2vY1Gd`). Enumerate it for every future proof update. Not-yet-pulled subfolders: 【18 マーケティング】(clippings/logos), 【16 ホームページ HP】, 【2 営業資料】, video folders. Manual drop folder: `context/proof/drive-dump/`.
- **Ownership:** 株式会社ベリクリーンエア is owned personally by 酒井全福 (Sakai) since Oct 2025 - bought from a Mr 辻, who bought it from 株式会社ベリカ (Feb 2024). Formerly 株式会社プラズマテック / ファストプラス. Belica (president 藤井泰伸, belica.co.jp) shares the office, holds the 発散防止抑制措置 permit and the granted patent (jointly with 酒井), and issues the PR releases. 大滝良彦 (Otaki) is the sales engineer / technical authority.
- **⛔ Do NOT claim 特化則対応/対策 on any page** - the filter cannot hold the required 1/10 concentrations (per Otaki). The current site meta descriptions say "特化則対策" and need fixing. Also NEVER SAY: ジクロロメタン, DMC, フッ素, エチレン as treatable solvents; 日本製; 防爆; the EU maker's overseas record as Belicleenair's own.
- **Customers:** only 4 cleared to name (八代塗装, Berry, 広島大学, 日威運動用品). A large NDA roster (Toyota, Kawasaki, Rohto, Mandom, Kyocera, NGK, Yuyama, Zebra...) is in proof-inventory - clearing some is the biggest site win. A 八代塗装 customer video exists, awaiting the file.
- **`/review-generator` run 12 Sep 2026 - live end to end, tested with a real 4-star post and a real email notification.** `website/app/review/page.tsx` is the star-rating gate: 4-5 stars copy the comment to clipboard then redirect to `site.config.ts` `googleReviewUrl` (`https://g.page/r/CeJ309V3W98bECE/review`); 1-3 stars POST to `app/api/review-feedback/route.ts`, which reuses the existing `CHAT_LOG_WEBHOOK` (the chatbot's Apps Script mailer) instead of a new Make.com/GHL scenario - no public link ever shown on that path. Works two ways: a personalized link (`/review?name=...&email=...&cid=...`, URL-encoded) skips asking for contact info again; the bare QR-code link (no params) asks for optional name/contact only on a negative rating. QR files at `website/public/review-qr.png` / `.svg`, generated by `code/make_review_qr.py` (fixed 12 Sep to point at the site's own `/review` gate, not the raw Google link - the original skill script would have let every scan skip the filter). **Found + fixed a real production bug during this run:** `layout.tsx` reads `ds.css`/`fonts.css` from disk at runtime (`readFileSync`, not a normal import - a Tailwind pipeline was resolving the custom properties to empty otherwise); Vercel's file tracer can't see that dependency, so it was never bundled into any serverless function - invisible until `/review` became this site's first genuinely dynamic PAGE. Fixed via `next.config.mjs` `outputFileTracingIncludes`, forcing both files into every route's bundle. **Sending cadence chosen: email, manual** (owner is on Salesforce, not GoHighLevel) - `review-requests.md` (repo root, gitignored) has the ask template + the velocity-cap rules (2-3/week, hard ceiling 5, Google deletes reviews that arrive too fast). `review-reply-templates.md` (repo root, gitignored) has 12 reply drafts in voice (4× 5-star, 2× 4-star, 6 hard cases) built from `references/review-replies.md`. Still open, no rush: hand the QR PNG to the owner's designer for invoices/trucks/counter cards; the test 4-star review is live under 酒井's own name on the real GBP listing - owner's call whether to keep, edit or delete it.

## Version

This is the living version of the SEO Blueprint. It updates when Google changes something. If a member reports a rule that stopped working, check the date on the relevant reference file before debugging their site.
