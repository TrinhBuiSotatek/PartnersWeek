# Test Cases — UC-2.14 Package Configuration

> Source: docs/QC/scenarios/UC-2.14/UC-2.14_package_config_scenarios_20260529.md
> Generated: 2026-05-29
> Platform: Web Responsive (Admin)
> Language: Vietnamese (source doc)

---

## I. S01 — Package and Distinctions (List Screen)

| TC ID | Test Title | Pre-conditions | Test Steps | Expected Result | Priority |
|---|---|---|---|---|---|
| TC_UC-2.14_S01_001 | Admin truy cập màn hình Package and Distinctions thành công | Admin đã đăng nhập vào hệ thống Admin | 1. Admin click vào menu "Package Configuration"<br>2. Hệ thống hiển thị màn hình S01 | Màn hình S01 hiển thị đúng: title "Package and Distinctions", description "Manage package for Company and NFT for other Distinctions", 2 sections (Package Management và Distinctions Management) | P1 |
| TC_UC-2.14_S01_002 | S01 hiển thị đúng 4 cards (Company Package, Collaboration, Investor, Bridge) | Admin đã truy cập S01 | 1. Quan sát S01 | S01 hiển thị đúng 4 cards: (1) Company Package card trong Package Management section; (2) Collaboration card; (3) Investor card; (4) Bridge card trong Distinctions Management section. Mỗi card có icon và navigate arrow. | P1 |
| TC_UC-2.14_S01_003 | Admin điều hướng đến Collaboration Configuration (S02-Collaboration) | Admin đã truy cập S01 | 1. Admin click vào Collaboration card (hoặc navigate icon)<br>2. Hệ thống điều hướng đến S02-Collaboration | Hệ thống hiển thị màn hình S02-Collaboration ở View mode với đầy đủ thông tin distinction | P1 |
| TC_UC-2.14_S01_004 | Admin điều hướng đến Investor Configuration (S02-Investor) | Admin đã truy cập S01 | 1. Admin click vào Investor card (hoặc navigate icon)<br>2. Hệ thống điều hướng đến S02-Investor | Hệ thống hiển thị màn hình S02-Investor ở View mode với đầy đủ thông tin distinction | P1 |
| TC_UC-2.14_S01_005 | Admin điều hướng đến Bridge Configuration (S02-Bridge) | Admin đã truy cập S01 | 1. Admin click vào Bridge card (hoặc navigate icon)<br>2. Hệ thống điều hướng đến S02-Bridge | Hệ thống hiển thị màn hình S02-Bridge ở View mode với đầy đủ thông tin distinction và Individual Price | P1 |
| TC_UC-2.14_S01_006 | Admin điều hướng đến Package Configuration (S02-Package) | Admin đã truy cập S01 | 1. Admin click vào Company Package card (hoặc navigate icon)<br>2. Hệ thống điều hướng đến S02-Package | Hệ thống hiển thị màn hình S02-Package với bảng Pricing Configuration (Class 0-7, Package Price, Activation Credit, Package feature) | P1 |

---

## II. S02-Collaboration — Edit Distinction

