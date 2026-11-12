---
name: im-docs-style-guide
description: >
  This skill should be used when creating, formatting or restyling a Google Doc
  for Integral Media (IM) or an IM client, including any Docs API batchUpdate
  that writes or styles a document. Triggers include: "create a Google Doc",
  "write this up as a doc", "findings and plan doc", "client-facing doc",
  "brand this doc", "restyle the doc", "IM branded Google Doc", "format the
  document", "fix the page breaks".
version: 1.0.0
---

# IM Google Docs Style Guide

Every Google Doc IM creates, internal or client-facing, carries the IM brand from the first write. A doc left in the default font (Arial, or Aptos when it came from Word) reads as unbranded and has to be restyled before anyone sees it.

Colours and fonts are the same as the HTML style guide (`im-html-style-guide`). This file covers how they map onto Google Docs, and how to control page breaks.

## Page set-up

| Setting | Value |
|---|---|
| Page size | A4 (595.28 × 841.89 pt) |
| Margins | Top and bottom 64 pt, left and right 68 pt |
| Header margin | 28 pt |
| Header | IM colour logo, left aligned, 128 pt wide (keeps its 604 × 71 ratio, so about 15 pt high) |

Logo URL for `insertInlineImage`: `https://www.integralmedia.com.au/images/logo/integralmedia_colour.png` (colour on light backgrounds). Create the header with `createHeader` (type `DEFAULT`) first, then insert the image at index 0 of the returned header segment.

## Language

Set every doc to **English (United Kingdom)**: File → Language → English (United Kingdom). Docs offers no English (Australia). Docs created through the Docs or Drive API default to US English whatever the account or workspace language, and the API cannot change it, so this step is done in the browser after creation. The workspace default language is English (UK) (Admin console, Account settings → Profile, set 12 Nov 2026), which covers docs created by hand.

Google's grammar checker still suggests "inquiry" for "enquiry" in a UK document. "Enquiry" is correct British and Australian usage; dismiss the suggestion.

## Type

| Element | Font | Size | Colour | Spacing |
|---|---|---|---|---|
| Title (Heading 1) | Julius Sans One 400 | 24 pt | Deep Navy `#002F6C` | 6 above, 6 below, line spacing 105 |
| Subtitle line (client · date) | Inter 400 | 11 pt | Slate `#64748b` | 20 below, Sky Blue `#27C1F4` 2 pt bottom border, 10 pt padding |
| Section heading (Heading 2) | Julius Sans One 400 | 15 pt | Deep Navy | 18 above, 8 below |
| Sub-heading | Inter 700 | 10.5 pt | Deep Navy | 12 above, 6 below |
| Body | Inter 400 | 10.5 pt | Charcoal `#333740` | 0 above, 8 below, line spacing 125 |
| Bold lead-in ("1. Lead delivery depends on one person.") | Inter 700 | 10.5 pt | Deep Navy | |
| Bullets and numbered lists | Inter 400 | 10.5 pt | Charcoal | 5 below, indent start 22, first line 6 |
| Links | | | Sky Blue | |

Julius Sans One has one weight. Never set it bold.

**Bold needs the weight as well as the flag.** If a range has been given `weightedFontFamily` with weight 400, `bold: true` alone renders regular. Set `weightedFontFamily: { fontFamily: 'Inter', weight: 700 }` together with `bold: true`. The same trap hits when you restyle a whole document: apply the base font first, then reapply bold, with weight 700, to every bold run.

## Tables

| Part | Style |
|---|---|
| Header row | Deep Navy background, white Inter 700 text, pinned (`pinTableHeaderRows`, 1 row) |
| Body cells | White background, Inter 9.5 pt, line spacing 115, 0 space above and below |
| First column (row labels) | Inter 700, Deep Navy |
| Highlighted rows | Sky Muted `#e6f7fe` background, for the rows the text says matter most |
| Borders | Cool Grey `#DCDDEB`, 0.75 pt, all sides |
| Cell padding | 6 pt top and bottom, 7 pt left and right, top aligned |
| Column widths | `FIXED_WIDTH`, totalling the text width (459 pt on A4 with the margins above) |

## Page breaks

Check page breaks every time, not only when asked. A heading at the foot of a page, a list split across pages, or a table row broken in half all look careless in a client document.

1. **Headings stay with what follows.** Set `keepWithNext: true` on every heading and sub-heading.
2. **Paragraphs don't split.** Set `keepLinesTogether: true` and `avoidWidowAndOrphan: true` on all body paragraphs.
3. **Short lists stay whole.** Set `keepWithNext: true` on every item of a list except the last, when the list is short enough to fit on one page.
4. **Table rows don't split.** Set `preventOverflow: true` on every row with `updateTableRowStyle`, and pin the header row so it repeats if the table runs over a page.
5. **Start major sections on a new page when they would otherwise split.** Use `pageBreakBefore: true` on the section heading, for example a questions section that would otherwise break part way through.
6. **Verify on the rendered pages.** Export the doc to PDF (`gdrive files export <id> out.pdf`), render it (`pdftoppm -r 60 -png out.pdf p`, then `magick p-*.png +append all.png`) and look at every page. Adjust and re-render until each page ends at a natural break. Do this again after any later content change, since every edit can move the breaks.

## Applying it

Style an existing doc in one `batchUpdate`, in this order. Later requests override earlier ones on overlapping ranges.

1. `createHeader`, then `updateDocumentStyle` (page size, margins, header margin).
2. Base text and paragraph style across the whole body.
3. Title, subtitle, headings and sub-headings.
4. Bold runs (weight 700) and lead-in colour.
5. Lists: indents and spacing.
6. Tables: text size, cell styles, header row, column widths, row overflow, pinned header.
7. Page-break settings.

Then insert the logo into the header in a second call, export, render and check.
