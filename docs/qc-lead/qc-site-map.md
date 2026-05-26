# QC Site Map: PartnersWeek

**Trạng thái:** Draft  
**Mode:** Update  
**Ngày tạo/cập nhật:** 2026-05-26  
**Người chuẩn bị:** QC Site Map Agent  
**Người review:** QC Lead  
**Baseline:** `project-context-master.md`  
**Mục đích:** Cung cấp bản đồ site/screen/navigation theo góc nhìn QC để hỗ trợ review spec, thiết kế scenario/test case, đánh giá impact, regression và verify bug.

> File này là screen-first QC site map.  
> File này không thay thế `project-context-master.md`, feature list, spec, wireframe, API doc hoặc `qc-dashboard.md`.

---

## 1. Metadata

| Thuộc tính | Giá trị |
|---|---|
| Project / Product | PARTNERS WEEK® |
| Platform | Web (responsive) |
| Source baseline | `project-context-master.md` |
| Site map readiness | Partial |
| Source quality | Derived (từ UC List + Specifications + WBS BA Planning, chưa có wireframe/official sitemap) |
| Dashboard relationship | Feature-level handoff only |
| Ghi chú | Chưa có wireframe hoặc official navigation doc. Screen inventory derived từ UC List. |

---

## 2. Sources consolidated

| # | File | Version | Loại | Ngày đọc cuối |
|---|---|---|---|---|
| 1 | project-context-master.md | no-version | Project baseline | 2026-05-26 |
| 2 | UC List.md | no-version | Feature inventory / Screen evidence | 2026-05-25 |
| 3 | PARTNERS_WEEK_Specifications_EN.md | no-version | Scope / Business rules | 2026-05-25 |
| 4 | WBS.xlxs (BA Planning sheet) | no-version | UC breakdown / Screen evidence / Business rules | 2026-05-26 |

---

## 3. Site / Portal / App overview

| Site / Portal / App | Mục đích | Nhóm user chính | Module / Area chính | Ghi chú QC |
|---|---|---|---|---|
| User Site (partnersweek.com) | Mua distinction, quản lý NFT/wallet, tham gia events, public directory | Company (A & B), Individual, Public Figure | Auth, Profile, Catalog/Purchase, NFT/Wallet, Events, Directory, Dashboard | Web responsive, FR & EN |
| Admin Site | Quản lý hệ thống, distribute awards/points, manage events/distinctions/users | Admin | Auth, Profile, Admin Mgmt, User Mgmt, Distinction Mgmt, Event Mgmt, Points, Awards, Dashboard | Web |

---

## 4. Screen-first site map tree

```text
PartnersWeek
├── User Site (partnersweek.com)
│   ├── Public
│   │   ├── Landing Page (Coming Soon)
│   │   ├── Public Directory (Search)
│   │   └── Homepage
│   ├── Auth
│   │   ├── Sign Up
│   │   ├── Sign In
│   │   └── Forgot Password
│   ├── Profile
│   │   ├── View Profile
│   │   ├── Edit Profile
│   │   └── Change Password
│   ├── Catalog / Purchase
│   │   ├── Browse Catalog
│   │   ├── Select Recipient
│   │   └── Confirm Order (Stripe Payment)
│   ├── NFT / Wallet
│   │   ├── Wallet Overview
│   │   └── NFT Transfer
│   ├── Events
│   │   ├── Event List
│   │   ├── Event Details
│   │   └── Purchase Ticket
│   └── User Dashboard
│       ├── View Owned Distinctions
│       ├── View Points Balance
│       └── View Transaction History
│
└── Admin Site
    ├── Auth
    │   ├── Sign In
    │   └── Forgot Password
    ├── Profile
    │   ├── View Profile
    │   ├── Edit Profile
    │   ├── Change Password
    │   └── Delete Profile
    ├── Admin Management
    │   ├── Admin List
    │   └── Create Admin Account
    ├── User Management
    │   ├── User List
    │   ├── User Details
    │   ├── Activate/Deactivate User
    │   ├── Waitlist
    │   ├── Registration Details
    │   └── Company Approval
    ├── Distinction Management
    │   ├── Distinction List
    │   └── Edit Distinction
    ├── Event Management
    │   ├── Event List & Details
    │   └── Create Event
    ├── Points Distribution
    │   ├── Points Distribution History
    │   └── Assign Points
    ├── NFT Partners Awards
    │   ├── Awards Distribution History
    │   └── Distribute Awards
    ├── Distinction Distribute
    ├── Directory Management
    │   ├── Search Directory (IPFS)
    │   └── Manage Public Directory
    └── Admin Dashboard
```

