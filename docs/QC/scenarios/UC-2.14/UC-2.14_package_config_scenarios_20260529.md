# Test Scenarios — UC-2.14 Package Configuration

> Source: docs/QC/uc-read/UC-2.14/UC-2.14_package_config_audited_20260529_v2.md + BA clarification (2026-05-29)
> Generated: 2026-05-29
> Updated: 2026-05-29 (v2 - expanded scope)
> Platform: Web Responsive (Admin)
> Language: Vietnamese (source doc)

---

## UC-2.14 — Package Configuration

### Scene 1: S01 - Package and Distinctions (List)

#### Scenario ID: TS_UC-2.14_S01_001
**Scenario Title:** Admin truy cập màn hình Package and Distinctions (S01)
**UC Reference:** UC-2.14 — Package Configuration
**Req-ID:** UC-2.14 §S01
**Test Type:** Functional
**Description:** Xác minh Admin click "Package Configuration" trên menu và hệ thống hiển thị đúng màn hình S01 với title, các section và cards đúng như thiết kế.
**Test Focus:** Happy path

---

#### Scenario ID: TS_UC-2.14_S01_002
**Scenario Title:** S01 hiển thị đúng 4 cards: Collaboration, Investor, Bridge, Package
**UC Reference:** UC-2.14 — Package Configuration
**Req-ID:** UC-2.14 §S01
**Test Type:** UI
**Description:** Xác minh S01 hiển thị đúng 4 cards trong 2 sections: (1) Package Management section với Company Package card; (2) Distinctions Management section với 3 distinction cards: Collaboration, Investor, Bridge.
**Test Focus:** Happy path

---

#### Scenario ID: TS_UC-2.14_S01_003
**Scenario Title:** Admin điều hướng đến Collaboration Configuration (S02-Collaboration)
**UC Reference:** UC-2.14 — Package Configuration
**Req-ID:** UC-2.14 §S01 Behavior
**Test Type:** Functional
**Description:** Xác minh Admin click vào Collaboration card và hệ thống điều hướng đến màn hình cấu hình Collaboration.
**Test Focus:** Happy path

---

#### Scenario ID: TS_UC-2.14_S01_004
**Scenario Title:** Admin điều hướng đến Investor Configuration (S02-Investor)
**UC Reference:** UC-2.14 — Package Configuration
**Req-ID:** UC-2.14 §S01 Behavior
**Test Type:** Functional
**Description:** Xác minh Admin click vào Investor card và hệ thống điều hướng đến màn hình cấu hình Investor.
**Test Focus:** Happy path

---

#### Scenario ID: TS_UC-2.14_S01_005
**Scenario Title:** Admin điều hướng đến Bridge Configuration (S02-Bridge)
**UC Reference:** UC-2.14 — Package Configuration
**Req-ID:** UC-2.14 §S01 Behavior
**Test Type:** Functional
**Description:** Xác minh Admin click vào Bridge card và hệ thống điều hướng đến màn hình cấu hình Bridge (có thêm Individual price config).
**Test Focus:** Happy path

---

#### Scenario ID: TS_UC-2.14_S01_006
**Scenario Title:** Admin điều hướng đến Package Configuration (S02-Package)
**UC Reference:** UC-2.14 — Package Configuration
**Req-ID:** UC-2.14 §S01 Behavior
**Test Type:** Functional
**Description:** Xác minh Admin click vào Company Package card và hệ thống điều hướng đến S02-Package (Pricing Configuration per Class).
**Test Focus:** Happy path

---

### Scene 2: S02-Collaboration - Edit Distinction (Name, Description, Type, Image)

#### Scenario ID: TS_UC-2.14_COLLAB_001
**Scenario Title:** Collaboration view mode - hiển thị đúng thông tin
**UC Reference:** UC-2.14 — Package Configuration
**Req-ID:** UC-2.14 §S02 Collaboration
**Test Type:** UI
**Description:** Xác minh màn hình Collaboration hiển thị đúng: Distinction name (Philanthropist/Collaboration?), Description, Type (Bridge/Investor/Philanthropist), NFT Artwork image - tất cả ở chế độ read-only.
**Test Focus:** Happy path

---

#### Scenario ID: TS_UC-2.14_COLLAB_002
**Scenario Title:** Chuyển sang Edit mode cho Collaboration
**UC Reference:** UC-2.14 — Package Configuration
**Req-ID:** UC-2.14 §S02 Behavior 1
**Test Type:** UI State
**Description:** Xác minh khi Admin click "Edit" button, màn hình chuyển sang Edit mode với các trường có thể chỉnh sửa: Distinction name, Description, Type, Image.
**Test Focus:** UI State transition

