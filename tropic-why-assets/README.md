# Tropic: "Why Tropic" interactive tabs (Unbounce)

**Design:** Figma "[Tropic] Design Feedback", page "BOFU Demo LP - Hi-Fi Mockup (11/5)", Why Tropic section (states 1–5)
**Interaction reference:** tropicapp.io homepage, "Why Tropic"

## Files

| File | Where it goes in Unbounce |
|------|---------------------------|
| `01-section-widget.html` | One **Custom HTML** widget in the Why Tropic section, under your existing headline/subheadline. Desktop: **1200 × 767**, left edge at the section's 120px margin (x = 120 on a 1440 page). |
| `02-section-styles.css` | Stylesheets → Add New → "Why Tropic tabs". Paste the whole file, `<style>` tags included. |
| `03-section-javascript.html` | Javascripts → Add New → "Why Tropic tabs", placement **Before Body End Tag**. |
| `tropic/images/` | GitHub: `analytics117/directive-lp-assets` → upload the `tropic` folder to the repo root so the files sit at `tropic/images/…` |

**Mobile view:** select the same widget, set it to the full content width (e.g. 280 wide) and **≈ 1030 tall**. The script reserves the height of the tallest card state, so the widget stays the same height whichever card is open (measured 1001–1028px at 260–320px widths). Push the section's bottom edge down so the widget fits.

## Image URLs

All five URLs in `01` share one base path:

`https://cdn.jsdelivr.net/gh/analytics117/directive-lp-assets@main/tropic/images/`

They work as soon as the folder is pushed to `main` (same jsDelivr pattern as the Enavate, Bevi and AudioHook pages). If you host them elsewhere, find-and-replace that one base path in `01`.

## Image → tab mapping

| Tab | File (in `tropic/images/`) | Source |
|-----|----------------------------|--------|
| 1. Day 1 impact | `why-tropic-01-day-1-impact.webp` | image1.png — price benchmark card, lime |
| 2. Proactive, always on delivery | `why-tropic-02-proactive-delivery.webp` | image2.png — renewal schedule, pink |
| 3. Flexible service model | `why-tropic-03-flexible-service.webp` | image3.png — printed benchmark report |
| 4. Accessible wherever you work | `why-tropic-04-accessible-anywhere.webp` | image4.png — integrations, lavender |
| 5. Unbiased from day one | `why-tropic-05-unbiased-day-one.webp` | image5.png — Supplier Code of Ethics badge |

Exported at 2× the 588 × 767 frame (1176 × 1534), WebP with transparency kept for the rounded corners. 3.0 MB of PNGs → 262 KB total.

## How it behaves

- Card 1 open on load. Clicking any card (or Enter/Space on it) opens it and closes the others.
- Image crossfades over 0.5s, the same timing as tropicapp.io. Text opens with a 0.3s height + fade.
- Arrow Up/Down, Home and End move between cards; buttons carry `aria-expanded` / `aria-controls`; visible focus ring.
- Image panel is a fixed 588:767 box, so loading or swapping images can't shift the layout.
- Mobile (≤ 600px, Unbounce's mobile view): image panel hides and each card shows its image under its text, the way tropicapp.io does it on phones. There's no mobile frame in Figma, so mobile type is scaled down from desktop: title 20px, text 16px, padding 24px.
- Reduced-motion users get instant switches.

### Autoplay (off by default)

tropicapp.io auto-advances every 7 seconds and shows a 4px purple progress bar on the open card. That bar isn't in the Figma design, so it's **off**. To turn it on, change `data-autoplay="0"` to `data-autoplay="7000"` on the first line of the markup in `01`. With it on, the bar appears, the timer restarts on every click, and it pauses on hover, on keyboard focus, and while the section is off-screen.

## Test after publishing

- Click all five cards on desktop: the right image shows for each, and nothing below the section moves.
- Mobile preview: each card opens with its image; the section below doesn't jump.
- Tab through with the keyboard; arrow keys move between cards.