---

## 5. Screen / Page inventory

| Screen ID | Site / Portal | Area / Module | Screen / Page | Type | Platform | Source | Status |
|---|---|---|---|---|---|---|---|
| SCR-001 | User | Public | Landing Page (Coming Soon) | Page | Web | Specifications | Derived |
| SCR-002 | User | Public | Public Directory | Page | Web | UC List (1.2) | Derived |
| SCR-003 | User | Public | Homepage | Page | Web | UC List (1.10) | Derived |
| SCR-004 | User | Auth | Sign Up | Page | Web | UC List (UC3.1) | Derived |
| SCR-005 | User | Auth | Sign In | Page | Web | UC List (UC3.2) | Derived |
| SCR-006 | User | Auth | Forgot Password | Page | Web | UC List (UC3.3) | Derived |
| SCR-007 | User | Profile | View Profile | Page | Web | UC List (UC4.1) | Derived |
| SCR-008 | User | Profile | Edit Profile | Page | Web | UC List (UC4.2) | Derived |
| SCR-009 | User | Profile | Change Password | Page | Web | UC List (UC4.3) | Derived |
| SCR-010 | User | Catalog/Purchase | Browse Catalog | Page | Web | UC List (UC5.1) | Derived |
| SCR-011 | User | Catalog/Purchase | Select Recipient | Page/Modal | Web | UC List (UC5.2) | Derived |
| SCR-012 | User | Catalog/Purchase | Confirm Order | Page | Web | UC List (UC5.3) | Derived |
| SCR-013 | User | NFT/Wallet | Wallet Overview | Page | Web | UC List (1.7) | Derived |
| SCR-014 | User | NFT/Wallet | NFT Transfer | Page/Modal | Web | UC List (1.6) | Derived |
| SCR-015 | User | Events | Event List | Page | Web | UC List (UC8.1) | Derived |
| SCR-016 | User | Events | Event Details | Page | Web | UC List (UC8.2) | Derived |
| SCR-036 | User | Events | Purchase Ticket | Page/Modal | Web | WBS (UC-8.3) | Derived |
| SCR-017 | User | Dashboard | User Dashboard | Dashboard | Web | UC List (1.9) | Derived |
| SCR-037 | User | Dashboard | View Owned Distinctions | Tab/Section | Web | WBS (UC-9.1) | Derived |
| SCR-038 | User | Dashboard | View Points Balance | Tab/Section | Web | WBS (UC-9.2) | Derived |
| SCR-039 | User | Dashboard | View Transaction History | Tab/Section | Web | WBS (UC-9.3) | Derived |
| SCR-018 | Admin | Auth | Sign In | Page | Web | UC List (UC10.1) | Derived |
| SCR-019 | Admin | Auth | Forgot Password | Page | Web | UC List (UC10.2) | Derived |
| SCR-020 | Admin | Profile | View Profile | Page | Web | UC List (UC11.1) | Derived |
| SCR-021 | Admin | Profile | Edit Profile | Page | Web | UC List (UC11.2) | Derived |
| SCR-022 | Admin | Profile | Change Password | Page | Web | UC List (UC11.3) | Derived |
| SCR-040 | Admin | Profile | Delete Profile | Page/Modal | Web | WBS (UC-11.3) | Derived |
| SCR-023 | Admin | Admin Mgmt | Admin List | Page | Web | UC List (UC12.1) | Derived |
| SCR-024 | Admin | Admin Mgmt | Create Admin Account | Page/Modal | Web | UC List (UC12.2) | Derived |
| SCR-025 | Admin | User Mgmt | User List | Page | Web | UC List (UC13.1) | Derived |
| SCR-041 | Admin | User Mgmt | User Details | Page | Web | WBS (UC-13.2) | Derived |
| SCR-042 | Admin | User Mgmt | Activate/Deactivate User | Action/Modal | Web | WBS (UC-13.3) | Derived |
| SCR-043 | Admin | User Mgmt | Waitlist | Page | Web | WBS (View waitlist) | Derived |
| SCR-044 | Admin | User Mgmt | Registration Details | Page | Web | WBS (View registration details) | Derived |
| SCR-045 | Admin | User Mgmt | Company Approval | Page/Modal | Web | WBS (Company approval) | Derived |
| SCR-026 | Admin | Distinction Mgmt | Distinction List | Page | Web | UC List (UC14.1) | Derived |
| SCR-027 | Admin | Distinction Mgmt | Edit Distinction | Page/Modal | Web | UC List (UC14.2) | Derived |
| SCR-028 | Admin | Event Mgmt | Event List & Details | Page | Web | UC List (UC15.1) | Derived |
| SCR-029 | Admin | Event Mgmt | Create Event | Page/Modal | Web | UC List (UC15.2) | Derived |
| SCR-030 | Admin | Points | Points Distribution History | Page | Web | UC List (UC16.1) | Derived |
| SCR-031 | Admin | Points | Assign Points | Page/Modal | Web | UC List (UC16.2) | Derived |
| SCR-032 | Admin | Awards | Awards Distribution History | Page | Web | UC List (UC17.1) | Derived |
| SCR-033 | Admin | Awards | Distribute Awards | Page/Modal | Web | UC List (UC17.2) | Derived |
| SCR-034 | Admin | Dashboard | Admin Dashboard | Dashboard | Web | UC List (2.18) | Derived |
| SCR-035 | Admin | Distinction | Distinction Distribute | Page | Web | UC List (2.19) | Derived |
| SCR-046 | Admin | Directory | Search Directory (IPFS) | Page | Web | WBS (Directory Management) | Derived |
| SCR-047 | Admin | Directory | Manage Public Directory | Page | Web | WBS (Directory Management) | Derived |

