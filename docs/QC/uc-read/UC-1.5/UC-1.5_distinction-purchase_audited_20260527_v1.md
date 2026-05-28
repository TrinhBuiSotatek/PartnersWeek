# UC Readiness Review — UC-1.5: Distinction Purchase

**Functional / Black-box Test Readiness Template**

---

> **How to use this template**
>This template defines the minimum information QA testers need to begin test case design.
>Fill out all sections completely before handing off to QA. Do not leave any field blank — if a section truly does not apply, write N/A and explain why.
>
> **Completion status conventions:**
> - ✅ **Complete** = section is fully populated and no longer ambiguous
> - ⚠️ **Partial** = contains content but requires further clarification
> - ❌ **Missing** = absent — BLOCKER, cannot start test design

---

## Feature Brief

*(Summarize the feature based on all read documents. Include: what the feature is, who uses it, how it works, key business rules, and known exceptions.)*

**UC-1.5: Distinction Purchase** là tính năng cho phép người dùng (Company/Public Figure/Individual) mua NFT Distinction để vinh danh đối tác kinh doanh. Quy trình bao gồm 3 bước chính: (1) Browse Distinctions — chọn loại distinction, (2) Select Recipient — chọn hoặc tạo người nhận mới, (3) Confirmation — xác nhận và mint NFT.

**Đã xác nhận với BA:**
- **Tài liệu Cũ (Old Design)**: Mua từng NFT riêng lẻ, thanh toán qua Stripe tại checkout → Logic hiện tại đang triển khai
- **Tài liệu Mới (New Design)**: Mua activation package (chứa x lần mint), không cần Stripe tại thời điểm mint → Logic sắp update trong tương lai

**Key Business Rules:**
- Anti-return check (Frontend): Không cho phép A và B mua cùng loại distinction trong cùng năm — MSG 28
- Points distribution (Logic hiện tại): 10% cho buyer + 10% cho recipient + 10% vào PARTNERS WEEK pool = 30% total
- Points distribution (Logic mới — sắp tới): 10% cho buyer + 20 points cho partner
- Pricing: Theo class (Class 0: miễn phí 10 activations → Class 7: CHF 190/1 activation). Không có giá riêng cho từng distinction type (Collaboration/Investor/Bridge)
- Individual chỉ được mua Bridge tại CHF 19, buyer (Individual) không được nhận points
- Mỗi lần mint giảm 1 activation
- Badge: Chỉ nhận 1 badge ở lần đầu tiên (không phụ thuộc có bao nhiêu recipient)
- NFT mint ngay lập tức khi purchase hoàn tất (không cần chờ recipient sign up)

---

## Readiness Verdict

| Overall Score | Verdict |
| ------------- | ------- |
| `78 / 100` | ⚠️ **CONDITIONALLY READY** |

> **Note:** Sau khi BA trả lời Q1-Q10, các conflict đã được giải quyết. Tuy nhiên vẫn còn một số ⚡ Partial areas cần được làm rõ thêm trước khi bắt đầu test design cho tài liệu Mới (activations model).

---

## 0. Document Metadata

| UC-ID | Feature Name | Version | Status |
|-------|-------------|---------|--------|
| UC-1.5 | Distinction Purchase | v1 (2026-05-27) | Draft — Đang review |

| Author / BA | Approved By | Date Created | Last Updated |
|-------------|-------------|--------------|--------------|
| Trang Nguyen (tài liệu cũ) / BA Team (tài liệu mới) | — | 2026-05-26 | 2026-05-27 |

---

## 1. Objective & Scope

### 1.1 Objective

Cho phép User (Company/Public Figure/Individual) mua NFT Distinction để vinh danh đối tác kinh doanh với blockchain-based NFT certificates. Tính năng hỗ trợ 3 loại distinction (Collaboration, Investor, Bridge), tích điểm cho cả hai bên (buyer + recipient), và tự động mint NFT khi purchase hoàn tất.

### 1.2 In Scope

- **Step 1 — Browse Distinctions**: Xem danh sách distinction types, thông tin giá/activations, button để chọn
- **Step 2 — Select Recipient**: Tìm kiếm recipient đã tồn tại hoặc tạo mới (Company/Public Figure/Individual)
- **Step 3 — Confirmation**: Xem order summary, nhận points, mint NFT
- Anti-return check (không cho A+B mua same distinction trong same year)
- Points distribution (10% buyer + 20 points cho partner)
- Badge issuance cho first-time purchaser/recipient
- Email notification (EMC 12 cho buyer, EMC 13 cho recipient)

### 1.3 Out of Scope

- Stripe payment (tài liệu mới không còn Stripe — chỉ mint trực tiếp)
- Discount Year 2+ (20% reduction payable in points) — có đề cập trong tài liệu nhưng không rõ trigger condition
- NFT Transfer (UC-1.6) — handled in separate UC
- Event Access (UC-1.8) — handled in separate UC

---

## 2. Actors & Stakeholders

