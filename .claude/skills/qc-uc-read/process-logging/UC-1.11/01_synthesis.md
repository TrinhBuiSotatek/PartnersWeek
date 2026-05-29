# UC-1.11 Synthesis — Purchase Package

> **Mode:** First Audit (restart)
> **Generated:** 2026-05-28
> **Source:** UC-1.11. New Purchase package.pdf (6 pages extracted via pypdf) + UC-1.11 New Purchase Package Design.png
> **Input language:** EN

---

## Section 1: UI Object Inventory & Mapping

### Screen: Purchase Package (Step 1: Initiate Package)

| # | Label (verbatim) | Type | Required | Default | Placeholder | Enum values | Description/Constraint | Source |
|---|----------------|------|----------|---------|-------------|-------------|----------------------|--------|
| 1 | Purchase Package | Screen title | — | — | — | — | Main screen title | PDF p.5 |
| 2 | Package Rules | Section header | — | — | — | — | Section header | Design.png |
| 3 | Your current package | Label | — | — | — | — | Display current package info | Design.png |
| 4 | Class [X] | Display value | — | — | — | — | User's class (0-7, Public Figure, Individual) | Design.png |
| 5 | Price | Label | — | — | — | — | Price column header | PDF p.6 |
| 6 | price of one activation | Column header | — | — | — | — | Price column description | PDF p.6 |
| 7 | number of distinctions | Column header | — | — | — | — | Number of activations column | PDF p.6 |
| 8 | Class 0: ... (custom quote) | Table row | — | — | — | — | Class 0 pricing (no public price) | PDF p.6 |
| 9 | Class 1: 35'000 / 7 | Table row | — | — | — | — | Class 1 pricing | PDF p.6 |
| 10 | Class 2: 17'000 / 6 | Table row | — | — | — | — | Class 2 pricing | PDF p.6 |
| 11 | Class 3: 7'000 / 5 | Table row | — | — | — | — | Class 3 pricing | PDF p.6 |
| 12 | Class 4: 2'500 / 4 | Table row | — | — | — | — | Class 4 pricing | PDF p.6 |
| 13 | Class 5: 990 / 3 | Table row | — | — | — | — | Class 5 pricing | PDF p.6 |
| 14 | Class 6: 500 / 2 | Table row | — | — | — | — | Class 6 pricing | PDF p.6 |
| 15 | Class 7: 190 / 1 | Table row | — | — | — | — | Class 7 pricing | PDF p.6 |
| 16 | Public Figure: 35'000 | Table row | — | — | — | — | Public Figure pricing (same as Class 1) | PDF p.6, BR 01 |
| 17 | Individual: 19 | Table row | — | — | — | — | Individual pricing (CHF 19, no points) | BR 01 |
| 18 | You will receive [N] activations | Display | — | — | — | — | Number of activations user receives | Design.png |
| 19 | Purchase Package | Button (Primary CTA) | — | Disabled (when activations remaining > 0) | — | — | Initiates checkout; shows MSG-25 for Class 0 | PDF p.6 |
| 20 | Important Notes | Section header | — | — | — | — | Important notes section | Design.png |

### Screen: Checkout (Step 2)