---

## 6. Navigation & screen flow

| Flow ID | Flow name | Role | Start screen | Main path | End screen / outcome | Related feature(s) | Notes |
|---|---|---|---|---|---|---|---|
| NAV-001 | Distinction Purchase | Company User | SCR-010 Browse Catalog | Browse → Select Recipient → Confirm Order (Stripe) | SCR-012 → NFT minted, points distributed | 1.5 (UC5.1-5.3) | Core flow |
| NAV-002 | User Registration | Visitor | SCR-001 Landing / SCR-003 Homepage | Landing/Home → Sign Up → Sign In | SCR-017 Dashboard | 1.3 (UC3.1-3.2) | Wallet auto-created |
| NAV-003 | NFT Transfer | Company User | SCR-013 Wallet | Wallet → NFT Transfer | SCR-014 → NFT in non-custodial wallet | 1.6 | 1x only, irreversible |
| NAV-004 | Event Ticket Purchase | Company with distinction | SCR-015 Event List | Event List → Event Details → Purchase Ticket (50 pts) | SCR-036 → Ticket issued | 1.8 (UC8.1-8.3) | Restricted access |
| NAV-005 | Admin Distribute Awards | Admin | SCR-032 Awards History | History → Distribute Awards | SCR-033 → NFT minted for recipient | 2.17 (UC17.1-17.2) | |
| NAV-006 | Admin Assign Points | Admin | SCR-030 Points History | History → Assign Points | SCR-031 → Points credited | 2.16 (UC16.1-16.2) | |
| NAV-007 | Admin Create Event | Admin | SCR-028 Event List | Event List → Create Event | SCR-029 → Event published | 2.15 (UC15.1-15.2) | |
| NAV-008 | Admin Company Approval | Admin | SCR-043 Waitlist | Waitlist → Registration Details → Company Approval | SCR-045 → Company approved/rejected | 2.13 | Từ WBS |

---

## 7. Role / access by screen

| Role / User type | Accessible site/module | Accessible screen | Key actions | Restriction / Rule | Source | Status |
|---|---|---|---|---|---|---|
| Visitor (unauthenticated) | User / Public | SCR-001, SCR-002, SCR-003, SCR-004, SCR-005, SCR-006 | View landing, directory, sign up/in | Không mua, không xem wallet/events | Specifications | Derived |
| Company (Class 0-6, Public Figure) | User / All modules | SCR-003 to SCR-017 | Mua distinction, transfer NFT, mua ticket event, view dashboard | Pricing theo class; event ticket chỉ khi có distinction/awards | UC List + Specifications | Derived |
| Individual (Class 7) | User / Limited | SCR-003 to SCR-009, SCR-010, SCR-012, SCR-017 | Chỉ mua "Pont" (CHF 19) | Không points distribution, không event access | Specifications | Derived |
| Admin | Admin / All modules | SCR-018 to SCR-047 | Full CRUD, distribute points/awards, manage events/distinctions/users, approve companies, manage directory | Full access | UC List + WBS | Derived |

