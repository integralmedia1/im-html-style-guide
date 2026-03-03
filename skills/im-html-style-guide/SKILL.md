---
name: im-html-style-guide
description: >
  This skill should be used when the user asks to create an HTML document,
  report, presentation, or proposal branded to Integral Media (IM). Triggers
  include: "create HTML report", "branded document", "IM report", "IM
  presentation", "Integral Media document", "make a branded HTML page",
  "quarterly review document", "client report HTML", "SEO report for
  [client]", "create a styled HTML page", "HTML with IM branding".
version: 1.0.0
---

# Integral Media — HTML Document Style Guide

To create an Integral Media branded HTML document, follow these rules.

## Getting Started

1. Read the template file: `${CLAUDE_PLUGIN_ROOT}/assets/im-document-template.html`
2. Duplicate it as your starting point
3. Replace the `<!-- TEMPLATE: Replace -->` markers with actual content
4. All documents must be **self-contained** — inline CSS, inline SVG logos, no external stylesheets

---

## Brand Colours

| Name | Hex | CSS Variable | Usage |
|------|-----|-------------|-------|
| **Sky Blue** | `#27C1F4` | `--sky` | Primary accent, links, highlights, timeline dots. Note: logo icon mark uses `#23B2EF` (original brand file shade) |
| **Deep Navy** | `#002F6C` | `--navy` | Hero/footer backgrounds, section titles, headings, step badges |
| **Charcoal** | `#333740` | `--charcoal` | Body text |
| **Cool Grey** | `#DCDDEB` | `--cool-grey` | Borders, dividers, tab bars |
| **White** | `#FFFFFF` | `--white` | Card backgrounds, hero text |

### Extended Palette (derived, not in brand guidelines)

These are utility colours that complement the brand:

| Name | Hex | CSS Variable | Usage |
|------|-----|-------------|-------|
| Navy Light | `#0a3d7a` | `--navy-light` | Hover states on navy |
| Sky Light | `#4fd1ff` | `--sky-light` | Hover states on sky |
| Sky Muted | `#e6f7fe` | `--sky-muted` | Code backgrounds, callout backgrounds |
| Slate | `#64748b` | `--slate` | Secondary text, nav links |
| Light | `#f1f5f9` | `--light` | Table header backgrounds |
| Lighter | `#f8fafc` | `--lighter` | Page background |
| Green | `#22c55e` | `--green` | Success states, checkmarks |
| Green Muted | `#dcfce7` | `--green-muted` | Success badges |
| Amber | `#f59e0b` | `--amber` | Warning/conditional states |
| Amber Muted | `#fef3c7` | `--amber-muted` | Warning badges |
| Red | `#ef4444` | `--red` | Error/danger states |
| Warm Gray | `#94a3b8` | `--warm-gray` | Muted decorative text |
| Red Muted | `#fee2e2` | `--red-muted` | Danger badges |

---

## Typography

### Font Stack

```css
--display: 'Julius Sans One', 'Trebuchet MS', sans-serif;
--sans: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
--mono: 'JetBrains Mono', 'SF Mono', 'Fira Code', monospace;
```

### Google Fonts Import

```css
@import url('https://fonts.googleapis.com/css2?family=Julius+Sans+One&family=Inter:wght@300;400;500;600;700&family=JetBrains+Mono:wght@400;500&display=swap');
```

### Julius Sans One — Display Font

Used for: hero titles, section titles, section numbers, step number badges.

**Critical styling rules (must match logo usage):**
- **Always uppercase** (`text-transform: uppercase`)
- **Weight 400** (only available weight — do NOT use `font-weight: bold`)
- **Tight letter-spacing** — tighter than the font's natural spacing to match the logo's compact character spacing:
  - Hero h1 (large): `letter-spacing: -0.5px`
  - Section titles (medium): `letter-spacing: 0px`
  - Section numbers (decorative): `letter-spacing: 0px`
- **Never use for body text** — display only, for headings and labels

### Inter — Body Font

Used for: all body text, card headings (h3), paragraphs, lists, status card titles.

| Context | Size | Weight | Line Height |
|---------|------|--------|-------------|
| Body text | 15px | 400 | 1.7 |
| Card headings (h3) | 16px | 600 | default |
| Card/step body | 14.5px | 400 | 1.75 |
| Hero description | 16px | 300 | 1.7 |
| Status card body | 13.5px | 400 | 1.7 |

### JetBrains Mono — Monospace Font

Used for: labels, nav items, inline code, architecture diagrams, status badges, timeline dates.

| Context | Size | Weight | Letter Spacing |
|---------|------|--------|---------------|
| Labels / nav | 11px | 500 | 1.5–2.5px |
| Inline code | 12.5px | 500 | — |
| Architecture diagrams | 12.5px | 400 | — |
| Status badges | 10px | 500 | 0.5px |

---

## Logo

### Inline SVG (colour on dark background — for hero/footer)

The SVG is included directly in the template HTML. Two variants exist:

1. **Header logo** — icon mark in Sky Blue (`#23B2EF`), wordmark in white. Height: 28px.
2. **Footer logo** — same but with `opacity: 0.7` on container and wordmark in `rgba(255,255,255,0.7)`. Height: 22px.

### Rules

- **Never use an external image file** for the logo — always inline SVG for self-contained documents
- **Never modify logo colours** outside of the two approved variants (colour on dark, colour on light)
- **Icon mark** (geometric "i" + lightning bolt) is always Sky Blue `#23B2EF`
- **Wordmark** ("INTEGRAL MEDIA") is white on dark backgrounds, Deep Navy on light backgrounds
- The SVG viewBox is `0 0 1208 142` — always preserve aspect ratio

