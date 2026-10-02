# BLU by TITAN: "A day with BLU" redesign

Date: 2026-10-02
Base: `design/cerulean-refresh` (Cerulean palette, main's home section and motion)
Build branch: `redesign/day-with-blu`
Wireframes: `niveux-site/wireframes/index.html` (option B), fonts: `niveux-site/wireframes/fonts.html` (option 2)

## Intent

- **What the client said:** improve the site design, starting from the Cerulean version. Keep the home section exactly as it is (main's layout, fonts, type styles and copy). Keep main's button and nav motion.
- **Assumed:** the page's job is to explain what BLU measures and get waitlist sign-ups. Success means a visitor understands the product and reaches the form. Mobile-first; the desktop layout is out of scope.

## Decisions

| Area | Decision |
|---|---|
| Structure | Option B, "A day with BLU": story-led middle section |
| Type below home | Unbounded (headlines, big numbers) + Hanken Grotesk (body, labels). Sentence case. |
| Type in home | Unchanged: Inter, Montserrat, Roboto |
| Motion | Glucose line drawing on scroll is the signature moment. Keep main's glow Join buttons, shine waitlist button and hide-on-scroll nav. Remove the intro tilt, internals zoom and phone grow. |
| Palette | Cerulean |

## Tokens

| Name | Hex | Use |
|---|---|---|
| Sky | `#0EA5E9` | Glucose line, highlights, dots |
| Deep cerulean | `#0369A1` | Headings, button fills |
| Ink | `#082032` | Statement band |
| Mist | `#F2F7FA` | Page background below home |
| Range | `#E0F2FE` | In-range band behind the glucose line |
| Slate | `#4F5759` | Body text |

Existing token names (`--teal`, `--teal-text`, `--teal-deep`, `--teal-mid`, `--ink`) are kept so the palette branches stay mergeable. New tokens: `--mist`, `--range`, `--slate`.

Type scale below home (Hanken body 16/1.55):
- Section headline: Unbounded 600, 26px/1.15, tracking -0.03em
- Moment headline: Unbounded 600, 21px/1.2
- Big numbers: Unbounded 400, 40px/1
- Time labels: Hanken Grotesk 600, 13px, slate
- Body: Hanken Grotesk 400, 16px/1.55, max 34ch in moments, 60ch elsewhere

## Page structure

```
HOME (unchanged, locked)
NAV (main's: drops in past home, hides on scroll down, glow "Join")
A DAY WITH BLU
  headline + one line
  | glucose line (left gutter, draws on scroll) over a pale in-range band
  o 7:00 morning ride    Compete with yourself        cyclist + daily score app
  o 13:00 lunch          Reminders that know your day bench + meal log app
  o 22:00 wind down      You are in control           reading + history app
  caption: "Illustrative day"
MAKE A STATEMENT (ink band)
  headline
  swipe strip, next photo peeking, caption under each (UNHIDE, SHOWOFF, BE BOLD, STANDOUT)
THE SENSOR
  headline, product image, Moonlight / Dark Night toggle
  facts: 15 days / 5 min / Sweat-proof / Sterile (big number + one line each, no cards)
  "What's inside" static internals figure
ON YOUR PHONE AND WATCH
  widgets photo, headline, one line
WAITLIST
  headline + small phone image, one line
  email form (label, input, hint, error), shine button
  next steps: Join the list -> Get the launch email -> Order your first sensors
FOOTER (unchanged)
```

## Components

- **Glucose line:** an inline SVG path in the left gutter of the day section, height matching the section. A pale `--range` band sits behind it. The path is drawn with `stroke-dasharray`/`stroke-dashoffset`; progress follows the section's scroll position, smoothed like main's scroll effects (lerp 0.12 per frame). Each moment has a dot on the line that fills with Sky once the line reaches it. The path is regenerated on resize so it fits the section height.
- **Moment:** time label, headline, one sentence, then the photo with the app screen beside it (not overlapping).
- **Statement strip:** horizontal scroll-snap; slides 82% wide so the next one peeks; captions below the images. No autoplay, so no pause button.
- **Facts:** two-column grid, number in Unbounded, explanation in Hanken. No card backgrounds or shadows; separated by space and one hairline.
- **Waitlist steps:** three short labels in a row, connected by a line. The content is a sequence, so the order is meaningful.

## Behaviour and quality floor

- Reduced motion: glucose line fully drawn, no button loops, nav still works.
- Keyboard focus visible on every control; skip link kept.
- Form: unchanged validation, loading, success and error states.
- All images keep their alt text; decorative SVG is `aria-hidden`.
- No layout shift from the line: the SVG is absolutely positioned in a reserved gutter.

## Out of scope

- Desktop layout, dark mode, brand fonts for the logo, connecting the form to a backend.

## Copy to confirm with the team

- "Order your first sensors" as the third waitlist step.
- "Illustrative day" caption wording.
