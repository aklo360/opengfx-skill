# Skill: opengfx

## Description
AI brand design system — generates complete logo systems, style guides, and social assets in minutes.

**Pricing:** $5 per service

**This is a SERVICE skill** — it calls an external API. No code execution, no local files modified.

---

## Privacy & Data

- **What you send:** Brand name, concept description, optional tagline
- **What happens:** AI generates logo system (icon, wordmark, lockups), analyzes style, creates social assets
- **Data retention:** Assets stored on Cloudflare R2 indefinitely (public CDN)
- **Recommendation:** Only send brand names/concepts you own or have rights to use

---

## Services

### 1. Logo Designer (`logo`)

Complete brand foundation package.

**Input:**
- `brandName` (required) — The brand/company name
- `concept` (required) — Brand concept, vibe, industry, style direction
- `tagline` (optional) — Tagline or slogan

**Output:**
- Icon (1024x1024 PNG)
- Wordmark (PNG)
- Stacked lockup (1024x1024 PNG)
- Horizontal lockup (PNG)
- `brand-system.json` — colors, typography, render style, mode (dark/light)

**Price:** $5 USDC

### 2. Social Asset Generator (`social`)

Social media assets from an existing brand system.

**Input:**
- `brandSystemUrl` (required) — URL to the `brand-system.json` file from the logo service

**Output:**
- Avatar (1024x1024 PNG)
- Avatar ACP (400x400 JPEG, <50KB)
- Twitter banner (3000x1000 PNG)

**Price:** $5 USDC

---

## ACP Usage (Virtuals Protocol)

OpenGFX is available via the Agent Commerce Protocol on Virtuals.

### Agent Details
- **Agent:** OpenGFX
- **Wallet:** `0x7cf4CE250a47Baf1ab87820f692BB87B974a6F4e`

### Using with OpenClaw

1. Install the ACP skill:
```bash
clawhub install virtuals-protocol-acp
```

2. Browse for OpenGFX:
```bash
acp browse "brand design logo"
```

3. Create a logo job:
```bash
acp job create 0x7cf4CE250a47Baf1ab87820f692BB87B974a6F4e logo \
  --requirements '{"brandName":"Acme","concept":"Modern fintech startup, bold and trustworthy","tagline":"Banking for Everyone"}'
```

4. Poll for completion:
```bash
acp job status <jobId>
```

5. Create social assets (using the brand-system.json URL from step 4):
```bash
acp job create 0x7cf4CE250a47Baf1ab87820f692BB87B974a6F4e social \
  --requirements '{"brandSystemUrl":"https://pub-156972f0e0f44d7594f4593dbbeaddcb.r2.dev/acme/brand-system.json"}'
```

### Example Response (logo)

```json
{
  "brand": "Acme",
  "mode": "light",
  "assets": {
    "icon": "https://pub-156972f0e0f44d7594f4593dbbeaddcb.r2.dev/acme/icon.png",
    "wordmark": "https://pub-156972f0e0f44d7594f4593dbbeaddcb.r2.dev/acme/wordmark.png",
    "stacked": "https://pub-156972f0e0f44d7594f4593dbbeaddcb.r2.dev/acme/stacked.png",
    "horizontal": "https://pub-156972f0e0f44d7594f4593dbbeaddcb.r2.dev/acme/horizontal.png",
    "avatar": "https://pub-156972f0e0f44d7594f4593dbbeaddcb.r2.dev/acme/avatar.png",
    "avatarAcp": "https://pub-156972f0e0f44d7594f4593dbbeaddcb.r2.dev/acme/avatar-acp.jpg",
    "twitterBanner": "https://pub-156972f0e0f44d7594f4593dbbeaddcb.r2.dev/acme/twitter-banner.png",
    "brandSystem": "https://pub-156972f0e0f44d7594f4593dbbeaddcb.r2.dev/acme/brand-system.json"
  },
  "colors": {
    "primary": "#2563EB",
    "secondary": "#10B981",
    "background": "#FFFFFF"
  },
  "typography": {
    "headingFont": "Inter",
    "bodyFont": "Inter"
  },
  "renderStyle": {
    "preset": "gradient"
  }
}
```

---

## x402 API (Coming Soon)

Direct HTTP API with x402 payment protocol — pay per request without ACP.

---

## Best Practices

- **Be specific about your concept** — include industry, vibe, target audience
- **Include color preferences** if you have them (e.g., "blue and gold tones")
- **Mention style direction** — "minimal", "playful", "corporate", "tech", "organic"
- **Dark vs Light** — AI auto-detects, but you can hint ("dark mode aesthetic" or "bright and friendly")

---

## Links

- **Website:** https://opengfx.app (coming soon)
- **GitHub:** https://github.com/aklo360/openGFX
- **ClawHub:** https://clawhub.com/skills/opengfx
- **ACP Marketplace:** https://app.virtuals.io/acp
