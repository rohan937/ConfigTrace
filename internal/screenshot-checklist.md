# ConfigTrace — Screenshot Checklist

> **Purpose:** Capture clean marketing/demo screenshots for the landing page, docs, social, and investor materials.
> **Before shooting:** Prepare a demo workspace with plausible data. No real customer data, real credentials, or personal accounts.

---

## General rules for all screenshots

- Use a dedicated demo/QA account — not your personal account with real emails visible
- Use a workspace named something clean (e.g., "Acme Corp" or "demo-workspace")
- Use a browser at 1440×900 or 1280×800 — standard for marketing screenshots
- Use a dark-mode browser theme consistent with the app's dark theme
- Remove browser bookmarks bar and extensions from the screenshot
- Avoid showing: personal Gmail addresses, real API key values, real customer names, private repos
- Use placeholder data that looks real but isn't (e.g., `api.example.com`, `example-project`, `acme-corp/api-service`)

---

## Landing Page Screenshots

### LP-1: Hero section
- **Purpose:** Primary marketing hero image, OG image candidate
- **URL:** configtrace.org
- **State:** Full hero section visible — badge, headline, subheading, CTAs, and product mock
- **Show:** "7 providers live" badge, "Know what changed before it becomes an incident" headline, the product mock with Cloudflare/GitHub/Stripe/AWS/Supabase provider chips
- **Avoid:** Any real personal email or account data in the mock
- **Size:** Full-width 1440px, crop tightly above the fold

### LP-2: Provider grid
- **Purpose:** Show the 7-provider coverage story
- **URL:** configtrace.org/#watches
- **State:** Full 7-provider grid visible, all "Live" badges showing
- **Show:** All 7 provider cards with their monitored surfaces
- **Crop:** Just the provider grid section

### LP-3: Trust / data minimization section
- **Purpose:** Trust/security messaging for the sales process
- **URL:** configtrace.org/#trust
- **State:** "Built for metadata, not customer data." heading + 7 provider trust cards
- **Show:** Full section with ✕ does-not-read lists
- **Use for:** Security conversations, onboarding materials

### LP-4: Risk classification section
- **Purpose:** Show the risk signal concept
- **URL:** configtrace.org/#risk
- **State:** 4 risk cards (low/medium/high/critical) with examples
- **Show:** Full risk grid with per-provider examples

---

## Docs Screenshots

### D-1: Docs homepage
- **Purpose:** Show that documentation exists; builds trust
- **URL:** configtrace.org/docs.html
- **State:** Docs homepage loaded — cards visible, provider mini-grid visible
- **Show:** Section cards, provider grid, teams/billing tables
- **Crop:** Above the fold or full page

### D-2: Provider setup guide (recommend AWS or Cloudflare)
- **Purpose:** Show quality of setup documentation
- **URL:** configtrace.org/docs/aws.html or /docs/cloudflare.html
- **State:** Setup guide loaded, IAM policy or token instructions visible
- **Show:** Steps section, code block, reads/never-reads grid
- **Avoid:** Any real account info in the screenshots

### D-3: Data Access & Permissions docs page
- **Purpose:** Trust/compliance screenshot
- **URL:** configtrace.org/docs/data-access.html
- **State:** Full data access page, metadata-first principle section visible
- **Show:** At least 2 provider perm-grids (reads + never-reads)

---

## App Screenshots

### A-1: Dashboard
- **Purpose:** Primary "product in action" shot
- **URL:** app.configtrace.org/dashboard
- **State:** Dashboard loaded with: 3–5 active integrations, at least 1 critical/high change in the recent changes feed, providers showing last sync times
- **Show:** Integration summary, recent risky changes feed, resource count
- **Avoid:** Real personal emails, real API key names that identify the account

### A-2: Timeline — security feed
- **Purpose:** Show the core value prop: a timeline of configuration changes
- **URL:** app.configtrace.org/timeline
- **State:** Timeline loaded with 6–10 sync entries: mix of no-changes, medium, high, and at least 1 critical
- **Show:** Risk level indicators (colored dots/badges), sync metadata, change summaries
- **Crop:** The top 6–8 entries to keep it clean

### A-3: Change detail
- **Purpose:** Show the "what changed" answer — the key product moment
- **URL:** app.configtrace.org/timeline/[change-id]
- **State:** A critical or high change detail open
- **Ideal scenarios to show:**
  - Cloudflare: CNAME rerouted from `prod.vercel.app` to `staging.vercel.app`
  - AWS: Security group inbound rule opened to 0.0.0.0/0
  - GitHub: Branch protection disabled on `main`
- **Show:** Provider badge, resource name, diff (old value/new value), risk badge (CRITICAL or HIGH), risk reason text
- **Avoid:** Real domain names, real resource IDs, personal email as actor

### A-4: Resources inventory
- **Purpose:** Show the breadth of configuration coverage
- **URL:** app.configtrace.org/resources
- **State:** Resources loaded with 20–50+ resources across 2–3 providers
- **Show:** Provider labels, resource types, resource names
- **Avoid:** Real internal resource names that identify your actual infrastructure

### A-5: Integrations marketplace
- **Purpose:** Show that 7 providers are supported
- **URL:** app.configtrace.org/integrations
- **State:** Integrations page with 3–4 providers connected (showing Active status + last sync), remaining providers showing "Connect"
- **Show:** Provider cards in both connected and unconnected state

### A-6: Workspace admin overview
- **Purpose:** Show workspace management capability
- **URL:** app.configtrace.org/settings/workspace
- **State:** Workspace overview page with hub cards visible
- **Show:** Members, Audit Log, Billing, Data Access hub cards

### A-7: Billing page
- **Purpose:** Show pricing/plan context for marketing and sales
- **URL:** app.configtrace.org/settings/workspace/billing
- **State:** Free or Pro plan visible, usage bars populated, plan comparison cards visible
- **Show:** Current plan badge, usage bars with real-looking usage, 3 plan cards
- **Avoid:** Any real billing details, Stripe customer IDs

### A-8: Data Access & Permissions (in-app)
- **Purpose:** In-app trust/privacy reference — useful for security-minded users
- **URL:** app.configtrace.org/settings/workspace/data-access
- **State:** Data Access page loaded with all 7 providers
- **Show:** Reads / does not read columns, at least 3 providers visible

---

## Screenshot log

| ID | Status | Date | Notes |
|----|--------|------|-------|
| LP-1 | ☐ | | |
| LP-2 | ☐ | | |
| LP-3 | ☐ | | |
| LP-4 | ☐ | | |
| D-1 | ☐ | | |
| D-2 | ☐ | | |
| D-3 | ☐ | | |
| A-1 | ☐ | | |
| A-2 | ☐ | | |
| A-3 | ☐ | | |
| A-4 | ☐ | | |
| A-5 | ☐ | | |
| A-6 | ☐ | | |
| A-7 | ☐ | | |
| A-8 | ☐ | | |

---

## Demo workspace data setup

Before shooting app screenshots, set up the demo workspace:

1. Create a fresh workspace named `Acme Corp` (or similar generic name)
2. Connect 3–4 integrations with test credentials:
   - Cloudflare (a test zone with placeholder records)
   - GitHub (a public test repo or a private repo with generic name)
   - AWS (a test account with a few security groups and Route 53 records)
3. Run first syncs to create baselines
4. Make a few changes in each provider (modify a DNS record, change a branch protection rule, etc.)
5. Run syncs to capture the changes as timeline entries
6. Verify at least one change appears as Critical and one as High
7. Make sure the workspace has no personal email addresses visible in member lists
