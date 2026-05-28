# Test Cases — UC-1.5 Distinction Browse (New Design)

**Total test cases:** 21 (GUI: 12, FUNC: 9)
**Platform variant:** web-responsive
**Source UC:** UC-1.5_distinction-purchase_audited_20260527_v2.md
**Source scenarios (if any):** N/A
**Output language:** EN

#### Requirement Traceability Matrix

| AC ID | Acceptance Criteria | Linked Test Cases | Status |
|-------|---------------------|-------------------|--------|
| AC-01 | Browse Distinctions Happy Path — User Class 1-6 login → hiển thị 3 distinction types | TC_001, TC_002, TC_003, TC_004, TC_005 | Covered |
| AC-02 | Class 0 Block — User Class 0 click Select → MSG 25, block | TC_006, TC_007 | Covered |
| AC-03 | Individual Bridge Only — User Individual → chỉ Bridge với CHF 19 | TC_008, TC_009 | Covered |
| AC-04 | Individual No Points — Individual mua Bridge → không points cho buyer | TC_010 | Covered |
| AC-05 | Company Mint Success — Recipient nhận 20 points | TC_021 | Covered |
| AC-06 | Activations Remaining Display — X activations, mint xong → X-1 remaining | TC_011, TC_012 | Covered |

---

## I. Screen: Browse Distinctions (New Design)

### I.1. UI/UX Verification — Screen: Browse Distinctions (New Design)

| TC ID | Title | Pre-conditions | Test Steps | Expected Result | Priority |
|-------|-------|----------------|------------|-----------------|----------|
| TC_001 | Verify screen initialization — Browse Distinctions | User has successfully logged in (Class 1-6) | 1. Access the Distinctions screen from menu\n2. Verify screen initialization | 2. Display "Browse Distinctions" screen with all components:\n- Page title: "Browse Distinctions"\n- Subtitle: "Choose a distinction type to recognize your business partners with blockchain-based NFT certificates"\n- "How It Works" section with title and content\n- List of 3 distinction types: Collaboration, Investor, Bridge\n- "Select" button for each distinction type\n- "Important Notes" section\n- Activations remaining count displayed | P0 |
| TC_002 | Verify page title — "Browse Distinctions" | User logged in (Class 1-6) | 1. Access Browse Distinctions screen\n2. Verify page title | 2. Display title: "Browse Distinctions" | P0 |
| TC_003 | Verify subtitle on Browse Distinctions screen | User logged in (Class 1-6) | 1. Access Browse Distinctions screen\n2. Verify subtitle | 2. Display subtitle: "Choose a distinction type to recognize your business partners with blockchain-based NFT certificates" | P0 |
| TC_004 | Verify "How It Works" section display | User logged in (Class 1-6) | 1. Access Browse Distinctions screen\n2. Verify "How It Works" section | 2. Display "How It Works" section with title and content explaining the process (per design) | P0 |
| TC_005 | Verify display of 3 distinction types | User logged in (Class 1-6) | 1. Access Browse Distinctions screen\n2. Verify distinction types list | 2. Display all 3 distinction types:\n- Collaboration\n- Investor\n- Bridge (Best Bridge) | P0 |
| TC_006 | Verify "Select" button when activations remaining > 0 | User logged in (Class 1-6) with activations remaining > 0 | 1. Access Browse Distinctions screen\n2. Verify "Select" button for each distinction type | 2. "Select" button is enabled (clickable) when activations remaining > 0 | P0 |
| TC_007 | Verify "Select" button when activations remaining = 0 | User logged in (Class 1-6) with activations remaining = 0 | 1. Access Browse Distinctions screen\n2. Verify "Select" button for each distinction type | 2. "Select" button is disabled (not clickable) when activations remaining = 0 | P0 |
| TC_008 | Verify "Important Notes" section display | User logged in (Class 1-6) | 1. Access Browse Distinctions screen\n2. Verify "Important Notes" section | 2. Display "Important Notes" section with title and important notices content | P0 |
| TC_009 | Verify activations remaining count display | User logged in (Class 1-6) | 1. Access Browse Distinctions screen\n2. Verify activations remaining count | 2. Display activations remaining count (e.g., "X distinction credit(s) remaining") | P0 |
| TC_010 | Verify responsive layout at desktop (≥ 1280px) | User logged in (Class 1-6) | 1. Access Browse Distinctions screen at desktop (1280px)\n2. Verify layout | 2. Layout displays correctly, not broken, all elements visible and properly aligned | P1 |
| TC_011 | Verify responsive layout at tablet (768px) | User logged in (Class 1-6) | 1. Access Browse Distinctions screen at tablet (768px)\n2. Verify layout | 2. Layout reflows correctly, no horizontal scroll, all elements visible | P1 |
| TC_012 | Verify responsive layout at mobile (375px) | User logged in (Class 1-6) | 1. Access Browse Distinctions screen at mobile (375px)\n2. Verify layout | 2. Layout reflows correctly, tap targets ≥ 44px, no overflow | P1 |