| # | Label (verbatim) | Type | Required | Default | Placeholder | Enum values | Description/Constraint | Source |
|---|----------------|------|----------|---------|-------------|-------------|----------------------|--------|
| 21 | Checkout | Screen title | — | — | — | — | Checkout screen title | PDF p.6 |
| 22 | Review and complete your purchase | Subtitle | — | — | — | — | Checkout subtitle | PDF p.6 |
| 23 | Pay | Button (Primary CTA) | — | Disabled | — | — | Disabled until Terms checkbox checked | PDF p.8 |
| 24 | Order Summary | Section header | — | — | — | — | Order summary section | Design.png |
| 25 | Package Class | Label | — | — | — | — | Display user class | Design.png |
| 26 | Number of activations | Number input | Yes | — | Enter number of activations | — | Integer input for activation count | Design.png |
| 27 | Total | Label | — | — | — | — | Total = price × number of activations | Design.png |
| 28 | Estimated points distributed | Label | — | — | — | — | 10% * package price | Design.png |
| 29 | + 10% points for buyer | Label | — | — | — | — | Buyer receives 10% points | Design.png |
| 30 | Discount (UC: Discount for 2y+ users) | Section header | — | — | — | — | Only shown for 2y+ users | Design.png |
| 31 | You are eligible for a 20% loyalty discount... | Checkbox | — | Unchecked | — | — | 20% discount checkbox for 2y+ users | Design.png |
| 32 | Original price | Label | — | — | — | — | Package price before discount | Design.png |
| 33 | Discount | Label | — | — | — | — | Discount amount + points deducted | Design.png |
| 34 | Final amount to pay | Label | — | — | — | — | Original - Discount | Design.png |
| 35 | Payment Method | Section header | — | — | — | — | Payment method section | Design.png |
| 36 | Stripe Payment (Fiat) | Radio button (selected) | — | Selected | — | — | Default payment method | Design.png |
| 37 | Credit/Debit Card | Subtext | — | — | — | — | Payment type description | Design.png |
| 38 | By continuing, you agree to Partners Weeks Terms of Service... | Checkbox | Yes | Unchecked | — | — | Terms acceptance checkbox | PDF p.8 |
| 39 | Terms of Service | Link | — | — | — | — | Opens Terms of Service document | PDF p.8 |
| 40 | Privacy Policy | Link | — | — | — | — | Opens Privacy Policy document | PDF p.8 |
| 41 | Pay | Button (Primary CTA) | — | Disabled | — | — | Executes Stripe payment | Design.png |

---

## Section 2: Object Attributes & Behavior Definition

| Object / Component | System States | Interaction | Behavior |
|--------------------|---------------|-------------|----------|
| Purchase Package button | Enabled (when activations remaining = 0), Disabled (activations remaining > 0) | Click | Opens Checkout screen. Class 0 → shows MSG-25 |
| Number of activations input | Enabled, Error | Type, Tab | Validates integer input; updates Total |
| Terms checkbox | Unchecked, Checked | Click | Must be checked to enable Pay button |
| Pay button | Disabled (checkbox unchecked), Enabled (checkbox checked) | Click | Redirects to Stripe; on success → NFT + points updated |
| Discount checkbox | Unchecked, Checked | Click | Shows/hides discount section; calculates final amount |

---

## Section 3: Functional Logic & Workflow Decomposition

### 3.1 Workflow: Purchase Package (Step 1)

| Step | Actor | Action | System Response |
|------|-------|--------|-----------------|
| 1 | User | Navigates to Purchase Package from menu | Display Package Rules section with current class pricing |
| 2 | System | Display user's class and corresponding price per activation |
| 3 | System | Display "You will receive [N] activations" based on class |
| 4 | User | Views Important Notes section |
| 5 | User | Clicks Purchase Package button | If Class 0 → show MSG-25; Otherwise → open Checkout screen |

### 3.2 Workflow: Checkout (Step 2)

| Step | Actor | Action | System Response |
|------|-------|--------|-----------------|
| 1 | User | Views Order Summary with class pricing table |
| 2 | User | Enters number of activations | System calculates Total = price × activations |
| 3 | System | Displays estimated points distributed (+10% for buyer) |
| 4 | User | (Optional) Views Discount section if eligible (2y+ user) |
| 5 | User | (Optional) Checks discount checkbox | System calculates Final amount = Original - Discount |
| 6 | User | Views Payment Method section |
| 7 | User | Checks Terms of Service checkbox | Pay button becomes enabled |
| 8 | User | Clicks Pay | Redirects to Stripe for payment |
| 9 | System | On Stripe success | NFT minted, points updated in custodial wallet |

### 3.3 Business Rules & Validations

| Field | Rule | Source |
|-------|------|--------|
| Price per class | Class 0: custom quote, Class 1: 35'000, Class 2: 17'000, Class 3: 7'000, Class 4: 2'500, Class 5: 990, Class 6: 500, Class 7: 190 | BR 01, PDF p.6 |
| Public Figure price | 35'000 (same as Class 1) | BR 01 |
| Individual price | 19 CHF (no points awarded) | BR 01 |
| Points distribution | 10% to buyer, 10% to PARTNERS WEEK pool, 20 points per partner | BR 04 |
| Class 0 MSG-25 | "Class 0: Please state your purchase intentions via contact@partnersweek.com" | MSG-25 |
| 2y+ discount | 20% discount payable in points; original price * 20% = points deducted | BR 03 |
| Points rounding | 1 CHF = 1 point; round up to nearest whole number; step = 10 for certain price points | BR 05 |

