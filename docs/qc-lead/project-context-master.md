# Project Context Master: PartnersWeek

**Trạng thái:** Draft  
**Ngày tạo/cập nhật:** 2026-05-26  
**Người chuẩn bị:** QC Context Agent  
**Người review:** QC Lead  
**Mục đích:** Cung cấp bối cảnh tổng quan cấp project để các QC Agent hiểu đúng hệ thống, phạm vi, rule chung, rủi ro và trạng thái tài liệu trước khi review spec, thiết kế scenario/test case, execute hoặc verify bug.

> File này là tài liệu high-level do Agent tổng hợp để QC Lead review và bổ sung.  
> File này không thay thế spec, wireframe, API document, use case detail hoặc các tài liệu chi tiết do BA/BE/Tech Lead cung cấp.  
> File này nên ngắn gọn, chỉ giữ thông tin có ảnh hưởng đến cách QC Agent hiểu dự án, đánh giá impact, review tài liệu hoặc thiết kế kiểm thử.

---

## Sources consolidated

| # | File | Version | Loại | Ngày đọc cuối |
|---|---|---|---|---|
| 1 | PARTNERS_WEEK_Specifications_EN.md | no-version | Scope / Business rules | 2026-05-25 |
| 2 | UC List.md | no-version | Feature inventory | 2026-05-25 |
| 3 | WBS.xlxs (sheet: BA Planning) | no-version | WBS / UC breakdown / Deadline / Wireframe status / Business rules bổ sung | 2026-05-26 |

---

## 1. Cách các QC Agent sử dụng file này

| Nhóm Agent / Skill | Cách sử dụng project context | Cần đọc thêm file nào |
|---|---|---|
| Site map / dashboard / high-level review | Hiểu cấu trúc tổng thể: 2 site (User + Admin), module, feature list, trạng thái tài liệu | UC List, qc-site-map, qc-dashboard |
| Spec review - level function | Dùng context về class pricing, NFT rules, points distribution, purchase flow để kiểm tra spec có đúng scope và rule chung không | Spec chi tiết từng UC, wireframe |
| Scenario design | Xác định flow mua distinction, NFT transfer, event access, points; role Company A/B/Admin; dependency blockchain/Stripe | Spec chi tiết, UC List |
| Test case design | Dùng rule chung (anti-return, class pricing, points 10%+10%+10%), platform web, payment CHF only để thiết kế expected result và precondition | Scenario, spec, wireframe |
| Test execute | Hiểu environment (Stripe sandbox, BASE blockchain testnet), test data (company classes), payment flow | Test cases, environment config |
| Bug verify | Hiểu impacted area: NFT minting, points calculation, Stripe payment, directory search | Bug report, spec, test case |

**Quy tắc sử dụng:**  
Nếu thông tin trong file này mâu thuẫn với spec/wireframe/API chi tiết đã approved, Agent phải báo conflict và ưu tiên tài liệu chi tiết đã approved.

---

## 2. Tóm tắt dự án

| Hạng mục | Nội dung |
|---|---|
| Tên dự án / sản phẩm | PARTNERS WEEK® |
| Domain / nghiệp vụ | Blockchain-based partnership recognition & NFT ecosystem |
| Loại dự án | New build (MVP V1.2) |
| Mục tiêu chính của dự án/release | Xây dựng nền tảng web cho phép doanh nghiệp mua NFT distinction để vinh danh đối tác, tích điểm và tham gia sự kiện |
| Người dùng chính | Company (buyer/recipient), Individual, Admin |
| Release / phase hiện tại | MVP V1.2 - Option B (USD 31,800 - 6-7 weeks) |
| Trạng thái tổng quan | In development |

**Tóm tắt ngắn:**  
PARTNERS WEEK® là nền tảng quốc tế sử dụng blockchain (BASE) để vinh danh quan hệ đối tác kinh doanh. Company A mua NFT distinction cho Company B, cả hai nhận NFT + points (10% mỗi bên, 10% vào pool). Points là pre-token có thể convert 1:1 sang utility token. Hệ thống hỗ trợ 3 loại distinction (Philanthrope, Investisseur, Pont), pricing theo class doanh nghiệp (dựa trên số nhân viên), thanh toán CHF qua Stripe, và tổ chức events cho các công ty có distinction/awards.

---

## 3. Phạm vi tổng thể và ranh giới kiểm thử

### 3.1 In scope cấp project/release

