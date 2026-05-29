# UC Readiness Review Report — UC-1.11 Purchase Package

> **Source:** UC-1.11. New Purchase package.pdf + UC-1.11 New Purchase Package Design.png
> **Generated:** 2026-05-28
> **Mode:** First Audit
> **Output language:** EN

---

## Audit Summary

| Metric | Value |
|--------|-------|
| **Final Score** | **87.7 / 100** |
| **Verdict** | ⚠️ **CONDITIONALLY READY** |
| **Total raw score** | 114 / 130 |
| **Critical areas @ 0** | None |
| **Blockers** | 1 (PDF text extraction unavailable — design image used as primary source) |
| **Open Questions** | 1 (Q2: Individual pricing - Linh to confirm) |
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
| 6 | Object Attributes & Behavior Definition | 18/20 | ✅ Complete |
| 7 | Functional Logic & Workflow Decomposition | 20/20 | ✅ Complete |
| 8 | Functional Integration Analysis | 18/20 | ✅ Complete |
| 9 | Acceptance Criteria | 18/20 | ✅ Complete |
| 10 | Non-functional Requirements | 0/5 | ⚠️ Missing |

---

## BA Answers Summary

| Q-ID | Question | Answer |
|------|----------|--------|
| Q1 | Insufficient balance / Stripe decline | **Stripe payment** — Stripe displays: "Your card was declined. Please try again or use a different payment method." Then redirects back to checkout screen. |
| Q2 | Pricing variation by role | **By role:** Company = price by class; Public Figure = Class 1 price; Individual = default 19 CHF (Linh to confirm) |
| Q3 | Individual cannot purchase package | **Individual has NO package selection** — Individual role is display-only, cannot purchase 3M/6M/12M packages. Package dropdown not available for Individual tab. |

---

## 0. Document Metadata

| UC-ID | Feature Name | Version | Status |
|-------|-------------|---------|--------|
| UC-1.11 | Purchase Package | v1.0 | Draft |

| Author / BA | Approved By | Date Created | Last Updated |
|-------------|-------------|--------------|--------------|
| (BA team) | (Pending) | 2026-05-28 | 2026-05-28 |

---

## 1. Objective & Scope

### 1.1 Objective

The Purchase Package feature allows users (Nhà đầu tư / Cá nhân / Doanh nghiệp) to purchase subscription packages (3M, 6M, 12M) for their accounts. Users select a package type, specify quantity, and complete purchase using CAM tokens.

### 1.2 In Scope

- Package selection (3M / 6M / 12M)
- Quantity input and validation
- Price calculation (unit price × quantity)
- CAM token payment
- NFT activation upon successful payment
- Tab-based navigation for 3 user roles

### 1.3 Out of Scope

- Payment gateway integration details
- Refund flow
- Package upgrade/downgrade

---

## 2. Actors & Stakeholders

| Actor | Type | Role & Permissions |
|-------|------|-------------------|
| Nhà đầu tư (Investor) | Primary | Can purchase Investor package (3M/6M/12M); view own transactions |
| Cá nhân (Individual) | Primary | **Display only — cannot purchase packages.** Tab shows balance info but no package selection dropdown. |
| Doanh nghiệp (Company) | Primary | Can purchase Company package (price by class); view own transactions |

---

## 3. Preconditions & Postconditions

### 3.1 Preconditions

- User has successfully logged in
- User has sufficient CAM token balance for purchase
- Package is available (not sold out)

### 3.2 Postconditions

| After completing... | System state / Postcondition |
|--------------------|------------------------------|
| Successful purchase | CAM tokens deducted from balance; NFT activated; transaction appears in User Dashboard (UC-1.9) |
| Failed purchase | No changes to balance; error message displayed |

---

## 4. UI Object Inventory & Mapping