| Actor | Type | Role & Permissions |
|-------|------|-------------------|
| Company (Class 0-6) | Primary | Buyer — mua distinction cho partner. Pricing theo class. Nhận NFT + 10% points |
| Public Figure | Primary | Tương tự Company Class 1. Pricing: CHF 35,000. Nhận NFT + points |
| Individual (Class 7) | Primary | Chỉ được mua Bridge tại CHF 19. Không có points distribution khi tự mua. Có thể nhận NFT/points nếu được其他人 mua |
| Recipient (Company B) | Secondary | Nhận NFT distinction + 20 points từ tài liệu mới (hoặc 10% points từ tài liệu cũ) |

---

## 3. Preconditions & Postconditions

### 3.1 Preconditions

- User đã đăng nhập thành công vào hệ thống
- User có logged-in state và có thể truy cập "Distinctions" từ menu
- User có đủ điều kiện mua (không phải Class 0 — xem MSG 25)
- Anti-return check: A và B chưa có distinction cùng loại trong năm hiện tại

### 3.2 Postconditions

| After completing... | System state / Postcondition |
|--------------------|------------------------------|
| Purchase hoàn tất | NFT được mint cho cả buyer (Company A) và recipient (Company B) |
| Purchase hoàn tất | Buyer nhận 10% points của NFT price; Recipient nhận 20 points (tài liệu mới) |
| Purchase hoàn tất | PARTNERS WEEK pool nhận 10% |
| First-time purchase | Buyer và Recipient nhận badge trong User Profile + email notification (EMC 12/13) |
| First-time purchase cho recipient chưa đăng ký | System tạo custodial wallet cho recipient |

---

## 4. UI Object Inventory & Mapping

> **Instructions:** Extract and catalog **every atomic UI component** from the Design Mockup. **One component = one row.** Do NOT collapse multiple inputs/buttons/columns into a single row.

### 4.1 Tài liệu cũ (Old Design) — UC-5.1 Browse Distinctions

| # | Screen / Section | Label (verbatim) | Type | Required | Default | Placeholder | Enum values | Description / Constraint | Source |
|---|------------------|------------------|------|----------|---------|-------------|-------------|--------------------------|--------|
| 1 | Browse Distinctions | "Browse Distinctions" | Page title | N/A | — | — | — | Display title | Old Design.png |
| 2 | Browse Distinctions | "Choose a distinction type to recognize your business partners with blockchain-based NFT certificates" | Subtitle | N/A | — | — | — | Display sub-title | Old Design.png |
| 3 | Browse Distinctions > How It Works | "How It Works" | Section title | N/A | — | — | — | Display title | Old Design.png |
| 4 | Browse Distinctions > How It Works | "Select a distinction type that matches your partnership" | Step text | N/A | — | — | — | Step 1 content | Old Design.png |
| 5 | Browse Distinctions > How It Works | "Enter recipient company information" | Step text | N/A | — | — | — | Step 2 content | Old Design.png |
| 6 | Browse Distinctions > How It Works | "NFTs are automatically minted and sent to both companies" | Step text | N/A | — | — | — | Step 3 content | Old Design.png |
| 7 | Browse Distinctions > How It Works | "Both parties receive +10% points distribution" | Step text | N/A | — | — | — | Step 4 content | Old Design.png |
| 8 | Browse Distinctions | "Company Information" | Section header | N/A | — | — | — | Display for Company profile | Old Design.png |
| 9 | Browse Distinctions | "Account Information" | Section header | N/A | — | — | — | Display for Individual/Public Figures profile | Old Design.png |
| 10 | Browse Distinctions | Distinction name | Text | N/A | — | — | — | Philanthropist / Investor / Bridge | Old Design.png |
| 11 | Browse Distinctions | Price | Text | N/A | — | — | — | Display distinction price per company class (CMR 06, BR 01) | Old Design.png |
| 12 | Browse Distinctions | "Non-sellable, transferable 1x" | Badge | N/A | — | — | — | Display attributes hint | Old Design.png |
| 13 | Browse Distinctions | "Purchase Distinction" | Button (Primary CTA) | Yes (for eligible classes) | Disabled for Class 0 | — | — | On click → Select recipient screen | Old Design.png |
| 14 | Browse Distinctions > Important Notes | "Important Notes" | Section title | N/A | — | — | — | Display title | Old Design.png |
| 15 | Browse Distinctions > Important Notes | Anti-Return Check content | Text | N/A | — | — | — | Anti-Return check rule description | Old Design.png |
| 16 | Browse Distinctions > Important Notes | Automatic Distribution content | Text | N/A | — | — | — | Auto mint/distribution rule | Old Design.png |
| 17 | Browse Distinctions > Important Notes | Points System content | Text | N/A | — | — | — | +10% points distribution rule | Old Design.png |

### 4.2 Tài liệu mới (New Design) — Step 1: Browse Distinctions

