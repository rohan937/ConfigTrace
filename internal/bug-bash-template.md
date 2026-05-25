# ConfigTrace — Bug Report Template

> **Purpose:** Standardized template for logging bugs during manual QA, provider testing, and beta.
> **Usage:** Copy one instance of the template below for each bug found. Paste into this file or a linked issue tracker.
> **Reference:** See `manual-qa-checklist.md` for QA scope; `provider-testing-checklist.md` for provider-specific tests.

---

## Severity definitions

| Severity | Definition | Examples |
|----------|------------|---------|
| **Critical** | Product is broken for a core user flow. Blocks demo, beta launch, or revenue. Must fix before shipping. | Sync silently fails with no error; stack trace visible to user; credentials exposed; change detail shows no diff |
| **High** | A significant feature is broken or misleading. Blocks a common path, not the entire product. Fix before beta. | Risk level wrong on a known-dangerous change; invite email not delivered; billing limit not enforced |
| **Medium** | Feature works but imperfectly. Workaround exists. OK for beta with documentation. | Pagination breaks on 51+ events; empty state missing on a secondary page; wrong timestamp timezone |
| **Low** | Minor issue that degrades polish but doesn't impair function. Fix in a normal sprint. | Inconsistent spacing; label truncated at narrow breakpoint; tooltip missing |
| **Polish** | Aesthetic or copy improvement. Not a bug. Log if worth fixing, but no urgency. | Wording could be clearer; icon not pixel-perfect; hover state missing |

---

## Bug report template

Copy the block below for each issue found.

---

### BUG-[NNN]: [Short title]

**Date:** YYYY-MM-DD
**Reporter:**
**Status:** Open / In progress / Fixed / Won't fix / Duplicate

---

**Area:** (Authentication / Dashboard / Timeline / Change Detail / Resources / Integrations / Members / Audit Log / Billing / Data Access / Settings / Email / Empty States / Error States / Loading States / Responsive / Provider: [name] / Other)

**Provider (if provider-specific):** AWS / Firebase / Supabase / Stripe / GitHub / Cloudflare / Vercel / N/A

**Environment:**
- App URL: app.configtrace.org (or staging URL)
- Browser + version:
- OS:
- Viewport:
- Plan:
- Workspace:

---

**Steps to reproduce:**

1.
2.
3.

**Expected:**

**Actual:**

**Severity:** Critical / High / Medium / Low / Polish

**Checklist reference (if applicable):** (e.g., `manual-qa-checklist.md` item 5.2 / provider test `A15`)

---

**Screenshots:**
(Attach or paste link)

**Console logs / error messages:**
```
(paste here)
```

**Network request (if relevant):**
(Endpoint, status code, response snippet)

---

**Suspected cause:**
(Optional — if you have a hypothesis)

**Fix status:**
- [ ] Logged
- [ ] Reproduced by a second person
- [ ] Root cause identified
- [ ] Fix in progress
- [ ] Fix deployed
- [ ] Verified fixed

---

---

## Bug log

Add new entries above the horizontal rule for each session. Keep them numbered sequentially.

| ID | Title | Area | Provider | Severity | Status | Date |
|----|-------|------|----------|----------|--------|------|
| BUG-001 | | | | | | |

---

## Session log

| Date | Tester | Scope (checklist used) | Bugs found | Notes |
|------|--------|------------------------|------------|-------|
| | | | | |