| TC ID | Test Title | Pre-conditions | Test Steps | Expected Result | Priority |
|---|---|---|---|---|---|
| TC_UC-2.14_COLLAB_001 | Collaboration View mode - hiển thị đúng thông tin (Name, Description, Type, Image) | Admin đã điều hướng đến S02-Collaboration | 1. Quan sát S02-Collaboration ở View mode | Màn hình hiển thị đúng: Distinction name (read-only), Description (read-only), Type (Bridge/Investor/Philanthropist - read-only), NFT Artwork image (read-only), Edit button (enabled) | P1 |
| TC_UC-2.14_COLLAB_002 | Collaboration - Chuyển sang Edit mode khi click Edit button | Admin đã điều hướng đến S02-Collaboration (View mode) | 1. Admin click vào "Edit" button | Màn hình chuyển sang Edit mode: button "Edit" thay đổi thành "Cancel" và "Save"; các trường Name, Description, Image trở thành editable; Type vẫn là read-only | P1 |
| TC_UC-2.14_COLLAB_003 | Collaboration - Admin chỉnh sửa Distinction Name thành công | Admin đã vào Edit mode của S02-Collaboration | 1. Admin xóa nội dung Name hiện tại<br>2. Admin nhập "Philanthropist Updated"<br>3. Admin click "Save" | Hệ thống lưu thành công, hiển thị MSG-05 "Action completed", quay về View mode với Name mới | P1 |
| TC_UC-2.14_COLLAB_004 | Collaboration - Admin chỉnh sửa Description thành công | Admin đã vào Edit mode của S02-Collaboration | 1. Admin xóa nội dung Description hiện tại<br>2. Admin nhập Description mới<br>3. Admin click "Save" | Hệ thống lưu thành công, hiển thị MSG-05, quay về View mode với Description mới | P1 |
| TC_UC-2.14_COLLAB_005 | Collaboration - Type field là read-only trong cả View và Edit mode | Admin đã vào Edit mode của S02-Collaboration | 1. Quan sát Type field trong Edit mode<br>2. Thử click vào Type field | Type field luôn là read-only, không có input field hoặc dropdown, Admin không thể thay đổi giá trị Type | P1 |
| TC_UC-2.14_COLLAB_006 | Collaboration - Upload NFT Artwork mới (PNG, đúng kích thước) | Admin đã vào Edit mode của S02-Collaboration | 1. Admin click vào upload area hoặc kéo thả file ảnh (2MB)<br>2. Hệ thống hiển thị preview ảnh mới<br>3. Admin click "Save" | Hệ thống lưu ảnh mới, hiển thị MSG-05, quay về View mode với ảnh mới | P1 |
| TC_UC-2.14_COLLAB_007 | Collaboration - Upload file không hợp lệ (wrong format) - MSG-20 | Admin đã vào Edit mode của S02-Collaboration | 1. Admin upload file PDF | Hệ thống hiển thị MSG-20: "Your uploaded file types are not supported by the system." và không lưu file | P2 |
| TC_UC-2.14_COLLAB_008 | Collaboration - Upload file vượt quá 5MB - MSG-06 | Admin đã vào Edit mode của S02-Collaboration | 1. Admin upload file 6MB | Hệ thống hiển thị MSG-06: "The file size exceeded <maximum file capacity>. Please upload file within 5MB." và không lưu file | P2 |
| TC_UC-2.14_COLLAB_009 | Collaboration - Lưu thành công với MSG-05 | Admin đã vào Edit mode của S02-Collaboration | 1. Admin chỉnh sửa Name<br>2. Admin click "Save" | Hệ thống lưu thành công, hiển thị toast message "Action completed" (MSG-05), chuyển về View mode với dữ liệu mới | P1 |
| TC_UC-2.14_COLLAB_010 | Collaboration - Hủy chỉnh sửa với MSG-04 | Admin đã vào Edit mode của S02-Collaboration với thay đổi chưa lưu | 1. Admin thay đổi Name thành "Changed"<br>2. Admin click "Cancel" | Hệ thống hủy tất cả thay đổi, hiển thị MSG-04 "This action has been canceled", reload S02 với dữ liệu ban đầu | P1 |
| TC_UC-2.14_COLLAB_011 | Collaboration - Boundary test: Name với 254 ký tự (pass) | Admin đã vào Edit mode của S02-Collaboration | 1. Admin nhập Name với 254 ký tự<br>2. Admin click "Save" | Hệ thống chấp nhận input 254 ký tự, lưu thành công với MSG-05 | P2 |
| TC_UC-2.14_COLLAB_012 | Collaboration - Boundary test: Name với 255 ký tự (pass) | Admin đã vào Edit mode của S02-Collaboration | 1. Admin nhập Name với 255 ký tự<br>2. Admin click "Save" | Hệ thống chấp nhận input 255 ký tự, lưu thành công với MSG-05 | P2 |
| TC_UC-2.14_COLLAB_013 | Collaboration - Boundary test: Name với 256 ký tự (blocked) | Admin đã vào Edit mode của S02-Collaboration | 1. Admin nhập Name với 256 ký tự | Hệ thống ngăn không cho nhập thêm sau ký tự thứ 255 (CMR-25) | P2 |
| TC_UC-2.14_COLLAB_014 | Collaboration - Boundary test: Description với 999 ký tự (pass) | Admin đã vào Edit mode của S02-Collaboration | 1. Admin nhập Description với 999 ký tự<br>2. Admin click "Save" | Hệ thống chấp nhận input 999 ký tự, lưu thành công | P2 |
| TC_UC-2.14_COLLAB_015 | Collaboration - Boundary test: Description với 1000 ký tự (pass) | Admin đã vào Edit mode của S02-Collaboration | 1. Admin nhập Description với 1000 ký tự<br>2. Admin click "Save" | Hệ thống chấp nhận input 1000 ký tự, lưu thành công | P2 |
| TC_UC-2.14_COLLAB_016 | Collaboration - Boundary test: Description với 1001 ký tự (blocked) | Admin đã vào Edit mode của S02-Collaboration | 1. Admin nhập Description với 1001 ký tự | Hệ thống ngăn không cho nhập thêm sau ký tự thứ 1000 (CMR-25) | P2 |

