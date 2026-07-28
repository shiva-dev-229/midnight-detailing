# Dedicated Gallery Page — Design

**Date:** 2026-07-27
**Status:** Approved

## Goal

Move completed-work photos off the single-page homepage into a dedicated
gallery page, organized by vehicle, so the landing page stays tight and the
gallery can grow independently.

## Decisions

- Homepage "The work" tile grid is **removed entirely**.
- The before/after tire comparison slider **stays on the homepage** (it lived
  inside the "The work" section, so it is pulled out into its own compact
  section).
- New gallery page organizes photos **grouped by vehicle** (Acura, Mazda,
  Mercedes).
- Shared CSS is **extracted into `styles.css`** linked by both pages (single
  source of truth).

## Files

### `styles.css` (new)
- Contains the full `<style>` block currently inline in `index.html`, moved
  verbatim (no rule changes) so both pages share identical styling.

### `index.html` (edited)
- Replace the inline `<style>...</style>` block with
  `<link rel="stylesheet" href="styles.css">`.
- Remove the "The work" gallery grid: the section eyebrow, `The work` header,
  `gallery-line`, and the `.gallery-grid` with its tiles.
- Keep the before/after tire slider (`.ba-wrap`) — move it into its own compact
  section (heading e.g. "The difference") so it no longer depends on the
  removed "The work" wrapper.
- Update links that pointed at the removed section to the new page:
  - Nav `Work` link (`#work`) → `gallery.html`
  - Hero `View the work` ghost-link (`#work`) → `gallery.html`
  - Footer `The work` link (`#work`) → `gallery.html`
- The "Recent Work" shut-line divider is kept if it still frames the slider;
  otherwise removed with the grid.

### `gallery.html` (new)
Standalone page linking `styles.css`, reusing existing class names and markup
patterns from `index.html`.

Structure:
1. **Top nav** — same bar and logo as homepage. Logo links to `index.html`.
   Cross-page links become `index.html#services` and `index.html#contact`.
   The `Work` link represents the current page.
2. **Intro** — mono eyebrow + large header ("Completed work") + one intro line
   including the hover-to-reveal-color hint.
3. **Three vehicle sections**, each a heading + its own `.gallery-grid` of
   tiles, reusing existing tile styling (grayscale→color hover, corner
   `tile-tag` labels):
   - Acura: `acura-01.jpg`, `acura-02.jpg`, `acura-03.jpg`
   - Mazda: `mazda-01.jpg`, `mazda-02.jpg`, `mazda-03.jpg`
   - Mercedes: `mercedes-01.jpg`, `mercedes-02.jpg`, `mercedes-03.jpg`,
     `mercedes-04.jpg`
4. **Closing booking CTA** — same Cal.com link/style (`mega-cta`) as homepage.
5. **Footer** — shared footer markup.

## Reused behavior (no change)
Monochrome theme, film grain, reveal-on-scroll animation, hover color reveal,
`onerror="this.style.display='none'"` image fallback, responsive grid.

## Out of scope
- No lightbox / click-to-enlarge.
- No filtering or sorting controls.
- No new photo processing — uses existing `assets/gallery/web/*.jpg`.

## Verification
- Homepage renders identically to before (aside from the removed grid) after
  CSS extraction — spot-check hero, services, before/after slider, footer.
- Gallery page: all 10 images load, grouped correctly; hover reveal works;
  nav/logo/CTA links resolve; layout is responsive.
