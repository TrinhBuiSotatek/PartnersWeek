# Test Scenarios — UC-1.11 Purchase Package

> Source: docs/QC/uc-read/UC-1.11/UC-1.11_purchase-package_audited_20260528_v2.md
> Generated: 2026-05-28
> Platform: web-responsive
> Output language: EN

## UC-1.11 — Purchase Package

### Scenario ID: TS_UC-1.11_001
**Scenario Title:** User navigates to Purchase Package and sees current class pricing
**UC Reference:** UC-1.11 Purchase Package
**Req-ID:** AC-01, AC-02
**Test Type:** UI
**Description:** User navigates to Purchase Package screen; system displays "Your current package" label with user's class and correct pricing table from BR 01
**Test Focus:** Happy path

### Scenario ID: TS_UC-1.11_002
**Scenario Title:** User sees correct activations count for their class
**UC Reference:** UC-1.11 Purchase Package
**Req-ID:** AC-03
**Test Type:** UI
**Description:** User on Purchase Package screen; system displays "You will receive [N] activations" where N matches the user's class from the pricing table
**Test Focus:** Happy path

### Scenario ID: TS_UC-1.11_003
**Scenario Title:** Purchase button enabled when user has 0 activations remaining
**UC Reference:** UC-1.11 Purchase Package
**Req-ID:** AC-04
**Test Type:** UI
**Description:** User has 0 activations remaining; Purchase Package button is enabled and clickable
**Test Focus:** Happy path

### Scenario ID: TS_UC-1.11_004
**Scenario Title:** Purchase button disabled when user has activations remaining
**UC Reference:** UC-1.11 Purchase Package
**Req-ID:** AC-05
**Test Type:** UI
**Description:** User has activations remaining (> 0); Purchase Package button is disabled
**Test Focus:** Alternative flow

### Scenario ID: TS_UC-1.11_005
**Scenario Title:** Class 0 user sees MSG-25 and cannot proceed to checkout
**UC Reference:** UC-1.11 Purchase Package
**Req-ID:** AC-06
**Test Type:** Error/Exception
**Description:** User is Class 0 and clicks Purchase Package button; system displays inline message "Class 0: Please state your purchase intentions via contact@partnersweek.com" (MSG-25); checkout does not open
**Test Focus:** Error/Exception

### Scenario ID: TS_UC-1.11_006
**Scenario Title:** Number of activations is set by admin per class/role
**UC Reference:** UC-1.11 Purchase Package
**Req-ID:** AC-08
**Test Type:** UI
**Description:** Number of activations is configured by admin based on user's class/role (e.g., Class 1: 7 activations, Class 2: 6 activations, etc. per BR 01 pricing table). User sees the admin-defined value and cannot change it. Total = price per class × admin-defined activations.
**Test Focus:** Happy path

