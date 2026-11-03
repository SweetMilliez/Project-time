# Design Standards (Phase II, Part 3)

Project: PlanX, a Productivity/Organizational App (tasks, schedule, and turning meeting recordings into text). Team: Goofy Goobers
Platform: Android (React Native + Expo)
Status: First draft. We will go over it as a team and lock it by Nov 5.

## 1. Style Direction: "Graffiti Cartoon"

We want the app to feel fun and a bit loud, like a notebook covered in stickers or a street art wall. It still has to be easy to read and quick to use, because people will open it to check their schedule fast.

**What makes the style**
- Thick dark outlines (2px) on cards, buttons and inputs
- Hard shadows with no blur, so things look like stickers or paper cut-outs
- Big rounded corners and chunky, friendly text
- Bright colours on a calm cream background (or a deep dark blue-purple in dark mode)
- A few graffiti touches like marker-style labels, paint splats and drips on empty screens. We only use these in small amounts so the app stays usable.

**Originality rules (we do not copy any show or brand)**
- No yellow sponge-style characters, and we avoid the yellow, brown and sea blue colour combo
- No characters, mascots, logos, fonts or screenshots from any show or brand
- If we make a mascot, it is an original character that our team designs
- If we use AI to help with images or designs, we do not put any franchise or character names in the prompts, and we save the prompts in `/design/ai-prompts.md`

## 2. Colour Palette

### Brand colours

| Role | Name | Hex | Use |
|---|---|---|---|
| Primary | Grape Pop | `#6A3DFF` | Main buttons, active tab, key actions |
| Secondary | Bubblegum | `#FF5CA8` | Secondary actions, highlights, badges |
| Accent | Lime Zap | `#B8F23A` | Record button, "new" tags, small pops of colour |
| Accent 2 | Splash Aqua | `#2ED3E6` | Info chips, links, the "today" marker on the calendar |
| Ink | Night Ink | `#1B1535` | Outlines, text on light backgrounds, shadows |

### Status colours

| Role | Name | Fill hex (badges, backgrounds, outlines) | Text/icon hex on light theme | Text/icon hex on dark theme | Required icon |
|---|---|---|---|---|---|
| Success | Mint | `#1FCB8A` | `#0B7A52` | `#1FCB8A` | `CheckCircle` |
| Warning | Tangerine | `#FF9F1C` | `#9A5B00` | `#FF9F1C` | `Warning` |
| Danger | Tomato | `#FF4B4B` | `#C62828` | `#FF4B4B` | `XCircle` |
| Info | Splash Aqua | `#2ED3E6` | `#0B7285` | `#2ED3E6` | `Info` |

**Rule:** The bright fill colours are too light to read as text or icons on the light theme (their contrast is only 1.7 to 3.2). So on light backgrounds we use the darker text/icon colour for any status text or icon. The bright colours are only used as fills behind Ink text, always with the 2px outline.

### Category colours (events and tasks)

| Category | Fill | Chip text colour | Icon |
|---|---|---|---|
| School | `#6A3DFF` | White (Ink text only gets 3.09, which is too low) | `GraduationCap` |
| Work | `#FF5CA8` | Ink | `Briefcase` |
| Personal | `#2ED3E6` | Ink | `User` |
| Health | `#1FCB8A` | Ink | `Heart` |
| Other | `#FF9F1C` | Ink | `DotsThree` |

**Rule:** We never show a category or status with colour only. Every chip has its icon and a text label too. This helps people who are colour blind (see Section 14 for the test results).

### Themes

| Token | Light theme | Dark theme |
|---|---|---|
| background | `#FFF9EE` (Cream) | `#14102B` (Deep Ink) |
| surface (cards) | `#FFFFFF` | `#221C45` |
| surfaceAlt | `#F1EAFF` | `#2E2760` |
| foreground (text) | `#1B1535` | `#FFF9EE` |
| mutedText | `#5B5480` | `#B9B2E0` |
| border / outline | `#1B1535` | `#FFF9EE` |
| shadow (hard offset) | `#1B1535` | `#6A3DFF` (a purple glow, because black is almost invisible on Deep Ink at 1.14:1) |
| primary | `#6A3DFF` | `#9B7BFF` |
| onPrimary | `#FFFFFF` | `#14102B` |
| secondary | `#FF5CA8` | `#FF7DBB` |
| onSecondary | `#1B1535` | `#14102B` |
| accent (lime) | `#B8F23A` | `#C6FF4D` |
| onAccent | `#1B1535` | `#14102B` |

