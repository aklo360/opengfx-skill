---
name: opengfx
description: AI brand design system — logo systems, style guides, and social assets in minutes.
version: 1.2.1
homepage: https://opengfx.app
source: https://github.com/aklo360/opengfx-skill
author: AKLO Labs <aklo@aklo.studio>
---

# Skill: opengfx

## Description
AI brand design system — generates complete logo systems, style guides, and social assets in minutes. **Brand name is optional** — if you don't have one, AI will generate the perfect name from your concept!

**Pricing:** $5 per service (Logo or Social)

**This is a SERVICE skill** — it documents how to use an external paid API via ACP. No code execution, no local files modified, no credentials requested.

---

## Requirements

This skill documents the OpenGFX API accessible via ACP (Agent Commerce Protocol).

**To use this service, you need:**
- An ACP-compatible agent/wallet (e.g., OpenClaw with ACP skill installed)
- USDC on Base chain for payments ($5 per service)

**This skill does NOT:**
- Install any binaries
- Request or store private keys
- Execute any code on your system

The `acp` commands shown below are examples — your agent framework handles the actual ACP integration.

---

## Privacy & Data

- **What you send:** Concept description (required), brand name (optional), tagline (optional)
- **What happens:** The service generates logo system (icon, wordmark, lockups), analyzes style, creates social assets
- **Data retention:** Assets stored on Cloudflare R2 for 30 days, then deleted. Contact aklo@aklo.studio for early deletion.
- **Recommendation:** Only submit brand names/concepts you own or have rights to use. Do not submit confidential or trademarked content.

---

## Payment Flow

This skill uses **ACP (Agent Commerce Protocol)** on Virtuals Protocol.

### How It Works

1. **Create Job** → Submit a job request to OpenGFX agent
2. **Pay** → ACP handles payment (USDC on Base chain)
3. **Poll** → Check job status until complete
4. **Receive** → Get asset URLs in the job deliverable

### Who Signs Payments?

**Your agent's wallet signs payments, not this skill.**

This skill only documents the API. Payment signing is handled by your agent's ACP integration (e.g., OpenClaw's built-in wallet, or your own wallet configuration).

**No private keys are needed or requested by this skill.**

---

## API Reference

**Agent Wallet:** `0x7cf4CE250a47Baf1ab87820f692BB87B974a6F4e`

### Create Logo Job (with name)

```bash
acp job create 0x7cf4CE250a47Baf1ab87820f692BB87B974a6F4e logo \
  --requirements '{"brandName":"Acme","concept":"Modern fintech startup, bold and trustworthy","tagline":"Banking for Everyone"}'
```

### Create Logo Job (AI names the brand)

```bash
# Just provide concept — AI will generate the perfect brand name!
acp job create 0x7cf4CE250a47Baf1ab87820f692BB87B974a6F4e logo \
  --requirements '{"concept":"AI-powered fitness coaching app for busy professionals"}'
```

**Response:**
```json
{
  "jobId": "abc-123",
  "status": "processing"
}
```

### Poll Job Status

```bash
acp job status <jobId>
```

**Response (completed):**
```json
{
  "brand": "Acme",
  "mode": "light",
  "assets": {
    "icon": "https://pub-156972f0e0f44d7594f4593dbbeaddcb.r2.dev/acme/icon.png",
    "wordmark": "https://pub-156972f0e0f44d7594f4593dbbeaddcb.r2.dev/acme/wordmark.png",
    "stacked": "https://pub-156972f0e0f44d7594f4593dbbeaddcb.r2.dev/acme/stacked.png",
    "horizontal": "https://pub-156972f0e0f44d7594f4593dbbeaddcb.r2.dev/acme/horizontal.png",
    "brandSystem": "https://pub-156972f0e0f44d7594f4593dbbeaddcb.r2.dev/acme/brand-system.json"
  }
}
```

### Create Social Assets (from Logo Service)

```bash
acp job create 0x7cf4CE250a47Baf1ab87820f692BB87B974a6F4e social \
  --requirements '{"brandSystemUrl":"https://pub-156972f0e0f44d7594f4593dbbeaddcb.r2.dev/acme/brand-system.json"}'
```

### Create Social Assets (BYOL — Bring Your Own Logo)

```bash
# AI extracts colors from your logo
acp job create 0x7cf4CE250a47Baf1ab87820f692BB87B974a6F4e social \
  --requirements '{"logoUrl":"https://example.com/my-logo.png","brandName":"My Brand"}'

# Or specify colors manually
acp job create 0x7cf4CE250a47Baf1ab87820f692BB87B974a6F4e social \
  --requirements '{"logoUrl":"https://example.com/my-logo.png","brandName":"My Brand","primaryColor":"#FF5500","secondaryColor":"#333333","renderStyle":"gradient"}'
```

**Response (completed):**
```json
{
  "brand": "Acme",
  "mode": "byol",
  "assets": {
    "avatar": "https://pub-156972f0e0f44d7594f4593dbbeaddcb.r2.dev/acme/avatar.png",
    "avatarAcp": "https://pub-156972f0e0f44d7594f4593dbbeaddcb.r2.dev/acme/avatar-acp.jpg",
    "twitterBanner": "https://pub-156972f0e0f44d7594f4593dbbeaddcb.r2.dev/acme/twitter-banner.png",
    "ogCard": "https://pub-156972f0e0f44d7594f4593dbbeaddcb.r2.dev/acme/og-card.png",
    "communityBanner": "https://pub-156972f0e0f44d7594f4593dbbeaddcb.r2.dev/acme/community-banner.png"
  }
}
```

---

## Pricing

| Service | Price | Output |
|---------|-------|--------|
| Logo System | $5 | Icon, wordmark, stacked, horizontal + brand-system.json |
| Social Assets | $5 | Avatar (1K + ACP) + Twitter banner + OG card + Community banner |

---

## Vendor Information

- **Service:** OpenGFX
- **Provider:** AKLO Labs
- **Website:** https://opengfx.app
- **GitHub:** https://github.com/aklo360/opengfx-skill
- **Support:** aklo@aklo.studio
- **Agent Wallet:** `0x7cf4CE250a47Baf1ab87820f692BB87B974a6F4e`
- **ACP Marketplace:** https://app.virtuals.io/acp

---

## Best Practices

- **Be specific about your concept** — include industry, vibe, target audience
- **Include color preferences** if you have them (e.g., "blue and gold tones")
- **Mention style direction** — "minimal", "playful", "corporate", "tech", "organic"
- **Dark vs Light** — AI auto-detects, but you can hint ("dark mode aesthetic" or "bright and friendly")
- **Test first** — Use a low-value test job to verify behavior before production use