---

## 8. Screen ↔ Feature mapping

| Screen ID | Screen / Page | Feature ID | Feature name | Mapping type | Regression anchor? | Notes |
|---|---|---|---|---|---|---|
| SCR-001 | Landing Page | 1.1 | Landing page | Primary | No | |
| SCR-002 | Public Directory | 1.2 | Public Directory | Primary | No | IPFS search |
| SCR-003 | Homepage | 1.10 | Homepage | Primary | No | |
| SCR-004 | Sign Up | 1.3 | User Authentication | Primary | Yes | Wallet auto-created |
| SCR-005 | Sign In | 1.3 | User Authentication | Primary | Yes | |
| SCR-006 | Forgot Password | 1.3 | User Authentication | Supporting | No | |
| SCR-007 | View Profile | 1.4 | User Profile | Primary | No | |
| SCR-008 | Edit Profile | 1.4 | User Profile | Primary | No | |
| SCR-009 | Change Password | 1.4 | User Profile | Supporting | No | |
| SCR-010 | Browse Catalog | 1.5 | Distinction Purchase | Primary | Yes | Core purchase entry |
| SCR-011 | Select Recipient | 1.5 | Distinction Purchase | Primary | Yes | Anti-return rule |
| SCR-012 | Confirm Order | 1.5 | Distinction Purchase | Primary | Yes | Stripe + NFT mint |
| SCR-013 | Wallet Overview | 1.7 | Wallet | Primary | Yes | Points + NFT display |
| SCR-014 | NFT Transfer | 1.6 | NFT Transfer | Primary | Yes | 1x limit |
| SCR-015 | Event List | 1.8 | Event Access | Primary | No | |
| SCR-016 | Event Details | 1.8 | Event Access | Primary | No | |
| SCR-036 | Purchase Ticket | 1.8 | Event Access | Primary | Yes | Restricted + 50 pts |
| SCR-017 | User Dashboard | 1.9 | User Dashboard | Primary | No | |
| SCR-037 | View Owned Distinctions | 1.9 | User Dashboard | Supporting | No | Sub-section of dashboard |
| SCR-038 | View Points Balance | 1.9 | User Dashboard | Supporting | No | Sub-section of dashboard |
| SCR-039 | View Transaction History | 1.9 | User Dashboard | Supporting | No | Sub-section of dashboard |
| SCR-018 | Admin Sign In | 2.10 | Admin Authentication | Primary | Yes | |
| SCR-019 | Admin Forgot Password | 2.10 | Admin Authentication | Supporting | No | |
| SCR-020 | Admin View Profile | 2.11 | Admin Profile | Primary | No | |
| SCR-021 | Admin Edit Profile | 2.11 | Admin Profile | Primary | No | |
| SCR-022 | Admin Change Password | 2.11 | Admin Profile | Supporting | No | |
| SCR-040 | Admin Delete Profile | 2.11 | Admin Profile | Supporting | No | Từ WBS |
| SCR-023 | Admin List | 2.12 | Admin Management | Primary | No | |
| SCR-024 | Create Admin Account | 2.12 | Admin Management | Primary | No | |
| SCR-025 | User List | 2.13 | User Management | Primary | No | |
| SCR-041 | User Details | 2.13 | User Management | Primary | No | Từ WBS |
| SCR-042 | Activate/Deactivate User | 2.13 | User Management | Supporting | No | Từ WBS |
| SCR-043 | Waitlist | 2.13 | User Management | Primary | No | Từ WBS |
| SCR-044 | Registration Details | 2.13 | User Management | Supporting | No | Từ WBS |
| SCR-045 | Company Approval | 2.13 | User Management | Primary | Yes | Từ WBS, gate cho user activation |
| SCR-026 | Distinction List | 2.14 | Distinction Management | Primary | No | |
| SCR-027 | Edit Distinction | 2.14 | Distinction Management | Primary | No | |
| SCR-028 | Event List & Details | 2.15 | Event Management | Primary | No | |
| SCR-029 | Create Event | 2.15 | Event Management | Primary | No | |
| SCR-030 | Points History | 2.16 | Points Distribution | Primary | Yes | |
| SCR-031 | Assign Points | 2.16 | Points Distribution | Primary | Yes | |
| SCR-032 | Awards History | 2.17 | NFT Partners Awards | Primary | No | |
| SCR-033 | Distribute Awards | 2.17 | NFT Partners Awards | Primary | Yes | Sellable NFT |
| SCR-034 | Admin Dashboard | 2.18 | Admin Dashboard | Primary | No | |
| SCR-035 | Distinction Distribute | 2.19 | Distinction Distribute | Primary | No | |
| SCR-046 | Search Directory (IPFS) | 2.20 | Directory Management | Primary | No | Từ WBS |
| SCR-047 | Manage Public Directory | 2.20 | Directory Management | Primary | No | Từ WBS |