---

#### Scenario ID: TS_UC-2.14_COLLAB_003
**Scenario Title:** Admin chỉnh sửa Distinction Name cho Collaboration
**UC Reference:** UC-2.14 — Package Configuration
**Req-ID:** UC-2.14 §S02 + BR-02
**Test Type:** Functional
**Description:** Xác minh Admin có thể chỉnh sửa Distinction Name (max 255 characters theo CMR-25) trong Edit mode.
**Test Focus:** Happy path

---

#### Scenario ID: TS_UC-2.14_COLLAB_004
**Scenario Title:** Admin chỉnh sửa Description cho Collaboration
**UC Reference:** UC-2.14 — Package Configuration
**Req-ID:** UC-2.14 §S02 + BR-02
**Test Type:** Functional
**Description:** Xác minh Admin có thể chỉnh sửa Description (max 1000 characters theo CMR-25) trong Edit mode.
**Test Focus:** Happy path

---

#### Scenario ID: TS_UC-2.14_COLLAB_005
**Scenario Title:** Type field là read-only trong cả View và Edit mode
**UC Reference:** UC-2.14 — Package Configuration
**Req-ID:** UC-2.14 §S02
**Test Type:** UI
**Description:** Xác minh Type field luôn là read-only, không cho phép Admin thay đổi Type.
**Test Focus:** Happy path

---

#### Scenario ID: TS_UC-2.14_COLLAB_006
**Scenario Title:** Admin upload NFT Artwork mới cho Collaboration
**UC Reference:** UC-2.14 — Package Configuration
**Req-ID:** UC-2.14 §S02 + CMR-15
**Test Type:** Functional
**Description:** Xác minh Admin có thể upload image mới (PNG, JPG, SVG, max 5MB) trong Edit mode cho Collaboration. Validation theo CMR-15.
**Test Focus:** Happy path

---

#### Scenario ID: TS_UC-2.14_COLLAB_007
**Scenario Title:** Collaboration - upload file không hợp lệ (wrong format)
**UC Reference:** UC-2.14 — Package Configuration
**Req-ID:** CMR-15 + MSG-20
**Test Type:** Error/Exception
**Description:** Xác minh khi Admin upload file không đúng định dạng (ví dụ: PDF, TXT), hệ thống hiển thị MSG-20: "Your uploaded file types are not supported by the system."
**Test Focus:** Error/Exception

---

#### Scenario ID: TS_UC-2.14_COLLAB_008
**Scenario Title:** Collaboration - upload file vượt quá 5MB
**UC Reference:** UC-2.14 — Package Configuration
**Req-ID:** CMR-15 + MSG-06
**Test Type:** Error/Exception
**Description:** Xác minh khi Admin upload file lớn hơn 5MB, hệ thống hiển thị MSG-06: "The file size exceeded <maximum file capacity>."
**Test Focus:** Boundary

---

#### Scenario ID: TS_UC-2.14_COLLAB_009
**Scenario Title:** Admin lưu Collaboration thành công (MSG-05)
**UC Reference:** UC-2.14 — Package Configuration
**Req-ID:** UC-2.14 §S02 Validation + MSG-05
**Test Type:** Functional
**Description:** Xác minh khi Admin click "Save" sau khi chỉnh sửa Collaboration, hệ thống lưu và hiển thị MSG-05: "Action completed."
**Test Focus:** Happy path

---

#### Scenario ID: TS_UC-2.14_COLLAB_010
**Scenario Title:** Admin hủy chỉnh sửa Collaboration (MSG-04)
**UC Reference:** UC-2.14 — Package Configuration
**Req-ID:** UC-2.14 §S02 Validation + MSG-04
**Test Type:** Functional
**Description:** Xác minh khi Admin click "Cancel", hệ thống hủy tất cả thay đổi và hiển thị MSG-04: "This action has been canceled."
**Test Focus:** Alternative flow

---

### Scene 3: S02-Investor - Edit Distinction (Name, Description, Type, Image)

#### Scenario ID: TS_UC-2.14_INVESTOR_001
**Scenario Title:** Investor view mode - hiển thị đúng thông tin
**UC Reference:** UC-2.14 — Package Configuration
**Req-ID:** UC-2.14 §S02 Investor
**Test Type:** UI
**Description:** Xác minh màn hình Investor hiển thị đúng: Distinction name, Description, Type, NFT Artwork image - tất cả ở chế độ read-only.
**Test Focus:** Happy path

