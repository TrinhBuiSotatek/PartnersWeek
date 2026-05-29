# Phase 1 — Synthesis: UC-2.14 Package Configuration

**Input language:** Vietnamese (source docs)
**UC-ID:** UC-2.14
**Source files read:**
- `docs/BA/UC-2.14/UC-2.14. New Package price Config.pdf` (v1, 2026-05-29)
- `docs/BA/UC-2.14/UC-2.14. Old View distinction list.pdf` (context - old UC-14.1)
- `docs/BA/UC-2.14/UC-2.14. Old Edit Distinction .pdf` (context - old UC-14.2)
- `docs/BA/UC-2.14/UC-2.14. Old Distinction Config.png` (design reference)
- `docs/BA/UC-2.14/UC-2.14. New Package Config.png` (new design)

**Blocked artefacts:** None

---

## 1. UI Object Inventory & Mapping

### Screen S01: Package and Distinctions (List)

| # | Name | Type | Required | Default Value | Placeholder | Enum Values | Section / Group | Source Image |
|---|------|------|----------|---------------|-------------|--------------|-----------------|--------------|
| 1 | Package and Distinctions | Title (Text) | N/A | — | — | — | Header | UC-2.14. New Package Config.png |
| 2 | "Manage package for Company and NFT for other Distinctions" | Description (Text) | N/A | — | — | — | Header | UC-2.14. New Package Config.png |
| 3 | Package Management | Section Title | N/A | — | — | — | Package Management | UC-2.14. New Package Config.png |
| 4 | Company Package | Card Title | N/A | — | — | — | Package Management > Card | UC-2.14. New Package Config.png |
| 5 | Package for company classes and public figures | Card Description | N/A | — | — | — | Package Management > Card | UC-2.14. New Package Config.png |
| 6 | Package card icon | Icon | N/A | — | — | — | Package Management > Card | UC-2.14. New Package Config.png |
| 7 | Navigate arrow icon (on Package card) | Icon Button | N/A | — | — | — | Package Management > Card | UC-2.14. New Package Config.png |
| 8 | Distinctions Management | Section Title | N/A | — | — | — | Distinction Management | UC-2.14. New Package Config.png |
| 9 | Distinction card(s) | Card | N/A | — | — | — | Distinction Management | UC-2.14. New Package Config.png |
| 10 | Distinction card icon | Icon | N/A | — | — | — | Distinction Management > Card | UC-2.14. New Package Config.png |
| 11 | Navigate arrow icon (on Distinction card) | Icon Button | N/A | — | — | — | Distinction Management > Card | UC-2.14. New Package Config.png |

### Screen S02: Package Configuration (Detail)

| # | Name | Type | Required | Default Value | Placeholder | Enum Values | Section / Group | Source Image |
|---|------|------|----------|---------------|-------------|--------------|-----------------|--------------|
| 1 | Back button | Button | N/A | — | — | — | Header | UC-2.14. New Package Config.png |
| 2 | Package name (as screen title) | Title (Text) | N/A | — | — | — | Header | UC-2.14. New Package Config.png |
| 3 | Edit button | Button | N/A | — | — | — | Header | UC-2.14. New Package Config.png |
| 4 | Pricing Configuration per Class | Section Title | N/A | — | — | — | Package Information | UC-2.14. New Package Config.png |
| 5 | Class column | Table Column (Header) | N/A | — | — | — | Pricing Configuration Table | UC-2.14. New Package Config.png |
| 6 | Package Price column | Table Column (Header) | N/A | — | — | — | Pricing Configuration Table | UC-2.14. New Package Config.png |
| 7 | Activation Credit column | Table Column (Header) | N/A | — | — | — | Pricing Configuration Table | UC-2.14. New Package Config.png |
| 8 | Package feature column | Table Column (Header) | N/A | — | — | — | Pricing Configuration Table | UC-2.14. New Package Config.png |
| 9 | Class 0 row | Table Row | N/A | — | — | — | Pricing Configuration Table | UC-2.14. New Package Config.png |
| 10 | Class 1 row (includes Public Figures note) | Table Row | N/A | — | — | — | Pricing Configuration Table | UC-2.14. New Package Config.png |
| 11 | Class 2 row | Table Row | N/A | — | — | — | Pricing Configuration Table | UC-2.14. New Package Config.png |
| 12 | Class 3 row | Table Row | N/A | — | — | — | Pricing Configuration Table | UC-2.14. New Package Config.png |
| 13 | Class 4 row | Table Row | N/A | — | — | — | Pricing Configuration Table | UC-2.14. New Package Config.png |
| 14 | Class 5 row | Table Row | N/A | — | — | — | Pricing Configuration Table | UC-2.14. New Package Config.png |
| 15 | Class 6 row | Table Row | N/A | — | — | — | Pricing Configuration Table | UC-2.14. New Package Config.png |
| 16 | Class 7 row | Table Row | N/A | — | — | — | Pricing Configuration Table | UC-2.14. New Package Config.png |
| 17 | Cancel button (edit mode) | Button | N/A | — | — | — | Header (edit mode) | UC-2.14. New Package Config.png |
| 18 | Save button (edit mode) | Button | N/A | — | — | — | Header (edit mode) | UC-2.14. New Package Config.png |
| 19 | Price input fields (Class 0-7) | Numeric Input | Yes | Current value as placeholder | — | Numbers only | Pricing Configuration Table (edit mode) | UC-2.14. New Package Config.png |

