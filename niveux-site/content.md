# NIVEUX — Website content

Extracted 2026-10-02 from the **mobile** version (375 px wide) of:
- Home: https://bwcgmwebsite.framer.website/comingsoon
- Everything else: https://bwcgmwebsite.framer.website/phone-duplicate

All images are in `images/`, downloaded at their original resolution. None of them have alt text on the live site.

---

## Brand basics
- Name: **NIVEUX**. It's written "niveux" in the wordmark and "NiveuX" once in the app copy.
- Product: a continuous glucose monitor (CGM), "edition I"
- Tagline: *Your Glucose, Simplified. 24/7.*
- Meta description: "Made with love in IISc"
- Brand blue: `#0039AC`. Button gradient: `#0039AC` → `#4474D4`
- Fonts:
  - **Dongle**: wordmark and nav "n" icon
  - **Montserrat**: section labels / small headings
  - **Inter**: big headlines and buttons
  - **Roboto**: body copy
  - **Cabin** (bold): "NIVEUX" in the product hero
  - **Noto Sans Limbu**: "meet" / "edition I"
- Photography: mostly black-and-white lifestyle shots of people wearing the square white sensor on the upper arm
- Every "Join Waitlist" button links to https://bwcgmwebsite.framer.website/page

---

## 1. Home (from /comingsoon)

**Image:** `00-home-hero-woman-street-sensor.jpg`. Full-bleed black-and-white photo of a woman with curly hair on a city street, wearing the sensor on her upper arm.

| Text | Style |
|---|---|
| INTRODUCING | Montserrat 20px, blue |
| niveux | Wordmark, Dongle 220px light, blue |
| we are building something awesome | Inter 18px light, white. Callout with a thin leader line |
| CRAFTED TO ENHANCE YOUR METABOLIC HEALTH | Inter 20px light, white. Leader line points at the sensor |
| COMING —— SOON | Inter 12px, white |
| **Join Waitlist** | Button, blue gradient |
| images are for representation. actual product may vary. | Disclaimer, 8px, blue |

---

## 2. Content sections (from /phone-duplicate), in page order

### Navigation (sticky, frosted glass)
- Left: rounded-square "n" logo icon (Dongle, white)
- Right: **Join** button (blue pill)

### Hero
**Images:**
- `02-hero-woman-sensor-portrait.jpg`: the same woman as the home page, cropped to a portrait
- `01-hero-blurred-backdrop.jpg`: a softer copy used behind the glass nav

> meet
> **NIVEUX**
> edition I
>
> YOUR GLUCOSE, SIMPLIFIED.
> 24/7.
>
> **[Join Waitlist]**

### Intro
> ## Take healthy decisions, with our new continuous glucose monitor
> Built with cutting-edge tech and precision sensors, enhance your routine with real-time insights, predictive tracking and seamless integration with your life

### Feature carousel (3 slides, dot pagination)
Each slide has a lifestyle photo, an app screen, a heading and body copy.

| Heading | Body | Photo | App screen |
|---|---|---|---|
| COMPETE WITH YOURSELF | Get a daily glucose score that shows how well you performed, pushing you to stay on top of your game | `04-feature-photo-cyclist.jpg` | `07-app-screen-daily-score-85.png` ("Daily Score 85") |
| YOU ARE IN CONTROL | NIVEUX tracks glucose every 5 minutes for 15 days continuously. It detects subtle change in glucose levels, offering early insights and suggests habit changes | `03-feature-photo-woman-reading-in-bed.jpg` | `08-app-screen-history-graph.png` ("History" glucose graph) |
| HARNESS THE POWER OF AI | NIVEUX pushes you forward with reminders for hydration, meals, and exercise, empowering you to stay fueled and ready to take on every challenge | `05-feature-photo-woman-on-bench.jpg` | `06-app-screen-new-log-food.png` ("New Log", food entry) |

All pairings were confirmed from the page's code.

### Make a statement (black section, auto-scrolling image ticker)
> ## Make a statement

Captions: **UNHIDE · SHOWOFF · BE BOLD · STANDOUT**

**Images** (people wearing the sensor as a visible accessory):
- `09-statement-woman-white-dress.jpg`
- `10-statement-man-smoke.jpg`
- `11-statement-woman-poolside.jpg`
- `12-statement-woman-white-dress-alt.jpg`

### Colourways
**Images:**
- `13-product-sensor-moonlight.png`: the sensor with a white base, a black glossy top and the "niveux" logo in teal
- `14-product-sensor-internals.png`: the sensor with its cover off, showing the circuit board inside

- `13b-product-sensor-dark-night.png`: the all-black Dark Night version. It only loads when the toggle is switched.

Toggle: **Moonlight** (selected) / **Dark Night**.

Statement captions by image: UNHIDE = 09, SHOWOFF = 10, BE BOLD = 11, STANDOUT = 12.

### The technical craft
> ## The technical craft
> Engineered for action and built to inspire.
> See what makes NIVEUX unique

This is a carousel of 5 cards with left/right arrows (`21-icon-arrow-left.svg`, `22-icon-arrow-right.svg`).

| Heading | Body | Image |
|---|---|---|
| SWEAT-PROOF PERFORMANCE | IP5X water proofing to reach your goals without a pause | `15-tech-sweat-proof-sensor-on-arm.jpg`: colour close-up of the sensor on an arm by a pool |
| LONG-LASTING ENDURANCE | Replace NIVEUX twice a month. Get order reminders on the App when you are low on stock, automatically | `16-tech-long-lasting-man-on-stairs.jpg` |
| ENGINEERED FOR ALL-DAY COMFORT | Non-woven polyester patch and a skin friendly adhesive provides makes sure the NIVEUX is comfortable day and night | `17-tech-comfort-feet-in-hammock.png` |
| HYGIENE-FIRST DESIGN | ETO sterilization ensures a sterile NIVEUX pack decontaminated and delivered every single time | `18-tech-hygiene-abstract.png`: colourful abstract with dark bars |
| dataGlance™ BY NIVEUX | The NiveuX app comes with useful widgets for mobile devices, so you stay updated, always | `19-tech-dataglance-phone-watch-widgets.png`: iPhone and Apple Watch widgets |

The live site shows the trademark as "DATAGLANCETM" (TM in plain letters), not "dataGlance™".

### Closing CTA
> ### SO FAR, SO GOOD?
> Be among the first to try NIVEUX
>
> **[Join Waitlist]**

**Image:** `20-waitlist-app-102-with-sensor.png`. The app home screen ("Hi Michael, You're Holding Steady Today!", 102 mg/dL, Time in Range 78%) with the sensor beside it.

---

## Copy issues on the live site
- "a skin friendly adhesive **provides makes sure**…": extra word
- "DATAGLANCETM" should be "dataGlance™"
- "NiveuX" vs "NIVEUX": inconsistent capitalisation
- Page title for /phone-duplicate is still "My Framer Site"