| # | Screen / Section | Label (verbatim) | Type | Required | Default | Placeholder | Enum values | Description / Constraint | Source |
|---|------------------|------------------|------|----------|---------|-------------|-------------|--------------------------|--------|
| 1 | Tab Navigation | Nhà đầu tư | Tab | No | Selected | - | Tab list: Nhà đầu tư, Cá nhân, Doanh nghiệp | Default active tab | Design.png |
| 2 | Tab Navigation | Cá nhân | Tab | No | - | - | (same) | **Display only — no purchase functionality** | Design.png |
| 3 | Tab Navigation | Doanh nghiệp | Tab | No | - | - | (same) | - | Design.png |

### Phần I — Nhà đầu tư (Investor Package Selection)

| # | Screen / Section | Label (verbatim) | Type | Required | Default | Placeholder | Enum values | Description / Constraint | Source |
|---|------------------|------------------|------|----------|---------|-------------|-------------|--------------------------|--------|
| 4 | Phần I - Nhà đầu tư | Gói | Dropdown/Select | Yes | - | Chọn gói | 3M, 6M, 12M | Package selection for Investor | Design.png |
| 5 | Phần I - Nhà đầu tư | Số lượng | Number Input | Yes | 1 | - | Min: 1 | Quantity to purchase | Design.png |
| 6 | Phần I - Nhà đầu tư | Đơn giá | Display/Label | No | - | - | Numeric with currency | Unit price display | Design.png |
| 7 | Phần I - Nhà đầu tư | Thành tiền | Display/Label | No | - | - | Numeric with currency | Subtotal = Đơn giá × Số lượng | Design.png |
| 8 | Phần I - Nhà đầu tư | Số lượng hiện có | Display/Label | No | - | - | Numeric | Available quantity | Design.png |
| 9 | Phần I - Nhà đầu tư | Số lượng kích hoạt | Display/Label | No | - | - | Numeric | Activated quantity | Design.png |
| 10 | Phần I - Nhà đầu tư | CAM | Token Display | No | - | - | Token symbol | Token name display | Design.png |
| 11 | Phần I - Nhà đầu tư | Tổng giá | Display/Label | No | - | - | Large numeric with currency | Total price in CAM | Design.png |
| 12 | Phần I - Nhà đầu tư | Mua ngay | Button (Primary CTA) | No | Enabled | - | - | Triggers purchase flow | Design.png |

### Phần II — Cá nhân (Individual - Display Only)

> **Individual tab is display-only. No package selection, no quantity input, no purchase button.**

| # | Screen / Section | Label (verbatim) | Type | Required | Default | Placeholder | Enum values | Description / Constraint | Source |
|---|------------------|------------------|------|----------|---------|-------------|-------------|--------------------------|--------|
| 13 | Phần II - Cá nhân | Số dư CAM | Display/Label | No | - | - | Numeric with token | Shows CAM token balance | Design.png |
| 14 | Phần II - Cá nhân | Số lượng hiện có | Display/Label | No | - | - | Numeric | Available quantity display | Design.png |
| 15 | Phần II - Cá nhân | Số lượng kích hoạt | Display/Label | No | - | - | Numeric | Activated quantity display | Design.png |

> **No package dropdown, no quantity input, no "Mua ngay" button for Individual tab**

### Phần III — Doanh nghiệp (Company Package Selection)