**Contrast rules (we tested these, see Section 14):**
- Body text has to meet WCAG AA, which means a contrast of at least 4.5:1. We calculated every text pairing in both themes and they all pass.
- Do not use lime, aqua, mint, tangerine or bubblegum as text on cream or white. Use them as fills behind Ink text.
- Every filled element keeps its 2px outline (Ink in light mode, Cream in dark mode). Light fills like lime (1.27:1) and aqua (1.73:1) barely show up on the cream background by themselves, so the outline is what makes the shape visible. Do not remove it.
- Disabled elements (40% opacity) do not need to meet contrast, but they still need to keep their labels.

## 3. Typography

All fonts are free (Google Fonts) and we can get them in Expo with the `@expo-google-fonts/*` packages.

| Role | Typeface | Weight | Use |
|---|---|---|---|
| Display / headings | **Lilita One** | Regular | Screen titles, big numbers, buttons |
| Body / UI | **Nunito** | 400, 600, 700 | Lists, forms, transcripts, notes |
| Graffiti accent | **Permanent Marker** | Regular | Small tags only, like "NEW", captions on empty screens and stickers. Never for body text or long labels |

### Type scale

| Style | Font | Size / line height | Use |
|---|---|---|---|
| Display | Lilita One | 32 / 38 | Splash screen, big empty states |
| H1 | Lilita One | 26 / 32 | Screen titles |
| H2 | Lilita One | 20 / 26 | Section headers |
| Body | Nunito 400 | 16 / 24 | Normal text |
| Body strong | Nunito 700 | 16 / 24 | Event titles, important text |
| Caption | Nunito 600 | 13 / 18 | Times and small info |
| Button | Lilita One | 17 / 22 | All buttons |
| Marker tag | Permanent Marker | 14 / 18 | Stickers and tags (3 words max) |

The smallest text size is 13. We should not lock the font size, so the app follows the Android system font size setting.

## 4. Shape, Spacing and Effects

| Token | Value |
|---|---|
| Spacing scale | 4, 8, 12, 16, 24, 32 |
| Screen side padding | 16 |
| Corner radius (small / medium / large / pill) | 10 / 16 / 24 / 999 |
| Outline width | 2 (3 for primary buttons) |
| Hard shadow | offset x 3, y 3, blur 0, colour = shadow token |
| Min touch target | 48 x 48 |
| Slight sticker tilt | -2 to 2 degrees, only on badges and tags |

## 5. Core Components

| Component | Spec |
|---|---|
| Primary button | Grape fill, white Lilita text, 3px Ink outline, hard shadow, pill shape. When pressed it moves 3px down and right and the shadow goes away, so it feels like pushing a sticker |
| Secondary button | Bubblegum fill, Ink text, same outline and shadow |
| Record button | Lime fill, Ink outline, big circle (72), pulses while recording |
| Card | Surface colour, 2px outline, radius 16, hard shadow |
| Input | Surface fill, 2px outline, radius 12. When focused the outline turns Grape and gets thicker (3) |
| Tab bar | Cream or Deep Ink bar, 2px outline on top, the active tab has a Grape pill behind the icon |
| Chip / tag | Category colour fill, icon and text label always shown, Ink text (white text on the School chip), can be tilted a little |
| Empty state | Marker caption, a simple paint splat or drip picture, and one clear button |
| Toast / feedback | Status colour fill, Ink outline, slides in from the top, goes away after 3s |

## 6. States and Feedback

- **Loading:** bouncing dots in the brand colours, or a skeleton card with a soft shimmer
- **Recording:** the Lime button pulses, a live timer in Lilita One, and a "Recording" marker tag
- **Transcribing:** a progress card with steps (Uploading, Transcribing, Finding events)
- **Error:** Tomato outline, `XCircle` icon, a short plain message in the danger text colour, and a retry button
- **Success:** Mint check with a quick pop animation
- **Disabled:** 40% opacity and no shadow

## 7. Icons

