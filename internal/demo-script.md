# ConfigTrace — Founder Demo Script

> **Last updated:** M56.3
> **Audience:** Technical founders, engineering leads, security-minded startup teams
> **Versions:** 5-minute pitch · 15-minute walkthrough

---

## Core narrative

> "Production does not only break because code changes. It breaks because
> *settings drift outside Git* — across AWS, Firebase, Supabase, Stripe, GitHub,
> Cloudflare, and Vercel — and nobody notices until an incident is already in progress."

ConfigTrace is the **security timeline for those settings.**
It tells you what changed, why it matters, and what to check next.

One-sentence category: **"Configuration security monitoring for cloud and SaaS tools."**

Git-history contrast (use this to open any version of the pitch):
**"Your code has Git history. Your production settings do not."**

---

## Positioning (30 seconds)

Use this to open any version of the demo:

> "Production does not only break because code changes. It breaks because settings
> drift outside Git. Your code has Git history — your production settings do not.
>
> DNS records, security group rules, Firestore rules, Stripe webhooks, branch
> protection settings — none of those changes go through Git. None of them have
> history. None of them have a diff. When something breaks, you're debugging blind.
>
> ConfigTrace is the security timeline for those settings.
> A baseline, a diff on every change, and a risk classification so you know which
> changes deserve immediate attention — across AWS, Firebase, Supabase, Stripe,
> GitHub, Cloudflare, and Vercel."

Key phrases to land:
- **"Your code has Git history. Your production settings do not."**
- **"ConfigTrace is the security timeline for configuration drift."**
- **"Configuration security monitoring for cloud and SaaS tools."**
- **"ConfigTrace monitors configuration metadata, not customer data."**
- **"It reads the rules that protect your data — not the data those rules protect."**
- **"It tells you what changed, why it matters, and what to check next."**

---

## 5-Minute Demo

Use for: cold intros, investor calls, conference pitches, first contact with a potential beta user.

### [0:00–0:30] Opening

> "Let me show you what ConfigTrace looks like in practice. I'm going to walk
> you through a production incident scenario."

Set the scene:
> "Imagine it's 2pm on a Tuesday. Your API starts returning errors. You check
> your code — no deploys in the last 6 hours. So what changed?"

### [0:30–1:30] The timeline

Navigate to the **Timeline** in the sidebar.

> "This is ConfigTrace's Timeline. Every sync across all your connected
> providers shows up here. Each entry shows when the sync ran, what changed,
> and how risky the change was."

Point to a high/critical entry:

> "This sync detected a critical change. Let me open it."

Click into the change detail.

> "You can see exactly what changed — the field, the old value, the new value,
> and when it was detected. No detective work required. The answer was already here."

**Talking point:** *"In a real incident, this is the difference between 3 minutes to root cause and 3 hours."*

### [1:30–2:30] The risk signal

Stay on the change detail. Point to the risk badge.

> "ConfigTrace classifies every change by blast radius — low, medium, high,
> or critical. A changed TXT comment is not the same as an AWS security
> group opened to the world. This one is critical because [explain the specific change]."

> "The risk reason tells you exactly what the risk is — not just that something changed."

### [2:30–3:30] Coverage

Navigate to **Integrations**.

> "ConfigTrace monitors 7 providers right now: AWS, Firebase, Supabase, Stripe,
> GitHub, Cloudflare, and Vercel. Each integration creates a baseline snapshot
> on the first sync. Every sync after that is a diff against the last known state."

**Talking point:** *"These are the settings that most teams have no version history for. ConfigTrace creates that history automatically."*

### [3:30–4:30] Trust / what it doesn't read

> "The most common question is: what does ConfigTrace actually read?
>
> It reads configuration metadata — the rules, policies, and settings that
> control your infrastructure. It never reads Firestore documents, S3 object
> contents, database rows, secret values, or customer data.
>
> For AWS, it reads security group rules and IAM policy documents — not your
> application data or logs.
>
> For Stripe, it reads webhook endpoints and product settings — not payment
> data or customer records."