---

## 2. Object Attributes & Behavior Definition

### S01 Objects

| Object / Component | System States | Interaction Matrix | Behavior |
|---|---|---|---|
| Package Management section | Static display | N/A | Container section |
| Company Package card | Default | Click anywhere on card / Navigate icon | Navigate to S02 (Package Configuration) |
| Navigate icon (Package) | Enabled | Click | Navigate to S02 |
| Distinctions Management section | Static display | N/A | Container section |
| Distinction card(s) | Default | Click anywhere on card / Navigate icon | Navigate to UC-14.2: Edit Distinction |
| Navigate icon (Distinction) | Enabled | Click | Navigate to UC-14.2: Edit Distinction |

### S02 Objects

| Object / Component | System States | Interaction Matrix | Behavior |
|---|---|---|---|
| Back button | Enabled | Click | Navigate back to S01 |
| Edit button | Enabled (View mode) | Click | Switch to Edit mode — button changes to Cancel + Save |
| Package name title | Static (read-only) | N/A | Display package name as screen title |
| Pricing Configuration table | View mode: read-only display | N/A | Display pricing data per class |
| Class labels | Static | N/A | Display company class (Class 0 to Class 7) |
| Package Price values | View mode: read-only / Edit mode: editable | Click to edit | In edit mode, each price becomes input field |
| Activation Credit values | Static (fixed, not editable) | N/A | Display distribution credits per class |
| Package feature text | Static | N/A | Display feature explanation per class |
| Cancel button | Enabled (Edit mode only) | Click | Cancel all edits, reload S02 with previous data, show MSG-04 |
| Save button | Disabled (until valid change) / Enabled (when valid) | Click | Save updated price, reload S02 with new data, show MSG-05 |
| Price input fields | Edit mode only | Type input | Accept numbers only; validate per CMR-01 for large numbers |

---

## 3. Functional Logic & Workflow Decomposition

### Main Flow (Happy Path)

```
Admin selects "Package Configuration" from menu
  → System navigates to S01: Package and Distinctions
Admin clicks on Company Package card / Navigate icon
  → System navigates to S02: Package Configuration (View mode)
Admin views pricing table (Class 0-7, Package Price, Activation Credit, Package feature)
Admin clicks "Edit" button
  → System switches to Edit mode
  → Button changes from "Edit" to "Cancel" and "Save"
  → Price values change to input fields with current values as placeholder
Admin edits package price(s)
  → System validates input (numbers only, CMR-01 rule for large values)
Admin clicks "Save"
  → System saves new price configuration
  → System shows MSG-05 (success message)
  → System reloads S02 with updated data (View mode)
```

### Alternative Flows

**AF-01: Cancel edit**
```
Admin in Edit mode clicks "Cancel"
  → System discards all changes
  → System reloads S02 with previous data
  → System shows MSG-04 (cancel confirmation)
```

**AF-02: Edit with no changes**
```
Admin clicks "Edit" then clicks "Save" without making any changes
  → System should handle gracefully (no error, but no save either)
```

### Exception & Error Flows

**EF-01: Invalid input (non-numeric)**
```
Admin enters non-numeric characters in price field
  → System rejects input (validation: accept numbers only)
```

**EF-02: Number exceeds maximum**
```
Admin enters number exceeding max price (999999999999 per CMR rule)
  → System shows MSG-09
```