- **Library:** Phosphor Icons (`phosphor-react-native`). We use the **Bold** weight for all UI icons and the **Fill** weight for the active tab
- **Size:** 24 normally, 20 inside chips, 28 in the tab bar
- **Colour:** the foreground token by default, onPrimary on filled buttons
- **Rule:** do not mix icon libraries. If an icon is missing, use the closest Phosphor icon or draw a custom one at 24px with a 2px stroke and rounded ends

Which icon goes with which screen (starter list). The four bottom tabs match our architecture document: Schedule `CalendarBlank`, Tasks `CheckSquare`, Record `Microphone`, Settings `Gear`. Other icons used inside screens: Transcripts `Notepad`, Add `Plus`, Suggestions `Sparkle`

## 8. Motion

- Most transitions take 150 to 250 ms, with a bouncy feel for buttons and pop-ins
- Screens use the normal stack slide, and switching tabs is a quick fade
- If the Android "remove animations" setting is on, we turn animations down

## 9. Graffiti Details (use a little, not a lot)

- Paint splats and drips only go on empty states, the splash screen and onboarding
- Maximum one marker tag per screen
- Never put graffiti behind text or on top of controls
- Keep busy screens (calendar, transcript) calm so they stay easy to read

## 10. App Identity (our team still has to decide)

- App name: **PlanX** (chosen in Phase 1, ticket: Title application)
- Logo: the PlanX wordmark in Lilita One on a Grape or Lime sticker shape with a paint splat
- Launch screen: Grape background, the PlanX wordmark, and a small splat animation (ticket: Start application)
- Android adaptive icon: 432 x 432 canvas, with the logo inside the centre 264 x 264 safe zone

## 11. Asset Organization

```
/design
  design-standards.md
  ai-prompts.md            (only if we use AI)
  /flows                   user flow diagrams
  /mockups                 exported screen images
  /assets
    /icons                 custom icons only (icon-<name>.svg)
    /logo                  logo-primary.svg, logo-mark.svg, logo-dark.svg
    /illustrations         empty-<screen>.svg, splat-<colour>.svg
    /fonts                 font files, if we bundle them
    README.md              says where each asset is used
```

Naming rule: lowercase, use hyphens, and make the name describe the file (`empty-transcripts.svg`, `icon-record-active.svg`).

## 12. Theme Tokens for Code

Make a `theme.ts` file and import the tokens from it. Do not type hex colours directly into screens.

```ts
export const palette = {
  grape: '#6A3DFF',
  bubblegum: '#FF5CA8',
  lime: '#B8F23A',
  aqua: '#2ED3E6',
  ink: '#1B1535',
  mint: '#1FCB8A',
  tangerine: '#FF9F1C',
  tomato: '#FF4B4B',
};

export const lightTheme = {
  background: '#FFF9EE',
  surface: '#FFFFFF',
  surfaceAlt: '#F1EAFF',
  foreground: '#1B1535',
  mutedText: '#5B5480',
  border: '#1B1535',
  shadow: '#1B1535',
  primary: '#6A3DFF',
  onPrimary: '#FFFFFF',
  secondary: '#FF5CA8',
  onSecondary: '#1B1535',
  accent: '#B8F23A',
  onAccent: '#1B1535',
  success: '#1FCB8A',
  warning: '#FF9F1C',
  danger: '#FF4B4B',
  info: '#2ED3E6',
  // text and icon colours for status (the fills above are too light to use as text on light)
  successText: '#0B7A52',
  warningText: '#9A5B00',
  dangerText: '#C62828',
  infoText: '#0B7285',
  onSchool: '#FFFFFF', // text on the School category chip
};

export const darkTheme = {
  ...lightTheme,
  background: '#14102B',
  surface: '#221C45',
  surfaceAlt: '#2E2760',
  foreground: '#FFF9EE',
  mutedText: '#B9B2E0',
  border: '#FFF9EE',
  shadow: '#6A3DFF',
  primary: '#9B7BFF',
  onPrimary: '#14102B',
  secondary: '#FF7DBB',
  onSecondary: '#14102B',
  accent: '#C6FF4D',
  onAccent: '#14102B',
  // the bright status colours are fine as text on dark backgrounds
  successText: '#1FCB8A',
  warningText: '#FF9F1C',
  dangerText: '#FF4B4B',
  infoText: '#2ED3E6',
};

export const radius = { sm: 10, md: 16, lg: 24, pill: 999 };
export const space = { xs: 4, sm: 8, md: 12, lg: 16, xl: 24, xxl: 32 };
export const shadowHard = { x: 3, y: 3 };
```