---

#### Scenario ID: TS_UC-2.14_INVESTOR_002
**Scenario Title:** Admin chỉnh sửa Investor (Name, Description, Type read-only, Image)
**UC Reference:** UC-2.14 — Package Configuration
**Req-ID:** UC-2.14 §S02 Behavior 1
**Test Type:** Functional
**Description:** Tương tự Collaboration - xác minh Admin có thể chỉnh sửa Name, Description, Image nhưng Type là read-only. Lưu thành công với MSG-05.
**Test Focus:** Happy path

---

#### Scenario ID: TS_UC-2.14_INVESTOR_003
**Scenario Title:** Investor - boundary test cho Distinction Name (255 chars)
**UC Reference:** UC-2.14 — Package Configuration
**Req-ID:** CMR-25
**Test Type:** Boundary
**Description:** Xác minh Admin không thể nhập quá 255 ký tự cho Distinction Name. Kiểm tra boundary: 254 chars = OK, 255 chars = OK, 256 chars = blocked.
**Test Focus:** Boundary

---

#### Scenario ID: TS_UC-2.14_INVESTOR_004
**Scenario Title:** Investor - boundary test cho Description (1000 chars)
**UC Reference:** UC-2.14 — Package Configuration
**Req-ID:** CMR-25
**Test Type:** Boundary
**Description:** Xác minh Admin không thể nhập quá 1000 ký tự cho Description. Kiểm tra boundary: 999 chars = OK, 1000 chars = OK, 1001 chars = blocked.
**Test Focus:** Boundary

---

### Scene 4: S02-Bridge - Edit Distinction + Individual Price

#### Scenario ID: TS_UC-2.14_BRIDGE_001
**Scenario Title:** Bridge view mode - hiển thị đầy đủ thông tin + Individual Price
**UC Reference:** UC-2.14 — Package Configuration
**Req-ID:** UC-2.14 §S02 Bridge + OQ-04
**Test Type:** UI
**Description:** Xác minh màn hình Bridge hiển thị đúng: Distinction name, Description, Type, NFT Artwork image, và Individual Price - tất cả ở chế độ read-only.
**Test Focus:** Happy path

---

#### Scenario ID: TS_UC-2.14_BRIDGE_002
**Scenario Title:** Admin chỉnh sửa Bridge (Name, Description, Type read-only, Image, Individual Price)
**UC Reference:** UC-2.14 — Package Configuration
**Req-ID:** UC-2.14 §S02 Behavior 1 + OQ-04
**Test Type:** Functional
**Description:** Xác minh Admin có thể chỉnh sửa tất cả các trường của Bridge BAO GỒM Individual Price. Type vẫn là read-only.
**Test Focus:** Happy path

---

#### Scenario ID: TS_UC-2.14_BRIDGE_003
**Scenario Title:** Admin chỉnh sửa Individual Price cho Bridge
**UC Reference:** UC-2.14 — Package Configuration
**Req-ID:** UC-2.14 §S02 Bridge + CMR-06
**Test Type:** Functional
**Description:** Xác minh Admin có thể chỉnh sửa Individual Price trong Edit mode với validation: numbers only, max 2 decimal places, max value 999999999999 (CMR-06).
**Test Focus:** Happy path

---

#### Scenario ID: TS_UC-2.14_BRIDGE_004
**Scenario Title:** Bridge Individual Price - input validation (CMR-06)
**UC Reference:** UC-2.14 — Package Configuration
**Req-ID:** CMR-06 + MSG-09
**Test Type:** Error/Exception
**Description:** Xác minh Individual Price input validation: chỉ chấp nhận số, max 2 decimal places, vượt quá 999999999999 hiển thị MSG-09.
**Test Focus:** Boundary

---

#### Scenario ID: TS_UC-2.14_BRIDGE_005
**Scenario Title:** Lưu Bridge với Individual Price mới thành công
**UC Reference:** UC-2.14 — Package Configuration
**Req-ID:** MSG-05
**Test Type:** Functional
**Description:** Xác minh khi Admin save Bridge với Individual Price mới, hệ thống lưu thành công và hiển thị MSG-05.
**Test Focus:** Happy path

---

### Scene 5: S02-Package - Price Configuration per Class

#### Scenario ID: TS_UC-2.14_PKG_001
**Scenario Title:** Package view mode - hiển thị bảng Pricing Configuration
**UC Reference:** UC-2.14 — Package Configuration
**Req-ID:** UC-2.14 §S02 Package
**Test Type:** UI
**Description:** Xác minh S02-Package hiển thị đúng bảng Pricing Configuration với các cột: Class, Package Price, Activation Credit, Package feature. 8 rows cho Class 0-7.
**Test Focus:** Happy path