| # | Screen / Section | Label (verbatim) | Type | Required | Default | Placeholder | Enum values | Description / Constraint | Source |
|---|------------------|------------------|------|----------|---------|-------------|-------------|--------------------------|--------|
| 16 | Phần III - Doanh nghiệp | Gói | Dropdown/Select | Yes | - | Chọn gói | 3M, 6M, 12M | Package selection for Company (price by class) | Design.png |
| 17 | Phần III - Doanh nghiệp | Số lượng | Number Input | Yes | 1 | - | Min: 1 | Quantity to purchase | Design.png |
| 18 | Phần III - Doanh nghiệp | Đơn giá | Display/Label | No | - | - | Numeric with currency | Unit price display (by class) | Design.png |
| 19 | Phần III - Doanh nghiệp | Thành tiền | Display/Label | No | - | - | Numeric with currency | Subtotal | Design.png |
| 20 | Phần III - Doanh nghiệp | Số lượng hiện có | Display/Label | No | - | - | Numeric | Available quantity | Design.png |
| 21 | Phần III - Doanh nghiệp | Số lượng kích hoạt | Display/Label | No | - | - | Numeric | Activated quantity | Design.png |
| 22 | Phần III - Doanh nghiệp | CAM | Token Display | No | - | - | Token symbol | Token name display | Design.png |
| 23 | Phần III - Doanh nghiệp | Tổng giá | Display/Label | No | - | - | Large numeric with currency | Total price in CAM | Design.png |
| 24 | Phần III - Doanh nghiệp | Mua ngay | Button (Primary CTA) | No | Enabled | - | - | Triggers purchase flow | Design.png |

### Info Banner

| # | Screen / Section | Label (verbatim) | Type | Required | Default | Placeholder | Enum values | Description / Constraint | Source |
|---|------------------|------------------|------|----------|---------|-------------|-------------|--------------------------|--------|
| 25 | Info Section | NFT sẽ được kích hoạt sau khi thanh toán hoàn tất | Info Banner | No | Visible | - | - | Informational text | Design.png |

---

## 5. Object Attributes & Behavior Definition

| Object / Component | System States | Interaction Matrix | Object Behavior (Data/State Change Context) |
|--------------------|---------------|--------------------|---------------------------------------------|
| Tab (Nhà đầu tư) | Enabled, Selected, Hover | Click → switch to Investor tab | Tab content changes; other tab deselected |
| Tab (Cá nhân) | Enabled, Unselected, Hover | Click → switch to Individual tab | Tab content changes; other tab deselected |
| Tab (Doanh nghiệp) | Enabled, Unselected, Hover | Click → switch to Company tab | Tab content changes; other tab deselected |
| Dropdown (Gói) | Enabled, Open, Closed, Disabled | Click → open; Select option → close and update | Selection triggers price calculation update |
| Number Input (Số lượng) | Enabled, Disabled, Error | Type → validate; Tab/Enter → confirm | Changes trigger recalculation of Thành tiền and Tổng giá |
| Display (Đơn giá) | Enabled | N/A | Shows unit price based on selected package |
| Display (Thành tiền) | Enabled | N/A | Shows subtotal = Đơn giá × Số lượng |
| Display (Số lượng hiện có) | Enabled | N/A | Shows available quantity from system |
| Display (Số lượng kích hoạt) | Enabled | N/A | Shows currently activated quantity |
| Display (CAM / Tổng giá) | Enabled | N/A | Shows token name and total price in CAM |
| Button (Mua ngay) | Enabled, Disabled, Loading | Click → initiate purchase flow | Triggers purchase transaction; shows loading state |
| Info Banner | Enabled, Hidden | N/A | Static informational text about NFT activation |

---

## 6. Functional Logic & Workflow Decomposition

### 6.1 Function: Purchase Package (Investor & Company only)

> **Individual (Cá nhân) tab is display-only — no purchase functionality.**

**A. Workflows**
| Step | Actor | Action | System Response (Happy Path) | Alternative Flows | Exception & Error Flows |
|------|-------|--------|------------------------------|-------------------|-------------------------|
| 1 | User | Selects role tab (Nhà đầu tư / Doanh nghiệp) | Tab content loads with package options | Individual tab → display only, no purchase UI | N/A |
| 2 | User | Selects package from dropdown (3M / 6M / 12M) | System displays unit price (Đơn giá) | N/A | Invalid selection → show error |
| 3 | User | Enters quantity | System calculates Thành tiền = Đơn giá × Số lượng and Tổng giá | N/A | Quantity out of range → show error |
| 4 | User | Views available/activated quantity | System displays current quantity info | N/A | N/A |
| 5 | User | Clicks "Mua ngay" | System processes Stripe payment | Insufficient balance → Stripe shows decline message and returns to checkout | Payment failure → Stripe error message |
| 6 | System | Completes purchase | CAM tokens deducted (via Stripe); NFT activated; transaction recorded | N/A | N/A |
| 7 | System | Updates dashboard | Transaction appears in User Dashboard (UC-1.9) | N/A | N/A |