---

## III. S02-Investor — Edit Distinction

| TC ID | Test Title | Pre-conditions | Test Steps | Expected Result | Priority |
|---|---|---|---|---|---|
| TC_UC-2.14_INVESTOR_001 | Investor View mode - hiển thị đúng thông tin | Admin đã điều hướng đến S02-Investor | 1. Quan sát S02-Investor ở View mode | Màn hình hiển thị đúng: Distinction name, Description, Type (read-only), NFT Artwork image | P1 |
| TC_UC-2.14_INVESTOR_002 | Investor - Admin chỉnh sửa Name, Description, Image (Type read-only), Save thành công | Admin đã điều hướng đến S02-Investor | 1. Admin click "Edit"<br>2. Admin chỉnh sửa Name và Description<br>3. Admin click "Save" | Hệ thống lưu thành công, hiển thị MSG-05, quay về View mode với dữ liệu mới | P1 |
| TC_UC-2.14_INVESTOR_003 | Investor - Boundary test: Name 255 chars (pass), 256 chars (blocked) | Admin đã vào Edit mode của S02-Investor | 1. Admin nhập Name với 255 ký tự<br>2. Admin click "Save"<br>3. Thử nhập 256 ký tự | Hệ thống chấp nhận 255 ký tự, lưu thành công. Nhập 256 ký tự → bị blocked. | P2 |
| TC_UC-2.14_INVESTOR_004 | Investor - Boundary test: Description 1000 chars (pass), 1001 chars (blocked) | Admin đã vào Edit mode của S02-Investor | 1. Admin nhập Description với 1000 ký tự<br>2. Admin click "Save"<br>3. Thử nhập 1001 ký tự | Hệ thống chấp nhận 1000 ký tự, lưu thành công. Nhập 1001 ký tự → bị blocked. | P2 |

---

## IV. S02-Bridge — Edit Distinction + Individual Price

