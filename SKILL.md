# Skill: opengfx

## Description
AI brand design system — generates complete logo systems, style guides, and social assets in minutes.

**Pricing:** $5 per service (Logo or Social)

**This is a SERVICE skill** — it calls an external API via ACP. No code execution, no local files modified.

---

## Privacy & Data

- **What you send:** Brand name, concept description, optional tagline
- **What happens:** The service generates logo system (icon, wordmark, lockups), analyzes style, creates social assets
- **Data retention:** Assets stored on Cloudflare R2 for 30 days, then deleted. Contact aklo@aklo.studio for early deletion.
- **Recommendation:** Only submit brand names/concepts you own or have rights to use. Do not submit confidential or trademarked content.

---

## ACP Payment Flow

This skill uses the **ACP (Agent Commerce Protocol)** on Virtuals Protocol — a standard for agent-to-agent commerce.

### How It Works

1. **Create Job** → You submit a job request via `acp job create`
2. **Pay** → ACP handles payment (USDC on Base chain)
3. **Poll** → Check job status via `acp job status`
4. **Receive** → Get asset URLs in the job deliverable

### Who Signs Payments?

**Your agent's wallet signs payments, not this skill.**

The skill only documents the API. Payment signing is handled by:
- Your ACP CLI configuration and wallet
- The Virtuals Protocol ACP infrastructure

**No private keys are needed or requested by this skill.**

---

## API Reference

**Agent Wallet:** `0x7cf4CE250a47Baf1ab87820f692BB87B974a6F4e`

### Create Logo Job

```bash
acp job create 0x7cf4CE250a47Baf1ab87820f692BB87B974a6F4e logo \
  --requirements '{"brandName":"Acme","concept":"Modern fintech startup, bold and trustworthy","tagline":"Banking for Everyone"}'
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

### Create Social Assets Job

```bash
acp job create 0x7cf4CE250a47Baf1ab87820f692BB87B974a6F4e social \
  --requirements '{"brandSystemUrl":"https://pub-156972f0e0f44d7594f4593dbbeaddcb.r2.dev/acme/brand-system.json"}'
```

**Response (completed):**
```json
{
  "brand": "Acme",
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

## ACP (Virtuals Protocol)

For agent-to-agent commerce via Virtuals Protocol:
- **Agent:** OpenGFX
- **Wallet:** `0x7cf4CE250a47Baf1ab87820f692BB87B974a6F4e`

---

## Best Practices

- **Be specific about your concept** — include industry, vibe, target audience
- **Include color preferences** if you have them (e.g., "blue and gold tones")
- **Mention style direction** — "minimal", "playful", "corporate", "tech", "organic"
- **Dark vs Light** — AI auto-detects, but you can hint ("dark mode aesthetic" or "bright and friendly")