**EF-03: System error on save**
```
Admin clicks "Save" but system error occurs
  → System shows MSG-33 (system error message)
  → Data remains unsaved
```

---

## 4. Functional Integration Analysis

### Impact Analysis

| Change | Affected Area | Impact Type |
|---|---|---|
| Package price change | User UI — CR 1. Purchase Package | Direct: new price applies to users who purchase after change |
| Price edit | Pricing Configuration per Class table | Direct: updates all class pricing |
| Class 1 price change | Public Figures package price | Linked: Public Figures price = Class 1 price (same value) |

### Data Consistency

| Item | Consistency Rule |
|---|---|
| Package Price per class | Must persist and reflect on User UI purchase flow |
| Class 1 = Public Figures price | When Class 1 price changes, Public Figures price also changes |
| Activation Credit | Fixed values; not configurable by Admin |

---

## 5. Acceptance Criteria (AC) Synthesis

### Interface (UI) Criteria

| AC-ID | Criteria | Source |
|---|---|---|
| AC-01 | S01 displays "Package and Distinctions" as title with correct description | New Doc §S01 |
| AC-02 | S01 displays Package Management section with Company Package card | New Doc §S01 |
| AC-03 | S01 displays Distinctions Management section with distinction card(s) | New Doc §S01 |
| AC-04 | S02 displays Back button, package name as title, Edit button | New Doc §S02 |
| AC-05 | S02 displays Pricing Configuration table with Class 0-7, Package Price, Activation Credit, Package feature columns | New Doc §S02 |
| AC-06 | S02 displays correct package information per class in view mode | New Doc §S02 |

### Function Criteria

| AC-ID | Criteria | Source |
|---|---|---|
| AC-07 | Click on Company Package card navigates to S02 | New Doc §S01 |
| AC-08 | Click on Distinction card navigates to UC-14.2 | New Doc §S01 |
| AC-09 | Click "Edit" switches from View to Edit mode with Cancel + Save buttons | New Doc §S02 Behavior 1 |
| AC-10 | In Edit mode, price fields become editable inputs with current value as placeholder | New Doc §S02 Behavior 1 |
| AC-11 | "Cancel" discards changes, reloads S02 with previous data, shows MSG-04 | New Doc §S02 Validation |
| AC-12 | "Save" validates input (numbers only), saves new price, shows MSG-05 on success | New Doc §S02 Validation |
| AC-13 | "Save" shows MSG-33 on system error | New Doc §S02 Validation |
| AC-14 | Input validation: accept numbers only, CMR-01 rule for large values | New Doc §S02 Validation |
| AC-15 | Price change applies to User UI for purchases made after the change | New Doc §S02 Note |

### Integration Criteria

| AC-ID | Criteria | Source |
|---|---|---|
| AC-16 | Class 1 price change automatically updates Public Figures price (same value) | New Doc §S02 Note |
| AC-17 | Activation Credit values are fixed and cannot be configured | New Doc §S02 Note |

---

## UI Coverage Delta Table

| Image | elements_in_image | rows_in_section_4 | Delta | Action |
|-------|-------------------|-------------------|-------|--------|
| UC-2.14. New Package Config.png (S01+S02 combined) | ~25 visible elements | 19 rows (S01: 11, S02: 8 in View mode) | -6 | S02 Edit mode elements not shown in design (Cancel, Save, input fields) — counted as implied, not missing |

**Note:** Design image shows View mode. Edit mode UI elements (Cancel button, Save button, input fields) are described in the specification but not visible in the static image. Delta = 0 for View mode coverage; Edit mode elements are documented from spec.

---

## Working Notes

1. **Input language detected:** Vietnamese (source PDF documents)
2. **UC-ID:** UC-2.14 (Package Configuration)
3. **CR scope:** Only company package price configuration; Bridge package excluded (kept as current version)
4. **Key behavior:** Public Figures price is linked to Class 1 price — change one, change both
5. **Distinction management:** Part of S01 but navigates to existing UC-14.2 (not in CR scope for this review)
6. **Reference documents:**
   - Old UC-14.1 (View Distinction List) and UC-14.2 (Edit Distinction) provide context for distinction management
   - Old distinction config design shows pricing tiers by company class (similar structure to new package config)
7. **Common rules referenced:** CMR-01 (large number handling), MSG-04/05/09/33 (messages)
8. **No requirement-common-files found** — common rules path `docs/ba/Common rule/common-rules.md` does not exist