| Area / module / capability | Mô tả ngắn | Priority | Ghi chú |
|---|---|---|---|
| Landing Page "Coming Soon" | Logo, mô tả, email signup, waitlist, early access 50 points | High | Tuần đầu tiên |
| User Authentication | Sign up, sign in, forgot password | High | |
| User Profile | View/edit profile, change password | Medium | |
| E-commerce Catalog | 3 annual distinctions, browse, select recipient, confirm order | High | Payment CHF via Stripe |
| NFT Distinction Minting | Mint NFT cho Company A & B, linked contracts, anti-return rule | High | BASE blockchain, Tatum API |
| NFT Transfer | Transfer 1x to non-custodial wallet | Medium | Non-sellable |
| Custodial Wallet | Auto-created via Tatum API | High | |
| Points Distribution | 10% A + 10% B + 10% pool = 30% total | High | |
| Public Directory | Search by company/distinctions/Awards, IPFS badge | Medium | |
| Event Management | Admin tạo event, user mua ticket (50 points) | Medium | Restricted: chỉ company có distinction/awards |
| Admin Dashboard | Basic analytics | Medium | |
| Admin Management | CRUD admin accounts, user list, distinction management | Medium | |
| Partners Awards NFT | Admin distribute special NFTs during events, sellable & transferable. Metadata: tên company, năm, tên event. Chỉ distribute trong "Partners Week" event (30/4 + 15 ngày) | Medium | Từ WBS |
| Year 2+ Discount | 20% reduction payable in points (1 point = CHF 1). VD: CHF 35,000 → CHF 28,000 + 7,000 points. Discount cũng áp dụng cho event ticket (50 pts → 40 pts) | Low | Cần verify anniversary logic |
| Email Notification | Email notification cho user và admin | Low | Chưa có spec chi tiết |
| Admin: Waitlist & Company Approval | View waitlist, view registration details, company approval | Medium | Từ WBS BA Planning |
| Admin: Directory Management | Search IPFS, manage public directory | Low | Từ WBS BA Planning |

### 3.2 Out of scope / chưa làm trong phase này

| Area / capability | Lý do loại trừ / deferred | Ảnh hưởng đến QC |
|---|---|---|
| Advanced Analytics Dashboard | Deferred to V2 - giảm cost V1 | Chỉ test basic analytics |
| Batch Operations | Deferred to V2 - V1 single operations only | Không cần test bulk import/export |
| Historical Data Migration (3èmelieu) | Confirmed removal from scope | Không cần test migration |
| Cryptocurrency payments | CHF only via Stripe | Không test crypto payment |

### 3.3 Assumption, dependency, constraint quan trọng

| Loại | Nội dung | Ảnh hưởng đến QC Agent | Cần xác nhận? |
|---|---|---|---|
| Dependency | BASE blockchain (mandatory) | Cần testnet/sandbox cho NFT minting | No |
| Dependency | Stripe payment gateway | Cần Stripe sandbox keys | No |
| Dependency | Tatum API cho custodial wallet + IPFS | Cần Tatum test API keys | No |
| Constraint | Payment CHF only, no crypto | Chỉ test CHF payment flow | No |
| Constraint | NFT non-sellable, transferable 1x only | Test transfer limit enforcement | No |
| Assumption | Points = pre-tokens, convert 1:1 khi tokenomics established | Chưa cần test token conversion trong V1 | Yes |
| Constraint | Languages: French & English | Test cả 2 ngôn ngữ | No |

---

## 4. Cấu trúc hệ thống và tài liệu high-level liên quan

### 4.1 System / site / portal overview

| Site / portal / app | Mục đích | Nhóm user chính | Module chính | Ghi chú |
|---|---|---|---|---|
| User Site (partnersweek.com) | Mua distinction, quản lý NFT/wallet, tham gia events | Company (A & B), Individual | Auth, Profile, Catalog, Purchase, NFT, Wallet, Events, Directory, Dashboard | Web responsive, FR & EN |
| Admin Site | Quản lý hệ thống, distribute awards/points, manage events | Admin | Auth, Profile, Admin Mgmt, User Mgmt, Distinction Mgmt, Event Mgmt, Points, Awards, Dashboard | Web |

### 4.2 Các file high-level liên quan

