# ConfigTrace — Manual QA Checklist

> **Scope:** app.configtrace.org — general product QA
> **Use:** Run before a demo, before private beta, or after any significant change
> **Format:** Check each item. Mark P (pass), F (fail), or S (skip/N/A).

---

## How to use this checklist

- Run through each section in order
- For failures, open `bug-bash-template.md` and log the issue
- A "skip" is only acceptable if the feature is genuinely not available in the current environment
- Aim to complete the full checklist in one session before any release or demo

---

## 1. Authentication

| # | Test | Expected result | Result |
|---|------|-----------------|--------|
| 1.1 | Open app.configtrace.org while signed out | Redirected to sign-in page | ☐ |
| 1.2 | Sign in with valid credentials | Lands on Dashboard, workspace loads | ☐ |
| 1.3 | Sign out from the user menu | Redirected to sign-in page, session cleared | ☐ |
| 1.4 | Attempt to access `/dashboard` while signed out | Redirected to sign-in, not a blank page | ☐ |
| 1.5 | Sign in on mobile viewport (375px) | Sign-in page is usable, no layout breaks | ☐ |

---

## 2. Workspace switcher

| # | Test | Expected result | Result |
|---|------|-----------------|--------|
| 2.1 | Open workspace switcher in the sidebar | Dropdown shows all workspaces for the account | ☐ |
| 2.2 | Switch to a different workspace | Page reloads with that workspace's data | ☐ |
| 2.3 | Create a new workspace | New workspace appears and is selected | ☐ |
| 2.4 | Rename a workspace | New name appears in the switcher and page header | ☐ |

---

## 3. Dashboard

| # | Test | Expected result | Result |
|---|------|-----------------|--------|
| 3.1 | Navigate to Dashboard | Page loads without errors | ☐ |
| 3.2 | Dashboard shows connected integrations summary | Provider names, last sync time, status visible | ☐ |
| 3.3 | Recent risky changes feed shows changes | High/critical changes listed with risk level | ☐ |
| 3.4 | Dashboard with zero integrations connected | Empty state shown, not a blank page or error | ☐ |
| 3.5 | Clicking a change on Dashboard | Navigates to the change detail | ☐ |

---

## 4. Timeline

| # | Test | Expected result | Result |
|---|------|-----------------|--------|
| 4.1 | Navigate to Timeline | Page loads, syncs listed in reverse-chronological order | ☐ |
| 4.2 | Timeline shows correct risk level colors (low/medium/high/critical) | Risk levels visually distinct and accurate | ☐ |
| 4.3 | Click a sync entry with changes | Expands or navigates to show the changes | ☐ |
| 4.4 | Timeline with no syncs yet | Empty state shown ("No sync history yet" or similar) | ☐ |
| 4.5 | Timeline pagination (if more than one page of syncs) | Pagination controls work, next page loads | ☐ |
| 4.6 | Filter timeline by provider (if available) | Shows only entries from that provider | ☐ |
| 4.7 | Filter timeline by risk level (if available) | Shows only entries at that risk level | ☐ |
| 4.8 | No-changes sync entry | Shows "No changes detected" clearly | ☐ |

---

## 5. Change Detail

| # | Test | Expected result | Result |
|---|------|-----------------|--------|
| 5.1 | Open a change detail from the timeline | Full diff visible: old value, new value, field name | ☐ |
| 5.2 | Risk badge visible and correct | Risk level badge (low/medium/high/critical) shown | ☐ |
| 5.3 | Risk reason visible | A human-readable explanation of why the change is risky | ☐ |
| 5.4 | Timestamp accurate | Shows the correct sync time | ☐ |
| 5.5 | Provider and integration name visible | Clear which integration the change came from | ☐ |
| 5.6 | "Back to Timeline" or breadcrumb navigation works | Returns to the timeline without losing state | ☐ |
| 5.7 | Change detail for a removed field | Shows old value with deletion indicator, not blank | ☐ |
| 5.8 | Change detail for an added field | Shows new value with addition indicator | ☐ |

---

## 6. Resources