## 13. Checklist (what is still open)

- [ ] Team approves the palette and fonts
- [x] Contrast check done for every colour pairing (Section 14)
- [x] Colour blindness test done (Section 14)
- [ ] Check the colours on a real Android phone, in sunlight and with the screen at low brightness
- [ ] Run the checks again if any hex colour changes
- [x] App name chosen in Phase 1: PlanX
- [ ] Draw the PlanX logo (original, nothing from any franchise)
- [ ] Confirm the icon library with Raina (she needs it before her final mockups)
- [ ] Copy the standards into `/design` in the repo and link them on the Kanban tickets

## 14. Accessibility Test Results

How we tested: we calculated the WCAG 2.x contrast ratio for every colour pairing using the hex values in this document. We also ran a colour blindness simulation (the Machado 2009 model for protanopia, deuteranopia and tritanopia) and compared how different the colours look using deltaE. If deltaE is under 20, we say the colours are hard to tell apart.

### Problems we found and fixed

| # | Problem | Result | Fix |
|---|---|---|---|
| 1 | Status colours used as text or icons on the light theme were too light | Success 2.01, Warning 1.96, Info 1.73, Danger 3.15 (need 4.5) | Added darker text/icon colours (Section 2). They now get 4.58 to 5.62 on all light surfaces |
| 2 | School chip had Ink text on Grape | 3.09 (need 4.5) | School chip uses white text, which gets 5.64 |
| 3 | In dark mode the shadow was black on Deep Ink, so it disappeared | 1.14 | Dark mode shadow is Grape `#6A3DFF`, which gets 3.27 against the dark background |
| 4 | Mint (Success/Health) and Aqua (Info/Personal) look almost the same with tritanopia, and Work and Health are close with deuteranopia | deltaE 9.5 and 17.4 | Colour is never the only signal. Every status and category has its own icon and a text label |

### What passes (light theme)

| Pairing | Ratio | Needed |
|---|---|---|
| Foreground on background / surface / surfaceAlt | 16.62 / 17.42 / 14.90 | 4.5 |
| Muted text on background / surface / surfaceAlt | 6.62 / 6.94 / 5.94 | 4.5 |
| White on Grape (primary button) | 5.64 | 4.5 |
| Ink on Bubblegum (secondary button) | 6.10 | 4.5 |
| Ink on Lime (record button) | 13.11 | 4.5 |
| Ink on Mint / Tangerine / Tomato / Aqua | 8.27 / 8.49 / 5.28 / 9.60 | 4.5 |
| Grape vs background (links, focus outline) | 5.38 | 3.0 |
| Ink outline vs background / surface | 16.62 / 17.42 | 3.0 |

### What passes (dark theme)

| Pairing | Ratio | Needed |
|---|---|---|
| Foreground on background / surface / surfaceAlt | 17.60 / 15.18 / 12.72 | 4.5 |
| Muted text on background / surface / surfaceAlt | 9.23 / 7.96 / 6.67 | 4.5 |
| Ink on light Grape (primary button) | 5.86 | 4.5 |
| Ink on light Bubblegum / Lime | 7.82 / 15.64 | 4.5 |
| Ink on Mint / Tangerine / Tomato / Aqua | 8.75 / 8.98 / 5.59 / 10.17 | 4.5 |
| Status colours as text on dark background | 5.59 to 10.17 | 4.5 |
| Light Grape vs dark background / surface (focus outline) | 5.86 / 5.05 | 3.0 |
| Cream outline vs background / surface | 17.60 / 15.18 | 3.0 |

### Limits we know about (not failures)
- Bright fills on cream (lime 1.27, aqua 1.73, mint 2.01, tangerine 1.96, bubblegum 2.73) do not stand out from the background by themselves. We accept this because every fill has a required 2px Ink outline (16.62) and an Ink text label.
- Mint vs Tomato scored 27 to 31 for protanopia and deuteranopia. That is different enough to tell apart but it is close, so the check and X icons are required and these two are never told apart by colour alone.
- These numbers are calculated, not tested on a real phone. The real device check is still open in Section 13.
