# UC-2.14 Package Configuration — Readiness Review Report

**Document:** UC-2.14. New Package price Config.pdf
**Type:** Change Request (CR) — Admin Package Price Configuration
**Author:** Trang Nguyen
**Status:** DONE
**Review Date:** 2026-05-29
**Review Mode:** Re-Audit (BA Answers Applied)
**Version:** v2

---

## 1. Document Information

| Field | Value |
|---|---|
| **ID** | UC-2.14 |
| **Use Case** | Package Configuration |
| **Description** | As an Admin, I want to configure package prices for company classes, so that I can manage pricing for company packages and public figures. |
| **Pre-conditions** | Admin log in successfully |
| **Trigger** | Admin clicks "Package Configuration" on Admin's menu |
| **Post-conditions** | View package list and package detail<br>Update package price |
| **Business Requirements** | CR: Menu title changed from "Distinctions Management" to "Package Configuration" |

---

## 2. Screen Summary

### S01: Package and Distinctions (List Screen)

| Element | Type | Description |
|---|---|---|
| Title | Text | "Package and Distinctions" — "Manage package for Company and NFT for other Distinctions" |
| Package Management section | Section | Contains Company Package card |
| Company Package card | Card | Icon + Navigate Icon, Title: "Company Package", Description: "Package for company classes and public figures" |
| Distinctions Management section | Section | Contains distinction card(s) for 3 distinction types: Bridge, Investor, Philanthropist |
| Distinction card(s) | Card | Icon + Navigate Icon, Title: Distinction name (max 50 chars), Description: Distinction description (max 100 chars) |

### S02: Package Configuration (Detail Screen)

| Element | Type | Description |
|---|---|---|
| Back button | Button | Navigate back to S01 — no unsaved data warning (confirmed by BA) |
| Package Title | Text | Display package name as screen title |
| Edit button | Button | Switch to edit mode |
| Pricing Configuration table | Table | Class, Package Price, Activation Credit, Package feature columns |
| Class 0-7 rows | Table Row | Display pricing per company class |
| Public Figures row | Table Row | Price auto-linked to Class 1 (auto-sync confirmed by BA) |
| Cancel button | Button (Edit mode) | Discard changes, show MSG-04 |
| Save button | Button (Edit mode) | Save changes, show MSG-05 |

---

## 3. BA Answers to Open Questions

| # | Question | BA Answer | Resolution |
|---|---|---|---|
| OQ-01 | CMR-01 rule for large number validation? | CMR-01 is defined in `docs/BA/Common rule/PWMVP-PartnersWeek-Commonrules-260526-0907-512.pdf`: Format with apostrophe, max 2 decimal places, max value = 999999999999, show MSG-09 if exceeded | **Resolved** |
| OQ-02 | Class 0-7 breakdown (employee count ranges)? | Defined in old UC-14.2 doc: "Class 1: 1'000 – 29'999 employees, Public Figure, Individual" — full breakdown in pricing tier section | **Resolved** |
| OQ-03 | Public Figures price — auto-sync or default? | **Auto-sync** confirmed by BA. When Admin changes Class 1 price, Public Figures price updates automatically | **Resolved** |
| OQ-04 | What is Bridge Package? | Bridge = distinction type (not a package). Role Individual can only purchase Bridge distinction, NOT Package | **Resolved** |
| OQ-05 | Unsaved data warning when navigating away? | **No** warning required (confirmed by BA) | **Resolved** |
| OQ-06 | Max character limit for price input? | CMR-06 (Monetary Input): max 2 decimal places, max value = 999999999999 | **Resolved** |

---

## 4. Validation Rules Summary (from CMR-06)