**Talking point:** *"ConfigTrace is built for metadata, not customer data."*

### [4:30–5:00] Close

> "This is what ConfigTrace does: it gives you a precise, timestamped record
> of every risky configuration change across your infrastructure — so the next
> incident takes minutes to diagnose, not hours.
>
> You can connect your first provider and get a baseline in about 3 minutes."

CTA: `app.configtrace.org`

---

## 15-Minute Demo

Use for: warm/technical audiences, onboarding beta users, recorded walkthroughs.

### [0:00–1:00] Opening + positioning

Use the full positioning statement from above. Ask a qualifying question:

> "Before I jump in — do you currently have any way to track when a Cloudflare
> DNS record or a GitHub branch protection rule changes? Or does that just
> happen invisibly in a dashboard somewhere?"

Let them answer. Confirm the gap. Then:

> "That's exactly what ConfigTrace solves. Let me show you."

---

### [1:00–3:00] Dashboard

Navigate to **Dashboard**.

> "The dashboard is the command center. You can see your connected providers,
> recent sync activity, and high/critical changes across your workspace at a glance."

Point to each section:
- **Connected integrations:** which providers are active and when they last synced
- **Recent risky changes:** a feed of high/critical changes requiring attention
- **Resources:** total resources monitored across providers

> "Everything you need to know at 2am during an incident is visible from here."

---

### [3:00–6:00] Timeline deep dive

Navigate to **Timeline**.

> "The Timeline is the main diagnostic view. Every sync that detected changes
> shows up here with its risk level."

Walk through a few entries:
- A clean/no-changes sync: "This one ran and found nothing. That's the baseline holding steady."
- A medium change: "This one found a medium-risk change — worth reviewing but not urgent."
- A critical change: "This one is critical. Let me open it."

**Open a change detail:**

> "This is what a change detail looks like. You have:
> - The provider and integration it came from
> - The resource that changed
> - The exact field, old value, and new value
> - The timestamp of detection
> - The risk classification and the reason"

**Sample incident to narrate through:**

> "Here's a real scenario. Someone went into the AWS console and modified an
> EC2 security group. They added an inbound rule allowing SSH from 0.0.0.0/0.
> That change wasn't in a pull request, it wasn't in a ticket, it wasn't
> anywhere in Git. But ConfigTrace caught it on the next sync and classified
> it as critical — because opening SSH to the world has obvious blast radius.
>
> Without this, you might not find out until a security audit, or worse,
> an incident."

---

### [6:00–8:00] Resources

Navigate to **Resources**.

> "Resources is the inventory view. Every piece of configuration ConfigTrace
> monitors shows up here — DNS records, security rules, policy documents,
> webhook endpoints. You can filter by provider or resource type."

> "This is useful for audits — you can see at a glance what ConfigTrace
> is watching, confirm coverage, and check current state."

---

### [8:00–10:00] Integrations

Navigate to **Integrations**.

> "Integrations is where you connect providers. We support 7 right now."

Walk through the 7 providers briefly:
- **AWS:** security groups, IAM, Route 53, S3 bucket config
- **Firebase:** Firestore rules, Storage rules, Auth config
- **Supabase:** RLS policies, auth config, storage buckets
- **Stripe:** webhook endpoints, products, API key metadata
- **GitHub:** branch protection, repo settings, webhooks, secrets metadata
- **Cloudflare:** DNS records, TTL, proxy status
- **Vercel:** project settings, env var metadata, custom domains

> "Each integration runs on a sync schedule — hourly on Free, 15 minutes on
> Pro, 5 minutes on Team. You can always trigger a manual sync on demand."

**Talking point:** *"The key thing is that we read only what we need to detect drift — not your application data."*

---

### [10:00–12:00] Workspace / Admin

Navigate to **Settings → Workspace**.

> "Workspace settings cover your team, audit log, and billing."

Show **Members**:
> "You can invite teammates and assign roles — owner, admin, or member.
> Members get read-only access to the timeline and change history."

