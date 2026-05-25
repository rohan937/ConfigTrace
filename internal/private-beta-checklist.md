# ConfigTrace — Private Beta Readiness Checklist

> **Purpose:** Gate review before inviting external users to private beta.
> **Rule:** All hard gates (marked 🔴) must pass before opening beta.
> **Soft checks (marked 🟡) should pass, but can proceed with documented exceptions.

---

## How to use

Work through each section. For any item that fails:
- Mark it `FAIL`
- Log the issue in `bug-bash-template.md`
- Decide: is it a hard blocker, or can it be documented as a known limitation?

---

## 1. Product readiness

### Hard gates 🔴

- [ ] 🔴 At least one full end-to-end AWS test completed and passed (see `provider-testing-checklist.md`)
- [ ] 🔴 At least one complete Cloudflare test passed (most common first provider)
- [ ] 🔴 At least one complete GitHub test passed
- [ ] 🔴 `Sync Now` works reliably for all connected providers
- [ ] 🔴 Change detail view shows correct diffs (old value / new value / risk reason)
- [ ] 🔴 Timeline renders correctly and is navigable
- [ ] 🔴 Workspace invite flow works end-to-end (invite sent → email received → user joins)
- [ ] 🔴 No raw stack traces or unhandled errors visible to end users
- [ ] 🔴 No production secrets or real credentials visible in any UI state

### Soft checks 🟡

- [ ] 🟡 Firebase end-to-end test passed, OR Firebase is explicitly listed as "in QA" in known limitations
- [ ] 🟡 Supabase end-to-end test passed, OR listed as in QA
- [ ] 🟡 Stripe end-to-end test passed, OR listed as in QA
- [ ] 🟡 Vercel end-to-end test passed, OR listed as in QA
- [ ] 🟡 Empty states are friendly and instructive (not blank pages)
- [ ] 🟡 Error states show human-readable messages (not raw HTTP codes)
- [ ] 🟡 Loading states visible on Dashboard, Timeline, Resources
- [ ] 🟡 Mobile viewport (375px) is usable — no horizontal overflow on core pages

---

## 2. Security and trust readiness

### Hard gates 🔴

- [ ] 🔴 No real credentials, API keys, or secret values visible in any UI
- [ ] 🔴 No S3 object data, Firestore document data, database rows, or user PII accessible via ConfigTrace UI
- [ ] 🔴 `data-access.html` (in-app Settings → Workspace → Data Access) accurately reflects what ConfigTrace reads
- [ ] 🔴 Public docs Data Access page (`/docs/data-access.html`) is accurate and matches in-app page
- [ ] 🔴 Billing RBAC enforced: non-admin/non-owner users cannot access billing settings
- [ ] 🔴 Members RBAC enforced: Member-role users cannot manage other members

### Soft checks 🟡

- [ ] 🟡 All provider connections use encrypted credential storage (confirm no plaintext)
- [ ] 🟡 Audit log captures member invites, integration creates/deletes, billing events
- [ ] 🟡 Session management works correctly (sign-out clears session)

---

## 3. Docs readiness

### Hard gates 🔴

- [ ] 🔴 Docs homepage (`configtrace.org/docs.html`) loads correctly
- [ ] 🔴 Getting started guide (`/docs/getting-started.html`) is accurate and complete
- [ ] 🔴 Data Access & Permissions page (`/docs/data-access.html`) is accurate
- [ ] 🔴 At least 3 provider setup guides reviewed for accuracy (recommend: AWS, Cloudflare, GitHub)
- [ ] 🔴 Troubleshooting page includes the most common support issues

### Soft checks 🟡

- [ ] 🟡 All 7 provider setup guides reviewed for accuracy
- [ ] 🟡 IAM policy JSON in AWS docs reflects current required permissions
- [ ] 🟡 No broken internal links in any docs page
- [ ] 🟡 Docs are mobile-readable at 375px

---

## 4. Billing readiness

### Hard gates 🔴

- [ ] 🔴 Billing page loads and shows correct plan + usage for the workspace
- [ ] 🔴 Free plan limits enforced (3 integrations, 1 member)
- [ ] 🔴 Over-limit state shows correctly when limits are hit
- [ ] 🔴 Non-admin users see a permissions message, not a 403 error

### Soft checks 🟡

- [ ] 🟡 Stripe checkout flow initiates correctly (if Stripe price IDs are configured)
- [ ] 🟡 Stripe billing portal opens for paid plan users
- [ ] 🟡 Plan upgrade flow tested end-to-end at least once (test mode OK)
- [ ] 🟡 Trial start/end events appear in the audit log if applicable

---

## 5. Support readiness

### Hard gates 🔴

- [ ] 🔴 A support contact method is documented (email at minimum)
- [ ] 🔴 Fallback invite link works (for users who don't receive invite email)
- [ ] 🔴 Known limitations are documented in `known-limitations.md` and reviewed

### Soft checks 🟡

- [ ] 🟡 Troubleshooting page covers the top 3–5 anticipated beta user issues
- [ ] 🟡 A process exists for logging and prioritizing bugs reported by beta users
- [ ] 🟡 Response time expectation set for beta (e.g., "we'll respond within 24 hours")

---

## 6. Demo readiness

### Hard gates 🔴

- [ ] 🔴 Demo script (`demo-script.md`) reviewed and practiced at least once
- [ ] 🔴 A demo workspace exists with plausible data (not real customer data)
- [ ] 🔴 Demo workspace shows at least one high/critical change in the timeline
- [ ] 🔴 Demo environment does not expose real personal emails or credentials

### Soft checks 🟡

- [ ] 🟡 5-minute version of demo can be delivered without referring to the script
- [ ] 🟡 Screenshot checklist completed for marketing/social assets
- [ ] 🟡 Demo works on a screen share setup (Zoom/Meet — verify layout at shared resolution)

---

## 7. Landing page and marketing

### Hard gates 🔴

- [ ] 🔴 `configtrace.org` landing page reflects all 7 live providers
- [ ] 🔴 "7 providers live" badge and hero copy are accurate
- [ ] 🔴 Trust/data minimization section is accurate for each provider
- [ ] 🔴 "Open app" CTA links to `app.configtrace.org`

### Soft checks 🟡

- [ ] 🟡 Landing page loads in under 3 seconds on a standard connection
- [ ] 🟡 No broken sections or layout issues at 375px
- [ ] 🟡 OG / social preview image is set and renders correctly

---

## 8. Known limitations acknowledged

### Hard gates 🔴

- [ ] 🔴 `known-limitations.md` is up to date and reviewed before inviting any beta users
- [ ] 🔴 Beta users will be informed that the product is in private beta and some providers may be in QA
- [ ] 🔴 No feature is being presented as production-ready that hasn't been manually QA'd

---

## Beta launch decision

**Date of this review:**
**Reviewer:**

| Section | Status | Notes |
|---------|--------|-------|
| Product readiness | Pass / Fail / Partial | |
| Security & trust | Pass / Fail / Partial | |
| Docs readiness | Pass / Fail / Partial | |
| Billing readiness | Pass / Fail / Partial | |
| Support readiness | Pass / Fail / Partial | |
| Demo readiness | Pass / Fail / Partial | |
| Landing page | Pass / Fail / Partial | |
| Limitations acknowledged | Pass / Fail | |

**Decision:** Ready for private beta / Not ready — [reason]

**Blocked items (if any):**

**Exceptions accepted (if any):**
