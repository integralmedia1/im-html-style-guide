# IM HTML Style Guide

Claude Code plugin that teaches Claude the Integral Media brand rules — so when you ask it to create an HTML report, presentation, or document, it automatically uses the right colours, fonts, logo, and layout.

## Install

Paste these into Claude Code (the `❯` prompt), one at a time:

```
/plugin marketplace add https://github.com/integralmedia1/im-html-style-guide.git
```

```
/plugin install im-html-style-guide
```

Then restart Claude Code to load the plugin.

**From your terminal** (outside Claude Code), the equivalent is:

```bash
claude plugin marketplace add https://github.com/integralmedia1/im-html-style-guide.git
claude plugin install im-html-style-guide
```

## Usage

Just ask Claude to make an HTML document. Any of these work:

- "Create an HTML report for [client name]"
- "Make a branded document about our SEO results"
- "Build an IM presentation for the quarterly review"

Claude will automatically use the brand template, inline the logo as SVG, and follow all style rules.

You can also invoke the skill directly with `/im-html-style-guide`.

## What's included

| Component | What it does |
|-----------|-------------|
| **Style guide** | Colours, typography, logo rules, do's and don'ts |
| **HTML template** | 888-line ready-to-go template with all CSS inline |
| **Logo variants** | SVG (colour, black, white, dark bg) + PNG brandmarks |
| **Component library** | Cards, callouts, steps, timelines, status grids, tables, tabs, diagrams |
| **White-label rules** | How to strip IM branding for Higher Ranking / Purpose Digital |

## Brand quick reference

| | Value |
|---|---|
| **Primary** | Sky Blue `#27C1F4` |
| **Secondary** | Deep Navy `#002F6C` |
| **Display font** | Julius Sans One (uppercase only, weight 400) |
| **Body font** | Inter |
| **Mono font** | JetBrains Mono |
| **Max width** | 960px |
| **Key rule** | Documents must be self-contained — inline CSS, inline SVG logos, no external stylesheets |

## Uninstall

```
/plugin uninstall im-html-style-guide
/plugin marketplace remove im-html-style-guide
```
