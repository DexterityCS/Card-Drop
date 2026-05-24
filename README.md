# 🎴 Card Drop

A Twitch channel points-triggered collectible card drop overlay. When a viewer redeems the reward, a randomized card flips over in OBS revealing a creature with rarity, stats, moves, type, and flavor text — complete with holographic effects on rare pulls.

**Live:** [`dexteritycs.github.io/Card-Drop/`](https://dexteritycs.github.io/Card-Drop/)

---

## Features

- 5 rarity tiers: Common, Uncommon, Rare, Epic, Legendary — each with distinct colors and weighted drop rates
- Holographic foil shimmer animation on Rare+ cards
- Per-card stats: HP, type, moves with energy costs, weakness, and flavor text
- Pull history sidebar with rarity breakdown and best streak tracking
- Connects to Twitch EventSub WebSocket — triggers live on channel point redemptions
- Self-serve setup flow — other streamers can configure it for their own channel
- Credentials persist in URL hash for SLOBS browser source compatibility

---

## Rarity Rates

| Rarity | Rate | Color |
|--------|------|-------|
| Common | 45% | Gray |
| Uncommon | 28% | Green |
| Rare | 17% | Blue |
| Epic | 8% | Purple |
| Legendary | 2% | Gold |

---

## Setup

### 1. Create a Twitch App

1. Go to [dev.twitch.tv/console](https://dev.twitch.tv/console)
2. Register a new application
3. Set OAuth Redirect URL to: `https://dexteritycs.github.io/Card-Drop/`
4. Copy your **Client ID**

### 2. Configure the Widget

1. Open `https://dexteritycs.github.io/Card-Drop/` in a browser
2. Click the **⚙ Setup** button
3. Enter your **Client ID**, **channel name**, and the exact **reward name** that triggers a drop
4. Click **Connect with Twitch** and authorize
5. Click **Save** — the overlay is now live and listening

### 3. Add to OBS / Streamlabs

1. Add a **Browser Source**
2. Paste the configured URL (with hash token) from the setup flow
3. Recommended size: `700` wide × `500` tall (adjust to your layout)
4. Check **Refresh browser when scene becomes active**

### 4. Create the Channel Points Reward

1. Twitch Dashboard → **Viewer Rewards → Channel Points → Manage Rewards**
2. Create a reward matching the name you set in the widget config (e.g. `Card Drop`)
3. Set your point cost and enable it

---

## Tech

- Vanilla HTML/CSS/JS — zero server, zero dependencies
- Twitch EventSub WebSocket for real-time redemption events
- Twitch OAuth Implicit Grant (token in URL hash for SLOBS)
- Canvas API for per-card generative art on the card face
