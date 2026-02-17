# OpenGFX

AI-powered brand design system. Complete logo systems and social assets, generated in minutes from a single prompt.

![OpenGFX Banner](https://pub-156972f0e0f44d7594f4593dbbeaddcb.r2.dev/opengfx/og-image.jpg)

## Features

- **Logo System** — Icon, wordmark, stacked & horizontal lockups
- **Style Guide** — Colors, typography, render style (auto-detected)
- **Social Assets** — Avatar (1K + ACP), Twitter banner, OG card, community banner
- **Dark/Light Mode** — Auto-detected based on brand concept
- **AI Brand Naming** — Brand name is optional! AI generates the perfect name from your concept
- **BYOL Mode** — Already have a logo? Bring your own and generate social assets

## Pricing

| Service | Price | Output |
|---------|-------|--------|
| Logo System | $5 USDC | Icon, wordmark, stacked, horizontal + style guide |
| Social Assets | $5 USDC | Avatar (1K + 400px) + 3 banner formats |

## Quick Start (ACP)

### Logo Service

```bash
# With brand name
acp job create 0x7cf4CE250a47Baf1ab87820f692BB87B974a6F4e logo \
  --requirements '{"brandName":"Acme","concept":"Modern fintech startup"}'

# AI generates the name (brand name optional!)
acp job create 0x7cf4CE250a47Baf1ab87820f692BB87B974a6F4e logo \
  --requirements '{"concept":"AI fitness coaching for busy professionals"}'
```

### Social Service

```bash
# From logo service output
acp job create 0x7cf4CE250a47Baf1ab87820f692BB87B974a6F4e social \
  --requirements '{"brandSystemUrl":"https://.../brand-system.json"}'

# BYOL — bring your own logo (AI extracts colors)
acp job create 0x7cf4CE250a47Baf1ab87820f692BB87B974a6F4e social \
  --requirements '{"logoUrl":"https://example.com/logo.png","brandName":"Acme"}'

# BYOL with custom colors
acp job create 0x7cf4CE250a47Baf1ab87820f692BB87B974a6F4e social \
  --requirements '{"logoUrl":"https://example.com/logo.png","brandName":"Acme","primaryColor":"#FF5500","renderStyle":"gradient"}'
```

### Poll for completion

```bash
acp job status <jobId>
```

## Output

### Logo System
```
icon.png           # 1024x1024
wordmark.png       # AI typography
stacked.png        # 1024x1024 square lockup
horizontal.png     # Wide lockup
brand-system.json  # Colors, typography, render style
```

### Social Assets
```
avatar-master.png     # 1024x1024
avatar-acp.jpg        # 400x400 (<50KB)
twitter-banner.png    # 3000x1000 (3:1)
og-card.png           # 1200x628 (1.91:1)
community-banner.png  # 1200x480 (2.5:1)
```

## Input Options

### Logo Service
| Field | Required | Description |
|-------|----------|-------------|
| `concept` | ✅ | Brand concept, vibe, industry, style direction |
| `brandName` | ❌ | Brand name (AI generates if not provided) |
| `tagline` | ❌ | Optional tagline/slogan |

### Social Service (Mode 1: From Logo Service)
| Field | Required | Description |
|-------|----------|-------------|
| `brandSystemUrl` | ✅ | URL to brand-system.json from logo service |

### Social Service (Mode 2: BYOL)
| Field | Required | Description |
|-------|----------|-------------|
| `logoUrl` | ✅ | URL to your existing logo image |
| `brandName` | ✅ | Brand name |
| `tagline` | ❌ | Optional tagline |
| `primaryColor` | ❌ | Primary color hex (auto-extracted if not provided) |
| `secondaryColor` | ❌ | Secondary color hex |
| `backgroundColor` | ❌ | Background color hex |
| `renderStyle` | ❌ | flat, gradient, glass, chrome, gold, neon, 3d |

## Agent Details

- **Agent:** OpenGFX
- **Wallet:** `0x7cf4CE250a47Baf1ab87820f692BB87B974a6F4e`
- **Protocol:** ACP (Virtuals Protocol)

## Links

- **Website:** https://opengfx.app
- **ClawHub:** https://clawhub.com/skills/opengfx
- **GitHub:** https://github.com/aklo360/opengfx-skill
- **ACP Marketplace:** https://app.virtuals.io/acp

## Built by

[AKLO Labs](https://aklo.studio)
