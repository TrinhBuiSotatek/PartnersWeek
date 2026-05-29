# Test Cases — UC-1.11 Purchase Package

**Total test cases:** 45 (GUI: 22, FUNC: 23)
**Platform variant:** web-responsive
**Source UC:** UC-1.11_purchase-package_audited_20260528_v2.md
**Source scenarios:** UC-1.11_purchase-package_scenarios_20260528_v1.md
**Output language:** EN

#### Requirement Traceability Matrix

| AC ID | Acceptance Criteria | Linked Test Cases | Status |
|-------|---------------------|-------------------|--------|
| AC-01 | Display current package with class | TC_001, TC_002 | Covered |
| AC-02 | Display correct pricing table per class | TC_002, TC_040, TC_041 | Covered |
| AC-03 | Display activations count for user's class | TC_004 | Covered |
| AC-04 | Purchase button enabled when 0 activations remaining | TC_005 | Covered |
| AC-05 | Purchase button disabled when activations > 0 | TC_006 | Covered |
| AC-06 | Class 0 sees MSG-25 inline | TC_012 | Covered |
| AC-07 | Checkout order summary display | TC_015 | Covered |
| AC-08 | Total = price × admin-defined activations | TC_017 | Covered |
| AC-09 | Points estimation (10% of ORIGINAL price) | TC_018, TC_032 | Covered |
| AC-10 | Discount section for 2y+ users | TC_020 | Covered |
| AC-11 | Discount: Final = 80%, points = 20% of ORIGINAL price | TC_022, TC_032 | Covered |
| AC-12 | Terms checkbox enables Pay button | TC_025 | Covered |
| AC-13 | Pay button disabled until Terms checked | TC_024 | Covered |
| AC-14 | Stripe success → NFT minted, points distributed | TC_033 | Covered |
| AC-15 | Stripe failure → error, return to checkout | TC_034 | Covered |
| AC-16 | Individual cannot access Purchase Package | TC_037 | Covered |
| AC-17 | Individual purchase → no points to anyone | TC_038, TC_039 | Covered |
| AC-18 | Monetary format (CHF XX'XXX) | TC_044 | Covered |
| AC-19 | Points rounding per BR 05 | TC_042, TC_043 | Covered |

---

## I. Screen: Purchase Package

### I.1. UI/UX verification — Screen: Purchase Package

| TC ID | Test Title | Pre-conditions | Step | Expected Result | Priority |
|-------|-----------|---------------|------|-----------------|----------|
| TC_001 | Verify screen initialization | User is logged in as Company Class 1-7 or Public Figure | Navigate to Purchase Package screen from menu | 1. Screen "Purchase Package" is displayed with "Package Rules" section header visible. 2. "Your current package" label is displayed. 3. User's class is displayed (e.g., "Class 1"). 4. Pricing table shows all class rows with "price of one activation" and "number of distinctions" columns. | High |
| TC_002 | Verify pricing table displays all classes correctly | User on Purchase Package screen | Observe pricing table | Pricing table displays correct data per BR 01: Class 0: custom quote, Class 1: 35'000 / 7, Class 2: 17'000 / 6, Class 3: 7'000 / 5, Class 4: 2'500 / 4, Class 5: 990 / 3, Class 6: 500 / 2, Class 7: 190 / 1, Public Figure: 35'000, Individual: 19 (with note "no points") | High |
| TC_003 | Verify "You will receive [N] activations" displays | User on Purchase Package screen | Observe activations display | "You will receive [N] activations" is displayed where N matches the admin-defined value for user's class (e.g., Class 1: 7, Class 2: 6, etc.) | High |
| TC_004 | Verify Purchase Package button is enabled when activations remaining = 0 | User is logged in with 0 activations remaining | Observe "Purchase Package" button | Button "Purchase Package" is enabled (clickable) | High |
| TC_005 | Verify Purchase Package button is disabled when activations remaining > 0 | User is logged in with activations remaining (> 0) | Observe "Purchase Package" button | Button "Purchase Package" is disabled (not clickable) | High |
| TC_006 | Verify Important Notes section is visible | User on Purchase Package screen | Observe Important Notes section | "Important Notes" section header is visible with content below | Medium |
| TC_007 | Verify responsive layout at desktop (1280px) | User on Purchase Package screen at 1280px viewport | Resize browser to 1280px width | Layout displays correctly: pricing table, button, and Important Notes section are properly laid out without horizontal scroll | Medium |
| TC_008 | Verify responsive layout at tablet (768px) | User on Purchase Package screen at 768px viewport | Resize browser to 768px width | Layout reflows correctly: elements adapt to narrower screen without clipping | Medium |
| TC_009 | Verify responsive layout at mobile (375px) | User on Purchase Package screen at 375px viewport | Resize browser to 375px width | Layout displays in stacked format: pricing table and button are readable, touch targets are adequate (≥44px) | Medium |

### I.2. Functional verification — Screen: Purchase Package

| TC ID | Test Title | Pre-conditions | Step | Expected Result | Priority |
|-------|-----------|---------------|------|-----------------|----------|
| TC_010 | Verify user navigates to Purchase Package from menu | User is logged in | Click on "Purchase Package" menu item | System navigates to Purchase Package screen and displays correctly | High |
| TC_011 | Verify Class 0 sees MSG-25 when clicking Purchase Package | User is logged in as Class 0 with 0 activations remaining | 1. On Purchase Package screen, click "Purchase Package" button | 1. Inline message displays: "Class 0: Please state your purchase intentions via contact@partnersweek.com" (MSG-25). 2. Checkout screen does NOT open. | High |
| TC_012 | Verify non-Class 0 user proceeds to Checkout | User is logged in as Class 1-7 or Public Figure with 0 activations remaining | Click "Purchase Package" button | System navigates to Checkout screen | High |
| TC_013 | Verify Individual cannot access Purchase Package | User is logged in as Individual | Attempt to navigate to Purchase Package screen | Purchase Package screen is NOT accessible OR displays no package options. Individual can only purchase distinction Bridge via UC-1.5 | High |

---

## II. Screen: Checkout

### II.1. UI/UX verification — Screen: Checkout

| TC ID | Test Title | Pre-conditions | Step | Expected Result | Priority |
|-------|-----------|---------------|------|-----------------|----------|
| TC_014 | Verify screen initialization | User navigated to Checkout from Purchase Package | Observe Checkout screen | 1. Screen title "Checkout" is displayed. 2. Subtitle "Review and complete your purchase" is displayed. 3. "Back" button is visible. | High |
| TC_015 | Verify Order Summary section displays | User on Checkout screen | Observe Order Summary section | "Order Summary" section header is visible with Package Class pricing table and activation count | High |
| TC_016 | Verify Number of activations displays as admin-defined value (read-only) | User on Checkout screen | Observe Number of activations field | Number of activations displays the admin-defined value for user's class and cannot be modified by user | High |
| TC_017 | Verify Total calculation displays correctly | User on Checkout screen | Observe Total display | Total = price per class × admin-defined activations. Format: CHF XX'XXX (e.g., 35'000, 17'000) per CMR-06 | High |
| TC_018 | Verify Estimated points distributed displays (10% of ORIGINAL price) | User on Checkout screen | Observe points display | "Estimated points distributed" = 10% × package price (ORIGINAL price, before any discount). Example: Class 1 (35'000) → 3'500 points. Label shows "+ 10% points for buyer" | High |
| TC_019 | Verify Discount section visible only for 2y+ users | User is 2y+ (signup >= 2 years) on Checkout | Observe Discount section | "Discount" section is visible with checkbox "You are eligible for a 20% loyalty discount because you have been with PARTNERS WEEK® for more than 2 years. Use X points to apply a 20% discount?" | High |
| TC_020 | Verify Discount section NOT visible for non-2y+ users | User is NOT 2y+ (signup < 2 years) on Checkout | Observe Discount section | "Discount" section is NOT visible | High |
| TC_021 | Verify Discount checkbox is unchecked by default | User is 2y+ on Checkout | Observe Discount checkbox | Discount checkbox is unchecked by default | High |
| TC_022 | Verify Discount calculation - Final = 80%, points = 20% of ORIGINAL | User is 2y+ on Checkout, discount checkbox unchecked | Check discount checkbox | 1. Original price remains displayed. 2. Discount shows equivalent monetary value + points deducted (Original × 20%). 3. "Final amount to pay" = Original × 80%. Example: Class 1 35'000 → Final = 28'000, Discount = 7'000 (700 points) | High |
| TC_023 | Verify Terms checkbox is unchecked by default | User on Checkout | Observe Terms checkbox | "By continuing, you agree to Partners Weeks Terms of Service..." checkbox is unchecked by default | High |
| TC_024 | Verify Pay button is disabled when Terms unchecked | User on Checkout, Terms checkbox unchecked | Observe "Pay" button | "Pay" button is disabled (not clickable) | High |
| TC_025 | Verify Pay button is enabled when Terms checked | User on Checkout, Terms checkbox unchecked | Check Terms checkbox | "Pay" button becomes enabled (clickable) | High |
| TC_026 | Verify Terms of Service link opens in new tab | User on Checkout | Click "Terms of Service" link | Terms of Service document opens in a new browser tab | Medium |
| TC_027 | Verify Privacy Policy link opens in new tab | User on Checkout | Click "Privacy Policy" link | Privacy Policy document opens in a new browser tab | Medium |
| TC_028 | Verify Back button returns to Purchase Package | User on Checkout | Click "Back" button | System returns to Purchase Package screen | High |
| TC_029 | Verify responsive layout at desktop (1280px) | User on Checkout at 1280px viewport | Resize browser to 1280px width | Layout displays correctly: Order Summary, Discount section (if visible), Payment Method section are properly laid out | Medium |
| TC_030 | Verify responsive layout at tablet (768px) | User on Checkout at 768px viewport | Resize browser to 768px width | Layout reflows correctly without horizontal scroll | Medium |
| TC_031 | Verify responsive layout at mobile (375px) | User on Checkout at 375px viewport | Resize browser to 375px width | Layout displays in stacked format, touch targets adequate | Medium |

### II.2. Functional verification — Screen: Checkout

| TC ID | Test Title | Pre-conditions | Step | Expected Result | Priority |
|-------|-----------|---------------|------|-----------------|----------|
| TC_032 | Verify points calculated on ORIGINAL price even with discount applied | User is 2y+ Class 1 (35'000) on Checkout | 1. Check discount checkbox. 2. Note Final amount and points displayed | Final amount = 28'000 (80% of 35'000). BUT Estimated points = 3'500 (10% × 35'000 ORIGINAL), NOT 2'800 (10% × 28'000). Points are ALWAYS based on ORIGINAL price. | High |
| TC_033 | Verify successful Stripe payment | User on Checkout with Terms checked, valid Stripe payment method | Click "Pay" button | 1. Stripe processes payment. 2. NFT minted for buyer. 3. Points distributed: 10% to buyer, 10% to pool, 20 per partner. 4. User redirected to success state. | High |
| TC_034 | Verify Stripe payment declined | User on Checkout with Terms checked, invalid/declined Stripe card | Click "Pay" button | 1. Stripe shows decline error message. 2. User returns to Checkout screen. 3. No state change: no NFT minted, no points deducted. | High |
| TC_035 | Verify Pay button shows loading state during Stripe processing | User on Checkout with Terms checked | Click "Pay" button | "Pay" button displays loading/spinner state while Stripe processes. After completion, button returns to normal state. | Medium |
| TC_036 | Verify double-click on Pay button processes only one payment | User on Checkout with Terms checked | Double-click "Pay" button quickly | System prevents duplicate payment - only ONE payment is processed | High |
| TC_037 | Verify Individual purchasing distinction Bridge (UC-1.5) - no points awarded to buyer | User is logged in as Individual | Complete purchase of distinction Bridge via UC-1.5 | No points are awarded to the Individual buyer (BR 01 exception: "no points are awarded to individuals") | High |
| TC_038 | Verify Individual purchase - no points awarded to anyone | User is Individual, purchases distinction Bridge via UC-1.5 | After successful purchase | Neither 10% to Individual buyer, nor 10% to partner B, nor 10% to PARTNERS WEEK pool is awarded | High |
| TC_039 | Verify Company Class 1-7 pricing displays correctly | User is Company Class 1-7 on Purchase Package | Observe pricing table | Class 1: 35'000, Class 2: 17'000, Class 3: 7'000, Class 4: 2'500, Class 5: 990, Class 6: 500, Class 7: 190 | High |
| TC_040 | Verify Public Figure pricing at 35'000 (same as Class 1) | User is Public Figure on Purchase Package | Observe pricing table | Public Figure price = 35'000 (same as Class 1 per BR 01) | High |
| TC_041 | Verify points rounding for 35'000 CHF package | User is Class 1 on Checkout | Observe points display | 10% of 35'000 = 3'500 points. Displayed as 3'500 (rounded to nearest whole number per BR 05) | Medium |
| TC_042 | Verify points rounding for 990 CHF package | User is Class 5 on Checkout | Observe points display | 10% of 990 = 99 points. Last digit = 9, rounds up per BR 05 rule 2 → Displayed as 99 points | Medium |
| TC_043 | Verify monetary format with apostrophe separators | User on Checkout | Observe price displays | Prices display with apostrophe as thousands separator: 35'000, 17'000, 7'000, 2'500, 990, 500, 190 (CMR-06 format) | Medium |
| TC_044 | Verify browser back button navigation from Checkout | User on Checkout | Press browser Back button | System navigates back to Purchase Package screen | Medium |
| TC_045 | Verify Points display when 2y+ user has discount applied | User is 2y+ Class 1 (35'000) on Checkout with discount | Observe points display | Final amount = 28'000 CHF, but Estimated points = 3'500 (10% × 35'000 ORIGINAL), NOT 2'800. Points always based on ORIGINAL package price. | High |

---

## ⚠️ Out-of-Scope Flags

| Area | Reason | Recommended Action |
|------|--------|-------------------|
| Performance load testing | Not in UC scope | N/A |
| Security beyond functional auth | Not in UC scope | N/A |
| NFT minting blockchain details | Payment gateway integration only in UC scope | N/A |
| Stripe webhook handling edge cases | Only basic decline scenario in UC | N/A |
| Refund flow | Explicitly out of scope | N/A |
| Package upgrade/downgrade | Explicitly out of scope | N/A |
| Individual purchasing package | Individual cannot purchase package (only distinction Bridge via UC-1.5) | N/A |