Show **Audit Log**:
> "The workspace audit log tracks all admin actions — who invited who, when
> integrations were added or removed, billing changes. Useful for compliance
> and incident reviews."

Show **Data Access**:
> "This page shows exactly what ConfigTrace reads from each provider — and
> what it never reads. It's designed to be shareable with your security team
> or anyone who asks about data access."

---

### [12:00–13:30] Docs

Open `configtrace.org/docs.html` in a browser tab.

> "We have public docs for every provider — step-by-step setup guides,
> exact permissions needed, and a Data Access & Permissions reference that
> explains what we read and what we don't.
>
> All the setup guides specify the minimum read-only permissions required.
> No write access is ever needed or requested."

---

### [13:30–15:00] Closing

> "So to summarize what ConfigTrace gives you:
>
> 1. A baseline snapshot of every configuration across 7 providers
> 2. Automatic detection of every change, diffed field-by-field
> 3. Risk classification on every change — low to critical
> 4. A timestamped timeline so 'what changed?' has an answer in seconds
> 5. A trust model built around metadata-only — no customer data, no secret values
>
> The goal is simple: give your team the same visibility into configuration
> that Git gives you for code."

CTA:
> "You can get started at app.configtrace.org. The free plan supports 3
> integrations, and the first sync creates your baseline in under a minute.
> I'd recommend starting with whichever provider you trust least — usually
> AWS or Cloudflare."

---

## Sample incidents for the demo

Use these when a live demo environment isn't showing interesting changes,
or to narrate realistic scenarios:

| Provider | Incident scenario | Risk level |
|----------|-------------------|------------|
| AWS | Security group inbound rule added: port 22 from 0.0.0.0/0 | Critical |
| AWS | IAM policy attached to role granting AdministratorAccess | Critical |
| Firebase | Firestore rules changed to `allow read, write: if true` | Critical |
| Supabase | RLS disabled on `public.orders` table | Critical |
| Stripe | Webhook endpoint URL changed from prod to staging | High |
| Cloudflare | A record deleted for `api.example.com` | Critical |
| GitHub | Branch protection disabled on `main` (required reviews removed) | High |
| Vercel | Production environment variable removed | High |

---

## Common questions and answers

**"What permissions does ConfigTrace need?"**
> Read-only API access. No write permissions. ConfigTrace uses the minimum
> permissions needed to read configuration metadata. Setup guides at
> configtrace.org/docs.html show the exact permissions for each provider.

**"Can you see our customer data?"**
> No. ConfigTrace reads the rules and settings that control your infrastructure —
> not the data those rules protect. It never reads Firestore documents, database
> rows, S3 objects, secret values, or payment data.

**"What happens if my sync fails?"**
> The timeline shows the failure, and you get an error message explaining why.
> Usually a credentials issue — token expired or permissions changed. You can
> update credentials and re-sync immediately.

**"How is this different from AWS Config / CloudTrail?"**
> AWS Config and CloudTrail are AWS-specific and require significant setup.
> ConfigTrace is cross-provider — it covers AWS, Firebase, Supabase, Stripe,
> GitHub, Cloudflare, and Vercel in one unified timeline and risk view.
> It also doesn't require you to set up additional AWS services to use it.

**"Do you support [provider X]?"**
> If it's one of the 7 live providers, yes. Shopify and additional provider
> depth are on the roadmap. We're also planning Slack/webhook alert notifications.

---

## Demo environment checklist

Before running a live demo, confirm:

- [ ] At least 2–3 integrations are active and have synced recently
- [ ] The timeline shows at least one high or critical change
- [ ] At least one change detail looks plausible (not internal test junk)
- [ ] The Resources view shows populated inventory
- [ ] The workspace has a clean name (not "Rohan's test ws 3")
- [ ] You're not logged into an account that shows real customer data or personal emails
- [ ] Billing page shows current plan correctly
- [ ] Docs pages load at configtrace.org/docs.html