| TC ID | Test Title | Pre-conditions | Test Steps | Expected Result | Priority |
|---|---|---|---|---|---|
| TC_UC-2.14_BRIDGE_001 | Bridge View mode - hiển thị đầy đủ thông tin + Individual Price | Admin đã điều hướng đến S02-Bridge | 1. Quan sát S02-Bridge ở View mode | Màn hình hiển thị đầy đủ: Distinction name, Description, Type (read-only), NFT Artwork image, và Individual Price | P1 |
| TC_UC-2.14_BRIDGE_002 | Bridge - Admin chỉnh sửa tất cả các trường (Name, Description, Image, Individual Price) | Admin đã điều hướng đến S02-Bridge | 1. Admin click "Edit"<br>2. Admin chỉnh sửa Name và Individual Price<br>3. Admin click "Save" | Hệ thống lưu tất cả thay đổi, hiển thị MSG-05, quay về View mode với dữ liệu mới | P1 |
| TC_UC-2.14_BRIDGE_003 | Bridge - Chỉnh sửa Individual Price thành công (valid number) | Admin đã vào Edit mode của S02-Bridge | 1. Admin nhập Individual Price: 19.00<br>2. Admin click "Save" | Hệ thống lưu Individual Price mới = 19.00, hiển thị MSG-05 | P1 |
| TC_UC-2.14_BRIDGE_004 | Bridge - Individual Price validation: vượt quá 999999999999 → MSG-09 | Admin đã vào Edit mode của S02-Bridge | 1. Admin nhập Individual Price: 999999999999.50 | Hệ thống hiển thị MSG-09: "Price must be less than or equal to {MAX_PRICE}" khi input vượt quá max | P2 |
| TC_UC-2.14_BRIDGE_005 | Bridge - Individual Price validation: input chữ cái bị blocked | Admin đã vào Edit mode của S02-Bridge | 1. Admin nhập "abc123" vào Individual Price field | Hệ thống chặn input, chỉ chấp nhận số và ký tự ". ,' " (CMR-01) | P2 |
| TC_UC-2.14_BRIDGE_006 | Bridge - Lưu với Individual Price mới thành công (MSG-05) | Admin đã vào Edit mode của S02-Bridge | 1. Admin nhập Individual Price: 25<br>2. Admin click "Save" | Hệ thống lưu thành công, hiển thị MSG-05: "Action completed" | P1 |

---

## V. S02-Package — Price Configuration per Class

