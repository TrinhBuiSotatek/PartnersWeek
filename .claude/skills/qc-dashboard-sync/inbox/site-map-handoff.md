---
source_skill: qc-site-map
handoff_type: site-map-feature-coverage
mode: update
generated_at: 2026-05-26T00:30:00+07:00
---

# Site Map Handoff for Dashboard

Site map vừa được update (thêm 12 screens mới từ WBS BA Planning). Handoff này chứa thông tin cấp **feature/UC** để `qc-dashboard-sync` tạo/cập nhật dashboard.

## Feature-level site map coverage

| Feature ID | Feature name | Site / Portal | Module | Mapped screen(s) | Folder alias(es) | In scope? | Site map status | Notes |
|---|---|---|---|---|---|---|---|---|
| 1.1 | Landing page | User | Public | SCR-001 | UC-1.1 | Yes | Mapped | |
| 1.2 | Public Directory | User | Public | SCR-002 | UC-1.2 | Yes | Mapped | IPFS search |
| 1.3 | User Authentication | User | Auth | SCR-004, SCR-005, SCR-006 | UC-1.3 | Yes | Mapped | |
| 1.4 | User Profile | User | Profile | SCR-007, SCR-008, SCR-009 | UC-1.4 | Yes | Mapped | |
| 1.5 | Distinction Purchase | User | Catalog/Purchase | SCR-010, SCR-011, SCR-012 | UC-1.5 | Yes | Mapped | Core flow |
| 1.6 | NFT Transfer | User | NFT/Wallet | SCR-014 | UC-1.6 | Yes | Mapped | |
| 1.7 | Wallet | User | NFT/Wallet | SCR-013 | UC-1.7 | Yes | Mapped | |
| 1.8 | Event Access | User | Events | SCR-015, SCR-016, SCR-036 | UC-1.8 | Yes | Mapped | UC-8.3 Purchase Ticket tách riêng |
| 1.9 | User Dashboard | User | Dashboard | SCR-017, SCR-037, SCR-038, SCR-039 | UC-1.9 | Yes | Mapped | Sub-UCs từ WBS |
| 1.10 | Homepage | User | Public | SCR-003 | UC-1.10 | Yes | Mapped | |
| 2.10 | Admin Authentication | Admin | Auth | SCR-018, SCR-019 | | Yes | Mapped | |
| 2.11 | Admin Profile | Admin | Profile | SCR-020, SCR-021, SCR-022, SCR-040 | | Yes | Mapped | Thêm Delete Profile |
| 2.12 | Admin Management | Admin | Admin Mgmt | SCR-023, SCR-024 | | Yes | Mapped | |
| 2.13 | User Management | Admin | User Mgmt | SCR-025, SCR-041, SCR-042, SCR-043, SCR-044, SCR-045 | | Yes | Mapped | Thêm User Details, Activate/Deactivate, Waitlist, Registration Details, Company Approval |
| 2.14 | Distinction Management | Admin | Distinction Mgmt | SCR-026, SCR-027 | | Yes | Mapped | |
| 2.15 | Event Management | Admin | Event Mgmt | SCR-028, SCR-029 | | Yes | Mapped | |
| 2.16 | Points Distribution | Admin | Points | SCR-030, SCR-031 | | Yes | Mapped | |
| 2.17 | NFT Partners Awards | Admin | Awards | SCR-032, SCR-033 | | Yes | Mapped | |
| 2.18 | Admin Dashboard | Admin | Dashboard | SCR-034 | | Yes | Mapped | |
| 2.19 | Distinction Distribute | Admin | Distinction | SCR-035 | | Yes | Mapped | |
| 2.20 | Directory Management | Admin | Directory | SCR-046, SCR-047 | | Need confirm | Mapped | Mới từ WBS, cần xác nhận scope |

## Feature-level gaps

| Feature ID | Feature name | Gap | Impact to QC | Owner | Priority |
|---|---|---|---|---|---|
| 2.20 | Directory Management | Mới phát hiện từ WBS, chưa có trong UC List chính thức | Chưa rõ có trong scope V1 không | BA / QC Lead | Medium |

## Unmapped screens

None.

## Notes

- 12 screens mới thêm từ WBS BA Planning (SCR-036 → SCR-047).
- Total: 47 screens (35 cũ + 12 mới).
- Feature 2.20 (Directory Management) cần QC Lead xác nhận scope trước khi dashboard-sync tạo row.
- Notification (Email) được mention trong WBS nhưng không đủ thông tin để tạo screen/feature — để pending.