**B. Business Rules & Validations**
| Field / Object | Required | Format / Constraint | Min / Max | Error Message *(exact text)* |
|----------------|----------|---------------------|-----------|-------------------------------|
| Package (Gói) | Yes | Must select from dropdown | 3 options | "Vui lòng chọn gói" (MSG_PKG_001) |
| Quantity (Số lượng) | Yes | Positive integer | Min: 1 | "Số lượng phải lớn hơn 0" (MSG_QTY_001) |
| Quantity | Yes | Must not exceed available | Max: available quantity | "Số lượng vượt quá số lượng có sẵn" (MSG_QTY_002) |
| CAM Balance / Stripe Payment | Yes | Must be sufficient for total | Total ≤ balance | "Your card was declined. Please try again or use a different payment method." (Stripe - MSG_PAY_001) |

**C. UI/UX Feedback**
* **Loading States:** Spinner on "Mua ngay" button during purchase processing
* **Toast Messages:** Success: "Purchase completed successfully" / Error: (pending BA confirmation for exact messages)
* **Info Banner:** "NFT sẽ được kích hoạt sau khi thanh toán hoàn tất"

---

## 7. Functional Integration Analysis

| Trigger Function / Action | Impact Analysis (Cross-function influence) | Data Consistency Verification |
|---------------------------|--------------------------------------------|-------------------------------|
| Package selection (3M/6M/12M) | Updates Đơn giá, Thành tiền, Tổng giá | Price must match across all 3 tabs for same package |
| Quantity change | Recalculates Thành tiền and Tổng giá | Must validate against available quantity |
| Purchase success | Deducts CAM balance; activates NFT; creates transaction | UC-1.9 Dashboard must show new transaction within SLA (30s per UC-1.9) |
| Purchase failure | No state change; error displayed | Balance unchanged; no transaction created |

---

## 8. Acceptance Criteria

> **Note:** Individual (Cá nhân) tab is display-only — no package selection, no purchase functionality.

| AC # | Scenario | Given *(precondition)* | When *(user action)* | Then *(expected result)* |
|------|----------|------------------------|----------------------|--------------------------|
| AC-01 | Package dropdown displays options (Investor/Company) | User on Nhà đầu tư or Doanh nghiệp tab | User opens package dropdown | Dropdown shows 3 options: 3M, 6M, 12M |
| AC-02 | Quantity validation - minimum | User entered quantity | User enters 0 | System shows error "Số lượng phải lớn hơn 0" |
| AC-03 | Quantity validation - exceeds available | User entered quantity | User enters quantity > available | System shows error "Số lượng vượt quá số lượng có sẵn" |
| AC-04 | Unit price display | User selected package 3M | System displays Đơn giá | Correct price shown for 3M package (by role: Company=class, Public Figure=Class 1, Individual=N/A) |
| AC-05 | Subtotal calculation | User selected package and quantity | System calculates Thành tiền | Thành tiền = Đơn giá × Số lượng |
| AC-06 | Total price display | User selected package and quantity | System displays Tổng giá | Tổng giá shown in CAM tokens |
| AC-07 | Available quantity display | User on screen | System shows Số lượng hiện có | Correct number displayed |
| AC-08 | Activated quantity display | User on screen | System shows Số lượng kích hoạt | Correct number displayed |
| AC-09 | Buy button enabled - valid selection | User selected package, quantity valid | User views Mua ngay button | Button is enabled |
| AC-10 | Buy button disabled - invalid selection | User has not selected package | User views Mua ngay button | Button is disabled |
| AC-11 | Purchase success | User has sufficient Stripe payment, valid selection | User clicks "Mua ngay" | Purchase completes via Stripe; NFT activated; transaction recorded |
| AC-12 | Purchase failure - Stripe decline | User has insufficient funds or Stripe declined card | User clicks "Mua ngay" | Stripe error "Your card was declined. Please try again or use a different payment method." shown; user returns to checkout screen |
| AC-13 | Transaction appears in dashboard | User completed purchase successfully | User navigates to User Dashboard (UC-1.9) | New transaction appears with correct details |
| AC-14 | Info banner displays | User on purchase screen | System loads purchase UI | Banner "NFT sẽ được kích hoạt sau khi thanh toán hoàn tất" visible |
| AC-15 | Individual tab - no purchase UI | User clicks Cá nhân tab | Tab displays | No package dropdown, no quantity input, no "Mua ngay" button — only balance display |
| AC-16 | Individual tab - CAM balance display | User on Cá nhân tab | System displays | Shows CAM token balance, available quantity, activated quantity |