| TC ID | Test Title | Pre-conditions | Test Steps | Expected Result | Priority |
|---|---|---|---|---|---|
| TC_UC-2.14_PKG_001 | Package View mode - hiển thị bảng Pricing Configuration đầy đủ | Admin đã điều hướng đến S02-Package | 1. Quan sát S02-Package ở View mode | Bảng hiển thị đúng 8 rows (Class 0-7) với 4 columns: Class, Package Price, Activation Credit, Package feature. Activation Credit là read-only. | P1 |
| TC_UC-2.14_PKG_002 | Package - Edit Package Price cho Class 0 thành công | Admin đã điều hướng đến S02-Package | 1. Admin click "Edit"<br>2. Admin nhập Package Price mới cho Class 0: 50000<br>3. Admin click "Save" | Hệ thống lưu giá mới, hiển thị MSG-05, reload S02 với Package Price mới cho Class 0 | P1 |
| TC_UC-2.14_PKG_003 | Package - Class 1 price change → Public Figures auto-sync | Admin đã điều hướng đến S02-Package | 1. Admin click "Edit"<br>2. Admin thay đổi Class 1 Price từ 35000 thành 40000<br>3. Quan sát Public Figures price<br>4. Admin click "Save" | Khi Class 1 price thay đổi, Public Figures price tự động thay đổi theo cùng giá trị (auto-sync). Sau khi save, cả hai đều = 40000. | P1 |
| TC_UC-2.14_PKG_004 | Package - Chỉnh sửa số Distinctions per Class | Admin đã điều hướng đến S02-Package | 1. Admin click "Edit"<br>2. Admin thay đổi số Distinctions cho Class 0<br>3. Admin click "Save" | Hệ thống lưu số Distinctions mới, hiển thị MSG-05 | P2 |
| TC_UC-2.14_PKG_005 | Package - Validation: Package Price vượt quá 999999999999 → MSG-09 | Admin đã vào Edit mode của S02-Package | 1. Admin nhập Package Price: 9999999999999 | Hệ thống hiển thị MSG-09: "Price must be less than or equal to {MAX_PRICE}" | P2 |
| TC_UC-2.14_PKG_006 | Package - Validation: Package Price với hơn 2 decimal places → prevent | Admin đã vào Edit mode của S02-Package | 1. Admin nhập Package Price: 1000.999 | Hệ thống ngăn không cho nhập phần thập phân thứ 3 (CMR-06: max 2 decimal places) | P2 |
| TC_UC-2.14_PKG_007 | Package - Validation: Package Price input chữ cái → blocked | Admin đã vào Edit mode của S02-Package | 1. Admin nhập Package Price: "ABC" | Hệ thống chặn input, chỉ chấp nhận số và ký tự ". ,' " (CMR-01) | P2 |
| TC_UC-2.14_PKG_008 | Package - Lưu Package Price mới thành công (MSG-05) | Admin đã vào Edit mode của S02-Package | 1. Admin nhập Package Price mới cho Class 0: 45000<br>2. Admin click "Save" | Hệ thống lưu thành công, hiển thị MSG-05: "Action completed", reload S02 với giá mới | P1 |
| TC_UC-2.14_PKG_009 | Package - Hủy chỉnh sửa Package Price (MSG-04) | Admin đã vào Edit mode của S02-Package với thay đổi chưa lưu | 1. Admin thay đổi Class 0 Price thành 50000<br>2. Admin click "Cancel" | Hệ thống hủy tất cả thay đổi, hiển thị MSG-04: "This action has been canceled", reload S02 với Class 0 Price = 35000 | P1 |
| TC_UC-2.14_PKG_010 | Package - System error khi save → MSG-33 | Admin đã vào Edit mode của S02-Package | 1. Admin nhập Package Price mới<br>2. Simulate system error when saving<br>3. Admin click "Save" | Hệ thống hiển thị MSG-33 (system error message) và dữ liệu không được lưu | P2 |
| TC_UC-2.14_PKG_011 | Package - Activation Credit là read-only (không thể chỉnh sửa) | Admin đã điều hướng đến S02-Package | 1. Admin click "Edit"<br>2. Thử click vào cột Activation Credit | Activation Credit luôn là read-only trong cả View mode và Edit mode, Admin không thể chỉnh sửa | P1 |
| TC_UC-2.14_PKG_012 | Package - Hiển thị Package Price đúng format (CMR-01: apostrophe separator) | Admin đã điều hướng đến S02-Package (View mode) | 1. Quan sát cách hiển thị giá trị trong bảng | Giá hiển thị đúng format: sử dụng apostrophe cho phần ngàn (ví dụ: 35'000), dấu chấm cho decimal (ví dụ: 1'234,56). Hover hiển thị full value với 6 decimal places. | P2 |
| TC_UC-2.14_PKG_013 | Package - Giá mới chỉ áp dụng cho purchases sau thay đổi | Admin đã thay đổi Package Price thành công | 1. Admin thay đổi Class 0 Price từ 35000 thành 50000 và lưu thành công<br>2. User purchase package sau thay đổi | User purchase sau khi Admin thay đổi giá sẽ được áp dụng giá mới (50000). Orders đã tạo trước đó vẫn giữ nguyên giá cũ (35000). | P1 |
| TC_UC-2.14_PKG_014 | Package - Admin edit rồi save không thay đổi gì | Admin đã điều hướng đến S02-Package | 1. Admin click "Edit"<br>2. Admin không thay đổi gì (giữ nguyên giá trị)<br>3. Admin click "Save" | Hệ thống xử lý gracefully, hiển thị MSG-05 "Action completed" và reload S02 | P2 |

---

## VI. Navigation & Common

