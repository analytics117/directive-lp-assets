# Enavate: Dynamics 365 Business Central (Unbounce)

Live page: https://d365.enavate.com/microsoft-dynamics-365-business-central/
Built from the Directive Unbounce starter kit and the approved Figma frame "Business Consulting BoFU", plus the review-round changes.

Everything lives in `enavate/business-central/` and every file is prefixed `bc-`, so nothing collides with other Enavate pages.
Assets are served from: `https://cdn.jsdelivr.net/gh/analytics117/directive-lp-assets@main/enavate/business-central`

## 1. GitHub
Replace the whole `enavate/business-central/` folder with this one (code files, `images/`, `fonts/`).
Files no longer used, safe to delete from GitHub: `images/bc-client-aaha.png`, `images/bc-cta-card.svg`, `images/bc-cta-card-v2.svg`.

## 2. Paste into Unbounce
| File | Where it goes |
|---|---|
| `bc-stylesheet.css` | Javascripts panel, placement **Head** (keep the `<style>` tags) |
| `bc-page.html` | The **Custom HTML** widget on the page canvas |
| `bc-javascript.html` | Javascripts panel, placement **Before Body End Tag** |
| `bc-confirmation-widget.html` | Custom HTML widget on the **form confirmation dialog** (dialog is fixed at 512px; widget about 460 x 280px desktop, about 270 x 300px mobile) |

## 3. The form
Native Unbounce form anywhere on the canvas; the script moves it into the hero and styles it.
Labels (become placeholders) and IDs, all **Required**:
First Name* `first_name` · Last Name* `last_name` · Email Address* `email` (type Email) · Phone Number* `phone_number` · Company Name* `company_name`.
Confirmation: "Show the form confirmation dialog". One-step form (set `TWO_STEP = true` in `bc-javascript.html` to split it).

## 4. CTAs
All "Get in Touch" buttons scroll to the hero form.

## What the page does
- Hero form sits 90px from the copy and never covers the woman's face; below 1100px the photo sits beside the headline (tablet) or above it (phone).
- Client logos scroll as a slow looping belt (pauses on hover).
- Proof cards fade in one by one and the numbers count up from 0 when scrolled into view.
- All animation turns off for visitors with reduced motion enabled.

## Open items before handing to the client
- **Team photo watermark:** the keyboard/desk photo in the Figma carries a faint Adobe Stock watermark. Get the licensed file and re-export `bc-team-photo.jpg` and `bc-team-photo-wide.jpg`.
- **Accent font:** the design uses Kepler Std (Adobe Fonts); Newsreader Italic stands in. If Enavate has an Adobe Fonts kit with Kepler, add it to the page and it takes over automatically.
- **Phone field:** no US flag / +1 prefix (Unbounce's native phone field has no country picker).
- **AAHA logo:** supplied file is 89 x 73px, so it may look slightly soft on high-resolution screens; a larger or SVG version would be sharper.