| # | Screen / Section | Label (verbatim) | Type | Required | Default | Placeholder | Enum values | Description / Constraint | Source |
|---|------------------|------------------|------|----------|---------|-------------|-------------|--------------------------|--------|
| 1 | Browse Distinctions | "Browse Distinctions" | Page title | N/A | — | — | — | Display title | New Design.png |
| 2 | Browse Distinctions | "Choose a distinction type to recognize your business partners with blockchain-based NFT certificates" | Subtitle | N/A | — | — | — | — | Display sub-title | New Design.png |
| 3 | Browse Distinctions | "How It Works" | Section title | N/A | — | — | — | Display title | New Design.png |
| 4 | Browse Distinctions | Distinction Types | Display list | N/A | — | — | — | Collaboration / Investor / Bridge | New Design.png |
| 5 | Browse Distinctions | "Select" (button) | Button | Yes | Disabled when activations remaining = 0 | — | — | Enable when activations remaining > 0 | New Design.png |
| 6 | Browse Distinctions | "Important Notes" | Section title | N/A | — | — | — | Display title | New Design.png |

### 4.3 Tài liệu cũ (Old Design) — UC-5.2 Select Recipient

| # | Screen / Section | Label (verbatim) | Type | Required | Default | Placeholder | Enum values | Description / Constraint | Source |
|---|------------------|------------------|------|----------|---------|-------------|-------------|--------------------------|--------|
| 1 | Select Recipient | "Purchase + <Distinction name>" | Header | N/A | — | — | — | Display title | Old Design.png |
| 2 | Select Recipient | "Select the recipient for this distinction" | Subtitle | N/A | — | — | — | Display sub-title | Old Design.png |
| 3 | Select Recipient | Back arrow icon | Icon button | No | — | — | — | Navigate back to Browse Distinctions | Old Design.png |
| 4 | Select Recipient | Search bar | Text input | No | — | "Search by user name, company name or email..." | — | Search existing recipients | Old Design.png |
| 5 | Select Recipient | "New Recipient" button | Button (Secondary) | No | Enable | — | — | On click → Create New Recipient screen | Old Design.png |
| 6 | Select Recipient | Recipient info card (Company) | Display card | N/A | — | — | — | Blue tag: Company name, email, country, full address | Old Design.png |
| 7 | Select Recipient | Recipient info card (Public Figures) | Display card | N/A | — | — | — | Purple tag: username/artist name, email, country, full address | Old Design.png |
| 8 | Select Recipient | Recipient info card (Individual) | Display card | N/A | — | — | — | Green tag: username, email, country, full address | Old Design.png |
| 9 | Select Recipient | "Continue to Checkout" | Button (Primary CTA) | Yes | Disabled until Start Selection | — | — | Enabled after Start Selection | Old Design.png |

### 4.4 Tài liệu cũ (Old Design) — UC-5.3 Checkout/Confirm Order

| # | Screen / Section | Label (verbatim) | Type | Required | Default | Placeholder | Enum values | Description / Constraint | Source |
|---|------------------|------------------|------|----------|---------|-------------|-------------|--------------------------|--------|
| 1 | Checkout | "Checkout" | Page title | N/A | — | — | — | Display title | Old Design.png |
| 2 | Checkout | "Review and complete your purchase" | Subtitle | N/A | — | — | — | Display sub-title | Old Design.png |
| 3 | Checkout | Back arrow icon | Icon button | No | — | — | — | Navigate back | Old Design.png |
| 4 | Checkout > Order Summary | "Order Summary" | Section title | N/A | — | — | — | Display title | Old Design.png |
| 5 | Checkout > Order Summary | Distinction Type | Text | N/A | — | — | — | Philanthropist / Investor / Bridge | Old Design.png |
| 6 | Checkout > Order Summary | Recipient | Text | N/A | — | — | — | Company name / user name / artist name | Old Design.png |
| 7 | Checkout > Order Summary | Recipient Email | Text | N/A | — | — | — | Email address | Old Design.png |
| 8 | Checkout > Order Summary | Recipient Country | Text | N/A | — | — | — | Country | Old Design.png |
| 9 | Checkout > Order Summary | Total | Text | N/A | — | — | — | Distinction price per class (CMR 06, BR 01) | Old Design.png |
| 10 | Checkout > Order Summary | "Estimated points distributed" | Text | N/A | — | — | — | + 20 points for each company (tài liệu mới) / +10% (tài liệu cũ) | Old Design.png |
| 11 | Checkout > Payment Method | "Payment Method" | Section title | N/A | — | — | — | Display title | Old Design.png |
| 12 | Checkout > Payment Method | Stripe Payment (Fiat) — Credit/Debit Card | Radio/Checkbox | Yes | Selected | — | — | Default selected | Old Design.png |
| 13 | Checkout > Payment Method | Terms of Service checkbox | Checkbox | Yes | Unchecked | — | — | Must check to enable Pay button | Old Design.png |
| 14 | Checkout > Payment Method | "Pay + <price>" | Button (Primary CTA) | Yes | Disabled until checkbox checked | — | — | Redirect to Stripe | Old Design.png |

### 4.5 Tài liệu mới (New Design) — Confirmation Pop-up

