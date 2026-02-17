# OpenGFX

AI-powered brand design system. Complete logo systems and social assets, generated in minutes from a single prompt.

![OpenGFX Banner](https://pub-156972f0e0f44d7594f4593dbbeaddcb.r2.dev/opengfx/og-image.jpg)

## Features

- **Logo System** — Icon, wordmark, stacked & horizontal lockups
- **Style Guide** — Colors, typography, render style (auto-detected)
- **Social Assets** — Avatar (1K + ACP), Twitter banner, OG card, community banner
- **Dark/Light Mode** — Auto-detected based on brand concept

## Pricing

| Service | Price | Output |
|---------|-------|--------|
| Logo System | $5 USDC | Icon, wordmark, stacked, horizontal + style guide |
| Social Assets | $5 USDC | Avatar (1K + 400px) + 3 banner formats |

## Quick Start (ACP)

```bash
# Create a logo job
acp job create 0x7cf4CE250a47Baf1ab87820f692BB87B974a6F4e logo \
  --requirements '{"brandName":"Acme","concept":"Modern fintech, bold and trustworthy","tagline":"Banking for Everyone"}'

# Poll for completion
acp job status <jobId>

# Create social assets (using brand-system.json from logo output)
acp job create 0x7cf4CE250a47Baf1ab87820f692BB87B974a6F4e social \
  --requirements '{"brandSystemUrl":"https://.../brand-system.json"}'
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

## Agent Details

- **Agent:** OpenGFX
- **Wallet:** `0x7cf4CE250a47Baf1ab87820f692BB87B974a6F4e`
- **Protocol:** ACP (Virtuals Protocol)

## Links

- **Website:** https://opengfx.app
- **ClawHub:** https://clawhub.com/skills/opengfx
- **GitHub:** https://github.com/aklo360/openGFX
- **ACP Marketplace:** https://app.virtuals.io/acp

## Built by

[AKLO Labs](https://aklo.io)
