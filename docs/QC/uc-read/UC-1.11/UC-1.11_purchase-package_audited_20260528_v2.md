# UC Readiness Review Report — UC-1.11 Purchase Package

> **Source:** UC-1.11. New Purchase package.pdf + UC-1.11 New Purchase Package Design.png
> **Generated:** 2026-05-28
> **Mode:** First Audit (re-audit after PDF text extraction fixed)
> **Output language:** EN

---

## Audit Summary

| Metric | Value |
|--------|-------|
| **Final Score** | **95.4 / 100** |
| **Verdict** | ✅ **READY** |
| **Total raw score** | 124 / 130 |
| **Critical areas @ 0** | None |
| **Blockers** | 0 |
| **Open Questions** | 0 |
| **Suggestions** | 1 |

---

## Knowledge Area Scores

| # | Knowledge Area | Score | Status |
|---|----------------|-------|--------|
| 1 | Feature Identity | 5/5 | ✅ Clear |
| 2 | Objective & Scope | 5/5 | ✅ Clear |
| 3 | Actors & User Roles | 10/10 | ✅ Clear |
| 4 | Preconditions & Postconditions | 10/10 | ✅ Clear |
| 5 | UI Object Inventory & Mapping | 15/15 | ✅ Complete |
| 6 | Object Attributes & Behavior Definition | 20/20 | ✅ Complete |
| 7 | Functional Logic & Workflow Decomposition | 20/20 | ✅ Complete |
| 8 | Functional Integration Analysis | 18/20 | ✅ Complete |
| 9 | Acceptance Criteria | 20/20 | ✅ Complete |
| 10 | Non-functional Requirements | 5/5 | ✅ Clear |

---

## BA Answers Summary

| Q-ID | Question | Answer |
|------|----------|--------|
| Q1 | Insufficient balance / Stripe decline | Stripe displays decline message; redirects back to checkout screen |
| Q2 | Pricing variation by role | Class 0: custom quote, Class 1: 35'000, Class 2: 17'000, Class 3: 7'000, Class 4: 2'500, Class 5: 990, Class 6: 500, Class 7: 190. Public Figure: 35'000. Individual: 19. Points: None for Individual (BR 01) |
| Q3 | Error messages | MSG-25 for Class 0: "Class 0: Please state your purchase intentions via contact@partnersweek.com" |

---

## 0. Document Metadata

| UC-ID | Feature Name | Version | Status |
|-------|-------------|---------|--------|
| UC-1.11 | Purchase Package | v1.0 | Draft |

---

## 1. Objective & Scope

### 1.1 Objective

Allow user to purchase package (subscription activations) based on their company class or user type. The feature displays pricing, calculates totals, handles 2y+ loyalty discounts, and processes payment via Stripe.

### 1.2 In Scope

- Display user's current package/class and pricing
- Number of activations input and validation
- Price calculation (price per class × activations)
- Points estimation (10% to buyer)
- 2y+ loyalty discount (20% in points)
- Stripe payment processing
- NFT minting and wallet update on success

### 1.3 Out of Scope

- NFT minting technical details (handled by blockchain)
- Refund flow
- Package upgrade/downgrade

---

## 2. Actors & Stakeholders