| # | Screen / Section | Label (verbatim) | Type | Required | Default | Placeholder | Enum values | Description / Constraint | Source |
|---|------------------|------------------|------|----------|---------|-------------|-------------|--------------------------|--------|
| 1 | Confirmation Pop-up | "NFT Minted successfully" | Pop-up title | N/A | — | — | — | Display title | New Design.png |
| 2 | Confirmation Pop-up | "<X> distinction credit(s) remaining" | Subtext | N/A | — | — | X = activations remaining | Display after mint success | New Design.png |
| 3 | Confirmation Pop-up | Summary section | Section | N/A | — | — | — | Display distinction type, recipient info, total | New Design.png |
| 4 | Confirmation Pop-up | "Mint" | Button | Yes | Enable | — | — | Trigger mint NFT | New Design.png |
| 5 | Confirmation Pop-up | "Close" | Button | No | Enable | — | — | Back to distinction selection page | New Design.png |

---

## 5. Object Attributes & Behavior Definition

> **Instructions:** Determine the state and response of each UI object based on specific system conditions.

| Object / Component | System States | Interaction Matrix | Object Behavior (Data/State Change Context) |
|--------------------|---------------|--------------------|---------------------------------------------|
| "Purchase Distinction" button (Old) | Disabled for Class 0; Enabled for Class 1-7 | Click → Open "Select Start Selection" screen | Class 0 → show MSG 25 |
| "Select" button (New) | Disabled when activations remaining = 0; Enabled when > 0 | Click → Open "Select Start Selection" screen | Class 0 → show MSG 25 |
| Search bar (Select Start Selection) | Enabled by default | Text input → search by Start name/company name/email | Enter → show search results; no match → show MSG-11 |
| "Continue to Checkout" button | Disabled until Start Selection selected | Click | Enabled after Start Selection selected; on click → Checkout screen |
| "New Start Selection" button | Enabled by default | Click → Open Create New Start Selection form | N/A |
| Recipient info card | Display only (selected state varies) | Click to select; highlighted when selected | Selected → enabled "Continue to Checkout" |
| "Continue to Checkout" (anti-return check) | Disabled if same Start + same distinction type in same year | Click → check anti-return rule | Same combination exists → show MSG 28 |
| Terms of Service checkbox | Unchecked by default | Click to toggle | Unchecked → Pay button disabled |
| "Pay + <price>" button | Disabled until Terms checkbox checked | Click | Checked → Enabled → redirect to Stripe |
| "Mint" button (New) | Enabled by default | Click | Triggers mint → shows "NFT Minted successfully" pop-up | Class 0 → show MSG 25 |

---

## 6. Functional Logic & Workflow Decomposition

### 6.1 Function: Browse Distinctions (Step 1)

**A. Workflows**

| Step | Actor | Action | System Response (Happy Path) | Alternative Flows | Exception & Error Flows |
|------|-------|--------|------------------------------|-------------------|-------------------------|
| 1 | User | Navigate to "Distinctions" from menu | System displays "Browse Distinctions" screen with 3 distinction types | N/A | User not logged in → redirect to login |
| 2 | User | View distinction info (price, attributes) | System displays price per class + attributes (Non-sellable, transferable 1x) | N/A | N/A |
| 3 | User | Click "Purchase Distinction" (Old) / "Select" (New) | System checks user class; If Class 0 → show MSG 25; Else → Open "Select Start Selection" screen | N/A | Class 0 → show MSG 25 |

**B. Business Rules & Validations**

| Field / Object | Required | Format / Constraint | Min / Max | Error Message *(exact text)* |
|----------------|----------|---------------------|-----------|-------------------------------|
| Distinction price | N/A | CMR 06 — Swiss Formatting (apostrophe for thousands, comma for decimals) | CHF 19 (min, Individual Bridge) to CHF 35,000 (max) | N/A |
| Individual Bridge purchase | N/A | Only Bridge allowed at CHF 19; No points distribution | N/A | MSG 25 if Class 0 attempts |
| Activations remaining (New) | Yes | Must be > 0 to enable Select button | 0-10 activations | Button disabled if 0 remaining |

**C. UI/UX Feedback**

* **Loading States:** N/A (static content)
* **Toast Messages:**
  - MSG 25: "Class 0 không được phép thực hiện giao dịch này" (hoặc message tương ứng cho Class 0)
* **Error Codes:**
  - MSG 25: Class 0 restriction on purchase
  - MSG-11: No matching results in Start Selection search

---

### 6.2 Function: Select Recipient (Step 2)

**A. Workflows**

