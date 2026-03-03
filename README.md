# im-html-style-guide

Claude Code plugin for creating Integral Media branded HTML documents.

Provides the full IM brand style guide, colour palette, typography rules, component reference, and a ready-to-use HTML template — so Claude automatically follows brand guidelines when generating HTML reports, presentations, or documents.

## Install

```bash
# From GitHub
/plugin install integralmedia1/im-html-style-guide

# From local clone
git clone git@github.com:integralmedia1/im-html-style-guide.git
/plugin install ./im-html-style-guide
```

## Usage

The skill auto-triggers when you ask Claude to create branded HTML documents. You can also invoke it directly:

```
/im-html-style-guide
```

**Trigger phrases:** "create HTML report", "branded document", "IM report", "IM presentation", "HTML document for Integral Media"

## What's included

- Full brand colour palette (Sky Blue, Deep Navy, extended semantic colours)
- Typography rules (Julius Sans One, Inter, JetBrains Mono)
- Logo usage guidelines with inline SVG
- Component reference (cards, callouts, steps, timelines, status grids, tables, tabs, architecture diagrams)
- Self-contained HTML template with all CSS and inline logos
- White-label considerations for partner brands

## Assets

The `assets/` directory contains:
- `im-document-template.html` — ready-to-use template with `<!-- TEMPLATE: Replace -->` markers
- SVG logo variants (colour, black, white, dark background)
- PNG brandmark variants (colour, black)
