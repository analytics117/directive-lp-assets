# Bevi LA: Unbounce build (variant A)

Page: **bevi.co/bevi-la/**
Built from the approved Figma ([Bevi] Design Review > LA ToFU LP > "LA TOFU LP - Hi-FI v3"), including the new CTA wording.

## 1. Upload to GitHub

Repo: `analytics117/directive-lp-assets`. From the **top level** of the repo, drag in the whole `bevi` folder so you end up with:

```
bevi/la/
  images/   43 files, all bla-*
  fonts/    7 files, all bla-*
  video/    4 files, all bla-*
  code/     4 files (paste into Unbounce, they don't need to live in GitHub)
```

Every file and every CSS class is prefixed `bla-`, so nothing clashes with later Bevi pages (use a new prefix for those).

Assets load from:
`https://cdn.jsdelivr.net/gh/analytics117/directive-lp-assets@main/bevi/la/`

Test one after upload, for example `.../images/bla-logo-bevi-white.png`.

## 2. Unbounce

1. Blank page, width **1440**, Bevi domain, URL `bevi-la`.
2. Page Properties > Title & Meta Data:
   - Title: `Bevi in LA | Still, sparkling and flavored water for your workplace`
   - Description: `See how Bevi pours filtered still and sparkling water, with flavors and boosts on tap, for LA offices. Get a side-by-side of our machines and how pricing works.`
   - noindex, nofollow. Favicon: Bevi's.
3. **Stylesheets** > Add New Stylesheet, name it *Page styles* > paste `bla-02-stylesheet.css` (keep the `<style>` tags).
4. **Javascripts** > Add New JavaScript, name it *Page scripts*, placement **Before Body End Tag** > paste `bla-03-javascript.html`.
5. **Custom HTML widget** in the first section, stretched to full page width, no height > paste `bla-01-page-widget.html`.
6. **Form** (one step, native Unbounce form, anywhere on the canvas; the script moves it into the white card):

   | Label | Field ID | Type |
   |---|---|---|
   | Work email | `email` | Email, required |

   Turn off multi-step. Button text: **Send my comparison** (the script also sets it). Leave "Append form data to URL" unticked.
   Confirmation: Show form confirmation dialog. **Desktop 520 x 440, mobile 300 x 420.**
7. **Confirmation dialog** > delete the default text > Custom HTML widget at X 0, Y 0, same size as the dialog, on desktop **and** mobile > paste `bla-04-confirmation-dialog-widget.html`.
8. Mobile view: nothing to arrange. The page stacks itself below 900px.

Nothing shows in the builder or preview. Publish, then check in an incognito window. The console should say `bla: scroll ready, 2 CTA buttons` and `bla: form placed in the card`.

## 3. What moves

- Hero: background video loop (muted) and a slow-drifting illustration strip.
- Logo belt: slow auto-scroll (28s per loop).
- Meet Bevi: flavor icons float up like bubbles and pop at the top.
- Real people, real pours: three fan videos; the centre one plays for 4.5s, then the cards rotate. Click a side card to bring it forward. Videos only load when the section is on screen.
- Pick your pour: arrows, click or swipe through 5 flavors; the background tint changes per flavor. Small bubbles rise in the background.
- Machine cards: "See all features" opens the spec panel per card.
- FAQs: one open at a time, first open.
- Every looping animation pauses off screen and stops for visitors with reduced motion turned on.

Settings at the top of `bla-03-javascript`: `BUTTON_LABEL`, `EMAIL_LABEL`, `EMAIL_HINT`, `EMAIL_IDS`, `FAN_MS`.

## 4. Changes from the Figma

- Hero quote avatar shows **KH** (Karen Hood). The Figma still had GC from the old quote.
- Problem column copy wraps by width instead of hard line breaks.
- Short last words are held together with non-breaking spaces (no one-word last lines).

## 5. Open items before launch

- Confirm Bevi is happy for the follow-up email to cover "how pricing works" (form copy and thank-you popup promise it).
- Confirm the nurture email that fires after submit (HubSpot) matches the promise: machine side-by-side, pricing, customer stories.
- Karen Hood (BCG) quote is a Boston customer, not LA.
- 99.9% vs 99.99% microplastic removal, "1 billion+" wording and "up to 5" mix count are still unconfirmed by Bevi.
- Where Bevi fits photos are Adobe Stock comps: license before launch.
- Run the SOP final check on the live page (submit a test lead, check the dialog, check mobile).