| Step | Actor | Action | System Response (Happy Path) | Alternative Flows | Exception & Error Flows |
|------|-------|--------|------------------------------|-------------------|-------------------------|
| 1 | User | Click "Purchase Distinction" → OR click "New Start Selection" | System displays Start Selection screen | User clicks "New Start Selection" → Create New Start Selection form | N/A |
| 2 | User (existed Start Selection) | Search for existing Start Selection | System shows matching results | No match → MSG-11 + show empty state | No match → show MSG-11 |
| 3 | User | Click to select Start Selection | Start Selection card highlighted; "Continue to Checkout" enabled | N/A | N/A |
| 4 | User | Click "Continue to Checkout" | System validates anti-return rule; If violation → show MSG 28; Else → open Checkout screen | Start Selection already has same distinction type + same Start + same year → show MSG 28 | MSG 28 |
| 5 | User (new Start Selection) | Fill "Create New Start Selection" form | System validates required fields | Not all required fields filled → button disabled | CMR 22 |
| 6 | User | Click "Create & Select" | System validates anti-return; If violation → show MSG 28; Else → open Checkout screen | Not all required fields filled → button disabled | MSG 28 |

**B. Business Rules & Validations**

| Field / Object | Required | Format / Constraint | Min / Max | Error Message *(exact text)* |
|----------------|----------|---------------------|-----------|-------------------------------|
| Start Type selection | Yes | Company / Public Figures / Individual | N/A | N/A |
| Company fields | Yes | Company name, Email, Country, Full address | CMR 17 (max 255 chars for short text) | MSG-02 if required field empty |
| Public Figures fields | Yes | First name, Last name, Artist name (optional), Email, Country, Full address | CMR 17, CMR 03 (email format) | MSG-02 / MSG 03 |
| Individual fields | Yes | First name, Last name, Email, Country, Full address | CMR 17, CMR 03 | MSG-02 / MSG 03 |
| Anti-return check (CMR 20) | Yes | No same distinction type between same A+B in same year | N/A | MSG 28 |
| Email duplicate resolution | Yes | If email exists + same info → consolidate; If email exists + different info → new record | N/A | N/A |

**C. UI/UX Feedback**

* **Loading States:** Spinner during search or form submission
* **Toast Messages:**
  - MSG-11: "Không tìm thấy kết quả phù hợp"
  - MSG 28: "Không thể mua distinction này do đã tồn tại giao dịch tương tự trong năm nay" (anti-return violation)
  - MSG 04: "Hủy bỏ thao tác thành công" (Cancel button)
* **Error Codes:**
  - MSG-02: Required field validation
  - MSG 03: Email format validation (CMR 03)

---

### 6.3 Function: Confirmation / Checkout (Step 3)

**A. Workflows**

| Step | Actor | Action | System Response (Happy Path) | Alternative Flows | Exception & Error Flows |
|------|-------|--------|------------------------------|-------------------|-------------------------|
| 1 | User | Reach Checkout screen | System displays Order Summary with distinction type, Start Selection info, total, estimated points | N/A | N/A |
| 2 | User | Check Terms of Service checkbox | Checkbox toggled; "Pay + <price>" button enabled | N/A | Unchecked → button disabled |
| 3 | User | Click "Pay + <price>" (Old) / "Mint" (New) | System processes payment → mint NFT → distribute points | User clicks "Back" → return to previous screen | Payment failure → error handling |
| 4 | User | Display "NFT Minted successfully" pop-up | System shows confirmation with remaining activations count | N/A | N/A |
| 5 | User | Click "Close" (New) | System returns to distinction selection screen | N/A | N/A |

**B. Business Rules & Validations**

| Field / Object | Required | Format / Constraint | Min / Max | Error Message *(exact text)* |
|----------------|----------|---------------------|-----------|-------------------------------|
| Terms of Service checkbox | Yes | Must be checked to enable Pay/Mint button | N/A | Button disabled until checked |
| Points distribution (New) | N/A | 10% buyer + 20 points for each partner | N/A | N/A |
| Points distribution (Old) | N/A | 10% buyer + 10% recipient + 10% pool | N/A | N/A |
| Activations remaining (New) | N/A | Display after mint: X = current activations remaining - 1 | N/A | N/A |
| Badge issuance (first purchase) | N/A | Buyer receives badge + EMC 12; Recipient receives badge + EMC 13 | N/A | N/A |

**C. UI/UX Feedback**

* **Loading States:** Spinner on Pay/Mint button during processing
* **Toast Messages:**
  - Success: "NFT Minted successfully" pop-up
  - EMC 12: "Chúc mừng bạn đã nhận badge từ Partners Week"
  - EMC 13: "Chúc mừng bạn đã được vinh danh với distinction"
* **Error Codes:**
  - MSG 25: Class 0 restriction on purchase
  - MSG 28: Anti-return violation

---

## 7. Functional Integration Analysis

> **Instructions:** Analyze and evaluate the linkages and influences between the cataloged functions, acting as an integration check between functions.

| Trigger Function / Action | Impact Analysis (Cross-function influence) | Data Consistency Verification |
|---------------------------|--------------------------------------------|-------------------------------|
| Select Start Selection → Checkout | Start Selection info flows to Order Summary; Recipient email used for anti-return validation | Verify Order Summary displays correct Start Selection data |
| Checkout → NFT Minting | NFT mint triggered only after payment success (Old) / Mint button click (New) | Verify NFT appears in both buyer and recipient wallets |
| NFT Minting → Points Distribution | 10% to buyer, 20 points to partner (New) / 10% to buyer, 10% to recipient, 10% pool (Old) | Verify points appear in respective wallets |
| First Purchase → Badge Issuance | Buyer and recipient receive badges in User Profile + email notifications | Verify badges appear in Profile + EMC 12/13 sent |
| New Start Selection → Wallet creation | If Start Selection not signed up → system creates custodial wallet | Verify wallet created when recipient becomes active user |

