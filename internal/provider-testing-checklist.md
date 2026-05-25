# ConfigTrace — Provider Testing Checklists

> **Scope:** End-to-end testing of each provider integration
> **Use:** Run after any provider connector change, before private beta, or during a scheduled QA session
> **Note:** Use real (but non-production) credentials where possible. Never use production AWS root keys, live Stripe keys, or customer-facing GitHub repos for QA.

---

## Setup notes

- Use a dedicated QA workspace separate from any live/demo workspace
- Log all failures in `bug-bash-template.md`
- A provider is QA-complete when all items in its section are checked Pass
- "Skip" is acceptable for sub-features not yet implemented, but note the reason

---

## AWS

> AWS is the broadest integration. Test methodically.

### Connection

| # | Test | Expected | Result |
|---|------|----------|--------|
| A1 | Connect with valid read-only IAM credentials (Key ID + Secret + Region) | Integration saved, status Active | ☐ |
| A2 | Connect with invalid Access Key ID | Clear error message, integration not saved | ☐ |
| A3 | Connect with valid Key ID but wrong Secret | Auth error message, integration not saved | ☐ |
| A4 | Connect with credentials that have no permissions attached | Specific permissions error (not a 500) | ☐ |
| A5 | Connect with credentials that have partial permissions (e.g., EC2 only, no IAM) | Sync partially succeeds, error noted for missing services | ☐ |

### Sync

