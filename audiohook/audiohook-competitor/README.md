# Audiohook competitor page (try.audiohook.com/competitor)

Audiohook vs. AudioGo, built from the approved design (audiioook.svg), the vs-audiogo hi-fi package and the Unbounce starter kit.

## 1. GitHub

Drop the `audiohook/competitor/` folder into `analytics117/directive-lp-assets` so it lands at `audiohook/competitor/` next to the existing page folders. Nothing already in the audiohook folder is touched.

- Every image and font is prefixed `cmp-` (podcast-ads-cost uses `pac-`, vs-audiogo uses `vag-`), and every CSS class is `cmp-`.
- Folder names: `competitor`, `images`, `fonts`, `code`. Check there is no trailing space in the folder name (it 404'd every link once before).
- Files are served from `https://cdn.jsdelivr.net/gh/analytics117/directive-lp-assets@main/audiohook/competitor/` and the code already points there. jsDelivr can cache `@main` for hours, so if an image looks stale, purge it at `https://purge.jsdelivr.net/gh/analytics117/directive-lp-assets@main/audiohook/competitor/images/<file>`.

## 2. Unbounce

1. New page, width 1440, one full-width section. Drop in one Custom HTML widget and paste `cmp-01-page-widget.html`.
2. Javascripts panel, placement **Head**: paste `cmp-02-stylesheet.css` (keep the `<style>` tags).
3. Javascripts panel, placement **Before Body End Tag**: paste `cmp-03-javascript.html` (keep the `<script>` tags).
4. Form: add Unbounce's native form in the same section, anywhere (the script moves it into the card). One step, with these fields, **all required**:

| Label | Field ID | Notes |
|---|---|---|
| First Name* | `first_name` | required |
| Last Name* | `last_name` | required |
| Work Email* | `email` | required, email validation |
| Company Name* | `company_name` | required |
| (optional) checkbox | `terms_agreement` | required. The design shows it; the script rewrites its label into the Terms and Privacy links |

   Set the button to "Talk to an expert" (the script also sets it). Without the checkbox, a consent note sits under the button instead. The script adds the asterisks and `required` itself, so an empty submit is blocked even if one is missed in the builder.
5. Confirmation dialog: put a Custom HTML widget on the dialog canvas, paste `cmp-04-confirmation-dialog-widget.html`, size it 560 x 360 or larger. Section 8 of the stylesheet handles the dialog frame (ink, 16px corners, white close X that turns magenta).
6. Page title: "Audiohook vs. AudioGo | Pay only for conversions". Every "Talk to an expert" button scrolls to the form and focuses the first field.

## 3. Motion

Both images you asked about are flat files in the design: the hero background is a single 1440 x 880 PNG, and the final-CTA phone is a single JPG. Neither is animated as a file, so:

- **Hero background:** the same canvas drift used on the podcast-ads-cost page. 28 podcast covers on three depth layers (one blurred, two sharp at different speeds) travel bottom-left to top-right and wrap seamlessly, each with a small bob. Masked to fade out before the headline. Pauses when off screen or the tab is hidden, holds a still frame for reduced-motion, desktop only (hidden at 900px and below). Speed and density are `speed` and `scale` in `initCovers` in the JS file.
- **Footer / final CTA image:** the phone drifts gently while the three widget cards (Radio, Podcast, Portfolio) float on staggered loops in front of it. The magenta edge glow around the section pulses slowly.
- Also animated: logo belt, comparison rows (staggered reveal), stat count-ups, step cards, testimonial auto-advance every 5s (`TESTIMONIAL_MS` in the JS).
- All loops pause when their section is off screen, and everything holds still under reduced motion.

`motion-preview.mp4` is a short capture of the build running.

## 4. Where this differs from the SVG (please confirm)

- **Widget numbers.** The SVG still shows the old baked values ($166.24 +$322.55, $367.82, dates 02/02/25). The build uses the corrected set from the vs-audiogo package (Radio $1,862.40 +$261.02, Podcast $2,415.12 +$268.35, 02/02/26 until 06/02/26) because the old maths doesn't add up. To use the SVG values instead, edit the text in `cmp-01-page-widget.html`.
- **Hairline above testimonials.** The SVG has a 1px grey full-width line at the top of the testimonial section. It is built in (`.cmp-proof` border-top); delete that border if it was a stray Figma stroke.
- **Mobile.** The form sits directly after the three bullets, above the IPVanish quote. The cover canvas and the CTA phone are hidden below 900px, as in the earlier build. The comparison table scrolls sideways inside its box.
- **Thank-you copy.** Heading is "Thanks, we've got it."; the line under it ("A member of the Audiohook team will be in touch shortly.") is placeholder wording.

## 5. Open items carried over

- Stats 68% / 4.2x / 92% are unsourced ("Based on Audiohook client data" is a placeholder).
- Good Ranchers and Furnée Brands quotes are paraphrased. Swap in approved wording.
- Hero bullet 2 says "upfront" twice (Figma copy, kept).
- "Self-serve or fully managed" (table) vs "a managed performance stack" (What changes intro): client to confirm.
- AudioGo facts are from audiogo.com as of Oct 2026; re-check before launch.
- Confirm usage rights for the podcast cover art. The 28 `cmp-cover-*.jpg` files are the same covers used on podcast-ads-cost (about 700KB total).

## 6. Checked

Built into a mock Unbounce page (fixed-width wrappers, absolutely positioned native form) and compared to the SVG at 1440: section heights match within a few px (total 5848 vs 5846). Tested: form relocation, all fields required, cover canvas/phone/widget motion, offscreen pause, carousel (auto, arrows), count-ups, CTA scroll and focus, no console errors, no horizontal overflow at 390, 820 and 1440. Not tested inside a live Unbounce account, so run the SOP's final check (submit a test lead, see the dialog, check mobile) before publishing.