| TC ID | Test Title | Pre-conditions | Test Steps | Expected Result | Priority |
|---|---|---|---|---|---|
| TC_UC-2.14_NAV_001 | Back button từ S02 quay về S01 | Admin đang ở S02 (bất kỳ: Collaboration/Investor/Bridge/Package) | 1. Admin click Back button trên S02 | Hệ thống điều hướng về S01 (Package and Distinctions list) | P1 |
| TC_UC-2.14_NAV_002 | Không có unsaved data warning khi rời S02 | Admin đang ở S02-Collaboration với thay đổi chưa lưu | 1. Admin thay đổi Name thành "Changed"<br>2. Admin click Back button | Hệ thống không hiển thị warning về unsaved data. Thay đổi được hủy theo behavior đã confirm với BA. | P2 |
| TC_UC-2.14_NAV_003 | Distinction Features info box hiển thị đúng các rules | Admin đã điều hướng đến S02 (bất kỳ distinction nào: Collaboration/Investor/Bridge) | 1. Quan sát Distinction Features info box | Info box hiển thị đúng các rules: Non-sellable, transferable 1x to non-custodial wallet; Both buyer and recipient receive NFT; 10% points bonus distributed to both parties; Anti-return validation prevents reciprocal exchanges in same year | P1 |
| TC_UC-2.14_NAV_004 | Verify Edit mode transition cho tất cả S02 (Collaboration, Investor, Bridge, Package) | Admin đã điều hướng đến từng S02 | 1. Lần lượt truy cập S02-Collaboration, S02-Investor, S02-Bridge, S02-Package<br>2. Tại mỗi màn hình, click "Edit" | Tất cả S02 đều chuyển sang Edit mode với behavior giống nhau: "Edit" → "Cancel" + "Save" | P1 |
| TC_UC-2.14_NAV_005 | Verify Cancel behavior cho tất cả S02 | Admin đang ở Edit mode với thay đổi chưa lưu | 1. Lần lượt test Cancel tại S02-Collaboration, S02-Investor, S02-Bridge, S02-Package | Tất cả đều hiển thị MSG-04 và hủy thay đổi giống nhau | P1 |

---

## Coverage Summary

| Section | Total TCs | GUI | FUNC |
|---|---|---|---|
| S01 - List & Navigation | 6 | 1 | 5 |
| S02-Collaboration | 16 | 2 | 14 |
| S02-Investor | 4 | 1 | 3 |
| S02-Bridge | 6 | 1 | 5 |
| S02-Package | 14 | 2 | 12 |
| Navigation & Common | 5 | 2 | 3 |
| **Total** | **51** | **9** | **42** |

---

## RTM (Requirements Traceability Matrix)