| File | Vai trò | Trạng thái | Ghi chú |
|---|---|---|---|
| PARTNERS_WEEK_Specifications_EN.md | Scope, business rules, pricing, confirmed/verify/postponed elements | Draft | Nguồn chính cho business logic |
| UC List.md | Danh sách feature/use case cho User site và Admin site | Draft | 19 UC groups, ~30+ sub-UCs |
| WBS.xlxs (BA Planning sheet) | UC breakdown chi tiết, deadline, wireframe status, business rules bổ sung | Draft | ODS format, đã đọc được. Wireframe status hầu hết "Done" |
| Site map | Cung cấp cấu trúc site/module/screen tổng thể | Missing | Chưa có file riêng |
| qc-dashboard | Theo dõi trạng thái tài liệu/spec/scenario/test case | Missing | Sẽ được tạo bởi qc-dashboard-sync |
| Project config | Cấu hình project, environment, accounts | Draft | Sections 2-5 chưa có dữ liệu thực |

---

## 5. Users, roles và permission tổng quan

| Role / actor | Mô tả | Workflow chính | Permission / responsibility tổng quan | Ghi chú QC |
|---|---|---|---|---|
| Company (Class 0-6) | Doanh nghiệp theo quy mô nhân viên | Mua distinction cho partner, nhận NFT + points, tham gia events | Mua distinction, transfer NFT 1x, mua ticket event | Pricing khác nhau theo class |
| Individual (Class 7) | Cá nhân không phải doanh nghiệp | Chỉ mua distinction "Pont" (CHF 19) | Chỉ mua Pont, không có points distribution khi tự mua. Nhưng CÓ THỂ nhận NFT awards + points nếu company/public figure mua cho | Hạn chế so với Company |
| Public Figure | Athletes, artists | Tương tự Company Class 0 | Mua distinction, nhận NFT + points | Price cố định CHF 35,000 |
| Admin | Quản trị viên hệ thống | Manage distinctions, events, points, awards, users | Full access: CRUD admin, distribute points/awards, manage events | |

**Lưu ý:**  
- Company A = buyer, Company B = recipient. Cả hai đều nhận NFT + 10% points.
- Anti-return rule: không thể mua cùng distinction giữa A & B trong cùng năm.
- Individual chỉ mua "Pont" (CHF 19), không có points distribution.

---

## 6. Business flow, module relationship và impact area

### 6.1 Flow chính cấp project

| Flow ID | Flow name | Actor chính | Module/site liên quan | Trigger | Kết quả chính | Ghi chú impact/regression |
|---|---|---|---|---|---|---|
| FLOW-001 | Distinction Purchase | Company A (User site) | Catalog, Payment (Stripe), NFT Minting (BASE/Tatum), Points, Wallet | User chọn distinction + recipient | NFT minted cho A & B, points distributed (30% total), payment processed | Core flow - impact toàn bộ hệ thống |
| FLOW-002 | NFT Transfer | Company A or B (User site) | Wallet, Blockchain (BASE) | User request transfer | NFT moved to non-custodial wallet (1x only) | Irreversible, check limit |
| FLOW-003 | Event Ticketing | Company with distinction (User site) | Events, Points, Wallet | User mua ticket (50 points) | Ticket issued, points deducted | Restricted access: chỉ company có distinction/awards |
| FLOW-004 | Partners Awards Distribution | Admin (Admin site) | Awards, NFT Minting, Points | Admin distribute during event | Special NFT minted, points assigned | Sellable & transferable (khác distinction) |
| FLOW-005 | Early Access Signup | Visitor (Landing page) | Landing, Email, Points | Email signup + join waitlist trước 10/02 | Account pre-registered, 50 pre-points (convert thành points thật khi user mua hàng sau launch) | Landing page hết sau 10/02 |

### 6.2 Quan hệ giữa module / data / integration

| Area A | Liên quan đến Area B | Kiểu liên quan | Ảnh hưởng QC |
|---|---|---|---|
| Purchase (Stripe) | NFT Minting (BASE/Tatum) | Data dependency | Payment success → trigger mint. Nếu mint fail sau payment? |
| NFT Minting | Points Distribution | Data dependency | Mint success → auto distribute 10%+10%+10% |
| Points | Event Ticketing | Data dependency | Points balance → ticket purchase eligibility |
| Distinction ownership | Event Access | Permission | Chỉ company có distinction/awards mới mua ticket |
| Company Class | Pricing | Data dependency | Class quyết định giá, cần verify class assignment |
| NFT Distinction | Anti-return rule | Workflow constraint | Cùng A-B cùng năm → block purchase |

---

## 7. Rule chung, data/state và integration cần nhớ

### 7.1 Rule chung áp dụng nhiều function

