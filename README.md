# IM HTML Style Guide

Claude Code plugin that teaches Claude the Integral Media brand rules — so when you ask it to create an HTML report, presentation, or document, it automatically uses the right colours, fonts, logo, and layout.

## Install

> **Important:** These commands are run from your **regular terminal** (bash/zsh), NOT from inside Claude Code's `❯` prompt. If Claude Code is open, exit it first with `/exit` or Ctrl+C.

```bash
claude plugin marketplace add integralmedia1/im-html-style-guide
claude plugin install im-html-style-guide
```

You should see two green ticks. Then open Claude Code as normal — the plugin loads automatically.

### Enable auto-updates (recommended)

By default, third-party plugins don't auto-update. To enable it so you always get the latest changes on startup:

1. Open Claude Code
2. Type `/plugin` to open the plugin manager
3. Go to the **Marketplaces** tab
4. Select `im-html-style-guide`
5. Enable **auto-update**

After that, the plugin refreshes automatically every time you start Claude Code.

## Manual update

If you haven't enabled auto-updates, pull the latest from your **terminal**:

```bash
claude plugin marketplace update im-html-style-guide
```

Then restart Claude Code.

## Usage

Once installed, just ask Claude to make an HTML document inside Claude Code. Any of these work:

- "Create an HTML report for [client name]"
- "Make a branded document about our SEO results"
- "Build an IM presentation for the quarterly review"

Claude will automatically use the brand template, inline the logo as SVG, and follow all style rules.

You can also invoke the skill directly with `/im-html-style-guide`.

## What's included

| Component | What it does |
|-----------|-------------|
| **Style guide** | Colours, typography, logo rules, do's and don'ts |
| **HTML template** | Ready-to-go template with all CSS inline |
| **Logo variants** | SVG (colour, black, white, dark bg) + PNG brandmarks |
| **Component library** | Cards, callouts, steps, timelines, status grids, tables, tabs, diagrams |
| **Lucide icons** | 24 pre-built inline SVG icons (no emoji) |
| **Mobile responsive** | 768px + 480px breakpoints, tested on mobile devices |
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
| **Icons** | Lucide inline SVGs (never emoji) |
| **Key rule** | Documents must be self-contained — inline CSS, inline SVG logos, no external stylesheets |

## Uninstall

From your **terminal** (not inside Claude Code):

```bash
claude plugin uninstall im-html-style-guide
claude plugin marketplace remove im-html-style-guide
```