| TC ID | Scenario | Priority | Status |
|---|---|---|---|
| TC_UC-2.14_S01_001 | TS_UC-2.14_S01_001 | P1 | Ready |
| TC_UC-2.14_S01_002 | TS_UC-2.14_S01_002 | P1 | Ready |
| TC_UC-2.14_S01_003 | TS_UC-2.14_S01_003 | P1 | Ready |
| TC_UC-2.14_S01_004 | TS_UC-2.14_S01_004 | P1 | Ready |
| TC_UC-2.14_S01_005 | TS_UC-2.14_S01_005 | P1 | Ready |
| TC_UC-2.14_S01_006 | TS_UC-2.14_S01_006 | P1 | Ready |
| TC_UC-2.14_COLLAB_001 | TS_UC-2.14_COLLAB_001 | P1 | Ready |
| TC_UC-2.14_COLLAB_002 | TS_UC-2.14_COLLAB_002 | P1 | Ready |
| TC_UC-2.14_COLLAB_003 | TS_UC-2.14_COLLAB_003 | P1 | Ready |
| TC_UC-2.14_COLLAB_004 | TS_UC-2.14_COLLAB_004 | P1 | Ready |
| TC_UC-2.14_COLLAB_005 | TS_UC-2.14_COLLAB_005 | P1 | Ready |
| TC_UC-2.14_COLLAB_006 | TS_UC-2.14_COLLAB_006 | P1 | Ready |
| TC_UC-2.14_COLLAB_007 | TS_UC-2.14_COLLAB_007 | P2 | Ready |
| TC_UC-2.14_COLLAB_008 | TS_UC-2.14_COLLAB_008 | P2 | Ready |
| TC_UC-2.14_COLLAB_009 | TS_UC-2.14_COLLAB_009 | P1 | Ready |
| TC_UC-2.14_COLLAB_010 | TS_UC-2.14_COLLAB_010 | P1 | Ready |
| TC_UC-2.14_COLLAB_011 | TS_UC-2.14_COLLAB_003 (BVA) | P2 | Ready |
| TC_UC-2.14_COLLAB_012 | TS_UC-2.14_COLLAB_003 (BVA) | P2 | Ready |
| TC_UC-2.14_COLLAB_013 | TS_UC-2.14_COLLAB_003 (BVA) | P2 | Ready |
| TC_UC-2.14_COLLAB_014 | TS_UC-2.14_COLLAB_004 (BVA) | P2 | Ready |
| TC_UC-2.14_COLLAB_015 | TS_UC-2.14_COLLAB_004 (BVA) | P2 | Ready |
| TC_UC-2.14_COLLAB_016 | TS_UC-2.14_COLLAB_004 (BVA) | P2 | Ready |
| TC_UC-2.14_INVESTOR_001 | TS_UC-2.14_INVESTOR_001 | P1 | Ready |
| TC_UC-2.14_INVESTOR_002 | TS_UC-2.14_INVESTOR_002 | P1 | Ready |
| TC_UC-2.14_INVESTOR_003 | TS_UC-2.14_INVESTOR_003 | P2 | Ready |
| TC_UC-2.14_INVESTOR_004 | TS_UC-2.14_INVESTOR_004 | P2 | Ready |
| TC_UC-2.14_BRIDGE_001 | TS_UC-2.14_BRIDGE_001 | P1 | Ready |
| TC_UC-2.14_BRIDGE_002 | TS_UC-2.14_BRIDGE_002 | P1 | Ready |
| TC_UC-2.14_BRIDGE_003 | TS_UC-2.14_BRIDGE_003 | P1 | Ready |
| TC_UC-2.14_BRIDGE_004 | TS_UC-2.14_BRIDGE_004 | P2 | Ready |
| TC_UC-2.14_BRIDGE_005 | TS_UC-2.14_BRIDGE_004 (BVA) | P2 | Ready |
| TC_UC-2.14_BRIDGE_006 | TS_UC-2.14_BRIDGE_005 | P1 | Ready |
| TC_UC-2.14_PKG_001 | TS_UC-2.14_PKG_001 | P1 | Ready |
| TC_UC-2.14_PKG_002 | TS_UC-2.14_PKG_002 | P1 | Ready |
| TC_UC-2.14_PKG_003 | TS_UC-2.14_PKG_003 | P1 | Ready |
| TC_UC-2.14_PKG_004 | TS_UC-2.14_PKG_004 | P2 | Ready |
| TC_UC-2.14_PKG_005 | TS_UC-2.14_PKG_005 | P2 | Ready |
| TC_UC-2.14_PKG_006 | TS_UC-2.14_PKG_006 | P2 | Ready |
| TC_UC-2.14_PKG_007 | TS_UC-2.14_PKG_007 | P2 | Ready |
| TC_UC-2.14_PKG_008 | TS_UC-2.14_PKG_008 | P1 | Ready |
| TC_UC-2.14_PKG_009 | TS_UC-2.14_PKG_009 | P1 | Ready |
| TC_UC-2.14_PKG_010 | TS_UC-2.14_PKG_010 | P2 | Ready |
| TC_UC-2.14_PKG_011 | TS_UC-2.14_PKG_011 | P1 | Ready |
| TC_UC-2.14_PKG_012 | TS_UC-2.14_PKG_012 | P2 | Ready |
| TC_UC-2.14_PKG_013 | TS_UC-2.14_PKG_013 | P1 | Ready |
| TC_UC-2.14_PKG_014 | TS_UC-2.14_PKG_014 | P2 | Ready |
| TC_UC-2.14_NAV_001 | TS_UC-2.14_NAV_001 | P1 | Ready |
| TC_UC-2.14_NAV_002 | TS_UC-2.14_NAV_002 | P2 | Ready |
| TC_UC-2.14_NAV_003 | TS_UC-2.14_NAV_003 | P1 | Ready |
| TC_UC-2.14_NAV_004 | TS_UC-2.14_COLLAB_002 (derived) | P1 | Ready |
| TC_UC-2.14_NAV_005 | TS_UC-2.14_COLLAB_010 (derived) | P1 | Ready |

---

**File:** UC-2.14_package_config_testcases_20260529.md
**Total Test Cases:** 51 (GUI: 9, FUNC: 42)
**Status:** Generated
**Ready for:** Test Execution