### Feature-level coverage summary for dashboard

| Feature ID | Feature name | Mapped screen(s) | Site map status | Gap / Note |
|---|---|---|---|---|
| 1.1 | Landing page | SCR-001 | Mapped | |
| 1.2 | Public Directory | SCR-002 | Mapped | |
| 1.3 | User Authentication | SCR-004, SCR-005, SCR-006 | Mapped | |
| 1.4 | User Profile | SCR-007, SCR-008, SCR-009 | Mapped | |
| 1.5 | Distinction Purchase | SCR-010, SCR-011, SCR-012 | Mapped | Core flow |
| 1.6 | NFT Transfer | SCR-014 | Mapped | |
| 1.7 | Wallet | SCR-013 | Mapped | |
| 1.8 | Event Access | SCR-015, SCR-016, SCR-036 | Mapped | UC-8.3 tách riêng Purchase Ticket |
| 1.9 | User Dashboard | SCR-017, SCR-037, SCR-038, SCR-039 | Mapped | Sub-UCs từ WBS |
| 1.10 | Homepage | SCR-003 | Mapped | |
| 2.10 | Admin Authentication | SCR-018, SCR-019 | Mapped | |
| 2.11 | Admin Profile | SCR-020, SCR-021, SCR-022, SCR-040 | Mapped | Thêm Delete Profile từ WBS |
| 2.12 | Admin Management | SCR-023, SCR-024 | Mapped | |
| 2.13 | User Management | SCR-025, SCR-041, SCR-042, SCR-043, SCR-044, SCR-045 | Mapped | Thêm User Details, Activate/Deactivate, Waitlist, Registration Details, Company Approval từ WBS |
| 2.14 | Distinction Management | SCR-026, SCR-027 | Mapped | |
| 2.15 | Event Management | SCR-028, SCR-029 | Mapped | |
| 2.16 | Points Distribution | SCR-030, SCR-031 | Mapped | |
| 2.17 | NFT Partners Awards | SCR-032, SCR-033 | Mapped | |
| 2.18 | Admin Dashboard | SCR-034 | Mapped | |
| 2.19 | Distinction Distribute | SCR-035 | Mapped | |
| 2.20 | Directory Management | SCR-046, SCR-047 | Mapped | Mới từ WBS, Need confirm scope |

---

## 9. Screen ↔ Data / API / Integration / State touchpoints

| Screen / Flow | Data object / API / Integration / State | Rule / lifecycle liên quan | QC impact | Source |
|---|---|---|---|---|
| SCR-004 Sign Up | Tatum API (wallet creation) | Wallet auto-created on registration | Verify wallet exists after signup | Specifications |
| SCR-010-012 Purchase Flow | Stripe API (payment), Tatum API (NFT mint), BASE blockchain | Anti-return rule, class pricing, points 30% | Core integration test: payment → mint → points | Specifications |
| SCR-014 NFT Transfer | BASE blockchain, Tatum API | Transfer 1x only, non-sellable | Verify limit enforcement | Specifications |
| SCR-016 Event Ticket | Points balance (deduct 50) | Restricted: chỉ company có distinction/awards | Verify eligibility + points deduction | Specifications |
| SCR-031 Assign Points | Points ledger | Admin distribute to Awards recipients / pre-registered | Verify balance update | UC List |
| SCR-033 Distribute Awards | Tatum API (NFT mint), BASE blockchain | Sellable & transferable (khác distinction) | Verify NFT metadata + sellable flag | Specifications |
| SCR-002 Public Directory | IPFS (badge storage) | Badge "Issued by PARTNERS WEEK®" | Verify IPFS retrieval + search | Specifications |