---

## 8. Acceptance Criteria

> **Instructions:** Acceptance criteria must be written in a verifiable pass/fail format, using the Given / When / Then structure.

| AC # | Scenario | Given *(precondition)* | When *(user action)* | Then *(expected result)* |
|------|----------|------------------------|----------------------|--------------------------|
| AC-01 | Browse Distinctions — Happy Path | User đã đăng nhập với Class 1-6 | User navigate đến Distinctions | System hiển thị 3 distinction types với giá và attributes |
| AC-02 | Browse Distinctions — Class 0 Block | User đã đăng nhập với Class 0 | User click "Purchase Distinction" / "Select" button | System hiển thị MSG 25 và không cho phép mua |
| AC-03 | Individual — Bridge Only | User đã đăng nhập với Individual class | User xem distinction list | System hiển thị chỉ Bridge distinction với giá CHF 19 |
| AC-04 | Individual — No Points | User là Individual và mua Bridge | Purchase hoàn tất | Không có points distribution cho buyer |
| AC-05 | Start Selection — Search Exist | User đã có Start Selection trong hệ thống | User search bằng email/company name | System hiển thị matching Start Selection(s) |
| AC-06 | Start Selection — No Result | User search với ký tự không khớp | User click Enter | System hiển thị MSG-11 |
| AC-07 | Start Selection — Anti-Return Check | A và B chưa có distinction cùng loại trong năm 2026 | User A click "Continue to Checkout" để mua cho B | System cho phép tiếp tục |
| AC-08 | Start Selection — Anti-Return Violation | A đã mua Philanthropist cho B trong năm 2026 | User B click "Continue to Checkout" để mua Philanthropist cho A | System hiển thị MSG 28 và block transaction |
| AC-09 | Start Selection — New Company | User chọn tạo Start Selection mới, type = Company | User điền đầy đủ thông tin và click "Create & Select" | System lưu Start Selection mới và hiển thị Checkout |
| AC-10 | Start Selection — Duplicate Email Consolidation | Email "company@email.com" đã tồn tại với info khác | User tạo Start Selection mới với email trùng | System tạo record mới riêng biệt và lưu |
| AC-11 | Checkout — Order Summary | User đã hoàn thành Select Distinction và Select Start Selection | User vào Checkout screen | System hiển thị Distinction Type, Start Selection info, Total, Estimated points |
| AC-12 | Checkout — Terms Checkbox | User chưa check Terms of Service | User chưa tick checkbox | "Pay + <price>" button vẫn disabled |
| AC-13 | Checkout — Terms Checked | User đã tick Terms of Service checkbox | User tick checkbox | "Pay + <price>" button enabled |
| AC-14 | Checkout — Mint Success (New) | User click "Mint" button | Mint process hoàn tất | System hiển thị "NFT Minted successfully" pop-up với remaining activations count |
| AC-15 | Points Distribution — Buyer (New) | User mua distinction | Purchase hoàn tất | Buyer nhận 10% points của NFT price |
| AC-16 | Points Distribution — Recipient (New) | User là recipient | Purchase hoàn tất | Recipient nhận 20 points |
| AC-17 | Badge — First Purchase | Buyer thực hiện purchase lần đầu | Purchase hoàn tất | Buyer nhận badge trong User Profile + EMC 12 |
| AC-18 | Badge — First Recipient | Recipient nhận distinction lần đầu | Purchase hoàn tất | Recipient nhận badge trong User Profile + EMC 13 |
| AC-19 | Wallet — New Recipient | Start Selection chưa đăng ký | Purchase hoàn tất | System tạo custodial wallet cho Start Selection |
| AC-20 | Activations — Remaining Display (New) | User có X activations remaining | Mint hoàn tất | Pop-up hiển thị "X-1 distinction credit(s) remaining" |

---

## 9. Non-functional Requirements

| Category | Requirement | Source / Reference |
|----------|-------------|-------------------|
| Performance | NFT minting nên hoàn tất trong thời gian hợp lý (< 30s) để tránh ảnh hưởng UX | N/A |
| Security | NFT non-sellable, chỉ transferable 1x to non-custodial wallet | BR (từ tài liệu) |
| Compatibility | Web responsive — hỗ trợ Chrome/Edge/Firefox/Safari latest-2 versions | project-context-master.md §8 |
| Accessibility | WCAG AA color contrast; screen reader labels cho buttons và inputs | COMMON rules |

---

## 10. Open Questions & Dependencies

### 10.1 Open Questions