### Scenario ID: TS_UC-1.11_007
**Scenario Title:** Total calculated correctly based on admin-defined activations
**UC Reference:** UC-1.11 Purchase Package
**Req-ID:** AC-08
**Test Type:** Functional
**Description:** User views Checkout with admin-defined Number of activations for their class; system calculates Total = price per class × admin-defined activations in correct monetary format (CHF XX'XXX per CMR-06)
**Test Focus:** Happy path

### Scenario ID: TS_UC-1.11_008
**Scenario Title:** System displays estimated points distributed (10% of original package price)
**UC Reference:** UC-1.11 Purchase Package
**Req-ID:** AC-09
**Test Type:** UI
**Description:** User on Checkout screen; system displays "Estimated points distributed = 10% × package price" and "+ 10% points for buyer" calculated on ORIGINAL price (before any discount)
**Test Focus:** Happy path

### Scenario ID: TS_UC-1.11_009
**Scenario Title:** 2y+ user sees discount section with checkbox
**UC Reference:** UC-1.11 Purchase Package
**Req-ID:** AC-10
**Test Type:** UI
**Description:** User is 2y+ (signup date >= 2 years); Checkout screen displays Discount section with checkbox "You are eligible for a 20% loyalty discount because you have been with PARTNERS WEEK® for more than 2 years. Use X points to apply a 20% discount?"
**Test Focus:** Happy path

### Scenario ID: TS_UC-1.11_010
**Scenario Title:** 2y+ user checks discount checkbox - final amount calculates correctly with 20% discount
**UC Reference:** UC-1.11 Purchase Package
**Req-ID:** AC-11
**Test Type:** Functional
**Description:** 2y+ user checks discount checkbox; system calculates Final amount = Original price × 80%; Discount shows monetary equivalent + points deducted = Original price × 20%. Points for buyer and pool are still calculated on ORIGINAL price (10% × original price, not discounted price).
**Test Focus:** Happy path

### Scenario ID: TS_UC-1.11_011
**Scenario Title:** User unchecks discount checkbox - original price applies
**UC Reference:** UC-1.11 Purchase Package
**Req-ID:** AC-11
**Test Type:** Alternative flow
**Description:** User checks discount checkbox (discount applied), then unchecks it; system reverts to Original price with no discount deducted
**Test Focus:** Alternative flow

### Scenario ID: TS_UC-1.11_012
**Scenario Title:** Discount applied - points calculated on original price (not discounted)
**UC Reference:** UC-1.11 Purchase Package
**Req-ID:** AC-11
**Test Type:** Functional
**Description:** User purchases Class 1 package (35'000 CHF) with 20% discount applied → Final = 28'000 CHF. Points are still calculated on 35'000 (original): buyer receives 3'500 points (10% × 35'000), pool receives 3'500 points (10% × 35'000). NOT 10% × 28'000.
**Test Focus:** Alternative flow

### Scenario ID: TS_UC-1.11_013
**Scenario Title:** Pay button disabled until Terms checkbox checked
**UC Reference:** UC-1.11 Purchase Package
**Req-ID:** AC-13
**Test Type:** UI
**Description:** User has not checked the Terms of Service checkbox; Pay button is disabled
**Test Focus:** Happy path

### Scenario ID: TS_UC-1.11_014
**Scenario Title:** Pay button enabled after Terms checkbox checked
**UC Reference:** UC-1.11 Purchase Package
**Req-ID:** AC-12
**Test Type:** UI
**Description:** User checks "By continuing, you agree to Partners Weeks Terms of Service..." checkbox; Pay button becomes enabled
**Test Focus:** Happy path

### Scenario ID: TS_UC-1.11_015
**Scenario Title:** User clicks Terms of Service link - opens document
**UC Reference:** UC-1.11 Purchase Package
**Req-ID:** AC-12
**Test Type:** UI
**Description:** User clicks "Terms of Service" link; system opens Terms of Service document in new tab
**Test Focus:** Alternative flow

### Scenario ID: TS_UC-1.11_016
**Scenario Title:** User clicks Privacy Policy link - opens document
**UC Reference:** UC-1.11 Purchase Package
**Req-ID:** AC-12
**Test Type:** UI
**Description:** User clicks "Privacy Policy" link; system opens Privacy Policy document in new tab
**Test Focus:** Alternative flow

### Scenario ID: TS_UC-1.11_017
**Scenario Title:** Successful Stripe payment - NFT minted and points distributed
**UC Reference:** UC-1.11 Purchase Package
**Req-ID:** AC-14
**Test Type:** End-to-End
**Description:** User clicks Pay with valid Stripe payment; Stripe processes successfully; NFT minted, points distributed (10% to buyer, 10% pool, 20 per partner per class); user redirected to success
**Test Focus:** Happy path

### Scenario ID: TS_UC-1.11_018
**Scenario Title:** Stripe payment declined - error shown and user returns to checkout
**UC Reference:** UC-1.11 Purchase Package
**Req-ID:** AC-15
**Test Type:** Error/Exception
**Description:** User clicks Pay but Stripe card is declined; system shows error message; user returns to Checkout screen; no state change (no NFT minted, no points deducted)
**Test Focus:** Error/Exception

### Scenario ID: TS_UC-1.11_019
**Scenario Title:** Pay button shows loading state during Stripe processing
**UC Reference:** UC-1.11 Purchase Package
**Req-ID:** AC-14
**Test Type:** UI
**Description:** User clicks Pay; button shows spinner/loading state while Stripe processes; after completion, button returns to normal state
**Test Focus:** Alternative flow

### Scenario ID: TS_UC-1.11_020
**Scenario Title:** User clicks Back button - returns to Purchase Package screen
**UC Reference:** UC-1.11 Purchase Package
**Req-ID:** AC-01
**Test Type:** UI
**Description:** User on Checkout screen clicks Back button; system returns to Purchase Package screen
**Test Focus:** Alternative flow

### Scenario ID: TS_UC-1.11_021
**Scenario Title:** Company Class 1-7 purchases - correct pricing per class
**UC Reference:** UC-1.11 Purchase Package
**Req-ID:** AC-02
**Test Type:** Functional
**Description:** User is Company Class 1-7; system displays correct price per class: Class 1: 35'000, Class 2: 17'000, Class 3: 7'000, Class 4: 2'500, Class 5: 990, Class 6: 500, Class 7: 190
**Test Focus:** Happy path

### Scenario ID: TS_UC-1.11_022
**Scenario Title:** Public Figure purchases at 35'000 CHF (same as Class 1)
**UC Reference:** UC-1.11 Purchase Package
**Req-ID:** AC-02, AC-16
**Test Type:** Functional
**Description:** User is Public Figure; system displays price 35'000 CHF (same as Class 1 per BR 01); buyer receives 10% points (3'500 for 35'000 package)
**Test Focus:** Happy path

### Scenario ID: TS_UC-1.11_023
**Scenario Title:** Individual CANNOT access Purchase Package feature
**UC Reference:** UC-1.11 Purchase Package
**Req-ID:** AC-16
**Test Type:** Permission/Role
**Description:** User is Individual class; Purchase Package screen is NOT available or shows no package options. Individual only purchases distinction Bridge (via UC-1.5 Distinction Purchase), not via package feature.
**Test Focus:** Permission/Role

### Scenario ID: TS_UC-1.11_024
**Scenario Title:** Individual purchasing distinction Bridge - no points awarded to anyone
**UC Reference:** UC-1.11 Purchase Package
**Req-ID:** AC-17
**Test Type:** Integration
**Description:** User is Individual and purchases distinction Bridge (via UC-1.5); system does NOT award points to anyone (neither 10% to Individual buyer, nor 10% to partner B, nor 10% to PARTNERS WEEK pool) per BR 01 exception
**Test Focus:** Integration

### Scenario ID: TS_UC-1.11_025
**Scenario Title:** Points rounding - 35'000 CHF package rounds to 3'500 points
**UC Reference:** UC-1.11 Purchase Package
**Req-ID:** AC-19
**Test Type:** Boundary
**Description:** User purchases Class 1 package (35'000 CHF); 10% = 3'500 points; system displays 3'500 (rounded to nearest whole number per BR 05)
**Test Focus:** Boundary

### Scenario ID: TS_UC-1.11_026
**Scenario Title:** Points rounding - 990 CHF package (step 10 rule)
**UC Reference:** UC-1.11 Purchase Package
**Req-ID:** AC-19
**Test Type:** Boundary
**Description:** User purchases Class 5 package (990 CHF); 10% = 99 points; system displays 99 points (last digit = 9, rounds up per BR 05 rule 2)
**Test Focus:** Boundary

### Scenario ID: TS_UC-1.11_027
**Scenario Title:** Monetary format displays correctly with apostrophe separators
**UC Reference:** UC-1.11 Purchase Package
**Req-ID:** AC-18
**Test Type:** UI
**Description:** System displays prices in correct format: 35'000, 17'000, 7'000, 2'500, 990, 500, 190 (apostrophe as thousands separator per CMR-06)
**Test Focus:** Happy path

### Scenario ID: TS_UC-1.11_028
**Scenario Title:** Browser back button from Checkout navigates correctly
**UC Reference:** UC-1.11 Purchase Package
**Req-ID:** AC-01
**Test Type:** UI
**Description:** User presses browser back button from Checkout screen; navigates to Purchase Package screen
**Test Focus:** Alternative flow

### Scenario ID: TS_UC-1.11_029
**Scenario Title:** Responsive layout at desktop (1280px)
**UC Reference:** UC-1.11 Purchase Package
**Req-ID:** AC-01
**Test Type:** UI
**Description:** Verify Purchase Package and Checkout screens display correctly at desktop resolution (1280px) - pricing table, form fields, buttons layout properly
**Test Focus:** Happy path

### Scenario ID: TS_UC-1.11_030
**Scenario Title:** Responsive layout at tablet (768px)
**UC Reference:** UC-1.11 Purchase Package
**Req-ID:** AC-01
**Test Type:** UI
**Description:** Verify screens reflow correctly at tablet resolution (768px) - pricing table and form elements adapt to narrower screen
**Test Focus:** Happy path

### Scenario ID: TS_UC-1.11_031
**Scenario Title:** Responsive layout at mobile (375px)
**UC Reference:** UC-1.11 Purchase Package
**Req-ID:** AC-01
**Test Type:** UI
**Description:** Verify screens reflow correctly at mobile resolution (375px) - stacked layout, readable text, touch-friendly targets
**Test Focus:** Happy path

### Scenario ID: TS_UC-1.11_032
**Scenario Title:** Important Notes section visible on Purchase Package screen
**UC Reference:** UC-1.11 Purchase Package
**Req-ID:** AC-01
**Test Type:** UI
**Description:** User on Purchase Package screen sees "Important Notes" section with relevant content
**Test Focus:** Happy path

### Scenario ID: TS_UC-1.11_033
**Scenario Title:** Double-click on Pay button - only one payment processed
**UC Reference:** UC-1.11 Purchase Package
**Req-ID:** AC-14
**Test Type:** Error/Exception
**Description:** User double-clicks Pay button; system prevents duplicate payment - only one payment processed
**Test Focus:** Error/Exception

### Scenario ID: TS_UC-1.11_034
**Scenario Title:** Points display for 2y+ user with discount - calculated on original price
**UC Reference:** UC-1.11 Purchase Package
**Req-ID:** AC-09, AC-11
**Test Type:** Functional
**Description:** 2y+ user with 20% discount on 35'000 package sees: Final amount = 28'000 CHF, but Estimated points = 3'500 (10% × 35'000 original), not 2'800. Points are always based on original package price.
**Test Focus:** Alternative flow

---

## ⚠️ Out-of-Scope Flags

| Scenario Area | Reason | Recommended Action |
|---------------|--------|--------------------|
| Performance load testing | Not in UC scope | N/A |
| Security beyond functional auth | Not in UC scope | N/A |
| NFT minting blockchain details | Payment gateway integration only in UC scope | N/A |
| Stripe webhook handling edge cases | Only basic decline scenario in UC | N/A |
| Refund flow | Explicitly out of scope | N/A |
| Package upgrade/downgrade | Explicitly out of scope | N/A |
| Individual purchasing package | Individual cannot purchase package (only distinction Bridge via UC-1.5) | N/A |