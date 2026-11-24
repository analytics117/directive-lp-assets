# Enavate: Dynamics 365 Consulting, Variant B (A/B test)

**Suggested variant name in Unbounce:** `B - BC Pathways (Design Review V2)`
**Page:** https://d365.enavate.com/enavate-dynamics-365-consulting/ (the page that holds the stats)
**Design:** Figma "[Enavate] Design Review", frame "Dynamics 365 Consulting BoFU – Test Variant V2"

## Files

| File | Where it goes in Unbounce |
|------|---------------------------|
| `01-page-widget.html` | One Custom HTML widget, full width (1440), no height |
| `02-stylesheet.css` | Stylesheets → Add New → "Page styles" (paste the whole file, `<style>` tags included) |
| `03-javascript.html` | Javascripts → "Page scripts", Before Body End Tag |
| `05-favicon-head.html` | Javascripts → "Favicon", Head |
| `images/` | GitHub: `analytics117/directive-lp-assets` → `enavate/d365-consulting-b/images/` |

Keep the **HubSpot Tracking Script** (Head, `js.hs-scripts.com/3002663.js`) and the **Clarity** head script on the variant.

## What's in it

- Same system as the Consulting page (Variant A): same fonts, text sizes, buttons and HubSpot form styling.
- Content is capped at 1200px; backgrounds and decorative pieces run full width.
- Form: HubSpot developer embed, **NEW BOFU - PPC - Dynamics 365** (`406fb81e-…`), so `source_campaign`
  and the thank-you redirect are the same as Variant A.
- The form's button reads "Get a Personalized Consultation" on this page only. HubSpot's form says
  "Get in Touch"; the stylesheet swaps the label visually, so the shared form isn't changed.
- `03` also tags Clarity sessions with `lp_variant` = the Unbounce variant ID, so heatmaps and
  recordings can be filtered A vs B.
- Images: 17 new files with the `dcb-` prefix (hero, three shaped photos, icons, pathways deco).
  Client logos, testimonial logos, footer logo and the gradient bars are reused from
  `enavate/d365-consulting/images/`.

## Unbounce A/B setup

1. Open the Consulting page → **Add Variant → Create new** (blank) → name it as above.
2. Add the widget, stylesheet and scripts from the table. Copy page settings from Variant A
   ("Scale the page size automatically", title, description, noindex).
3. Variant A: add the Clarity tag to its Page scripts (Before Body End):
   ```html
   <script>
     /* Tag Clarity sessions with the Unbounce variant so heatmaps can be split A vs B */
     (function go(n){ if (window.clarity && window.ub && ub.page) { clarity('set','lp_variant', ub.page.variantId); } else if (n < 20) { setTimeout(function(){ go(n+1); }, 500); } })(0);
   </script>
   ```
4. **Goals:** clear the conversion goals on both variants (no link counts as a conversion).
5. **A/B Test:** set A and B to 50/50.
6. Save → Republish.

## Conversions (waits for Brittany)

`../enavate-hubspot-forms/unbounce-conversion-script-for-thank-you-page.html` goes in the footer of
https://www.enavate.com/talk-with-an-expert-thank-you-conversion-contact-us. Once it's live, Unbounce
counts a conversion for whichever variant the visitor saw (72-hour cookie).

## Test after publishing

- `/enavate-dynamics-365-consulting/e.html` shows Variant B (Unbounce gives it the next letter; Variant A is `d`).
- One real test submission: lands on the Enavate thank-you page; HubSpot contact has the D365 `source_campaign`.
- Clarity → Filters → Custom tags → `lp_variant` shows both letters after a few sessions.