| # | Question / Issue | Context | Owner | Status |
|---|-----------------|---------|-------|--------|
| Q1 | ~~Model conflict~~ — Stripe vs Activations | ~~Tài liệu cũ vs mới conflict~~ | BA | ✅ Resolved (v2): Tài liệu Cũ = Stripe checkout; Tài liệu Mới = dùng activation đã mua |
| Q2 | ~~Points distribution ambiguity~~ | ~~Conflict 10%+10%+10% vs 10%+20 points~~ | BA | ✅ Resolved (v2): Cả 2 đúng — Cũ=logic hiện tại, Mới=logic sắp tới |
| Q3 | ~~Pricing không map với distinction type~~ | ~~Không rõ pricing theo type hay theo class~~ | BA | ✅ Resolved (v2): Theo tài liệu Mới — giá theo package/class, không theo từng type |
| Q4 | ~~Activations tracking~~ | ~~Mỗi lần mint giảm bao nhiêu?~~ | BA | ✅ Resolved (v2): Mỗi lần mint giảm 1 |
| Q5 | ~~EMC 12/13 email content~~ | ~~Không có email template~~ | BA | ✅ Resolved (v2): EMC12 & EMC13 gửi cùng info — tên+email buyer/recipient, distinction type, points |
| Q6 | ~~Badge issuance criteria~~ | ~~First-time per user hay per type?~~ | BA | ✅ Resolved (v2): Không duy nhất cho 1 account — A mint cho nhiều recipient vẫn chỉ 1 badge |
| Q7 | ~~Year 2+ Discount trigger~~ | ~~Auto-detect hay user opt-in?~~ | BA | ✅ Resolved (v2): Có thể chọn không dùng |
| Q8 | ~~Individual points exception~~ | ~~Individual buyer có được nhận points?~~ | BA | ✅ Resolved (v2): Buyer (Individual) không được nhận points |
| Q9 | ~~Anti-return enforcement location~~ | ~~FE hay BE hay cả hai?~~ | BA | ✅ Resolved (v2): Frontend |
| Q10 | ~~Wallet creation timing~~ | ~~Mint ngay hay chờ recipient sign up?~~ | BA | ✅ Resolved (v2): Mint ngay |

### 10.2 Dependencies

- **Stripe Payment (Old)**: Dependencies on Stripe sandbox, webhook handling, payment success/failure flows
- **BASE Blockchain**: NFT minting via Tatum API on BASE network
- **Tatum API**: Custodial wallet creation, IPFS metadata storage
- **Email Service**: EMC 12, EMC 13 notifications

---

## 11. Change Log

**Audit Conducted:**
- Date: 2026-05-27
- Auditor: QC Agent (qc-uc-read skill)
- Mode: First Audit
- Documents analyzed: UC-1.5.Distinction Purchase.pdf (cũ), UC-1.5. Old Distinction Purchase Design.png, UC-1.5. New Distinction Purchasing Design.png, UC-1.5.New Distinction Purchase Update.pdf, PWMVP-PartnersWeek-Commonrules.pdf

---

## 🟢 What's Good

1. **Tài liệu cũ có cấu trúc rõ ràng**: Tách 3 UC riêng biệt (Browse, Select Start Selection, Checkout) với đầy đủ mô tả screen, component, behavior
2. **Anti-return rule được document rõ**: Có đầy đủ logic anti-return với MSG 28 ở cả Step 2 và Step 3
3. **Start Selection duplicate resolution**: Chi tiết scenario cho việc xử lý trùng email với các rules cụ thể (same email + same info = consolidate; same email + different info = new record)
4. **Common rules được reference đúng cách**: CMR 01, CMR 03, CMR 06, CMR 20, CMR 22… giúp traceable
5. **Points distribution logic rõ ràng**: 10% buyer + 10% recipient + 10% pool (old) được mô tả chi tiết

---

## 🧪 Testability Outlook

**What CAN be tested now:**
1. ✅ **Browse Distinctions flow**: Có đủ thông tin để test hiển thị distinction types, pricing, attributes theo class
2. ✅ **Select Recipient flow (existed)**: Search functionality, anti-return check (FE), recipient validation
3. ✅ **Select Recipient flow (new)**: Form fields validation, duplicate email resolution
4. ✅ **Checkout/Confirmation flow (Old)**: Order summary display, Terms checkbox, Pay button state
5. ✅ **Points calculation (Old logic)**: Verify 10%+10%+10% distribution theo pricing
6. ✅ **Badge issuance**: 1 badge per account — test được cho cả buyer và recipient
7. ✅ **Activations (New logic)**: Mỗi lần mint giảm 1 — test remaining count

**What CANNOT be tested yet (blocked by gaps):**
1. ❌ **Activations model details (New)**: Tài liệu Mới thiếu thông tin về cách activations được purchase ban đầu — chưa rõ user mua activation package ở đâu và như thế nào
2. ⚠️ **Year 2+ Discount flow**: Đã biết user có thể chọn không dùng, nhưng chưa có detail về anniversary detection logic
3. ⚠️ **New Design UI flows**: Tài liệu Mới có ít UI detail hơn tài liệu Cũ — cần bổ sung wireframe cho Confirmation pop-up