### Favicon

Use this inline data URI in the `<head>`:

```html
<link rel="icon" type="image/svg+xml" href="data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 166 142'><path d='M122.748 94.3069L106.15 139.418L35.686 3.69806L33.6758 0L74.2812 0.106144' fill='%2323B2EF'/><path d='M165.181 0H134.199V142H165.181V0Z' fill='%2323B2EF'/><path d='M26.7985 141.723H0.523438V81.779C0.523438 81.779 0.524017 55.1074 0.524017 53.4409H30.9802V141.723' fill='%2323B2EF'/><path d='M15.4909 32.2727C24.0462 32.2727 30.9817 25.0482 30.9817 16.1364C30.9817 7.2245 24.0462 0 15.4909 0C6.9355 0 0 7.2245 0 16.1364C0 25.0482 6.9355 32.2727 15.4909 32.2727Z' fill='%2323B2EF'/></svg>">
```

---

## Page Structure

### Layout

- Max content width: `960px`, centred with `margin: 0 auto`
- Side padding: `40px` (desktop), `20px` (mobile)
- Page background: `--lighter` (`#f8fafc`)

### Hero (Header)

- Background: `--navy`
- Decorative glow: `radial-gradient` circle in top-right (Sky Blue at 15% opacity)
- Bottom accent: 3px gradient line (`sky → navy → sky`)
- Contains: logo, label (monospace, uppercase, sky colour with left dash), h1 (Julius Sans One), description paragraph

### Sticky Navigation

- White background, bottom border in cool grey
- Links: monospace, 11px, uppercase, 1.5px letter-spacing
- Hover: navy text + sky bottom border

### Sections

- Padding: `70px 0 20px`
- Section header: number (Julius Sans One, 56px, sky at 35% opacity) + title (Julius Sans One, 28px, navy, uppercase)
- Bottom border on header: 1px cool grey

### Cards

- White background, cool grey border, 10px border-radius
- Padding: 32px
- Subtle hover shadow: `0 4px 24px rgba(0,47,108,0.06)`
- Card headings: Inter 16px 600 with optional 28px icon square (navy background, 6px radius)

### Footer

- Background: `--navy`
- Logo at reduced opacity (0.7)
- "Last updated" text: monospace, 11px, white at 40% opacity

---

## Component Reference

### Callout Box

```html
<div class="callout">
  <strong>Note:</strong> Important information here.
</div>
```

Sky muted background, 3px sky left border, rounded right corners.

### Step Cards (numbered)

```html
<div class="step">
  <div class="step-num">1</div>
  <h3>Step Title</h3>
  <p>Description text.</p>
</div>
```

White card with 88px left padding, navy number badge (40x40, 10px radius, Julius Sans One).

### Auto-list (inside steps)

```html
<div class="auto-list">
  <p>Section Label</p>
  <ul>
    <li>Item with green checkmark</li>
  </ul>
</div>
```

Lighter background, monospace label, green check marks.

### Timeline

Vertical timeline with sky-to-grey gradient line, dot markers, date labels in monospace.

### Status Cards (3-column grid)

Cards with coloured top borders (amber for warning, green for success, red for danger). Status badges use matching muted backgrounds.

### Registry Tables

Clean minimal tables with monospace uppercase headers, light background header row, subtle bottom borders.

### Tab Bar (spreadsheet visualisation)

Horizontal tabs mimicking a spreadsheet tab bar. Active tab in navy, hidden tabs dashed border.

### Architecture Diagram

Navy background code block with syntax highlighting via span classes: `.comment` (30% white), `.highlight` (sky), `.accent` (green #86efac), `.warm` (yellow #fcd34d).

### Inline Code

```css
code {
  font-family: var(--mono);
  font-size: 12.5px;
  background: var(--sky-muted);
  padding: 2px 7px;
  border-radius: 4px;
  color: var(--navy);
  font-weight: 500;
}
```

### Status Badges

```html
<span class="status-badge paused">paused</span>
<span class="status-badge active">active</span>
<span class="status-badge archived">archived</span>
```

### Conditional Labels

```html
<span class="cond">If condition</span>
```

Amber muted background, monospace uppercase, 10.5px.

---

## Responsive Breakpoints

Single breakpoint at `768px`:
- Hero h1: 42px → 28px
- Container padding: 40px → 20px
- Section number: 56px → 40px
- Section title: 28px → 22px
- Step left padding: 88px → 72px
- Status grid: 3 columns → 1 column
- Nav links: smaller font + tighter padding

---

## Do's and Don'ts

### Do

- Use the template as a starting point
- Keep the hero + nav + sections + footer structure
- Use inline SVG for the logo (self-contained documents)
- Apply `text-transform: uppercase` and tight letter-spacing on Julius Sans One
- Use the extended colour palette for status/semantic colours
- Include the favicon data URI

### Don't

- Use Julius Sans One for body text
- Bold Julius Sans One (`font-weight: 400` only)
- Add wide letter-spacing to Julius Sans One (tighten it to match the logo)
- Use colours outside the palette without good reason
- Link to external stylesheets (documents must be self-contained)
- Include any client-specific branding if the document is for a white-label partner (Higher Ranking, Purpose Digital). In that case, remove all IM logos and references — use navy + sky colours only.
- Reference Integral Media in documents intended for Higher Ranking or Purpose Digital clients

---

## White-Label Considerations

If creating a document for a **white-label partner** (Higher Ranking, Purpose Digital):
- Remove all IM logos and "Integral Media" text
- The navy/sky colour palette is safe to use (it's generic enough)
- Replace the hero label and footer with partner-appropriate text
- Do NOT include any IM email addresses, names, or references