| Actor | Type | Role & Permissions |
|-------|------|-------------------|
| Company (Class 0-7) | Primary | Can purchase package based on class pricing; receives NFT + 10% points |
| Public Figure | Primary | Pricing same as Class 1 (35'000); receives NFT + 10% points |
| Individual | Primary | Can purchase at 19 CHF; NO points awarded (BR 01) |

---

## 3. Preconditions & Postconditions

### 3.1 Preconditions

- User has logged in system successfully
- User is a company or public figure
- User has sufficient CAM token balance (or Stripe payment method)

### 3.2 Postconditions

| After completing... | System state / Postcondition |
|--------------------|------------------------------|
| Successful purchase | CAM tokens or CHF paid; NFT activated; points distributed (10% to buyer, 10% pool, 20 per partner); transaction appears in User Dashboard |
| Payment failure | No state change; Stripe error shown; user returns to checkout |

---

## 4. UI Object Inventory & Mapping

### Step 1: Package Rules Section

| # | Label (verbatim) | Type | Required | Default | Placeholder | Enum values | Description / Constraint | Source |
|---|----------------|------|----------|---------|-------------|-------------|--------------------------|--------|
| 1 | Purchase Package | Screen title | — | — | — | — | Main screen title | PDF p.5 |
| 2 | Package Rules | Section header | — | — | — | — | Section header | Design |
| 3 | Your current package | Label | — | — | — | — | Display user's current package | Design |
| 4 | Class [X] | Display | — | — | — | — | User's class (0-7, Public Figure, Individual) | Design |
| 5 | price of one activation | Column header | — | — | — | — | Price column | PDF p.6 |
| 6 | number of distinctions | Column header | — | — | — | — | Number of activations column | PDF p.6 |
| 7 | Class 0: custom quote | Table row | — | — | — | — | Class 0 — no public price | PDF p.6 |
| 8 | Class 1: 35'000 / 7 | Table row | — | — | — | — | Class 1 pricing | PDF p.6 |
| 9 | Class 2: 17'000 / 6 | Table row | — | — | — | — | Class 2 pricing | PDF p.6 |
| 10 | Class 3: 7'000 / 5 | Table row | — | — | — | — | Class 3 pricing | PDF p.6 |
| 11 | Class 4: 2'500 / 4 | Table row | — | — | — | — | Class 4 pricing | PDF p.6 |
| 12 | Class 5: 990 / 3 | Table row | — | — | — | — | Class 5 pricing | PDF p.6 |
| 13 | Class 6: 500 / 2 | Table row | — | — | — | — | Class 6 pricing | PDF p.6 |
| 14 | Class 7: 190 / 1 | Table row | — | — | — | — | Class 7 pricing | PDF p.6 |
| 15 | Public Figure: 35'000 | Table row | — | — | — | — | Public Figure pricing (same as Class 1) | BR 01 |
| 16 | Individual: 19 | Table row | — | — | — | — | Individual pricing (CHF 19, no points) | BR 01 |
| 17 | You will receive [N] activations | Display | — | — | — | — | Number of activations for user's class | Design |
| 18 | Purchase Package | Button | — | Enabled when activations remaining = 0 | — | — | Triggers MSG-25 for Class 0 | PDF p.6 |
| 19 | Important Notes | Section header | — | — | — | — | Important notes section | Design |

### Step 2: Checkout

| # | Label (verbatim) | Type | Required | Default | Placeholder | Enum values | Description / Constraint | Source |
|---|----------------|------|----------|---------|-------------|-------------|--------------------------|--------|
| 20 | Checkout | Screen title | — | — | — | — | Checkout screen title | PDF p.6 |
| 21 | Review and complete your purchase | Subtitle | — | — | — | — | Checkout subtitle | PDF p.6 |
| 22 | Back | Button | — | — | — | — | Returns to previous screen | PDF p.6 |
| 23 | Order Summary | Section header | — | — | — | — | Order summary section | Design |
| 24 | Package Class | Display | — | — | — | — | User's class (same pricing table) | Design |
| 25 | Number of activations | Integer input | Yes | — | Enter number of activations | — | Activation count | Design, CMR 01 |
| 26 | Total | Label | — | — | — | — | Total = price × activations | Design |
| 27 | Estimated points distributed | Label | — | — | — | — | 10% × package price | Design |
| 28 | + 10% points for buyer | Label | — | — | — | — | Buyer receives 10% points | BR 04 |
| 29 | Discount | Section header | — | — | — | — | Only for 2y+ users | Design |
| 30 | You are eligible for a 20% loyalty discount... | Checkbox | — | Unchecked | — | — | 20% discount for 2y+ users | BR 03 |
| 31 | Original price | Label | — | — | — | — | Price before discount | Design |
| 32 | Discount | Label | — | — | — | — | Discount amount + points deducted | Design |
| 33 | Final amount to pay | Label | — | — | — | — | Original - Discount | Design |
| 34 | Payment Method | Section header | — | — | — | — | Payment section | Design |
| 35 | Stripe Payment (Fiat) | Radio | — | Selected | — | — | Default payment method | PDF p.8 |
| 36 | Credit/Debit Card | Subtext | — | — | — | — | Card payment type | PDF p.8 |
| 37 | Terms of Service | Link | — | — | — | — | Opens ToS document | PDF p.8 |
| 38 | Privacy Policy | Link | — | — | — | — | Opens Privacy Policy | PDF p.8 |
| 39 | By continuing, you agree to Partners Weeks Terms of Service... | Checkbox | Yes | Unchecked | — | — | Must check to enable Pay | PDF p.8 |
| 40 | Pay | Button | — | Disabled | — | — | Enabled when Terms checked | PDF p.8 |

---

## 5. Object Attributes & Behavior Definition

| Object / Component | System States | Interaction Matrix | Behavior |
|--------------------|---------------|---------------------|----------|
| Purchase Package button | Enabled (activations remaining = 0), Disabled (activations remaining > 0) | Click | Opens Checkout OR shows MSG-25 for Class 0 |
| Number of activations input | Enabled, Error, Disabled | Type, Tab | Validates integer; updates Total |
| Discount checkbox | Unchecked, Checked | Click | Shows/hides discount calculation |
| Terms checkbox | Unchecked, Checked | Click | Enables/disables Pay button |
| Pay button | Disabled, Enabled, Loading | Click | Processes Stripe payment |
| Back button | Enabled | Click | Returns to Purchase Package screen |

---

## 6. Functional Logic & Workflow Decomposition

### 6.1 Function: Purchase Package Flow

**A. Workflows**

| Step | Actor | Action | System Response (Happy Path) | Alternative Flows | Exception & Error Flows |
|------|-------|--------|------------------------------|-------------------|-------------------------|
| 1 | User | Navigates to Purchase Package from menu | Display Package Rules with user's class pricing | — | — |
| 2 | System | Display current class and "You will receive [N] activations" | — | — | — |
| 3 | User | Views Important Notes section | — | — | — |
| 4 | User | Clicks Purchase Package button | If Class 0 → show MSG-25; Else → open Checkout | Class 0 → MSG-25 inline message | — |

### 6.2 Function: Checkout Flow

| Step | Actor | Action | System Response (Happy Path) | Alternative Flows | Exception & Error Flows |
|------|-------|--------|------------------------------|-------------------|-------------------------|
| 1 | User | Views Order Summary with pricing table | Display class pricing | — | — |
| 2 | User | Enters number of activations | System calculates Total = price × activations | Invalid input → show error | — |
| 3 | System | Displays estimated points (+10% for buyer) | — | — | — |
| 4 | User | (Optional) Checks discount checkbox if eligible (2y+) | System calculates final amount with 20% discount | — | — |
| 5 | User | Checks Terms of Service checkbox | Pay button becomes enabled | — | — |
| 6 | User | Clicks Pay | Redirect to Stripe | Stripe decline → show error, return to checkout | Payment failure |
| 7 | System | Payment successful | Mint NFT, distribute points (10% buyer, 10% pool, 20 per partner) | — | — |

**B. Business Rules & Validations**

| Field / Object | Required | Format / Constraint | Error Message | Source |
|----------------|----------|---------------------|---------------|--------|
| Number of activations | Yes | Positive integer | — | — |
| Class 0 purchase | — | Must contact via email | "Class 0: Please state your purchase intentions via contact@partnersweek.com" | MSG-25 |
| Terms checkbox | Yes | Must be checked to enable Pay | — | — |

**Pricing (BR 01):**
| Class | Price (CHF) | Activations |
|-------|-------------|-------------|
| 0 | Custom quote | — |
| 1 | 35'000 | 7 |
| 2 | 17'000 | 6 |
| 3 | 7'000 | 5 |
| 4 | 2'500 | 4 |
| 5 | 990 | 3 |
| 6 | 500 | 2 |
| 7 | 190 | 1 |
| Public Figure | 35'000 | — |
| Individual | 19 | — |

**Points Distribution (BR 04):**
- 10% to buyer
- 10% to PARTNERS WEEK pool
- 20 points per partner (for each partner of each class)

**Discount for 2y+ (BR 03):**
- 20% discount payable in points
- Price after discount = original price × 80%

**Individual note:** No points are awarded to individuals (neither 10% for them, nor 10% for B, nor 10% for pool)

**C. UI/UX Feedback**
- MSG-25 displayed inline when Class 0 clicks Purchase Package
- Pay button only enabled when Terms checkbox is checked
- Loading state on Pay button during Stripe processing

---

## 7. Functional Integration Analysis

| Trigger Function / Action | Impact Analysis | Data Consistency |
|---------------------------|-----------------|-------------------|
| Number of activations input | Updates Total, points estimation | Total = class price × activations |
| Discount checkbox checked | Calculates Final amount = Original - (Original × 20%) | Points balance deducted |
| Pay button clicked | Redirects to Stripe for payment | Payment processed before NFT minting |
| Stripe success | Mint NFT, distribute points | Points distributed per BR 04 formula |
| Individual purchase | No points awarded | BR 01 exception: no points for Individual |

---

## 8. Acceptance Criteria

| AC # | Scenario | Given | When | Then |
|------|----------|-------|------|------|
| AC-01 | Display current package with class | User logged in | User navigates to Purchase Package | Display "Your current package" with user's class |
| AC-02 | Display correct pricing table | User on Purchase Package | System displays pricing | Show correct prices per class (BR 01 table) |
| AC-03 | Display activations count | User on Purchase Package | System displays package info | Show number of activations for user's class |
| AC-04 | Purchase button enabled when no activations | User has 0 activations remaining | User views Purchase Package button | Button is enabled |
| AC-05 | Purchase button disabled when activations > 0 | User has activations remaining | User views Purchase Package button | Button is disabled |
| AC-06 | Class 0 sees MSG-25 | User is Class 0 | User clicks Purchase Package | Display MSG-25 inline |
| AC-07 | Checkout order summary | User on Checkout screen | System displays Order Summary | Show Package Class, Number of activations, Total, Estimated points |
| AC-08 | Total calculation | User enters activations | System calculates | Total = price per class × activations (CMR-06 monetary format) |
| AC-09 | Points estimation display | User on Checkout | System displays points | Show "Estimated points distributed" = 10% × package price and "+ 10% points for buyer" |
| AC-10 | Discount for 2y+ users | User is 2y+ (signup >= 2 years) | User on Checkout | Display Discount section with checkbox |
| AC-11 | Discount calculation | User checks discount checkbox | System calculates | Final amount = Original price × 80%; points deducted = Original price × 20% |
| AC-12 | Terms checkbox enables Pay | User checks Terms checkbox | System enables Pay button | Pay button becomes enabled |
| AC-13 | Pay disabled until Terms checked | User has not checked Terms | User views Pay button | Pay button is disabled |
| AC-14 | Stripe payment success | User clicks Pay with valid payment | Stripe processes | NFT minted, points distributed, redirect to success |
| AC-15 | Stripe payment failure | User clicks Pay but Stripe declines | Stripe shows error | User returns to checkout screen; no state change |
| AC-16 | Individual purchases at 19 CHF | User is Individual class | System displays pricing | Show Individual price: 19 CHF; no points awarded |
| AC-17 | Individual: no points distribution | User is Individual | After purchase | No points awarded (BR 01 exception) |
| AC-18 | Monetary format | System displays price | User views any price | Format: CHF XX'XXX (apostrophe for thousands, CMR-06) |
| AC-19 | Points rounding | System calculates points | Points displayed | Round to nearest whole number (BR 05) |

---

## 9. Open Questions & Dependencies

### Open Questions

| # | Question | Context | Status |
|---|----------|---------|--------|
| — | None | All critical questions resolved | Closed |

### Dependencies

- UC-1.9 (User Dashboard) — transaction display after purchase
- Stripe integration — payment processing
- Points system — balance management and distribution

---

## 10. Change Log

| Version | Date | Author | Summary of Changes |
|---------|------|--------|-------------------|
| v1.0 | 2026-05-28 | QC Agent | Initial audit (re-audit with corrected PDF text extraction) |
| v2.0 | 2026-05-28 | QC Agent | Re-audit after PDF extraction fixed; Individual can purchase (not display-only) |

---

## Unified Gap & Question Report

| ID | Priority | Ref | Question | Why It Matters | Status |
| --- | --- | --- | --- | --- | --- |
| — | — | — | No gaps remaining | All critical information extracted from PDF | Closed |

---

## 🟢 What's Good

- Complete pricing table with all 8 classes + Public Figure + Individual
- Clear MSG-25 handling for Class 0 users
- 2y+ discount logic well documented (BR 03)
- Points distribution formula clearly specified (BR 04)
- Individual note explicitly states "no points awarded"
- Terms checkbox flow (must check to enable Pay) is clear
- Checkout flow is complete with all sections

---

## 🧪 Testability Outlook

**What CAN be tested now:**
- UI element display and layout verification
- Pricing table accuracy per class
- Number of activations validation
- Total calculation accuracy
- Discount calculation for 2y+ users
- Terms checkbox → Pay button enable/disable
- Points estimation display

**What needs integration testing:**
- Stripe payment flow (requires Stripe sandbox)
- NFT minting after successful payment (requires blockchain)
- Points distribution after purchase (requires wallet system)

**Suggested test focus areas:**
- Happy path: Complete purchase flow for each class (0-7, Public Figure, Individual)
- Alternative scenarios: 2y+ discount application, different activation counts
- Boundary & validation: Number of activations input validation
- Error & exception: Class 0 MSG-25, Stripe decline handling
- UI-specific: Monetary format display, responsive layout

---

## 📌 Summary & Recommendation

**Overall state:** UC-1.11 Purchase Package is ✅ **READY** with score 95.4/100.

**Key findings:**
1. PDF text extraction successful — all pricing data captured
2. Individual CAN purchase packages at 19 CHF (not display-only as previously misunderstood)
3. Individual has NO points awarded per BR 01
4. Class 0 triggers MSG-25 instead of purchase flow
5. 2y+ discount logic clear: 20% discount payable in points

**Recommendation:** Proceed to test design. All critical information available.

---

*Report generated by qc-uc-read skill. Next step: invoke /qc-func-scenario-design for UC-1.11.*