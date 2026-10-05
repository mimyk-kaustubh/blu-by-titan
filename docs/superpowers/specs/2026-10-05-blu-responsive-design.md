# BLU by TITAN: tablet and desktop layouts

Date: 2026-10-05
Base: `palette/cerulean` ("A day with BLU" redesign, Glass treatment)
Build branch: `feature/responsive`
Wireframes: `niveux-site/wireframes/responsive.html`

## Intent

- **What the client said:** make the site responsive for desktop and tablets. Take the home section's tablet and desktop layouts from the original `/comingsoon` page. For the rest, rearranging is enough. Keep white space on the sides on desktop. "A day with BLU" becomes a sideways chart on desktop.
- **Assumed:** the phone layout, copy, fonts, colours and animations do not change. Success means the page looks designed for the screen at any width, with nothing overlapping, cut off or scrolling sideways.

## Breakpoints

| Width | Layout |
|---|---|
| < 768px | Phone, unchanged |
| 768px to 1099px | Tablet |
| >= 1100px | Desktop |

All new rules live inside `@media (min-width: 768px)` and `@media (min-width: 1100px)`. No existing phone rule is edited, so the phone layout cannot regress.

## Container

- `.site` loses its 430px cap from 768px up and becomes full width.
- Section content sits in a centred column: `max-width` 720px (tablet) / 1120px (desktop), side padding 32px minimum.
- Edge-to-edge bands: the home section background and the statement band. Their contents align to the column.

## Home (from `/comingsoon`)

Measured from the original at 1440px and 820px:

- Section height 800px. One photo box, 1200 x 800, centred horizontally (`left: 50%; translateX(-50%)`), `object-position: 50% 0`. On desktop it shows whole with page background either side; on tablet the section clips its edges.
- "INTRODUCING": centred, 18px, top 32px.
- Logo: centred below it, 250px wide, wipe-in kept. (Revised during build: the photo fixes the model's hair at about 158px from the top, so a 400px logo would overlap it. 250px, the phone size, clears it.)
- "we are building something awesome": right-aligned text, top 516px, positioned as an offset from the photo centre (`left: 50%`).
  - Desktop: left = 50% - 174px, width 155px.
  - Tablet: left = 50% - 141px, width 220px.
- "Crafted to enhance your metabolic health": left-aligned text, width 168px.
  - Desktop: left = 50% + 215px, top 581px.
  - Tablet: left = min(50% + 215px, 100% - 192px), top 559px, so it never touches the right edge.
- Leader lines move with their text blocks.
- Bottom row (Coming Soon + Join Waitlist): centred, 303px wide, top 729px (desktop) / 707px (tablet).
- Tablet section height is 778px, as in the original.
- Bottom fade spans the full width.
- Fonts and motion unchanged (Inter, Montserrat, letter flip, glow button).

## Nav

Same glass pill, widened to the content column. Logo left, Join right. No menu links.

## A day with BLU

- **Tablet:** vertical line kept. Each moment becomes two columns: time, headline and text on the left; photo and app screen on the right.
- **Desktop:** sideways chart.
  - Header, then a horizontal chart strip (height 120px), then three columns, one per moment.
  - The SVG trace is rebuilt in a horizontal mode: x = time, y = glucose level, with the in-range band as a horizontal bar. One dot per moment sits above the left edge of its column, in line with its time label.
  - Curve shape matches the vertical one: a dip after the first moment, a rise after the second, settling at the third.
  - Progress is tied to the chart strip's position on screen: 0 when its top reaches 85% down the viewport, 1 when it reaches 35%. Same per-frame smoothing as now.
  - The trace switches mode when the viewport crosses 1100px (matchMedia + the existing ResizeObserver).
  - Reduced motion: fully drawn in both modes.

## Make a statement

- **Tablet:** swipe strip kept; slides 38% wide so about two and a half show.
- **Desktop:** four columns, no scrolling; `overflow: visible`, `tabindex` scrolling unnecessary but harmless.

## The sensor

Two columns from 768px: product image and toggle left, heading, text and the four facts right. Facts stay a 2 x 2 grid.

## Technical craft

Heading and intro centred. The internals image is 560px wide on tablet and desktop. The zoom starts at 2.4x instead of 4.2x from 768px up, because the source image is only 1099px wide.

## Features

- **Tablet:** two columns; the fifth card (widgets) spans both.
- **Desktop:** six-column grid; the first three cards span two columns each, the last two span three each.

## Waitlist

Two columns from 768px: heading, text, form and steps on the left; phone image on the right (260px tall on tablet, 420px on desktop). The small phone image beside the heading is hidden at these widths, since the large one replaces it.

## Footer

Logo left, disclaimer right, on one row.

## Images

- Keep `images/web/*.webp` (max 900px) as the phone source.
- Add `images/web-lg/*.webp` exported from the originals at up to 1600px wide (never upscaled) for: the statement photos, the three day photos, the five feature images, the two product shots and the waitlist phone.
- Use `srcset` with width descriptors and `sizes` so each device downloads the smallest adequate file.
- Hero already ships at full resolution.

## Known limits (not fixed here)

- Logo is a raster cut-out; at 250px it is sharp, and its size is limited by the photo composition rather than resolution.
- Internals source image is low resolution; the reduced zoom works around it.

## Verification

At 375, 768, 1024, 1280 and 1920px wide:
- No horizontal scroll (`scrollWidth === clientWidth`).
- No element in the home section overlaps another.
- Phone (375px): computed layout of every section root matches the current build.
- Glucose line: vertical below 1100px, horizontal at and above; dots fill as it draws.
- Form: validation, loading, success and error states work.
- All images load; no broken `srcset` entries.