| # | Test | Expected | Result |
|---|------|----------|--------|
| A6 | Trigger manual Sync Now | Sync completes, timeline entry created | ☐ |
| A7 | First sync creates baseline | Timeline shows "Baseline created", resources populated | ☐ |
| A8 | Second sync with no changes | Timeline shows "No changes detected" | ☐ |
| A9 | Scheduled sync runs (verify after plan's sync interval) | New timeline entry created automatically | ☐ |

### Resources

| # | Test | Expected | Result |
|---|------|----------|--------|
| A10 | Resources page shows EC2 security groups | Security group names, IDs, and rules visible | ☐ |
| A11 | Resources page shows IAM policies | Policy names visible; no password or key values | ☐ |
| A12 | Resources page shows Route 53 records (if present) | Record types, names, values visible | ☐ |
| A13 | Resources page shows S3 bucket configuration (if present) | Bucket names, policy status visible; no object data | ☐ |
| A14 | RDS/CloudTrail/GuardDuty resources appear if in monitored surfaces | Visible in resources list | ☐ |

### Change detection

| # | Test | Expected | Result |
|---|------|----------|--------|
| A15 | Modify an EC2 security group rule (add/change inbound rule on a test SG) | Change detected on next sync, risk level appropriate | ☐ |
| A16 | Change detail for security group rule change | Shows old rule, new rule, risk badge, risk reason | ☐ |
| A17 | Delete a security group inbound rule | Change detected as removal, risk assessed | ☐ |
| A18 | Modify a Route 53 record value (test zone only) | DNS change detected, risk level appropriate | ☐ |
| A19 | Attach/modify an IAM policy (safe test — on a non-critical test role) | Change detected if within monitored surfaces | ☐ |

### Data access boundaries

| # | Test | Expected | Result |
|---|------|----------|--------|
| A20 | Resources view contains no S3 object contents | No bucket data visible, only configuration metadata | ☐ |
| A21 | Resources view contains no CloudWatch log event content | No log data visible | ☐ |
| A22 | Secrets Manager or SSM Parameter values not visible | No secret values in any resource or change detail | ☐ |
| A23 | IAM user passwords not exposed | No password fields visible anywhere | ☐ |

### Error handling

| # | Test | Expected | Result |
|---|------|----------|--------|
| A24 | Revoke the IAM key after connecting, then sync | Sync fails with a clear credentials error, not silent failure | ☐ |
| A25 | Remove a specific permission from the IAM policy, then sync | Sync shows which resource type failed due to missing permission | ☐ |

---

## Firebase

### Connection

| # | Test | Expected | Result |
|---|------|----------|--------|
| FB1 | Connect with a valid service account JSON | Integration saved, status Active | ☐ |
| FB2 | Connect with malformed/truncated JSON | Clear parse error, integration not saved | ☐ |
| FB3 | Connect with a service account missing Firebase Viewer role | Permission error on first sync | ☐ |

### Sync

| # | Test | Expected | Result |
|---|------|----------|--------|
| FB4 | Trigger manual Sync Now | Sync completes, resources populated | ☐ |
| FB5 | First sync creates baseline snapshot | Firestore rules, Storage rules, Auth config visible | ☐ |

### Resources

| # | Test | Expected | Result |
|---|------|----------|--------|
| FB6 | Firestore security rules appear in resources | Rule text visible (e.g., `allow read: if request.auth != null`) | ☐ |
| FB7 | Firebase Storage rules appear | Rule text visible | ☐ |
| FB8 | Auth configuration visible | Sign-in providers, authorized domains visible | ☐ |
| FB9 | Firebase Hosting config visible (if project uses hosting) | Hosting settings visible | ☐ |
| FB10 | Cloud Functions metadata visible (names, not code) | Function names and triggers visible; no source code | ☐ |

### Change detection

| # | Test | Expected | Result |
|---|------|----------|--------|
| FB11 | Modify Firestore rules (test project only) | Change detected on next sync | ☐ |
| FB12 | Change detail for Firestore rule change | Old rule, new rule, risk level, risk reason all visible | ☐ |
| FB13 | Change rules to allow public access (`if true`) | Classified as critical risk | ☐ |
| FB14 | Add or remove an authorized domain in Auth | Change detected | ☐ |

### Data access boundaries

| # | Test | Expected | Result |
|---|------|----------|--------|
| FB15 | No Firestore document contents in resources or change details | No user data visible | ☐ |
| FB16 | No Firebase Auth user records visible | No user emails, UIDs, or auth tokens visible | ☐ |
| FB17 | No Storage file contents visible | No file data or URLs to file contents visible | ☐ |

---

## Supabase

### Connection

| # | Test | Expected | Result |
|---|------|----------|--------|
| SB1 | Connect with valid access token + project ref | Integration saved, status Active | ☐ |
| SB2 | Connect with expired or invalid access token | Clear auth error, integration not saved | ☐ |
| SB3 | Connect with correct token but wrong project ref | Project not found error, clear message | ☐ |

### Sync

| # | Test | Expected | Result |
|---|------|----------|--------|
| SB4 | Trigger manual Sync Now | Sync completes, resources visible | ☐ |
| SB5 | RLS policies appear in resources | Policy names, tables, commands, and expressions visible | ☐ |

### Resources

| # | Test | Expected | Result |
|---|------|----------|--------|
| SB6 | RLS policy expressions visible | Policy SQL text like `using (auth.uid() = user_id)` visible | ☐ |
| SB7 | Auth configuration visible | OAuth providers, redirect URLs, JWT settings | ☐ |
| SB8 | Storage bucket metadata visible | Bucket names, public/private status visible | ☐ |
| SB9 | Edge Function metadata visible | Names, status visible; no function source code | ☐ |

### Change detection

| # | Test | Expected | Result |
|---|------|----------|--------|
| SB10 | Disable RLS on a test table | Change detected, classified as high or critical | ☐ |
| SB11 | Modify an RLS policy expression (test table) | Change detected, old and new policy text visible in diff | ☐ |
| SB12 | Add or remove an auth OAuth provider | Change detected | ☐ |

### Data access boundaries

| # | Test | Expected | Result |
|---|------|----------|--------|
| SB13 | No table row data visible in resources or change details | No customer data visible | ☐ |
| SB14 | No auth user records visible | No user emails, sessions, or tokens visible | ☐ |
| SB15 | Service role key value not exposed | Key metadata only (name/ID), not the key value | ☐ |

---

## Stripe

### Connection

| # | Test | Expected | Result |
|---|------|----------|--------|
| ST1 | Connect with a valid restricted read-only API key (`rk_test_…`) | Integration saved, status Active | ☐ |
| ST2 | Connect with an invalid key | Clear auth error, integration not saved | ☐ |
| ST3 | Connect with a live key in test environment | Integration connects (note: monitor whether live data appears) | ☐ |

### Sync

| # | Test | Expected | Result |
|---|------|----------|--------|
| ST4 | Trigger manual Sync Now | Sync completes, webhook endpoints and products visible | ☐ |
| ST5 | Webhook endpoints appear in resources | URLs, enabled status, subscribed events visible | ☐ |
| ST6 | Products and prices appear in resources | Names, amounts, currencies visible | ☐ |

### Change detection

| # | Test | Expected | Result |
|---|------|----------|--------|
| ST7 | Add a new webhook endpoint in Stripe dashboard | Change detected on next sync | ☐ |
| ST8 | Disable an existing webhook endpoint | Change detected, risk level appropriate | ☐ |
| ST9 | Change a webhook URL (test endpoint) | Change detected, old URL and new URL visible in diff | ☐ |

### Data access boundaries

| # | Test | Expected | Result |
|---|------|----------|--------|
| ST10 | No customer records or payment data visible | No card numbers, bank details, or customer PII | ☐ |
| ST11 | API key values not exposed | Only key metadata (name, created date), not actual key value | ☐ |
| ST12 | Webhook signing secrets not exposed | Secret not visible in resources or change details | ☐ |

---

## GitHub

### Connection

| # | Test | Expected | Result |
|---|------|----------|--------|
| GH1 | Connect with a valid PAT + `owner/repo` | Integration saved, status Active | ☐ |
| GH2 | Connect with an expired or invalid PAT | Clear auth error, integration not saved | ☐ |
| GH3 | Connect with a PAT missing the `repo` scope | Permissions error on first sync or during connection | ☐ |
| GH4 | Connect with a private repo the PAT can't access | Access error, clear message | ☐ |

### Sync

| # | Test | Expected | Result |
|---|------|----------|--------|
| GH5 | Trigger manual Sync Now | Sync completes, branch protection rules visible | ☐ |
| GH6 | Branch protection rules visible | Protected branches listed with rule details | ☐ |
| GH7 | Webhooks visible | Endpoint URLs, event subscriptions, active status | ☐ |
| GH8 | Actions secrets metadata visible | Secret names and created dates visible; no values | ☐ |
| GH9 | Actions variables visible | Names and values visible | ☐ |
| GH10 | Deploy keys visible | Key names and read/write access level visible | ☐ |

### Change detection

| # | Test | Expected | Result |
|---|------|----------|--------|
| GH11 | Disable a branch protection rule (test repo) | Change detected, classified as high risk | ☐ |
| GH12 | Remove a required reviewer from branch protection | Change detected, risk level appropriate | ☐ |
| GH13 | Add a new webhook to the repo | Change detected | ☐ |
| GH14 | Change repo visibility (private → public on test repo, if safe) | Change detected, classified as critical | ☐ |

### Data access boundaries

| # | Test | Expected | Result |
|---|------|----------|--------|
| GH15 | No source code or file contents visible | File tree or code not present in resources | ☐ |
| GH16 | No commit history visible | Commit hashes/messages not shown | ☐ |
| GH17 | No Actions secret values exposed | Only secret names visible | ☐ |
| GH18 | No pull request content visible | PR titles, descriptions, or comments not shown | ☐ |

---

## Cloudflare

### Connection

| # | Test | Expected | Result |
|---|------|----------|--------|
| CF1 | Connect with a valid scoped API token + Zone ID | Integration saved, status Active | ☐ |
| CF2 | Connect with an invalid API token | Clear auth error, integration not saved | ☐ |
| CF3 | Connect with a valid token but wrong Zone ID | Zone not found error, clear message | ☐ |
| CF4 | Connect with a token that has Edit (not Read) permissions | Should work (read is a subset of edit), but note in QA | ☐ |

### Sync

| # | Test | Expected | Result |
|---|------|----------|--------|
| CF5 | Trigger manual Sync Now | Sync completes, DNS records visible | ☐ |
| CF6 | All record types present (A, AAAA, CNAME, MX, TXT, NS) | All record types in the zone appear | ☐ |
| CF7 | TTL and proxy status visible per record | `ttl` and `proxied` fields visible for each record | ☐ |

### Change detection

| # | Test | Expected | Result |
|---|------|----------|--------|
| CF8 | Add a new DNS record (test subdomain) | Change detected on next sync | ☐ |
| CF9 | Change a CNAME target | Change detected, old and new content visible in diff | ☐ |
| CF10 | Delete a DNS record | Deletion detected, classified as high or critical | ☐ |
| CF11 | Toggle proxy status on a record | Change detected | ☐ |
| CF12 | Change TTL value on a record | Change detected | ☐ |

### Data access boundaries

| # | Test | Expected | Result |
|---|------|----------|--------|
| CF13 | No traffic/visitor data visible | No analytics or request log data | ☐ |
| CF14 | No Workers script code visible | Script names only if monitored, not code | ☐ |

---

## Vercel

### Connection

| # | Test | Expected | Result |
|---|------|----------|--------|
| VC1 | Connect with a valid API token + project name/ID | Integration saved, status Active | ☐ |
| VC2 | Connect with an invalid token | Clear auth error, integration not saved | ☐ |
| VC3 | Connect with a valid token but nonexistent project | Project not found error, clear message | ☐ |

### Sync

| # | Test | Expected | Result |
|---|------|----------|--------|
| VC4 | Trigger manual Sync Now | Sync completes, project settings and domains visible | ☐ |
| VC5 | Project settings visible | Framework, build command, output directory visible | ☐ |
| VC6 | Custom domains visible | Domain names and redirect config visible | ☐ |
| VC7 | Environment variable names visible (not values) | Names and target environments (prod/preview/dev) visible | ☐ |

### Change detection

| # | Test | Expected | Result |
|---|------|----------|--------|
| VC8 | Add a new environment variable (test project) | Change detected on next sync | ☐ |
| VC9 | Remove an environment variable | Deletion detected | ☐ |
| VC10 | Add or remove a custom domain | Change detected | ☐ |
| VC11 | Change deployment protection settings | Change detected if within monitored surfaces | ☐ |

### Data access boundaries

| # | Test | Expected | Result |
|---|------|----------|--------|
| VC12 | No environment variable values visible | Only names and target environments; no values shown | ☐ |
| VC13 | No build logs or runtime logs visible | No log output in resources or change details | ☐ |
| VC14 | No deployed code or function source code visible | No code in any resource view | ☐ |

---

## Cross-provider

| # | Test | Expected | Result |
|---|------|----------|--------|
| XP1 | Multiple providers active in one workspace | Timeline interleaves changes from all providers correctly | ☐ |
| XP2 | Dashboard summary reflects all providers | All connected providers shown with their last sync | ☐ |
| XP3 | Resources page with multiple providers | Filter by provider works, all resources visible | ☐ |
| XP4 | Timeline filter by provider works cross-workspace | Correct provider's entries shown | ☐ |

---

## QA session log

**Date:**
**Providers tested:**
**Tester:**
**Workspace used:**
**Issues found:** (link to bug-bash-template.md entries)