| # | Test | Expected result | Result |
|---|------|-----------------|--------|
| 6.1 | Navigate to Resources | Page loads, resources listed | ☐ |
| 6.2 | Resources show provider labels | Each resource clearly labeled with its provider | ☐ |
| 6.3 | Filter by provider | Shows only resources from that provider | ☐ |
| 6.4 | Filter by resource type (if available) | Shows only that resource type | ☐ |
| 6.5 | Click a resource | Opens detail or expands the resource | ☐ |
| 6.6 | Resources page with zero resources | Empty state shown clearly | ☐ |
| 6.7 | Search/filter resources (if available) | Returns correct results | ☐ |
| 6.8 | Pagination works if resources exceed one page | Loads next page correctly | ☐ |

---

## 7. Integrations

| # | Test | Expected result | Result |
|---|------|-----------------|--------|
| 7.1 | Navigate to Integrations | Page loads, shows all 7 provider cards | ☐ |
| 7.2 | Connect a new integration (use test credentials) | Integration created and appears in the list | ☐ |
| 7.3 | Integration shows last sync time after first sync | Timestamp visible and recent | ☐ |
| 7.4 | Trigger manual "Sync Now" | Sync starts, spinner/status updates, completes | ☐ |
| 7.5 | Sync Now updates last-sync timestamp | Timestamp reflects the new sync | ☐ |
| 7.6 | Delete an integration | Integration removed from list, confirmation prompt shown | ☐ |
| 7.7 | Connect with invalid credentials | Friendly error message, integration not saved | ☐ |
| 7.8 | Integration limit reached (Free plan: 3 max) | Clear limit error shown, upgrade prompt visible | ☐ |
| 7.9 | Integration detail page shows status, resource count | All metadata visible | ☐ |

---

## 8. Members & Invites

| # | Test | Expected result | Result |
|---|------|-----------------|--------|
| 8.1 | Navigate to Settings → Workspace → Members | Page loads, current members listed | ☐ |
| 8.2 | Invite a new member (enter email, select role) | Invite sent, pending invite appears in the list | ☐ |
| 8.3 | Fallback invite link visible | "Copy invite link" available for each pending invite | ☐ |
| 8.4 | Copy invite link copies to clipboard | Clipboard action succeeds, visual confirmation shown | ☐ |
| 8.5 | Revoke a pending invite | Invite removed from list, action confirmed | ☐ |
| 8.6 | Role badges visible for each member | Owner/Admin/Member clearly labeled | ☐ |
| 8.7 | Member limit reached (Free: 1, Pro: 5) | Clear limit error shown with upgrade prompt | ☐ |
| 8.8 | Non-admin user cannot manage members | Manage buttons hidden or disabled for Member role | ☐ |

---

## 9. Audit Log

| # | Test | Expected result | Result |
|---|------|-----------------|--------|
| 9.1 | Navigate to Settings → Workspace → Audit Log | Page loads, events listed | ☐ |
| 9.2 | Events have timestamps, actor, and event type | All columns populated | ☐ |
| 9.3 | Filter by category (All / Members / Billing / Integrations / Workspace) | Shows correct filtered events | ☐ |
| 9.4 | Pagination works (if more than 50 events) | Next/prev page loads correctly | ☐ |
| 9.5 | Empty audit log state | "No audit events recorded yet." shown | ☐ |
| 9.6 | Audit log reflects recent actions | Invite, integration create, etc. appear after performing them | ☐ |

---

## 10. Billing

| # | Test | Expected result | Result |
|---|------|-----------------|--------|
| 10.1 | Navigate to Settings → Workspace → Billing | Page loads, current plan visible | ☐ |
| 10.2 | Usage bars show current integrations and members used | Numbers accurate, bars render | ☐ |
| 10.3 | Plan comparison cards visible | Free / Pro / Team cards shown with limits | ☐ |
| 10.4 | "Upgrade" CTA visible for non-current plans | Upgrade button shown, links to checkout | ☐ |
| 10.5 | "Manage" button for current plan (if paid) | Opens Stripe billing portal | ☐ |
| 10.6 | Non-admin/non-owner user visits Billing | "Owners and admins only" message shown, not 500 error | ☐ |
| 10.7 | Over-limit banner when usage >= limit | Banner shown identifying which limit is hit | ☐ |
| 10.8 | Stripe checkout flow initiates (if configured) | Redirects to Stripe checkout page | ☐ |

---

## 11. Data Access page (in-app)

