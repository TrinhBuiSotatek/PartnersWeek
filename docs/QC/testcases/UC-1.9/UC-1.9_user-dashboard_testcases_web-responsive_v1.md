# Test Cases — UC-1.9 User Dashboard (New Design)

**Total test cases:** 31 (GUI: 23, FUNC: 8)
**Platform variant:** web-responsive
**Source UC:** UC-1.9_user-dashboard_audited_20260528_v1.md
**Source scenarios:** UC-1.9_user-dashboard_scenarios_20260528_v1.md
**Output language:** EN

#### Requirement Traceability Matrix

| AC ID | Acceptance Criteria | Linked Test Cases | Status |
|-------|---------------------|-------------------|--------|
| AC-01 | User Dashboard displays with correct page title | TC_001, TC_002 | Covered |
| AC-02 | Transaction table shows Date, Name, Type, Price, Status columns | TC_003, TC_004 | Covered |
| AC-03 | Distinction icons display correctly (🥇🏅🌉) | TC_005, TC_006 | Covered |
| AC-04 | Status badges display with correct colors (#ECFDF5, #D97706, #DC2626) | TC_007, TC_008 | Covered |
| AC-05 | All 3 roles can access dashboard | TC_009, TC_010, TC_011 | Covered |
| AC-06 | After successful purchase, transaction appears in dashboard | TC_012, TC_013 | Covered |
| AC-07 | Transaction history sorted by newest first | TC_014 | Covered |
| AC-08 | Empty state: Display "No transactions yet" | TC_015 | Covered |
| AC-09 | Transaction appears within 30 seconds after mint | TC_016 | Covered |
| AC-10 | Click transaction row opens Transaction Details popup | TC_011, TC_012 | Covered |
| AC-11 | Popup displays complete transaction information | TC_013, TC_014, TC_015 | Covered |
| AC-12 | Close popup via X button or click outside | TC_022, TC_023 | Covered |
| AC-13 | Share certificate section with social icons | TC_017, TC_018, TC_019, TC_020, TC_021 | Covered |

---

## I. Screen: User Dashboard (New Design)

### I.1. UI/UX Verification — Screen: User Dashboard (New Design)

| TC ID | Title | Pre-conditions | Test Steps | Expected Result | Priority |
|-------|-------|----------------|------------|-----------------|----------|
| TC_001 | Verify screen initialization — User Dashboard | User successfully logged in (Company/Public Figure/Individual) | 1. Access User Dashboard screen\n2. Verify screen initialization | 2. Display "User Dashboard" screen with all components:\n- Page title: "User Dashboard"\n- Section "Transaction History"\n- Transaction table with 5 columns: Date, Name, Type, Price, Status | P0 |
| TC_002 | Verify page title — "User Dashboard" | User logged in (Company/Public Figure/Individual) | 1. Access User Dashboard screen\n2. Verify page title | 2. Display page title: "User Dashboard" | P0 |
| TC_003 | Verify display of 5 columns in transaction table | User logged in (Company/Public Figure/Individual) | 1. Access User Dashboard screen\n2. Verify table columns | 2. Display all 5 columns:\n- Date (date column)\n- Name (distinction name column)\n- Type (distinction type column)\n- Price (price in CHF column)\n- Status (status column) | P0 |
| TC_004 | Verify column content display | User logged in with transaction history | 1. Access User Dashboard screen\n2. Verify column content | 2. Each column displays correct content:\n- Date: YYYY-MM-DD format\n- Name: distinction name + icon\n- Type: distinction type (Collaboration/Investor/Bridge)\n- Price: price with CHF unit\n- Status: badge with corresponding color | P0 |
| TC_005 | Verify icon display for Collaboration | User logged in with Collaboration transaction | 1. Access User Dashboard screen\n2. Find transaction with type Collaboration\n3. Verify icon display | 3. Icon displayed: 🥇 (gold medal) | P0 |
| TC_006 | Verify icons display for Investor and Bridge | User logged in with Investor and Bridge transactions | 1. Access User Dashboard screen\n2. Find transaction type Investor\n3. Find transaction type Bridge\n4. Verify icons display | 3. Investor icon: 🏅 (medal)\n4. Bridge icon: 🌉 (bridge emoji) | P0 |
| TC_007 | Verify color of Completed badge | User logged in with Completed transaction | 1. Access User Dashboard screen\n2. Find transaction with status Completed\n3. Verify badge color | 3. Badge color: #ECFDF5 (light green) | P0 |
| TC_008 | Verify colors of Pending and Failed badges | User logged in with Pending and Failed transactions | 1. Access User Dashboard screen\n2. Find transaction with status Pending\n3. Find transaction with status Failed\n4. Verify badge colors | 3. Pending badge color: #D97706 (amber/orange)\n4. Failed badge color: #DC2626 (red) | P0 |
| TC_009 | Verify responsive layout at desktop (≥ 1280px) | User logged in (Company/Public Figure/Individual) | 1. Access User Dashboard screen at desktop (1280px)\n2. Verify layout | 2. Layout displays correctly, not broken, all elements visible and properly aligned | P1 |
| TC_010 | Verify responsive layout at tablet (768px) | User logged in (Company/Public Figure/Individual) | 1. Access User Dashboard screen at tablet (768px)\n2. Verify layout | 2. Layout reflows correctly, no horizontal scroll, all elements visible | P1 |

### I.2. UI/UX Verification — Popup: Transaction Details

| TC ID | Title | Pre-conditions | Test Steps | Expected Result | Priority |
|-------|-------|----------------|------------|-----------------|----------|
| TC_011 | Verify click on transaction row opens popup | User logged in with transaction history | 1. Access User Dashboard screen\n2. Click on any transaction row\n3. Observe popup | 3. Popup displays with title "Transaction Details" | P0 |
| TC_012 | Verify popup title — "Transaction Details" | User logged in and popup opened | 1. Click on transaction row\n2. Verify popup title | 2. Title displays: "Transaction Details" | P0 |
| TC_013 | Verify fields in Transaction Details popup | User logged in and popup opened | 1. Click on transaction row\n2. Verify fields in popup | 2. Popup displays all required fields:\n- Package Class\n- Activations Purchased\n- Payment Status | P0 |
| TC_014 | Verify field content in popup | User logged in with transaction having complete data | 1. Click on transaction row\n2. Verify each field's content in popup | 2. Each field displays correct information corresponding to the selected transaction | P0 |
| TC_015 | Verify distinction icon in popup | User logged in and Transaction Details popup opened | 1. Click on transaction row\n2. Verify distinction icon displayed on right side of popup | 2. Distinction icon displays correctly based on type:\n- 🥇 Collaboration\n- 🏅 Investor\n- 🌉 Bridge | P0 |
| TC_016 | Verify "Send NFT" button in popup | User logged in and Transaction Details popup opened | 1. Click on transaction row\n2. Verify "Send NFT" button in popup | 2. "Send NFT" button displays and is in enabled state | P0 |
| TC_017 | Verify "Share certificate" section in popup | User logged in and Transaction Details popup opened | 1. Click on transaction row\n2. Verify "Share certificate" section in popup | 2. "Share certificate" section displays with icons:\n- Facebook\n- X (Twitter)\n- LinkedIn\n- Copy link | P0 |
| TC_018 | Verify click Facebook icon in Share certificate | User logged in and Transaction Details popup opened | 1. Click on transaction row\n2. Click Facebook icon in Share certificate section\n3. Observe behavior | 3. Opens Facebook share window or copies link to clipboard | P1 |
| TC_019 | Verify click X (Twitter) icon in Share certificate | User logged in and Transaction Details popup opened | 1. Click on transaction row\n2. Click X (Twitter) icon in Share certificate section\n3. Observe behavior | 3. Opens X share window or copies link to clipboard | P1 |
| TC_020 | Verify click LinkedIn icon in Share certificate | User logged in and Transaction Details popup opened | 1. Click on transaction row\n2. Click LinkedIn icon in Share certificate section\n3. Observe behavior | 3. Opens LinkedIn share window or copies link to clipboard | P1 |
| TC_021 | Verify click "Copy link" in Share certificate | User logged in and Transaction Details popup opened | 1. Click on transaction row\n2. Click "Copy link" in Share certificate section\n3. Observe behavior | 3. Link copied to clipboard, feedback displayed to user | P1 |
| TC_022 | Verify close popup via X button | User logged in and Transaction Details popup opened | 1. Click on transaction row (opens popup)\n2. Click X button (close) on popup\n3. Observe popup close | 3. Popup closes, return to dashboard screen | P0 |
| TC_023 | Verify close popup via click outside (overlay) | User logged in and Transaction Details popup opened | 1. Click on transaction row (opens popup)\n2. Click on outside area (overlay)\n3. Observe popup | 3. Popup closes, return to dashboard screen | P1 |

### I.3. Functional Verification — Screen: User Dashboard (New Design)

| TC ID | Title | Pre-conditions | Test Steps | Expected Result | Priority |
|-------|-------|----------------|------------|-----------------|----------|
| TC_024 | Verify Individual role accesses dashboard successfully | User logged in with Individual role | 1. Access User Dashboard screen\n2. Verify dashboard displays | 2. Dashboard displays fully, Individual user has access permission | P0 |
| TC_025 | Verify Company role accesses dashboard successfully | User logged in with Company role | 1. Access User Dashboard screen\n2. Verify dashboard displays | 2. Dashboard displays fully, Company user has access permission | P0 |
| TC_026 | Verify Public Figure role accesses dashboard successfully | User logged in with Public Figure role | 1. Access User Dashboard screen\n2. Verify dashboard displays | 2. Dashboard displays fully, Public Figure user has access permission | P0 |
| TC_027 | Verify transaction appears after successful purchase from UC-1.5 | User logged in, completed distinction purchase in UC-1.5 and mint succeeded | 1. Complete distinction purchase in UC-1.5 (mint succeeded)\n2. Access User Dashboard\n3. Verify new transaction appears | 3. New transaction appears in table with complete info: Date, Name, Type, Price, Status | P0 |
| TC_028 | Verify transaction sorting — newest first | User logged in with multiple transactions | 1. Access User Dashboard screen\n2. Verify transaction sorting order | 2. Newest transaction appears at first position (sorted by date descending) | P0 |
| TC_029 | Verify empty state — "No transactions yet" | User logged in with no transactions | 1. Access User Dashboard screen with account having no transactions\n2. Verify screen displays | 2. Display icon and text "No transactions yet" when no transactions exist | P0 |
| TC_030 | Verify transaction appearance timing SLA (30 seconds) | User logged in, completed purchase and mint succeeded | 1. Complete mint successfully in UC-1.5\n2. Start timer\n3. Access User Dashboard and verify transaction appears\n4. Record time from mint success to transaction appearance | 4. Transaction appears on dashboard within 30 seconds after mint success | P0 |
| TC_031 | Verify browser Back button from User Dashboard | User logged in (Company/Public Figure/Individual) | 1. Access User Dashboard screen\n2. Press browser Back button | 2. Return to previous screen (depending on application navigation history) | P2 |

---

## ⚠️ Out-of-Scope Flags

| Scenario Area | Reason | Recommended Action |
|---------------|--------|--------------------|
| Performance load testing | Not in UC scope | N/A |
| Security beyond functional auth | Not in UC scope | N/A |
| Old Design (2 tabs) testing | New Design replaces Old Design | N/A |