### I.2. Functional Verification — Screen: Browse Distinctions (New Design)

| TC ID | Title | Pre-conditions | Test Steps | Expected Result | Priority |
|-------|-------|----------------|------------|-----------------|----------|
| TC_013 | Verify Class 0 is blocked when clicking Select — displays MSG 25 | User logged in with Class 0 | 1. Access Browse Distinctions screen\n2. Click "Select" button of any distinction type | 2. Display MSG 25: "Class 0 is not allowed to perform this transaction" and do not allow progression to next step | P0 |
| TC_014 | Verify Individual class sees only Bridge distinction at CHF 19 | User logged in with Individual class | 1. Access Browse Distinctions screen\n2. Verify distinction types displayed\n3. Verify price displayed | 2. Display only Bridge distinction (do not display Collaboration or Investor)\n3. Price displayed: CHF 19 | P0 |
| TC_015 | Verify Individual purchasing Bridge does not receive points | User is Individual, logged in | 1. Individual purchases Bridge distinction\n2. Complete purchase\n3. Verify buyer's points balance | 3. Buyer (Individual) does not receive points from this transaction | P0 |
| TC_016 | Verify click Select navigates to Step 2 — Select Recipient | User logged in (Class 1-6) with activations remaining > 0 | 1. Access Browse Distinctions screen\n2. Click "Select" button of any distinction type (e.g., Collaboration) | 2. Navigate to Step 2: Select Recipient screen with selected distinction type | P0 |
| TC_017 | Verify anti-return rule — A already purchased for B this year | Company A purchased distinction for Company B in year 2026 | 1. Company A accesses Browse Distinctions\n2. Select same distinction type as purchased for Company B\n3. Click "Select"\n4. Select Company B as recipient\n5. Click "Continue to Checkout" | 5. Display MSG 28: "Cannot purchase this distinction because a similar transaction already exists this year" | P0 |
| TC_018 | Verify when activations remaining = 0, Select button is disabled | User logged in (Class 1-6) with activations remaining = 0 | 1. Access Browse Distinctions screen\n2. Click "Select" button (disabled) | 2. No action occurs when clicking disabled button | P0 |
| TC_019 | Verify screen reload — data is refreshed | User logged in (Class 1-6) | 1. Access Browse Distinctions screen\n2. Press F5 or Refresh browser\n3. Verify data | 3. Data is refreshed, displaying full distinctions info and activations remaining | P1 |
| TC_020 | Verify browser Back button from Browse Distinctions | User logged in (Class 1-6) | 1. Access Browse Distinctions screen\n2. Press browser Back button | 2. Return to previous screen (depending on application navigation history) | P2 |
| TC_021 | Verify Company mint success — recipient receives 20 points | Company logged in (Class 1-6), selected recipient and completed mint | 1. Company mint distinction for recipient\n2. Mint succeeds\n3. Verify recipient's points balance | 3. Recipient receives 20 points from the mint transaction | P0 |

---

## ⚠️ Out-of-Scope Flags

| Scenario Area | Reason | Recommended Action |
|---------------|--------|--------------------|
| NFT minting integration | No detailed spec for minting flow in UC | Defer to integration testing phase |
| Stripe payment (Old Design) | New document no longer has Stripe — different payment model | N/A — use New Design |
| Year 2+ Discount flow | No spec for anniversary detection | Defer to separate UC |