# QC Dashboard

> **Source of truth** cho trạng thái artifact của tất cả features/use cases trong dự án.
>
> **Ownership:**
> - `qc-dashboard-sync` — **owner duy nhất** của file này. Quản lý cột: `Site`, `Feature ID`, `Folder ID`, `Module`, `Feature/Use case name`, `In scope?`, `Files stt`. Tạo file từ template khi chưa có; tự thêm row khi phát hiện folder UC mới qua bottom-up; KHÔNG tự quyết định `In scope?` (chỉ copy từ site-map handoff hoặc set `Need confirm` cho bottom-up).
> - `qc-uc-read` quản lý cột: `UC review stt`.
> - `qc-func-scenario-design` quản lý cột: `Scenario design stt`.
> - `qc-func-tc-design` quản lý cột: `TC design stt`.
> - `qc-site-map` là nguồn duy nhất quyết định feature list + In scope? (qua handoff `site-map-handoff.md` và Mode 3 reconcile của orphans).
> - `qc-context-master` produce project context (KHÔNG tự ghi vào dashboard).
> - Cột `Execute stt` hiện đang pending (chưa có skill quản lý — để trống).
>
> **DO NOT delete rows.** Feature/UC ra khỏi scope vẫn giữ row, user có thể edit `In scope?` về `No` thủ công nếu cần.

| Site | Feature ID | Folder ID | Module | Feature/Use case name | In scope? | Files stt | UC review stt | Scenario design stt | TC design stt | Execute stt |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| User | 1.1 | UC-1.1 | Public | Landing page | Yes | Specs: V1<br>WF: Missing<br>Audited: Missing<br>Scenario: Missing<br>TC md: Missing<br>TC xlsx: Missing | | | | |
| User | 1.2 | UC-1.2 | Public | Public Directory | Yes | Specs: V1<br>WF: Missing<br>Audited: Missing<br>Scenario: Missing<br>TC md: Missing<br>TC xlsx: Missing | | | | |
| User | 1.3 | UC-1.3 | Auth | User Authentication | Yes | Specs: V1<br>WF: Missing<br>Audited: Missing<br>Scenario: Missing<br>TC md: Missing<br>TC xlsx: Missing | | | | |
| User | 1.4 | UC-1.4 | Profile | User Profile | Yes | Specs: V1<br>WF: Missing<br>Audited: Missing<br>Scenario: Missing<br>TC md: Missing<br>TC xlsx: Missing | | | | |
| User | 1.5 | UC-1.5 | Catalog/Purchase | Distinction Purchase | Yes | Specs: V1<br>WF: V1<br>Audited: V2<br>Scenario: Missing<br>TC md: V1<br>TC xlsx: V1 | UC review: ✅ READY (70,0/100) — Q1-Q10 BA resolved | | v1 generated | |
| User | 1.6 | UC-1.6 | NFT/Wallet | NFT Transfer | Yes | Specs: V1<br>WF: Missing<br>Audited: Missing<br>Scenario: Missing<br>TC md: Missing<br>TC xlsx: Missing | | | | |
| User | 1.7 | UC-1.7 | NFT/Wallet | Wallet | Yes | Specs: V1<br>WF: Missing<br>Audited: Missing<br>Scenario: Missing<br>TC md: Missing<br>TC xlsx: Missing | | | | |
| User | 1.8 | UC-1.8 | Events | Event Access | Yes | Specs: V1<br>WF: Missing<br>Audited: Missing<br>Scenario: Missing<br>TC md: Missing<br>TC xlsx: Missing | | | | |
| User | 1.9 | UC-1.9 | Dashboard | User Dashboard | Yes | Specs: V1<br>WF: V1<br>Audited: V1<br>Scenario: V1<br>TC md: V1<br>TC xlsx: V1 | UC review: ✅ READY (100,0/100) — all Qs resolved | v1 generated | v1 generated | |
| User | 1.10 | UC-1.10 | Public | Homepage | Yes | Specs: V1<br>WF: Missing<br>Audited: Missing<br>Scenario: Missing<br>TC md: Missing<br>TC xlsx: Missing | | | | |
| Admin | 2.10 | 2.10 | Auth | Admin Authentication | Yes | Specs: Missing<br>WF: Missing<br>Audited: Missing<br>Scenario: Missing<br>TC md: Missing<br>TC xlsx: Missing | | | | |
| Admin | 2.11 | 2.11 | Profile | Admin Profile | Yes | Specs: Missing<br>WF: Missing<br>Audited: Missing<br>Scenario: Missing<br>TC md: Missing<br>TC xlsx: Missing | | | | |
| Admin | 2.12 | 2.12 | Admin Mgmt | Admin Management | Yes | Specs: Missing<br>WF: Missing<br>Audited: Missing<br>Scenario: Missing<br>TC md: Missing<br>TC xlsx: Missing | | | | |
| Admin | 2.13 | 2.13 | User Mgmt | User Management | Yes | Specs: Missing<br>WF: Missing<br>Audited: Missing<br>Scenario: Missing<br>TC md: Missing<br>TC xlsx: Missing | | | | |
| Admin | 2.14 | 2.14 | Distinction Mgmt | Distinction Management | Yes | Specs: Missing<br>WF: Missing<br>Audited: Missing<br>Scenario: Missing<br>TC md: Missing<br>TC xlsx: Missing | | | | |
| Admin | 2.15 | 2.15 | Event Mgmt | Event Management | Yes | Specs: Missing<br>WF: Missing<br>Audited: Missing<br>Scenario: Missing<br>TC md: Missing<br>TC xlsx: Missing | | | | |
| Admin | 2.16 | 2.16 | Points | Points Distribution | Yes | Specs: Missing<br>WF: Missing<br>Audited: Missing<br>Scenario: Missing<br>TC md: Missing<br>TC xlsx: Missing | | | | |
| Admin | 2.17 | 2.17 | Awards | NFT Partners Awards | Yes | Specs: Missing<br>WF: Missing<br>Audited: Missing<br>Scenario: Missing<br>TC md: Missing<br>TC xlsx: Missing | | | | |
| Admin | 2.18 | 2.18 | Dashboard | Admin Dashboard | Yes | Specs: Missing<br>WF: Missing<br>Audited: Missing<br>Scenario: Missing<br>TC md: Missing<br>TC xlsx: Missing | | | | |
| Admin | 2.19 | 2.19 | Distinction | Distinction Distribute | Yes | Specs: Missing<br>WF: Missing<br>Audited: Missing<br>Scenario: Missing<br>TC md: Missing<br>TC xlsx: Missing | | | | |
| Admin | 2.20 | 2.20 | Directory | Directory Management | Need confirm | Specs: Missing<br>WF: Missing<br>Audited: Missing<br>Scenario: Missing<br>TC md: Missing<br>TC xlsx: Missing | | | | |
| User | 1.11 | UC-1.11 | Catalog/Purchase | Purchase Package | Need confirm | Specs: V1<br>WF: V1<br>Audited: V2<br>Scenario: V1<br>TC md: V1<br>TC xlsx: V1 | UC review: ✅ READY (95,4/100) — all Qs resolved | v1 generated | v1 generated | |
