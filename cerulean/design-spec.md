# NIVEUX — Design & animation spec

Extracted 2026-10-02 from the live Framer site, **mobile layout only**. The values come from the published code bundles and from measuring the page at 375 px wide. The rebuild is in `index.html`.

## Tokens
| Token | Value |
|---|---|
| Main Blue | `#0039AC` |
| Blue 2 (gradient end) | `#4474D4` |
| Page background | `#F7F7F7` |
| Card background | `#FFFFFF` |
| Dark knob (Dark Night) | `#2E2E2E` |
| Framer default ease | `cubic-bezier(.44, 0, .56, 1)` |

## Type
| Use | Font | Size / line-height / weight |
|---|---|---|
| Wordmark "niveux" | Dongle | 160px / 0.7 / 300, letter-spacing −0.03em |
| Nav logo "n" | Dongle | 42px / 0.7 / 400 |
| INTRODUCING | Montserrat | 16px / 1.2 / 400 |
| Big headlines ("Take healthy decisions…", "The technical craft") | Inter | 32px / 1.2 / 600 |
| "Make a statement" | Montserrat | 32px / 1.2 / 700 |
| Section labels (COMPETE WITH YOURSELF, SO FAR, SO GOOD?) | Montserrat | 24px / 1.2 / 600, uppercase |
| Statement captions (UNHIDE…) | Montserrat | 24px / 1.2 / 400 |
| Body | Roboto | 16px / 1.2 / 400 |
| Home taglines | Inter | 18–20px / 1.2 / 300 |
| Buttons | Inter | 16–18px / 1.2 / 500 |

## Layout (375 px wide)
1. **Home** (from /comingsoon): 796px tall. The photo is `object-position: 50% 0`.
   - The wordmark block sits at top 45px.
   - Taglines are right-aligned at 494px and 577px, each with a 1px white leader line.
   - A 90px grey fade (`#ABABAB`) runs along the bottom.
   - The CTA row is at 728px.
2. **Info**: `#F7F7F7`, padding 52 / 32.
3. **Benefits carousel**: 3 slides, gap 24, each slide 654px tall on white.
   - Square photo at the top, with the phone mockup (177×259) overlapping its bottom-right corner at top 200px.
   - Copy starts at 436px with 32px left padding.
   - Dots: 6px, gap 20, on an `#F7F7F7` pill with blur(12px), padding 12, radius 17. Inactive dots are at 0.5 opacity.
4. **Make a statement**: black section with the title at 48 / 25.
   - Slides are full-width with a 525px-tall cover photo and a caption 19px below it.
5. **Colourways**: `#F7F7F7`, 657px tall. The product image is about 362px square.
   - Toggle pill: 240×48, radius 30, `rgba(247,247,247,.39)`, blur(62px), shadow `0 0 16px 4px rgba(0,0,0,.08)`.
6. **Technical craft**: 433px tall.
   - Title at top 72, subtitle at 322.
   - The sensor-internals image sits behind them, centred at 222px.
7. **Features carousel**: 5 cards, gap 16, 510px tall, padding 16, image 358×272.
   - Dots: 9px, inactive at 0.3 opacity.
8. **Closing CTA**: `#F7F7F7`.
   - Label at 54, phone image in a 300px-tall box, full-width shine button.
9. **Footer**: white, with the disclaimer at 8px.

## Components

### Nav (phone)
- **Wrapper:** `linear-gradient(180deg, rgba(232,240,255,.72) 0%, rgba(171,171,171,0) 85%)`, padding 12 12 20 20.
- **Pill:** 68px tall, radius 33, `rgba(191,210,255,.13)`, `backdrop-filter: blur(23px)`.
- **Logo:** 40×40, 4px white border, radius 9.

### Glow button ("Join", "Join Waitlist" on home)
- **Container:** radius 118, padding 14 / 28, `rgba(255,255,255,.05)`.
- **Glow:** a radial white gradient with `blur(15px)`.
- **Stroke:** a radial white gradient. It shows as a 2px ring because the Fill is inset 2px.
- **Fill:** `radial-gradient(50% 252% at 50% 50%, #0039AC, #4474D4)`, radius 114.

### Shine button ("Join Waitlist", full width)
- 44px tall, radius 23.
- **Background:** `radial-gradient(50% 100% at 51.4% 54%, #0039AC, rgba(0,57,171,.64))`.
- **Inner highlight:** `radial-gradient(95% 598.5% at 53.4% 54.1%, rgb(128,170,255), transparent)`.
- **Shine lines:** two 28×2 lines, one at the top-left and one at the bottom-right, filled with `rgb(199,218,255)` that fades to transparent at each end.

## Animations
| Element | Trigger | Animation | Timing (from the Framer config) |
|---|---|---|---|
| "niveux" wordmark, disclaimer | Page load | Each character flips in: `rotateY(90°) → 0`, opacity 0 → 1 | Spring, bounce 0, 0.4s per character, 0.05s stagger |
| Home taglines, COMING — SOON | Page load | Same character flip | Starts after 0.8s |
| Nav | Load | Drops in from `y: -150` | Spring, bounce 0.2, 0.4s |
| Nav | Scroll | Hides (`y: -150`, opacity 0) when scrolling down and returns when scrolling up | Tween 0.4s, Framer ease |
| Glow button | Always | The light orbits the button: Top → Right → Bottom → Left | Steps every 0.7s, each transition 0.8s linear |
| Glow button | Hover | The glow and stroke spread to fill the centre | 0.8s linear |
| Shine button | Always | The top line slides +60px and the bottom line −60px, both fading out | 1.3s ease, then a 2s pause, looping |
| Info block | Scroll | `rotateX(10°) → 0` | Spring, stiffness 500, damping 60 |
| Technical-craft background image | Scroll | Zooms from scale 4.2 at 0.5 opacity to scale 0.8 at full opacity | Spring, stiffness 135, damping 60 |
| Waitlist phone image | Scroll | Grows from scale 0.5 to 1 | Spring, stiffness 500, damping 60 |
| Benefits and Features carousels | Swipe | Native scroll-snap (centre), with progress dots | Dots fade over 0.3s |
| Make a statement slideshow | Auto | Advances left every 2s, loops forever, can be dragged, pauses on hover | Spring, stiffness 200, damping 40 |
| Colourway toggle | Tap | The knob slides across, its colour switches white ↔ `#2E2E2E`, and the product image crossfades | Spring, bounce 0.2, 0.4s |
| Carousel arrows | Tap | Shrink to scale 0.9 | 0.05–0.15s |

## How the rebuild approximates Framer
- **Springs:** approximated with cubic-bezier curves.
  - Bounce 0.2 → `cubic-bezier(.34,1.25,.64,1)`
  - Soft spring → `cubic-bezier(.22,1,.36,1)`
- **Glow-button orbit:** CSS `@property` animating the gradient's position and size.
- **Scroll effects:** progress runs from 0, when the element's top enters at the bottom of the screen, to 1, when it reaches 35% from the top. The value is smoothed each frame.
- **Nav:** stays hidden over the home hero, because the Coming Soon page had no nav, and appears once you scroll past the hero.
- **Width:** the layout is capped at 430px wide and centred on larger screens, because the original desktop layout is broken.