| # | Test | Expected result | Result |
|---|------|-----------------|--------|
| 11.1 | Navigate to Settings → Workspace → Data Access | Page loads correctly | ☐ |
| 11.2 | All 7 providers listed | AWS, Firebase, Supabase, Stripe, GitHub, Cloudflare, Vercel all shown | ☐ |
| 11.3 | "Reads" column populated per provider | Accurate list of monitored surfaces | ☐ |
| 11.4 | "Does not read" column populated per provider | Clear list of what's excluded | ☐ |

---

## 12. Settings

| # | Test | Expected result | Result |
|---|------|-----------------|--------|
| 12.1 | Navigate to Settings | Page loads, personal settings visible | ☐ |
| 12.2 | Navigate to Settings → Workspace | Workspace overview with hub cards visible | ☐ |
| 12.3 | Hub cards link to Members, Audit Log, Billing, Data Access | All 4 links work | ☐ |
| 12.4 | Workspace rename works | New name persists after page refresh | ☐ |

---

## 13. Email flows

| # | Test | Expected result | Result |
|---|------|-----------------|--------|
| 13.1 | Send a workspace invite | Invitee receives email with working link | ☐ |
| 13.2 | Invite link works when clicked | Opens ConfigTrace, prompts sign-up or sign-in, joins workspace | ☐ |
| 13.3 | High/critical change email alert (if testable) | Email received after a high/critical sync | ☐ |
| 13.4 | Email alerts do not send for low/medium changes | Only high/critical changes trigger alert emails | ☐ |

---

## 14. Empty states

| # | Test | Expected result | Result |
|---|------|-----------------|--------|
| 14.1 | New workspace with no integrations — Dashboard | Empty state message shown, not blank or error | ☐ |
| 14.2 | New workspace with no integrations — Timeline | Empty state with guidance to connect a provider | ☐ |
| 14.3 | New workspace with no integrations — Resources | Empty state shown | ☐ |
| 14.4 | No pending invites — Members page | "No pending invites" shown, not blank | ☐ |
| 14.5 | No audit events — Audit Log | "No audit events recorded yet." shown | ☐ |

---

## 15. Error states

| # | Test | Expected result | Result |
|---|------|-----------------|--------|
| 15.1 | Integration with invalid/expired token | Sync shows error state with readable message, not raw stack | ☐ |
| 15.2 | Permission denied on billing (non-admin) | Friendly "admin only" message, not 403 raw error | ☐ |
| 15.3 | Network error during sync (simulate or wait for) | Error message shown, not blank page or spinner forever | ☐ |
| 15.4 | Invalid invite link (expired or wrong workspace) | Friendly error page or message | ☐ |

---

## 16. Loading states

| # | Test | Expected result | Result |
|---|------|-----------------|--------|
| 16.1 | Initial page load on Dashboard | Loading indicator visible before data appears | ☐ |
| 16.2 | Sync Now button during active sync | Button shows loading/disabled state, not double-triggerable | ☐ |
| 16.3 | Workspace switcher on slow connection | Loading state while switching, no flash of wrong data | ☐ |

---

## 17. Responsive / mobile

| # | Test | Expected result | Result |
|---|------|-----------------|--------|
| 17.1 | Dashboard at 375px width | No horizontal overflow, content readable | ☐ |
| 17.2 | Timeline at 375px width | Timeline entries readable, risk badges visible | ☐ |
| 17.3 | Sidebar at mobile width | Sidebar hidden or collapsed, nav accessible | ☐ |
| 17.4 | Integrations page at mobile width | Provider cards stack, no overflow | ☐ |
| 17.5 | Change detail at mobile width | Diff readable, no horizontal overflow on long values | ☐ |

---

## Summary

| Section | Items | Passed | Failed | Skipped |
|---------|-------|--------|--------|---------|
| Auth | 5 | | | |
| Workspace | 4 | | | |
| Dashboard | 5 | | | |
| Timeline | 8 | | | |
| Change Detail | 8 | | | |
| Resources | 8 | | | |
| Integrations | 9 | | | |
| Members | 8 | | | |
| Audit Log | 6 | | | |
| Billing | 8 | | | |
| Data Access | 4 | | | |
| Settings | 4 | | | |
| Email flows | 4 | | | |
| Empty states | 5 | | | |
| Error states | 4 | | | |
| Loading states | 3 | | | |
| Responsive | 5 | | | |
| **Total** | **102** | | | |

**QA session date:**
**Tester:**
**App version / commit:**
**Overall result:** Pass / Fail / Needs work
