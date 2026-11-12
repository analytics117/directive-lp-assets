# Audiohook vs. Spotify Ads: Unbounce build

Page: **try.audiohook.com/vs-spotify-ads**
Built from the approved Figma (Competitor BoFU Spotify Ads | LP) and the live /competitor page's code, so type sizes, spacing and motion match it.

## 1. Upload to GitHub

Drag this whole folder into `analytics117/directive-lp-assets/audiohook/` so you end up with:

```
audiohook/vs-spotify-ads/
  images/   52 files, all spt-*
  fonts/    5 files, all spt-*
  code/     4 files (paste into Unbounce, they don't need to live in GitHub)
```

Every file and every CSS class is prefixed `spt-`, so nothing clashes with `competitor/` (cmp-) or `podcast-ads-cost/` (pac-).
Check the folder name has no trailing space (it broke every link once before).

Assets load from:
`https://cdn.jsdelivr.net/gh/analytics117/directive-lp-assets@main/audiohook/vs-spotify-ads/`

Test one after upload, for example `.../images/spt-logo-light.svg`.

## 2. Unbounce

1. Page width **1440**. URL slug `vs-spotify-ads`.
2. **Javascripts panel**
   - `spt-02-stylesheet.css` → placement **Head** (keep the `<style>` tags)
   - `spt-03-javascript.html` → placement **Before Body End Tag**
3. **Custom HTML widget** in the first section → paste `spt-01-page-widget.html`.
4. **Form** (one step, native Unbounce form, anywhere on the canvas; the script moves it into the card):
   | Label | Field ID | Type |
   |---|---|---|
   | First Name | `first_name` | Single line, required |
   | Last Name | `last_name` | Single line, required |
   | Work Email | `email` or `work_email` | Email, required |
   | Company Name | `company_name` | Single line, required |

   Button text: Talk to an expert. **No checkbox**: the design uses the "By submitting, you agree…" line, which the script adds above the button. (If a required checkbox with ID `terms_agreement` is added, the script turns its label into the Terms/Privacy line instead.)
   Confirmation: Show form confirmation dialog. Desktop 512 × 375, mobile 240 × 310.
5. **Confirmation dialog** → Custom HTML widget at X 0, Y 0, same size as the dialog, on desktop and mobile → paste `spt-04-confirmation-dialog-widget.html`. Delete the dialog's default text.
6. Mobile view: nothing to arrange; the page stacks itself below 900px (form above the IPVanish quote, hero covers and CTA phone hidden, comparison table scrolls sideways).

## 3. Settings you might change (top of spt-03-javascript)

`TESTIMONIAL_MS` (5000), `COUNT_MS` (1200), `TERMS_URL`, `PRIVACY_URL`, `BUTTON_LABEL`.

## 4. Changes from the /competitor code

- Copy swapped to Spotify Ads throughout; table is 5 rows and 1040px wide (per design).
- Hero H1 on three lines; hero bullets align with the billing cards.
- Consent line sits above the button, left aligned (design), instead of under it.
- Form fields get 24px between them (Unbounce nests fields one level down, so the form's gap never reached them on /competitor).
- Work Email accepts `email` or `work_email`. /competitor's form uses `work_email`, which its script didn't recognise, so that field missed the autocomplete hint there.
- "Millions" stat counts 1 → 1,000,000 then rolls into the word.
- Thin rule left of each stat (design).

## 5. Open items before launch

- Stats 68% / 4.2x / 92% / Millions are unsourced; the design drops the "Based on Audiohook client data" note.
- Spotify facts (auction CPM, $250 start, Music and Podcasts only, managed for larger budgets): re-check against Spotify Advertising before launch.
- Footer disclaimer in the Figma said "AudioGo is a product of AdsWizz Inc."; replaced with a Spotify trademark line. Confirm wording with the client.
- Widget numbers match the design and /competitor ($166.24 +$322.55, $215.12 +$158.55); the deltas don't add up mathematically.
- Good Ranchers and Furnée quotes are still paraphrased; cover-art rights unconfirmed.
- Run the SOP final check on the live page (submit a test lead, check the dialog, check mobile).