---

## 10. Regression / impact anchors

| Anchor | Type | Related feature(s) | Related screen(s) | Vì sao quan trọng | Suggested regression focus |
|---|---|---|---|---|---|
| Stripe Payment | Integration | 1.5 Distinction Purchase | SCR-012 | Mọi purchase đều qua Stripe; fail = block revenue | Payment success/fail/webhook handling |
| NFT Minting (BASE/Tatum) | Integration | 1.5, 1.6, 2.17 | SCR-012, SCR-014, SCR-033 | NFT là core product; mint fail = critical | Mint success, linked contracts, metadata |
| Points Distribution | Core flow | 1.5, 2.16 | SCR-012, SCR-031 | 30% distribution on every purchase | Calculation accuracy, balance update |
| Anti-return Rule | Data state | 1.5 | SCR-011, SCR-012 | Prevent duplicate A→B same year | Block logic, year boundary |
| Custodial Wallet | Shared component | 1.3, 1.7, 1.5, 1.6 | SCR-004, SCR-013 | Auto-created, holds all NFTs + points | Creation on signup, balance display |
| Event Access Restriction | Permission | 1.8 | SCR-016 | Only distinction/awards holders | Eligibility check accuracy |
| Class-based Pricing | Data state | 1.5 | SCR-010, SCR-012 | 8 classes + Public Figure + Individual | Price lookup per class |

---

## 11. Gaps / conflicts / assumptions

| ID | Issue | Type | Impact to QC | Suggested owner | Priority | Status |
|---|---|---|---|---|---|---|
| GAP-001 | Không có wireframe hoặc official sitemap/navigation doc | Missing | Screen inventory 100% derived từ UC List, có thể thiếu screens | BA / Design | Medium | Open |
| GAP-002 | Chưa rõ screen flow chi tiết cho Purchase (bao nhiêu step, confirmation modal?) | Missing | Navigation flow có thể không chính xác | BA | Medium | Open |
| GAP-003 | Distinction Distribute (2.19) vs Distinction Management (2.14) - overlap? | Unclear | Có thể trùng chức năng hoặc là flow khác | BA | Low | Open |
| GAP-004 | Individual user (Class 7) - có access Event List không? | Assumption | Assumed: không có event access (chỉ Pont, no points) | BA | Low | Open |
| GAP-005 | Homepage (1.10) vs Landing Page (1.1) - khác nhau thế nào? | Unclear | Có thể là cùng 1 screen hoặc 2 screens khác nhau | BA | Low | Open |
| GAP-006 | Directory Management (2.20) - feature mới từ WBS, chưa có trong UC List chính thức. Cần xác nhận có trong scope V1 không? | Need confirm | Có thể thêm/bỏ feature khỏi dashboard | BA / QC Lead | Medium | Open |
| GAP-007 | Notification (Email) - WBS mention nhưng không có screen/UC chi tiết | Missing | Chưa rõ trigger conditions, template, delivery | BA | Low | Open |

---

## 12. Readiness assessment

| Area | Status | Reason | Required action |
|---|---|---|---|
| Screen inventory | Partial | Derived từ UC List + WBS BA Planning, chưa có wireframe xác nhận | QC Lead review + BA cung cấp wireframe |
| Navigation flow | Partial | Chỉ có high-level flows, thiếu chi tiết step-by-step | Cần wireframe/user flow doc |
| Role/access by screen | Partial | Derived từ Specifications, chưa có role matrix chính thức | BA xác nhận |
| Screen-feature mapping | Ready | Mỗi screen đều map được tới UC/Feature ID | |
| Data/API/integration/state touchpoints | Partial | Biết integrations chính nhưng thiếu API spec chi tiết | Tech Lead cung cấp API doc |
| Regression/impact usage | Ready | Đã xác định core anchors | |
| Dashboard feature-level handoff | Ready | 21 features mapped (thêm 2.20 Directory Management), sẵn sàng handoff | |

**Kết luận:** Tạm đủ  
**Ghi chú cho QC Lead:** Site map đã update với 12 screens mới từ WBS (47 total). Cần xác nhận: (1) Directory Management (2.20) có trong scope V1 không? (2) Notification feature cần spec chi tiết. Các GAP-001 đến GAP-007 cần BA clarify.
