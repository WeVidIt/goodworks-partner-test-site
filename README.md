# Good Works partner test site

A small, made-up partner website ("Cedar Lane Film Club") that carries the real Good Works partner sales widget. It lives on a different web address from Good Works on purpose, so staff can test the widget the way a real partner's visitors would meet it, and demo it to partners.

Live page: https://wevidit.github.io/goodworks-partner-test-site/

Nothing here is a real club. It is plain HTML and CSS with no build step, no frameworks and no trackers.

## What is on the page

- One film, No Limbs No Limits: The Nick V Story, with a Good Works widget in the small-card style that opens the purchase window. The title goes on sale November 10, 2026, and until then the card says it is not available.
- A short "how it works" and a "for partners" block showing the two lines of code a partner pastes.
- Artwork is loaded from public Good Works addresses. Prices are never typed on the page; the widget reads them from the title.

## How the widget gets on the page

Every widget is two things:

1. The Good Works loader script, added once at the bottom of the page.
2. One `goodworks-vod` tag per widget, with that widget's code in `embed`.

The loader draws the card and the purchase window inside a frame from goodworkshub.com. Card details are typed into Stripe's frames, so they never touch this page.

## How to add another widget

1. In the Good Works admin, go to VOD, then Tools, then Partner sales, open the "Test Partner (GitHub Pages)" partner and make a widget for the title: tick Buy, Rent or both, set the button words, and keep the look on Auto.
2. Turn the widget on. A widget that is off, or a title that is not on sale yet, shows "not available here right now" and sells nothing.
3. Copy the widget's tag from the snippet box in admin.
4. In `index.html`, copy the `article` block in the films section, change the artwork and words, and paste the new tag inside its `widget` box. Leave the loader script at the bottom as it is.
5. Commit to `main`. GitHub Pages republishes in a minute or two.

## How this was set up

- A public repository under the WeVidIt organization, with GitHub Pages serving the `main` branch from the root. The empty `.nojekyll` file tells Pages to serve the files exactly as they are.
- In the Good Works admin, staff add a partner with one site address. The address is the origin only, `https://wevidit.github.io`, because a widget's allowed list matches the origin and not the page path.
- Staff then make one widget per title on that partner with Buy and Rent ticked, and paste the widget's tag into `index.html`. The widget is made off and turned on once the page carries its code.
- The widget's title picker lists whole films only, so a single episode cannot be chosen there yet. That is why the page carries one film.

## Known limits

- Apple Pay needs a domain file at the root of the web address. This project site lives under a path on wevidit.github.io, so it cannot host that file, and Apple Pay is not set up here. Card payment works.
- The page only controls where the widget sits. The title's own rules (hidden, archived, area, sale day) still decide whether a purchase can start.
- No Limbs No Limits has renting switched off, so its card offers Buy only.

## Files

- `index.html`: the page and the widget tags
- `styles.css`: the look, built for phones first and widened for desktops
- `.nojekyll`: serve as-is on GitHub Pages
