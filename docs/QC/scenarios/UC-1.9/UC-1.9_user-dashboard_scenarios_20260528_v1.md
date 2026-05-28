# Test Scenarios — UC-1.9 User Dashboard

> Source: docs/QC/uc-read/UC-1.9/UC-1.9_user-dashboard_audited_20260528_v1.md
> Generated: 2026-05-28
> Platform: web-responsive
> Output language: EN

## UC-1.9 — User Dashboard

### Scenario ID: TS_UC-1.9_001
**Scenario Title:** User accesses dashboard and views transaction history
**UC Reference:** UC-1.9 User Dashboard
**Req-ID:** AC-01, AC-02
**Test Type:** Functional
**Description:** User with existing transactions logs in and navigates to User Dashboard to view their transaction history
**Test Focus:** Happy path

### Scenario ID: TS_UC-1.9_002
**Scenario Title:** User views empty state when no transactions exist
**UC Reference:** UC-1.9 User Dashboard
**Req-ID:** AC-08
**Test Type:** Functional
**Description:** User with no transaction history accesses dashboard and sees "No transactions yet" message with icon
**Test Focus:** Happy path

### Scenario ID: TS_UC-1.9_003
**Scenario Title:** Company role accesses dashboard successfully
**UC Reference:** UC-1.9 User Dashboard
**Req-ID:** AC-05
**Test Type:** Functional
**Description:** User logged in as Company role navigates to User Dashboard and can view transactions
**Test Focus:** Permission/Role

### Scenario ID: TS_UC-1.9_004
**Scenario Title:** Public Figure role accesses dashboard successfully
**UC Reference:** UC-1.9 User Dashboard
**Req-ID:** AC-05
**Test Type:** Functional
**Description:** User logged in as Public Figure role navigates to User Dashboard and can view transactions
**Test Focus:** Permission/Role

### Scenario ID: TS_UC-1.9_005
**Scenario Title:** Individual role accesses dashboard successfully
**UC Reference:** UC-1.9 User Dashboard
**Req-ID:** AC-05
**Test Type:** Functional
**Description:** User logged in as Individual role navigates to User Dashboard and can view transactions
**Test Focus:** Permission/Role

### Scenario ID: TS_UC-1.9_006
**Scenario Title:** Transaction appears after successful purchase from UC-1.5
**UC Reference:** UC-1.9 User Dashboard
**Req-ID:** AC-06, AC-09
**Test Type:** Integration
**Description:** After user completes a distinction purchase in UC-1.5, the transaction appears in User Dashboard within 30 seconds
**Test Focus:** Happy path

### Scenario ID: TS_UC-1.9_007
**Scenario Title:** Transaction table displays correct columns
**UC Reference:** UC-1.9 User Dashboard
**Req-ID:** AC-02
**Test Type:** UI
**Description:** Verify transaction table shows all 5 columns: Date, Name, Type, Price, Status
**Test Focus:** Happy path

### Scenario ID: TS_UC-1.9_008
**Scenario Title:** Distinction icons display correctly
**UC Reference:** UC-1.9 User Dashboard
**Req-ID:** AC-03
**Test Type:** UI
**Description:** Verify distinction type icons display correctly: 🥇 Collaboration, 🏅 Investor, 🌉 Bridge
**Test Focus:** Happy path

### Scenario ID: TS_UC-1.9_009
**Scenario Title:** Status badge colors are correct
**UC Reference:** UC-1.9 User Dashboard
**Req-ID:** AC-04
**Test Type:** UI
**Description:** Verify status badges display correct colors: Completed (#ECFDF5), Pending (#D97706), Failed (#DC2626)
**Test Focus:** Happy path

### Scenario ID: TS_UC-1.9_010
**Scenario Title:** Transactions sorted by newest first
**UC Reference:** UC-1.9 User Dashboard
**Req-ID:** AC-07
**Test Type:** Functional
**Description:** Verify transaction list is sorted by date in descending order (newest first)
**Test Focus:** Happy path

### Scenario ID: TS_UC-1.9_011
**Scenario Title:** Dashboard refresh shows updated transactions
**UC Reference:** UC-1.9 User Dashboard
**Req-ID:** AC-06
**Test Type:** Functional
**Description:** User refreshes dashboard page and sees most current transaction list
**Test Focus:** Alternative flow

### Scenario ID: TS_UC-1.9_012
**Scenario Title:** Browser back button navigates correctly
**UC Reference:** UC-1.9 User Dashboard
**Req-ID:** AC-01
**Test Type:** UI
**Description:** User presses browser back button from User Dashboard and navigates to previous screen
**Test Focus:** Alternative flow

### Scenario ID: TS_UC-1.9_013
**Scenario Title:** User accesses dashboard via direct URL
**UC Reference:** UC-1.9 User Dashboard
**Req-ID:** AC-01
**Test Type:** End-to-End
**Description:** User directly navigates to User Dashboard URL without prior navigation and dashboard displays correctly
**Test Focus:** Happy path

### Scenario ID: TS_UC-1.9_014
**Scenario Title:** Multiple transactions display correctly
**UC Reference:** UC-1.9 User Dashboard
**Req-ID:** AC-02, AC-07
**Test Type:** Functional
**Description:** User with 10+ transactions views dashboard and all transactions display correctly with proper sorting
**Test Focus:** Boundary

### Scenario ID: TS_UC-1.9_015
**Scenario Title:** Transaction timing SLA verification
**UC Reference:** UC-1.9 User Dashboard
**Req-ID:** AC-09
**Test Type:** Acceptance
**Description:** Verify transaction appears in dashboard within 30 seconds after successful mint
**Test Focus:** Happy path

### Scenario ID: TS_UC-1.9_016
**Scenario Title:** Page title displays correctly
**UC Reference:** UC-1.9 User Dashboard
**Req-ID:** AC-01
**Test Type:** UI
**Description:** Verify User Dashboard page shows correct title "User Dashboard"
**Test Focus:** Happy path

### Scenario ID: TS_UC-1.9_017
**Scenario Title:** Dashboard responsive layout at desktop (1280px)
**UC Reference:** UC-1.9 User Dashboard
**Req-ID:** AC-01
**Test Type:** UI
**Description:** Verify dashboard layout displays correctly at desktop resolution (1280px)
**Test Focus:** Happy path

### Scenario ID: TS_UC-1.9_018
**Scenario Title:** Dashboard responsive layout at tablet (768px)
**UC Reference:** UC-1.9 User Dashboard
**Req-ID:** AC-01
**Test Type:** UI
**Description:** Verify dashboard layout reflows correctly at tablet resolution (768px)
**Test Focus:** Happy path

### Scenario ID: TS_UC-1.9_019
**Scenario Title:** Dashboard responsive layout at mobile (375px)
**UC Reference:** UC-1.9 User Dashboard
**Req-ID:** AC-01
**Test Type:** UI
**Description:** Verify dashboard layout reflows correctly at mobile resolution (375px)
**Test Focus:** Happy path

---

## ⚠️ Out-of-Scope Flags

| Scenario Area | Reason | Recommended Action |
|---------------|--------|--------------------|
| Performance load testing | Not in UC scope | N/A |
| Security beyond functional auth | Not in UC scope | N/A |
| Old Design (2 tabs) testing | New Design replaces Old Design | N/A |