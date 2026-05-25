# ConfigTrace — Internal Operating Docs

> **Audience:** Founder / operator use only.
> These files are version-controlled but not linked from the public site, nav, or sitemap.
> Do not include secrets, credentials, or sensitive strategic information in this directory.

---

## What is this folder?

This is the internal launch/demo/QA pack for ConfigTrace. It contains the materials
needed to demo the product, QA it manually, prepare for private beta, and log bugs
systematically — rather than doing any of those things ad-hoc.

These are operational documents, not product or engineering specs.

---

## File index

| File | Use when |
|------|----------|
| [demo-script.md](demo-script.md) | Before any product demo or investor/user call |
| [manual-qa-checklist.md](manual-qa-checklist.md) | General QA pass on app.configtrace.org |
| [provider-testing-checklist.md](provider-testing-checklist.md) | Testing a specific provider end-to-end |
| [private-beta-checklist.md](private-beta-checklist.md) | Gate review before opening private beta |
| [screenshot-checklist.md](screenshot-checklist.md) | Capturing marketing/demo screenshots |
| [known-limitations.md](known-limitations.md) | Understanding current product constraints |
| [bug-bash-template.md](bug-bash-template.md) | Logging bugs during a structured QA session |

---

## When to use which file

### Before a demo
1. Read `known-limitations.md` to know what not to show or how to explain gaps
2. Read `demo-script.md` — use the 5-min version for cold intros, 15-min for warm/technical
3. Run through the first section of `manual-qa-checklist.md` to confirm the app is working

### Before private beta
1. Work through `private-beta-checklist.md` top to bottom
2. Run the full `manual-qa-checklist.md`
3. Run `provider-testing-checklist.md` for each provider you want live at beta
4. Verify `known-limitations.md` reflects current state and nothing critical is missing

### Before a manual provider QA session
1. Open `provider-testing-checklist.md`
2. Open `bug-bash-template.md` in a separate doc to log any issues found

### Before capturing marketing screenshots
1. Open `screenshot-checklist.md`
2. Prepare a clean demo workspace with plausible-looking (not real) data
3. Review the "what to avoid" notes for each screenshot

---

## What belongs in this folder

- Demo scripts and talking points
- QA checklists
- Launch readiness gates
- Screenshot guidance
- Known limitations
- Bug report templates
- Operational notes

## What does NOT belong here

- Real credentials or API keys
- Production database contents or exports
- Private customer data
- Sensitive business strategy
- Passwords or secrets of any kind

---

## Product context (as of M56.3)

**App:** app.configtrace.org
**Landing:** configtrace.org
**Docs:** configtrace.org/docs.html

**Providers live (7):** AWS · Firebase · Supabase · Stripe · GitHub · Cloudflare · Vercel

**Recent milestones completed:**
- M56.1: Marketing landing page refresh
- M56.2: Public docs and provider setup guides
- M56.3: This internal QA pack