---

#### Scenario ID: TS_UC-2.14_PKG_002
**Scenario Title:** Package Price - edit cho Class 0
**UC Reference:** UC-2.14 — Package Configuration
**Req-ID:** UC-2.14 §S02 Package + CMR-06
**Test Type:** Functional
**Description:** Xác minh Admin có thể chỉnh sửa Package Price cho Class 0 trong Edit mode với validation CMR-06.
**Test Focus:** Happy path

---

#### Scenario ID: TS_UC-2.14_PKG_003
**Scenario Title:** Class 1 price change - Public Figures auto-sync
**UC Reference:** UC-2.14 — Package Configuration
**Req-ID:** UC-2.14 §S02 Note + OQ-03
**Test Type:** Integration
**Description:** Xác minh khi Admin thay đổi Class 1 price, Public Figures price tự động cập nhật theo (auto-sync). Kiểm tra cả hai giá trị thay đổi cùng nhau.
**Test Focus:** Alternative flow

---

#### Scenario ID: TS_UC-2.14_PKG_004
**Scenario Title:** Package - số Distinctions per Class
**UC Reference:** UC-2.14 — Package Configuration
**Req-ID:** UC-2.14 §S02 Package
**Test Type:** Functional
**Description:** Xác minh Admin có thể chỉnh sửa số Distinctions per Class trong Edit mode (nếu có trường này).
**Test Focus:** Happy path

---

#### Scenario ID: TS_UC-2.14_PKG_005
**Scenario Title:** Package Price - validation: vượt max value (MSG-09)
**UC Reference:** UC-2.14 — Package Configuration
**Req-ID:** CMR-06 + MSG-09
**Test Type:** Error/Exception
**Description:** Xác minh khi Admin nhập price vượt quá 999999999999, hệ thống chặn và hiển thị MSG-09: "Price must be less than or equal to {MAX_PRICE}."
**Test Focus:** Boundary

---

#### Scenario ID: TS_UC-2.14_PKG_006
**Scenario Title:** Package Price - validation: >2 decimal places
**UC Reference:** UC-2.14 — Package Configuration
**Req-ID:** CMR-06
**Test Type:** Error/Exception
**Description:** Xác minh hệ thống chỉ chấp nhận tối đa 2 decimal places. Input 3 decimal places bị prevent.
**Test Focus:** Boundary

---

#### Scenario ID: TS_UC-2.14_PKG_007
**Scenario Title:** Package Price - validation: non-numeric input
**UC Reference:** UC-2.14 — Package Configuration
**Req-ID:** CMR-01 + CMR-06
**Test Type:** Error/Exception
**Description:** Xác minh hệ thống chỉ chấp nhận số và ký tự ". ,' ". Input chữ cái hoặc ký tự đặc biệt bị blocked.
**Test Focus:** Boundary

---

#### Scenario ID: TS_UC-2.14_PKG_008
**Scenario Title:** Lưu Package Price mới thành công (MSG-05)
**UC Reference:** UC-2.14 — Package Configuration
**Req-ID:** MSG-05
**Test Type:** Functional
**Description:** Xác minh khi Admin click "Save" sau khi chỉnh sửa Package Price, hệ thống lưu và hiển thị MSG-05: "Action completed."
**Test Focus:** Happy path

---

#### Scenario ID: TS_UC-2.14_PKG_009
**Scenario Title:** Hủy chỉnh sửa Package (MSG-04)
**UC Reference:** UC-2.14 — Package Configuration
**Req-ID:** MSG-04
**Test Type:** Functional
**Description:** Xác minh khi Admin click "Cancel", hệ thống hủy tất cả thay đổi và hiển thị MSG-04: "This action has been canceled."
**Test Focus:** Alternative flow

---

#### Scenario ID: TS_UC-2.14_PKG_010
**Scenario Title:** System error khi save Package (MSG-33)
**UC Reference:** UC-2.14 — Package Configuration
**Req-ID:** MSG-33
**Test Type:** Error/Exception
**Description:** Xác minh khi xảy ra system error khi save, hệ thống hiển thị MSG-33 (system error) và dữ liệu không được lưu.
**Test Focus:** Error/Exception

---

