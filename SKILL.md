---
name: antidesign
description: Browse and select from 54 curated design systems (Vercel, Stripe, Linear, Apple, etc.) and copy the DESIGN.md into your current project. Use when you need a production-grade design system for a new or existing project.
---

# antidesign -- Design System Selection Skill

You are helping the user select and apply a production-grade design system from the antidesign collection. Follow this workflow exactly.

## Setup

The skill directory contains 54 curated DESIGN.md files at `design-md/<brand>/DESIGN.md`. Each is a complete 9-section design system document extracted from real websites.

First, determine the skill directory location. It is wherever this SKILL.md file lives. The design files are at `<skill-dir>/design-md/`.

Verify the collection is available:
```bash
ls <skill-dir>/design-md/ | wc -l
```

Also determine the user's current working directory -- this is where the DESIGN.md will be written.

## Phase 1: Design System Selection

Use **AskUserQuestion** to narrow down the right design system in 2-3 rounds.

### Round 1: Market & Aesthetic (ask both simultaneously)

**Question 1: Target market** (header: "Market")

Ask: "What market or industry is this project targeting?"

Options:
- **Developer tools & APIs** -- SaaS for developers, CLIs, platforms, integrations
- **AI & Machine learning** -- AI products, model APIs, ML infrastructure
- **Fintech & Payments** -- Banking, crypto, payments, financial services
- **Consumer & Marketplace** -- Consumer apps, marketplaces, media, social
- **Enterprise & B2B** -- Enterprise software, infrastructure, cloud services

**Question 2: Visual aesthetic** (header: "Aesthetic")

Ask: "What visual style fits this project?"

Options:
- **Minimal & typography-first** -- Clean whitespace, tight letter-spacing, type carries the design. Feels precise and modern.
- **Warm & approachable** -- Organic shapes, warm colors, generous spacing. Feels human and inviting.
- **Bold & dark-native** -- Dark backgrounds, high contrast, vivid accents. Feels technical and powerful.
- **Clean & precise** -- Balanced layouts, neutral palette, systematic spacing. Feels polished and professional.

### Round 2: Select a Design System

Based on the market + aesthetic answers, use the mapping table below to select the top 3 recommended brands:

**DESIGN RECOMMENDATION MAP:**

| Market | Minimal & typography | Warm & approachable | Bold & dark-native | Clean & precise |
|--------|---------------------|--------------------|--------------------|-----------------|
| Developer tools | vercel, linear.app, resend | notion, mintlify, intercom | cursor, supabase, warp | figma, expo, stripe |
| AI & ML | vercel, linear.app, opencode.ai | claude, cohere, ollama | mistral.ai, x.ai, elevenlabs | replicate, together.ai, runwayml |
| Fintech | stripe, wise, revolut | revolut, wise, intercom | kraken, coinbase, kraken | stripe, wise, coinbase |
| Consumer | uber, pinterest, airbnb | airbnb, spotify, pinterest | spotify, bmw, spacex | apple, pinterest, uber |
| Enterprise | hashicorp, mongodb, sanity | intercom, airtable, miro | nvidia, spacex, clickhouse | ibm, apple, hashicorp |

Read the first ~20 lines of each recommended brand's DESIGN.md to extract the visual theme description for the option preview:

```
Read <skill-dir>/design-md/<brand>/DESIGN.md (limit: 20 lines)
```

Ask: "Which design system should we use?"

Show the 3 recommended brands as options with brief descriptions from the theme section. Include a 4th option: **"Browse all 54"** to see the full list.

If the user picks "Other" or "Browse all 54", show the full categorized list and let them name a brand:

### AI & Machine Learning
`claude`, `cohere`, `elevenlabs`, `minimax`, `mistral.ai`, `ollama`, `opencode.ai`, `replicate`, `runwayml`, `together.ai`, `voltagent`, `x.ai`

### Developer Tools & Platforms
`cursor`, `expo`, `linear.app`, `lovable`, `mintlify`, `posthog`, `raycast`, `resend`, `sentry`, `supabase`, `superhuman`, `vercel`, `warp`, `zapier`

### Infrastructure & Cloud
`clickhouse`, `composio`, `hashicorp`, `mongodb`, `sanity`, `stripe`

### Design & Productivity
`airtable`, `cal`, `clay`, `figma`, `framer`, `intercom`, `miro`, `notion`, `pinterest`, `webflow`

### Fintech & Crypto
`coinbase`, `kraken`, `revolut`, `wise`

### Enterprise & Consumer
`airbnb`, `apple`, `bmw`, `ibm`, `nvidia`, `spacex`, `spotify`, `uber`

## Phase 2: Apply the Design System

1. Read the full DESIGN.md from the collection:
   ```
   Read <skill-dir>/design-md/<brand>/DESIGN.md
   ```

2. Check if a DESIGN.md already exists in the current project directory. If it does, ask the user:
   - **Replace** -- Overwrite the existing DESIGN.md
   - **Keep both** -- Write as DESIGN-<brand>.md instead
   - **Cancel** -- Don't write anything

3. Write the contents to the project's `DESIGN.md` (or the alternate name). Add a source comment at the top:
   ```markdown
   <!-- Design system sourced from antidesign/<brand> -->
   <!-- Repository: https://github.com/anti-enterprises/antidesign -->
   <!-- Preview: design-md/<brand>/preview.html -->

   ```

   Do NOT modify the design system content itself -- copy it verbatim.

## Phase 3: Report

Print a summary:

```
=== Design system applied ===

Brand:   <brand>
Source:   antidesign/design-md/<brand>/DESIGN.md
Written:  <project-dir>/DESIGN.md
Preview:  <skill-dir>/design-md/<brand>/preview.html

The DESIGN.md contains 9 sections:
  1. Visual Theme & Atmosphere
  2. Color Palette & Roles
  3. Typography Rules
  4. Component Stylings
  5. Layout Principles
  6. Depth & Elevation
  7. Do's and Don'ts
  8. Responsive Behavior
  9. Agent Prompt Guide

To customize further, run /design-consultation.
To preview the design tokens, open the preview.html file in a browser.
```

## Important Rules

- **Do NOT modify the DESIGN.md content** -- these are curated design systems meant to be used as-is.
- **Always add the source comment header** so the origin is traceable.
- **Check for existing DESIGN.md** before writing -- never silently overwrite.
- This skill works standalone -- it does NOT require proj-init or any other skill.
