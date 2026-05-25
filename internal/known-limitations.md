# ConfigTrace — Known Limitations

> **Last updated:** M56.3
> **Purpose:** Honest, current record of product constraints.
> **Use:** Read before demos, before beta, and when answering user questions about gaps.

This document reflects the current state of the product. Limitations are tracked here
so they can be communicated clearly rather than discovered mid-demo or during user onboarding.

---

## Product / feature gaps

### Manual QA not complete for all providers

**Detail:** End-to-end manual testing has not been completed for all 7 providers. AWS, Cloudflare, and GitHub have the most validation behind them. Firebase, Supabase, Stripe, and Vercel integrations are built and functional but require a dedicated manual QA pass (see `provider-testing-checklist.md`).

**Impact:** Some edge cases in those connectors may not be caught until beta user testing.

**Mitigation:** Run `provider-testing-checklist.md` for each provider before presenting it to beta users as production-ready.

---

### GitHub App flow not implemented

**Detail:** GitHub connections currently use Personal Access Tokens (PATs). A GitHub App installation flow (OAuth, installable per-organization) has not been built yet.

**Impact:** PAT-based connections require manual token creation, scoped to one repository, and are tied to a user account (not an org). Tokens can expire.

**When asked:** "We currently support PAT-based repository monitoring. A GitHub App installation flow is on the roadmap for broader, permission-scoped access across multiple repos."

---

### Slack and webhook notifications not implemented

**Detail:** High/critical change alerts currently go out via email only. There is no Slack integration, webhook delivery, or PagerDuty routing.

**When asked:** "Email alerts are live. Slack and webhook notifications are coming next."

---

### Change acknowledgment and snooze not implemented

**Detail:** Users cannot mark a change as "reviewed" or "expected" to suppress future alerts for known-good drift. Every change in the timeline requires manual attention or acceptance.

**Impact:** For integrations with frequent expected changes, the timeline can fill with low-signal entries.

**Workaround:** Risk levels (low/medium) separate signal from noise at the alert level. Timeline filtering helps manage volume.

---

### Shopify not supported

**Detail:** Shopify is on the provider roadmap but not implemented.

---

### Audit log filtering is client-side within a loaded page

**Detail:** The Audit Log category filter (All / Members / Billing / Integrations / Workspace) filters the currently loaded page of results client-side. For workspaces with more events than one page (50), filtering across all historical events requires pagination.

**Impact:** Filtered views may miss events on older pages.

**Mitigation:** Backend filtering will replace client-side filtering in a future update.

---

### Resource search is client-side / page-limited

**Detail:** Resource search/filtering operates on the currently loaded set of resources. For workspaces with large resource counts that require pagination, search results may be incomplete.

---

### Additional provider depth deferred

**Detail:** Current provider coverage focuses on the highest-signal configuration surfaces. Several sub-surfaces are planned but not yet implemented:

- AWS: CloudFront distributions, ECS task definitions, Lambda function configuration, KMS key policies
- Firebase: Remote Config, App Check configuration
- Stripe: Customer portal settings, tax settings
- Vercel: Edge config, middleware configuration
- GitHub: Organization-level settings, Actions workflow permissions

---

### Public demo workspace / seeded data not yet created

**Detail:** There is no pre-built demo workspace with seeded plausible data. Demos currently require a live workspace with real (or test) integrations configured.

**Impact:** Demo setup requires manual preparation before each demo session.

**Mitigation:** See `screenshot-checklist.md` for demo workspace setup guidance.

---

### Docs permission policy not fully QA'd against live connectors

**Detail:** The public docs (provider setup guides, data access page) were written based on the connector implementation. Until each provider's manual QA is complete, the exact permissions listed in docs should be considered a best-effort representation. After each manual QA session, update the docs if any permissions listed are inaccurate or incomplete.

---

## Billing limitations

### Stripe billing portal / checkout availability

**Detail:** Billing checkout (upgrade) and billing portal (manage subscription) require Stripe price IDs to be configured server-side. If these are not configured in the deployment environment, the Billing page will show a "Billing is not fully configured" message.

**This is a configuration/deployment concern, not a code bug.** The Billing page handles this case gracefully.

---

## Infrastructure / operational

### No uptime monitoring or public status page

**Detail:** There is no public status page (e.g., status.configtrace.org) and no automated uptime monitoring configured. Beta users experiencing downtime have no self-service status check.

---

### Scheduled sync intervals are plan-gated

**Detail:** Free plan syncs hourly, Pro syncs every 15 minutes, Team syncs every 5 minutes. Users on the Free plan cannot get faster syncs without upgrading.

---

## Out of scope (by design)

These are not bugs or limitations — they are intentional design decisions:

- **ConfigTrace does not read S3 object contents, Firestore documents, database rows, or secret values.** This is architectural, not a gap.
- **ConfigTrace does not perform remediation.** It detects and surfaces drift. Fixing it is always the user's responsibility.
- **ConfigTrace does not track Git commits.** Git already does that. ConfigTrace tracks the configuration that lives outside version control.
- **ConfigTrace does not store full audit trails of changes made via dashboards** (e.g., who in AWS made a change). It detects *what* changed, not the actor behind the change in external systems.

---

## Changelog

| Date | Update |
|------|--------|
| M56.3 | Initial version created |