#### Scenario ID: TS_UC-2.14_PKG_011
**Scenario Title:** Activation Credit là read-only (không thể chỉnh sửa)
**UC Reference:** UC-2.14 — Package Configuration
**Req-ID:** UC-2.14 §S02 Note
**Test Type:** UI
**Description:** Xác minh Activation Credit luôn là read-only, Admin không thể chỉnh sửa giá trị này trong cả View và Edit mode.
**Test Focus:** Happy path

---

#### Scenario ID: TS_UC-2.14_PKG_012
**Scenario Title:** Package Price hiển thị đúng format (CMR-01: apostrophe separator)
**UC Reference:** UC-2.14 — Package Configuration
**Req-ID:** CMR-01 + CMR-06
**Test Type:** UI
**Description:** Xác minh giá được hiển thị với định dạng đúng: apostrophe cho phần ngàn (ví dụ: 35'000), dấu chấm cho decimal (ví dụ: 1'234,56).
**Test Focus:** Happy path

---

#### Scenario ID: TS_UC-2.14_PKG_013
**Scenario Title:** Giá mới chỉ áp dụng cho purchases sau thay đổi
**UC Reference:** UC-2.14 — Package Configuration
**Req-ID:** UC-2.14 §S02 Note
**Test Type:** Integration
**Description:** Xác minh sau khi Admin thay đổi Package Price, giá mới chỉ áp dụng cho User purchase made AFTER the change. Orders đã tạo trước đó giữ nguyên giá cũ.
**Test Focus:** Alternative flow

---

#### Scenario ID: TS_UC-2.14_PKG_014
**Scenario Title:** Admin edit rồi save không thay đổi gì
**UC Reference:** UC-2.14 — Package Configuration
**Req-ID:** UC-2.14 §S02 Behavior 1
**Test Type:** Alternative flow
**Description:** Xác minh khi Admin vào Edit mode và save mà không thay đổi gì, hệ thống xử lý gracefully và hiển thị MSG-05.
**Test Focus:** Alternative flow

---

### Scene 6: Navigation & Common

#### Scenario ID: TS_UC-2.14_NAV_001
**Scenario Title:** Back button từ S02 quay về S01
**UC Reference:** UC-2.14 — Package Configuration
**Req-ID:** UC-2.14 §S02 Component
**Test Type:** Functional
**Description:** Xác minh Admin click Back button trên bất kỳ S02 nào (Collaboration/Investor/Bridge/Package) đều quay về S01.
**Test Focus:** Happy path

---

#### Scenario ID: TS_UC-2.14_NAV_002
**Scenario Title:** Không có unsaved data warning khi rời S02
**UC Reference:** UC-2.14 — Package Configuration
**Req-ID:** OQ-05 Resolved
**Test Type:** UI
**Description:** Xác minh khi Admin rời S02 (click Back, click menu khác) không có warning về unsaved data - đã được BA confirm.
**Test Focus:** Happy path

---

#### Scenario ID: TS_UC-2.14_NAV_003
**Scenario Title:** Verify Distinction Features info box (read-only)
**UC Reference:** UC-2.14 — Package Configuration
**Req-ID:** UC-2.14 §S02
**Test Type:** UI
**Description:** Xác minh Distinction Features info box hiển thị đúng các rules: non-sellable, transferable 1x, 10% points bonus, anti-return validation.
**Test Focus:** Happy path

---

## ⚠️ Out-of-Scope Flags

| Scenario Area | Reason | Recommended Action |
|---|---|---|
| MSG-33 exact wording | Message code MSG-33 not found in Message List document (v1 available up to MSG-32). Gap flagged. | Confirm MSG-33 definition with BA |
| Full class breakdown (Class 2-6 employee ranges) | Not explicitly defined in current CR doc | Extract from old UC-14.2 for test data |
| Performance/Load testing | NFR — out of scope for functional scenario design | Defer to specialist testing |
| Security beyond functional auth | NFR — out of scope for functional scenario design | Defer to security testing |

---

## Coverage Summary

| Section | Scenarios | Test Focus |
|---|---|---|
| S01 - List & Navigation | 6 | Happy path, UI |
| S02-Collaboration | 10 | Happy path, Boundary, Error |
| S02-Investor | 4 | Happy path, Boundary |
| S02-Bridge | 5 | Happy path, Boundary, Integration |
| S02-Package | 14 | Happy path, Boundary, Error, Integration |
| Navigation & Common | 3 | Happy path, UI |
| **Total** | **42** | |

---

**File:** UC-2.14_package_config_scenarios_20260529_v2.md
**Status:** Updated v2 (expanded scope from 20 to 42 scenarios)
**Ready for:** Test Case Design (/qc-func-tc-design)