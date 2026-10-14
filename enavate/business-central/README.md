# Enavate: Dynamics 365 Business Central (Unbounce)

Page URL: https://d365.enavate.com/enavate-dynamics-365-business-central/
Built from the Directive Unbounce starter kit and the approved Figma frame "Business Consulting BoFU".

Everything lives in `enavate/business-central/` and every file is prefixed `bc-`, so nothing collides with what's already in the `enavate` folder.

## 1. Upload to GitHub
Drop the whole `business-central` folder into the repo's `enavate/` folder.

## 2. Set the asset URL (one find-and-replace)
The code points at:

    https://cdn.jsdelivr.net/gh/GITHUB-OWNER/GITHUB-REPO@main/enavate/business-central

Replace `GITHUB-OWNER/GITHUB-REPO` with the real repo in `bc-page.html`, `bc-stylesheet.css` and `bc-confirmation-widget.html`.
If you serve assets some other way, swap the whole base URL instead.

## 3. Paste into Unbounce
| File | Where it goes |
|---|---|
| `bc-stylesheet.css` | Javascripts panel, placement **Head** (keep the `<style>` tags) |
| `bc-page.html` | One **Custom HTML** widget on the page canvas |
| `bc-javascript.html` | Javascripts panel, placement **Before Body End Tag** |
| `bc-confirmation-widget.html` | Custom HTML widget on the **form confirmation dialog** canvas (at least 520px wide) |

## 4. The form
Add a native Unbounce form anywhere on the canvas. The script moves it into the hero and styles it to the design.
Fields, in this order, with these labels (labels become the placeholders):

- First Name*
- Last Name*
- Email Address*
- Phone Number*
- Company Name*

Set the form's confirmation to "Show the form confirmation dialog".
It is a one-step form, matching the design. To split it into two steps, set `TWO_STEP = true` in `bc-javascript.html`.

## 5. CTAs
Both "Get in Touch" buttons scroll to the hero form. No external URL is needed.

## Notes
- Accent font: the design uses Kepler Std Italic (Adobe Fonts), which can't be self-hosted. Newsreader Italic (open licence) stands in. If Enavate has an Adobe Fonts kit with Kepler, add it to the page and it takes over automatically.
- Phone field: the design shows a US flag and "+1" prefix. Unbounce's native phone field has no country picker, so it's a plain field.
- There is no mobile frame in the design, so mobile layouts follow the desktop system (grids collapse 4>2>1 and 3>2>1, type steps down).
