---
name: im-sheets-style-guide
description: >
  This skill should be used when the user asks to format a Google Spreadsheet
  with Integral Media (IM) branding, or when building Google Sheets API
  batchUpdate requests for IM-branded spreadsheets. Triggers include: "format
  this spreadsheet", "IM sheets style", "branded Google Sheet", "style this
  sheet", "format the audit spreadsheet", "apply IM formatting", "Google Sheets
  batchUpdate formatting", "make this sheet look professional".
version: 1.0.0
---

# Integral Media — Google Sheets Style Guide

Brand-faithful formatting for Google Sheets, derived from the IM HTML style guide (`integralmedia1/im-html-style-guide`). Adapted for Sheets constraints: limited fonts, no border-radius/shadows/text-transform. All colour combinations pass WCAG AA (4.5:1+ for normal text).

---

## Colour Palette

| Token | Hex | RGB (0-1) | WCAG Notes | Usage |
|-------|-----|-----------|------------|-------|
| `navy` | `#002F6C` | `0.0, 0.184, 0.424` | 17.5:1 vs white | Document title row bg, summary tab colour |
| `navy-light` | `#0A3D7A` | `0.039, 0.239, 0.478` | 14.4:1 vs white | Section divider row bg |
| `sky` | `#27C1F4` | `0.153, 0.757, 0.957` | Accent only | Tab colours (data tabs), accent borders |
| `sky-muted` | `#E6F7FE` | `0.902, 0.969, 0.996` | 6.3:1 vs slate-dark | Notes/data source bg, LOW priority bg |
| `charcoal` | `#333740` | `0.200, 0.216, 0.251` | 14.8:1 vs white | All body text |
| `cool-grey` | `#DCDDEB` | `0.863, 0.867, 0.922` | — | All borders, horizontal rules |
| `light` | `#F1F5F9` | `0.945, 0.961, 0.976` | 14.0:1 vs charcoal | Column header bg, alternating row band |
| `lighter` | `#F8FAFC` | `0.973, 0.980, 0.988` | 16.7:1 vs navy | Sub-header bg |
| `slate-dark` | `#475569` | `0.278, 0.333, 0.412` | 6.3:1 vs sky-muted | Secondary text (notes, footnotes) |
| `white` | `#FFFFFF` | `1.0, 1.0, 1.0` | — | Primary row bg, text on dark bg |
| `subtitle-grey` | `#CCCCCC` | `0.8, 0.8, 0.8` | 10.8:1 vs navy | Subtitle text on navy bg |
| `red-muted` | `#FEE2E2` | `0.996, 0.886, 0.886` | 12.4:1 vs charcoal | HIGH priority bg |
| `amber-muted` | `#FEF3C7` | `0.996, 0.953, 0.780` | 13.8:1 vs charcoal | MEDIUM priority bg |
| `amber` | `#F59E0B` | `0.961, 0.620, 0.043` | — | Warning row left border accent |
| `green-muted` | `#DCFCE7` | `0.863, 0.988, 0.906` | 14.2:1 vs charcoal | VERIFIED / complete bg |