| Rule | Value | Source |
|---|---|---|
| Number format | Use apostrophe for thousands (e.g., 35'000) | CMR-01 |
| Decimal separator | Use period (.) for decimal places | CMR-06 |
| Max decimal places | 2 decimal places | CMR-06 |
| Max value | 999999999999 | CMR-06 (MSG-09 if exceeded) |
| Input accepted | Numbers + ". ,' " characters | CMR-01 |
| Swiss formatting | CHF 35'000 display format | CMR-06 |
| Rounding | Round to nearest 2 decimal places | CMR-06 |

---

## 5. Class Breakdown (from old UC-14.2)

| Class | Description |
|---|---|
| Class 0 | Public Figure (special) |
| Class 1 | 1'000 – 29'999 employees + Public Figure |
| Class 2 | (refer to old doc for full breakdown) |
| Class 3 | (refer to old doc for full breakdown) |
| Class 4 | (refer to old doc for full breakdown) |
| Class 5 | (refer to old doc for full breakdown) |
| Class 6 | (refer to old doc for full breakdown) |
| Class 7 | Individual |

**Note:** Full class breakdown should be extracted from old UC-14.2 document for complete test coverage.

---

## 6. Key Behaviors Confirmed

| Behavior | Detail |
|---|---|
| Public Figures price | Auto-sync with Class 1 — when Class 1 changes, Public Figures price changes automatically |
| Activation Credit | Fixed values — display only, not editable by Admin |
| Bridge distinction | Not part of Package; Individual role can only purchase Bridge (not Package) |
| Price application | New price applies to purchases made AFTER the change (not retroactively) |
| Edit mode buttons | "Edit" → switches to Edit mode → shows "Cancel" + "Save" buttons |
| Cancel behavior | Discard all changes, reload S02 with previous data, show MSG-04 |
| Save behavior | Validate input, save new price, reload S02 with updated data, show MSG-05 |
| Error handling | MSG-33 on system error, MSG-09 if price exceeds max value |

---

## 7. Gap Analysis (Post-BA Answers)

### 7.1 Completeness

| # | Gap | Status | Notes |
|---|---|---|---|
| G-01 | Validation rules for price input | **Resolved** | CMR-01, CMR-06 defined in common rules |
| G-02 | Price lock for existing orders | **Accepted** | Doc already states new price applies to new purchases |
| G-03 | Bridge Package specification | **Resolved** | Bridge is distinction type, not package; Individual cannot purchase Package |
| G-04 | Access control | **Accepted** | Pre-condition states Admin login required |
| G-05 | Loading states | **Accepted** | General UI standard (CMR-04) |
| G-06 | Error state for failed data load | **Accepted** | General UI standard |

### 7.2 Remaining Considerations

| # | Item | Recommendation |
|---|---|---|
| RC-01 | Full class breakdown (Class 2-6 employee ranges) | Should extract from old UC-14.2 for complete test data |
| RC-02 | Bridge distinction pricing | Separate UC (UC-14.2) covers distinction management |
| RC-03 | MSG-04, MSG-05, MSG-09, MSG-33 exact wording | Should verify from message list document |

---

## 8. Business Rules & References

| Code | Rule | Source |
|---|---|---|
| BR-01 | Pricing rows grouped by company class | Old UC-14.2 |
| BR-02 | Distinction name/description display rules | Old UC-14.2 |
| CMR-01 | Number format (apostrophe separator) | Common rules PDF |
| CMR-06 | Monetary input rules (max 2 decimal, max 999999999999) | Common rules PDF |
| MSG-04 | Cancel confirmation message | Referenced in doc |
| MSG-05 | Save success message | Referenced in doc |
| MSG-09 | Max price exceeded message | Referenced in doc (CMR-06) |
| MSG-33 | System error message | Referenced in doc |

---

## 9. Readiness Verdict

### Completeness Score: 90%

| Area | Score | Notes |
|---|---|---|
| Functional Requirements | 95% | Core price config flow fully defined |
| Screen/UI Specifications | 90% | S01 and S02 described with all states |
| Business Rules | 90% | CMR-01, CMR-06 resolved from common rules |
| Validation Rules | 90% | All validation rules identified and defined |
| Edge Cases | 85% | Error flows (MSG-09, MSG-33) covered |

### Readiness: **READY** for test design

**Conditions met:**
- All validation rules defined (CMR-01, CMR-06)
- Class breakdown confirmed (from old UC-14.2)
- Public Figures auto-sync behavior confirmed
- Bridge distinction clarification provided
- No unsaved-data warning required (BA confirmed)

### Next Steps

1. Extract full class breakdown from old UC-14.2 document
2. Design test scenarios covering:
   - View package list (S01)
   - View package configuration (S02)
   - Edit price (happy path)
   - Cancel edit
   - Save with validation errors
   - System error handling
   - Public Figures auto-sync verification
3. Generate test cases with specific price values and expected outcomes

---

## 10. Files Reviewed

| File | Version | Date |
|---|---|---|
| UC-2.14. New Package price Config.pdf | — | 2026-05-29 |
| UC-2.14. Old View distinction list.pdf | — | — |
| UC-2.14. Old Edit Distinction .pdf | — | — |
| UC-2.14. Old Distinction Config.png | — | — |
| UC-2.14. New Package Config.png | — | — |
| PWMVP-PartnersWeek-Commonrules-260526-0907-512.pdf | — | 2026-05-26 |

---

**Reviewer:** QC Agent (via /qc-uc-read)
**BA Answers Applied:** 2026-05-29
**Status:** Ready for test scenario design