| Rule | Áp dụng cho | Ảnh hưởng đến review/spec/scenario/test case |
|---|---|---|
| Anti-return: không mua cùng distinction giữa A & B cùng năm | Purchase flow, Distinction management | Cần test duplicate purchase blocking |
| Points distribution: 10% A + 10% B + 10% pool = 30% total (auto distribution khi purchase) | Purchase, Points, Wallet | Verify calculation chính xác theo giá distinction. Admin cũng có thể manually distribute points cho Awards recipients và pre-registered companies |
| NFT non-sellable, transferable 1x to non-custodial wallet | NFT Transfer, Wallet | Test transfer limit, block sell attempt |
| Payment CHF only via Stripe | Purchase, Event ticketing | Không test crypto, chỉ Stripe sandbox |
| Company class based on employee count | Registration, Purchase pricing | Verify class assignment logic, pricing lookup |
| Year 2+ discount: 20% max payable in points (1 point = CHF 1) | Purchase (returning customers), Event ticketing | VD distinction: CHF 35,000 → CHF 28,000 + 7,000 pts. VD event: 50 pts → 40 pts. User có thể chọn KHÔNG dùng discount. Individual KHÔNG có discount |
| Pre-points (50): chỉ cho user đăng ký trước 10/02 trên landing page | Registration, Points | Pre-points convert thành points thật khi user thực hiện purchase đầu tiên (auto distribution) |
| Event ticket restricted: chỉ company có distinction/awards | Event access | Test eligibility check |
| Languages: French & English | Toàn bộ UI | Test cả 2 ngôn ngữ |

### 7.2 Data object / state quan trọng cấp project

| Object / entity | Mô tả | State / lifecycle chính | Ghi chú QC |
|---|---|---|---|
| NFT Distinction | Token vinh danh partnership | Minted → Held → Transferred (1x, final) | Non-sellable, linked contracts A & B |
| NFT Partners Awards | Token đặc biệt từ admin | Minted → Held → Sold/Transferred | Sellable & transferable (khác distinction). Metadata: tên company recipient, class, năm. Chỉ distribute trong "Partners Week" event (30/4 + 15 ngày hàng năm). Default: Name "Partners Award", no description, no price, default image, year = mint date |
| Points / Pre-tokens | Điểm tích lũy | Earned → Available → Spent (ticket/discount) | Convert 1:1 to utility token (future) |
| Custodial Wallet | Ví tự động tạo | Created (auto on registration) → Active | Via Tatum API |
| Distinction Order | Đơn mua distinction | Created → Paid → NFT Minted → Completed | Stripe payment → blockchain mint |
| Company | Doanh nghiệp đăng ký | Registered → Class Assigned → Active | Class 0-7 + Public Figure + Individual |

### 7.3 Integration / API / job / notification quan trọng

| Item | Loại | Module liên quan | Ghi chú QC / risk |
|---|---|---|---|
| Stripe | Payment Gateway | Purchase, Event ticketing | CHF only, sandbox testing, webhook handling |
| Tatum API | Blockchain + IPFS | NFT Minting, Wallet creation, Badge storage | Custodial wallet auto-creation, IPFS metadata |
| BASE blockchain | Smart Contract | NFT Distinction, NFT Awards | Linked contracts A & B, anti-return logic on-chain |
| Medusa | E-commerce backend | Catalog, Orders | Product management, order processing |
| IPFS | Storage | Public Directory, Badge | Badge "Issued by PARTNERS WEEK®" |

---

## 8. Platform, environment, device và NFR/ràng buộc

### 8.1 Platform và environment tổng quan

| Hạng mục | Nội dung | Ghi chú QC |
|---|---|---|
| Platform type | Web application (responsive) | partnersweek.com |
| Browser / OS / device cần quan tâm | TBD - cần xác nhận browser matrix | Assumption: modern browsers |
| Hosting | Infomaniak | |
| Test environment | TBD | Cần cấu hình Stripe sandbox + Tatum testnet |
| Integration mode | Stripe Sandbox, Tatum Test API, BASE testnet | Cần API keys cho test |
| Test data / account tổng quan | Company classes 0-7, Individual, Public Figure, Admin | Cần tạo test data cho mỗi class |
| Languages | French & English | Test cả 2 |

### 8.2 NFR, security, compliance, legal, audit

| Loại ràng buộc | Nội dung đã biết | Ảnh hưởng QC |
|---|---|---|
| Security | Custodial wallet management, payment processing | Verify wallet isolation, payment security |
| Privacy | Company data, transaction history | TBD - cần xác nhận GDPR/privacy requirements |
| Performance | TBD | Blockchain transaction latency có thể ảnh hưởng UX |
| Legal | NFT ownership, trademark "PARTNERS WEEK®" | Badge must show "Issued by PARTNERS WEEK®" |