### Accessibility Notes
- `slate` (#64748B) replaced with `slate-dark` (#475569) for all secondary text — original was borderline 4.5:1 on sky-muted, new value gives 6.3:1 headroom
- Minimum font size: 10pt everywhere (no 9pt)
- Separator rows: 20px minimum (invisible rows break keyboard nav + screen readers)
- Priority/warning rows use colour + text label + left border accent (not colour-only)

---

## Element Specifications

| Element | Background | Text Colour | Font | Size | Bold | Height | Merge | Borders |
|---------|-----------|-------------|------|------|------|--------|-------|---------|
| Document title | `navy` | `white` | Roboto | 14pt | Yes | 40px | Full width | Bottom: 3px `sky` accent |
| Subtitle rows | `navy` | `subtitle-grey` | Roboto | 10pt | No | 22px | Full width | None |
| Section divider | `navy-light` | `white` | Roboto | 11pt | Yes | 30px | Full width | None |
| Column header | `light` | `charcoal` | Roboto | 10pt | Yes | 28px | No | Bottom: 1px `cool-grey` |
| Sub-header | `lighter` | `navy` | Roboto | 10pt | Yes | 26px | Full width | Bottom: 1px `cool-grey` |
| Data cell (single-line) | `white` | `charcoal` | Roboto | 10pt | No | 24px | No | Bottom: 1px `cool-grey` |
| Data cell (wrapped) | `white` | `charcoal` | Roboto | 10pt | No | 42px | No | Bottom: 1px `cool-grey` |
| Alt data cell (single-line) | `light` | `charcoal` | Roboto | 10pt | No | 24px | No | Bottom: 1px `cool-grey` |
| Alt data cell (wrapped) | `light` | `charcoal` | Roboto | 10pt | No | 42px | No | Bottom: 1px `cool-grey` |
| Data source note | `sky-muted` | `slate-dark` | Roboto | 10pt | Italic | 24px | Full width | None |
| Separator row | `white` | — | — | — | — | **20px** | — | None |
| HIGH priority | `red-muted` | `charcoal` | Roboto | 10pt | Yes | 24px | No | Left: 3px `red` |
| MEDIUM priority | `amber-muted` | `charcoal` | Roboto | 10pt | Yes | 24px | No | Left: 3px `amber` |
| LOW priority | `sky-muted` | `charcoal` | Roboto | 10pt | Yes | 24px | No | Left: 3px `sky` |
| Warning row | `amber-muted` | `charcoal` | Roboto | 10pt | **Yes** | 24px | No | Left: 3px `amber` |

---

## Design Decisions

- **Font:** Roboto everywhere (closest to Inter in Sheets). Roboto Mono for email addresses and IDs.
- **Hierarchy:** Navy title → navy-light sections → light headers → white/light data rows (4 levels)
- **Borders:** Horizontal rules only — 1px cool-grey bottom border on every data row. No full grid.
- **Sky accent:** Used sparingly — tab colours + title bottom accent border only. Never as cell bg.
- **Separator rows:** 20px empty rows for breathing space, accessible for keyboard nav.
- **Text wrapping:** Default to **WRAP on all content columns**. Only use CLIP/OVERFLOW on explicitly short-value columns (single status words, yes/no, single IDs under 15 chars). When in doubt, WRAP.
- **Frozen rows:** Row 1 on data tabs, none on Summary/report tabs.
- **Alignment:** Left-align all text columns. Never centre-align text columns.
- **Tab colours:** Summary = navy (#002F6C), data tabs = sky (#27C1F4).

### Column Width Guidelines

| Content Type | Width (px) |
|-------------|-----------|
| Dates | 140 |
| Email addresses | 250 |
| IDs / short codes | 110-140 |
| Names / labels | 220-280 |
| Status / role | 120-140 |
| Notes / descriptions | 300-400 |
| URLs | 320-400 |

---

## Anti-Patterns (Do Not)

- Full grid borders (overwhelming)
- Bright saturated cell backgrounds (unprofessional, accessibility issues)
- Multiple font families (visual noise)
- Centre-aligned text columns (harder to scan)
- Font sizes below 10pt (readability on laptop screens)
- Invisible separator rows (<20px)
- Colour-only status indicators (accessibility failure)
- Relying on sheet default for white backgrounds (residual formatting bleeds through from previous sessions)
- Formatting only the data range without clearing surrounding columns/rows (old banding/formatting artifacts remain visible)

---

## White-Label Adaptation

Same formatting rules apply for white-label partner clients — just remove all IM references from content. No brand modifications needed to the formatting itself.

---

## API Reference

When building batchUpdate requests, use the RGB (0-1) values from the colour palette. Google Sheets API expects `{ red: 0.0, green: 0.184, blue: 0.424 }` format.

### Implementation Rules

- **Explicit white backgrounds:** Always set explicit white backgrounds on ALL data rows. Never rely on the sheet default — previous formatting sessions may have left residual cell-level backgrounds that override the sheet default.
- **Clear beyond data range:** After formatting the data range, clear all backgrounds from `endColumn` to column Z and from `endRow` to row 100+. Old banded ranges and formatting often extend beyond the visible data area.
- **Default wrap strategy:** Set `wrapStrategy: "WRAP"` on all content columns. Only use CLIP/OVERFLOW on columns with short single-value content (yes/no, single IDs under 15 chars).

### API Gotchas

- **Unmerge before merge:** Always send `unmergeCells` on the full sheet range before applying any new `mergeCells` requests. Otherwise you'll get "You must select all cells in a merged range to merge or unmerge them" errors from cells merged in previous sessions.
- **Banding conflicts:** `addBanding` fails if any banded range already overlaps the target range. The correct delete method is `deleteBanding` (not `deleteBandedRange`). Query existing banded ranges first and delete ALL of them, not just known IDs.

### Typical Request Order per Tab

0. `unmergeCells` — clear all existing merges on the full sheet range
1. `deleteBanding` — query and remove ALL existing banded ranges
2. `updateSheetProperties` — tab colour, frozen rows
3. `mergeCells` — section dividers, title rows, note rows
4. `updateDimensionProperties` — column widths + row heights
5. `repeatCell` — backgrounds, text formatting, fonts, alignment, wrap
6. `updateBorders` — horizontal rules, accent borders
7. `addBanding` — alternating rows on data sections with 8+ rows
8. Clear formatting beyond data range — explicit white bg on surrounding empty cells