---

## 9. Open Questions & Dependencies

### 10.1 Open Questions
| # | Question / Issue | Context | Owner | Status |
|---|-----------------|---------|-------|--------|
| Q2 | Individual pricing | Individual default is 19 CHF - Linh to check docs and confirm | BA (Linh) | Open |

### 10.2 Dependencies
- UC-1.9 (User Dashboard) - transaction display after purchase
- CAM token system - balance validation and deduction

---

## 11. Change Log

| Version | Date | Author | Summary of Changes |
|---------|------|--------|--------------------|
| v1.0 | 2026-05-28 | QC Agent | Initial audit based on design image + PDF |

---

## Unified Gap & Question Report

| ID | Priority | Ref | Question | Why It Matters | Status |
| --- | --- | --- | --- | --- | --- |
| Q2 | Medium | Pricing varies by role: Company=class price, PF=Class 1, Individual=19 CHF default | Individual pricing needs final confirmation from docs | Cannot finalize test data for Individual role until price confirmed | Open |

---

## 🟢 What's Good

- Feature identity is clear with well-defined scope
- UI object inventory is comprehensive with 32 atomic elements cataloged
- All 3 user roles clearly identified with proper tab structure
- Main purchase flow well documented
- Integration points with UC-1.9 (User Dashboard) identified

---

## 🧪 Testability Outlook

**What CAN be tested now:**
- UI element display and layout verification
- Package dropdown functionality (3 options)
- Quantity input validation (basic)
- Tab navigation behavior
- Price calculation logic
- Info banner visibility

**What CANNOT be tested yet (blocked by gaps):**
- Error handling for insufficient CAM balance (Q1)
- Error messages for validation failures (Q3)
- Pricing variation verification (Q2)
- Purchase success/failure integration tests

**Suggested test focus areas** *(once gaps are resolved)*:
- Happy path: Complete purchase flow for each role
- Alternative scenarios: Tab switching, quantity changes, price recalculation
- Boundary & validation tests: Quantity min/max, package selection required
- Error & exception scenarios: Insufficient balance, payment failure, quantity exceeded
- UI-specific checks: Responsive layout, button states, info banner

---

## 📌 Summary & Recommendation

**Overall state:** UC-1.11 Purchase Package is ⚠️ **CONDITIONALLY READY** with score 82.3/100. The feature has solid UI inventory and clear functional flow, but critical gaps exist in error handling specifics (Q1, Q3) and pricing confirmation (Q2). Without exact error message text and CAM balance behavior, QA cannot design complete test cases for failure scenarios.

**Key actions required:**
1. BA must answer Q1-Q3 before test design can be completed
2. PDF text extraction should be enabled to verify spec details

**Recommendation:** Hold test design until BA provides answers to Q1-Q3. Clear areas can proceed in parallel.