---

## 9. Đánh giá mức độ đủ context cấp project

| Nhóm context | Trạng thái | Độ tin cậy | Ảnh hưởng nếu thiếu/sai | Cần QC Lead bổ sung gì |
|---|---|---|---|---|
| Project goal & scope | Ready | High | | |
| System/site/module overview | Ready | High | | |
| Feature/use case inventory | Ready | High | | UC List đầy đủ |
| Users/roles/permission overview | Partial | Medium | Thiếu chi tiết permission per function | Cần spec chi tiết từng UC |
| Business flows & module relationship | Ready | Medium | | Cần verify error handling flows |
| Common rules/data/state/integration | Ready | High | | Một số rules cần verify (Year 2+ discount, Awards) |
| Platform/environment/device/NFR | Partial | Low | Thiếu browser matrix, test environment URLs | Cần QC Lead cung cấp environment info |
| Document status tracking | Missing | Low | Chưa có qc-dashboard | Sẽ tạo sau khi chạy qc-site-map + qc-dashboard-sync |

**Kết luận:**  
Context cấp project **tạm đủ** để các QC Agent bắt đầu review spec và thiết kế scenario. So với lần trước: WBS đã đọc được, bổ sung thêm business rules (discount, pre-points, Partners Awards metadata, Individual nhận NFT). Thiếu chính yếu còn lại: (1) environment/test account thực tế, (2) browser matrix, (3) xác nhận UC/function mới từ WBS có trong scope không (Q-008).

---

## 10. Open questions và việc cần QC Lead xác nhận

| ID | Câu hỏi / thông tin cần xác nhận | Vì sao quan trọng | Ảnh hưởng nếu chưa rõ | Priority | Owner | Status |
|---|---|---|---|---|---|---|
| Q-001 | Year 2+ Discount: chính xác logic tính anniversary date? User có thể chọn không dùng discount — nhưng trigger condition là gì (auto detect year 2+ hay user opt-in)? | Ảnh hưởng test case cho returning customers | Thiết kế test case sai | Medium | BA | Open |
| Q-002 | Partners Awards NFT: flow chi tiết distribute — admin chọn recipient thế nào? Có cần recipient đã registered không? Sellable conditions (marketplace hay P2P)? | WBS cho biết metadata + event constraint nhưng thiếu flow chi tiết | Không thể thiết kế scenario đầy đủ | Medium | BA | Open |
| Q-003 | Browser/device matrix cần support? | Ảnh hưởng compatibility testing | Có thể miss bugs trên browser cụ thể | Medium | QC Lead | Open |
| Q-004 | Test environment URLs và API keys (Stripe sandbox, Tatum test, BASE testnet)? | Cần để execute test | Không thể chạy test | High | Tech Lead | Open |
| Q-005 | Error handling khi NFT mint fail sau khi payment đã success? (Refund? Retry?) | Critical business flow | Test case thiếu negative scenario quan trọng | High | BA / Tech Lead | Open |
| Q-006 | WBS file đã đọc được (ODS format, sheet BA Planning). Resolved. | — | — | — | — | Resolved |
| Q-007 | requirement-common-files folder (docs/ba/Common rule) chưa tồn tại - có tài liệu common rules riêng không? | Các skill downstream cần đọc common rules | Có thể miss business rules chung | Medium | BA | Open |
| Q-008 | WBS BA Planning có thêm UC/function chưa có trong UC List hiện tại: UC-8.3 (Purchase tickets riêng), UC-9.1/9.2/9.3 (Dashboard sub-UCs), UC-11.3 (Delete Profile), UC-13.2/13.3 (User Details, Activate/Deactivate), Waitlist management, Company approval, Directory Management, Notification. Cần xác nhận có thêm vào scope không? | Ảnh hưởng feature list và dashboard | Có thể thiếu test coverage | Medium | BA / QC Lead | Open |

---

## Phụ lục A. Nguyên tắc giữ file gọn

- Chỉ ghi thông tin cấp project hoặc thông tin dùng chung cho nhiều Agent/skill.
- Không copy toàn bộ nội dung từ spec, wireframe, API document hoặc use case detail.
- Không ghi test case chi tiết trong file này.
- Không lặp lại danh sách feature dài nếu đã có `feature list` hoặc `qc-dashboard`.
- Nếu thông tin đã có ở file khác, chỉ tóm tắt vai trò và dẫn Agent đọc file đó.
- Nếu một thông tin chỉ ảnh hưởng một function cụ thể, đưa vào function-level context/spec review, không đưa vào file này.