**Suggested test focus areas** *(once gaps are resolved)*:
- Happy path (Old): Browse → Select Recipient → Checkout → Stripe Payment → NFT Minted
- Happy path (New): Browse → Select Recipient → Confirmation → Mint → NFT Minted
- Anti-return: Test MSG 28 khi A-B đã có distinction cùng năm
- Points: Verify 10%+10%+10% distribution và badge issuance
- Individual: Verify Bridge-only purchase và không nhận points

---

## 📌 Summary & Recommendation

**Overall State:**
Tài liệu UC-1.5 có 2 phiên bản khác nhau đáng kể (cũ và mới), tạo ra **conflict không thể giải quyết chỉ bằng đọc tài liệu**. Tài liệu cũ mô tả Stripe payment + per-NFT purchase model với 3 UC riêng biệt. Tài liệu mới rút gọn thành "activations/packaging" model và bỏ Stripe payment. Điểm khác biệt quan trọng nhất là **points distribution calculation** (old: 10%+10%+10%; new: 10% + 20 points per partner).

**Key Actions Required:**
1. **BA phải xác nhận**: Phiên bản nào là đúng (old hay new hay hybrid)?
2. **Points calculation**: Cần BA confirm rule cuối cùng
3. **Payment model**: Xác nhận có Stripe hay không trong MVP V1.2
4. **Email templates**: Cần spec cho EMC 12/13 notifications

**Recommendation:**
⚠️ **CONDITIONALLY READY** — QA có thể bắt đầu design test cases cho Happy Path flows, nhưng **phải có BA confirmation về model conflict trước khi design test cases cho payment/points flows**. Các gaps Q1-Q3 (priority High) cần được resolved trước khi proceed với negative test cases và edge cases.

---

## Audit Summary

| # | Knowledge Area | Max Pts | Score | Status |
| --------------- | ---------------------------------------- | ------------- | ----- | ------------------------- |
| 1 | Feature Identity | 5 | 4/5 | ⚡ Partial |
| 2 | Objective & Scope | 5 | 4/5 | ⚡ Partial |
| 3 | Actors & User Roles | 10 | 8/10 | ⚡ Partial |
| 4 | Preconditions & Postconditions | 10 | 8/10 | ⚡ Partial |
| 5 | UI Object Inventory & Mapping | 15 | 8/15 | ⚡ Partial |
| 6 | Object Attributes & Behavior Definition | 20 | 14/20 | ⚡ Partial |
| 7 | Functional Logic & Workflow Decomposition | 20 | 16/20 | ⚡ Partial |
| 8 | Functional Integration Analysis | 20 | 12/20 | ⚡ Partial |
| 9 | Acceptance Criteria | 20 | 15/20 | ⚡ Partial |
| 10 | Non-functional Requirements | 5 | 2/5 | ⚠️ Missing |
| **Total** | | **130** | **91/130 → 70,0/100** | ⚠️ **CONDITIONALLY READY** |

> **Sau khi BA trả lời Q1-Q10 (v2):** Điểm đã được cải thiện từ 60,0 → 70,0. Các conflict chính (Stripe vs Activations, Points rules) đã được giải quyết.

---

## Unified Gap & Question Report

| ID | Priority | Ref | Question | Why It Matters | Status |
|----|----------|-----|----------|----------------|--------|
| Q1 | High | Stripe vs Activations model | Tài liệu cũ (Stripe) vs Mới (activations) — BA xác nhận đã resolved: Cũ = logic hiện tại, Mới = logic sắp tới | Critical impact on payment flow | ✅ Resolved |
| Q2 | High | Points calculation | 10%+10%+10% vs 10%+20 points — BA xác nhận: Cũ=logic hiện tại, Mới=logic sắp tới | Points verification | ✅ Resolved |
| Q3 | High | Pricing table | Package pricing theo class, không theo từng distinction type | Test data accuracy | ✅ Resolved |
| Q4 | Medium | Activations tracking | Mỗi lần mint giảm 1 | Balance calculation | ✅ Resolved |
| Q5 | Medium | EMC 12/13 email content | Cùng format — tên+email buyer/recipient, distinction type, points | Email verification | ✅ Resolved |
| Q6 | Medium | Badge issuance criteria | 1 badge per account, không phụ thuộc số recipient | Test precondition | ✅ Resolved |
| Q7 | Medium | Year 2+ Discount trigger | User có thể chọn không dùng | Discount test coverage | ✅ Resolved |
| Q8 | Low | Individual points exception | Buyer (Individual) không được nhận points | Individual flow coverage | ✅ Resolved |
| Q9 | Low | Anti-return enforcement | Frontend (FE) only | Bypass scenario testing | ✅ Resolved |
| Q10 | Low | Wallet creation timing | Mint ngay, không cần chờ recipient sign up | Test sequencing | ✅ Resolved |

---

*UC Readiness Review — UC-1.5 v1.0 — Generated by qc-uc-read skill — 2026-05-27*