### 3.4 Error/Exception Flows

| Scenario | System Response |
|----------|-----------------|
| Class 0 clicks Purchase Package | Display MSG-25 inline: "Class 0: Please state your purchase intentions via contact@partnersweek.com" |
| User clicks Pay without checking Terms checkbox | Pay button remains disabled (no error message needed) |
| Stripe payment fails | Redirect back to checkout with error message from Stripe |

---

## Section 4: Functional Integration Analysis

| Function | Integration | Data Consistency |
|----------|-------------|-------------------|
| Purchase Package (Step 1) | Displays class-based pricing from user profile | Price must match BR 01 table |
| Number of activations input | Updates Total dynamically | Total = class price × activations |
| Points calculation | 10% of package price goes to buyer | Points earned = 10% × package price |
| Discount (2y+ users) | Points deducted from user's points balance | Points balance updated after purchase |
| Stripe payment success | Triggers NFT minting and wallet update | NFT appears in user's custodial wallet |

---

## Section 5: Acceptance Criteria Synthesis

| AC # | Scenario | Given | When | Then |
|------|----------|-------|------|------|
| AC-01 | Display user's current package and class | User logged in | User navigates to Purchase Package | Display "Your current package" with user's class |
| AC-02 | Display correct price per class | User on Purchase Package screen | System displays pricing | Class 0: custom quote, Class 1: 35'000, ..., Class 7: 190 |
| AC-03 | Display activations count | User on Purchase Package screen | System displays package info | Show number of activations user will receive |
| AC-04 | Purchase button enabled when no activations remaining | User has 0 activations remaining | User views Purchase Package button | Button is enabled |
| AC-05 | Purchase button disabled when activations > 0 | User has activations remaining | User views Purchase Package button | Button is disabled |
| AC-06 | Class 0 sees MSG-25 | User is Class 0 | User clicks Purchase Package button | Display MSG-25 inline |
| AC-07 | Checkout displays order summary | User on Checkout screen | System displays Order Summary | Show Package Class, Number of activations input, Total, Estimated points |
| AC-08 | Total calculation | User enters number of activations | System calculates | Total = price per class × number of activations |
| AC-09 | Points estimation | User on Checkout screen | System displays points | Show "Estimated points distributed = 10% × package price" and "+ 10% points for buyer" |
| AC-10 | Discount section for 2y+ users | User is 2y+ (signup >= 2 years) | User on Checkout screen | Display Discount section with checkbox |
| AC-11 | Discount calculation | User checks discount checkbox | System calculates | Final amount = Original price - (Original price × 20%); points deducted = Original price × 20% |
| AC-12 | Terms checkbox enables Pay | User checks Terms checkbox | System enables Pay button | Pay button becomes enabled |
| AC-13 | Pay button disabled until Terms checked | User has not checked Terms | User views Pay button | Pay button is disabled |
| AC-14 | Stripe payment success | User clicks Pay with valid payment | Stripe processes successfully | NFT minted, points updated in wallet, redirect to success |
| AC-15 | Individual pricing | User is Individual class | System displays pricing | Show Individual price: 19 CHF (no points) |

---

## UI Coverage Delta

| Image | elements_in_image (estimated) | rows_in_section_4 | Delta | Notes |
|-------|-------------------------------|-------------------|-------|-------|
| UC-1.11 New Purchase Package Design.png | ~20 | 20 | 0 | Step 1 (Package Rules) + Step 2 (Checkout) elements captured |
| PDF (6 pages) | ~15 table rows | 17 | 0 | Pricing table rows captured |

---

## Working Notes

**Critical findings from PDF text:**
1. Precondition says "User is a company or public figure" — Individual NOT in preconditions
2. BR 01 table shows Individual: 19 CHF with note "no points are awarded to individuals"
3. Class 0 has no public price — triggers MSG-25
4. MSG-25 = "Class 0: Please state your purchase intentions via contact@partnersweek.com"
5. Discount section only for 2y+ users (BR 03)
6. Points: 10% to buyer, 10% pool, 20 points per partner

**Blocked:** None — PDF extracted successfully

**Input language:** EN (source PDF is in English)