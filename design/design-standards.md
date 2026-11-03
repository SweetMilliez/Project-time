# Design Standards (Phase II, Part 3)

Project: Productivity/Organizational App (schedule, appointments, voice-to-text meeting capture)
Platform: Android (React Native + Expo)
Status: STARTER DRAFT. Team to review and lock by Nov 5.

## 1. Style Direction: "Graffiti Cartoon"

The app should feel fun, loud and friendly, like a sticker-covered notebook or a street-art wall, while staying easy to read and quick to use.

**Core traits**
- Thick dark outlines (2px) on cards, buttons and inputs
- Hard offset shadows (no blur), so elements look like stickers or cut-outs
- Big rounded corners, chunky friendly type
- Bright, saturated colours on a calm cream or deep ink background
- Small graffiti touches (marker-style labels, paint splats, drips on empty states), used sparingly so the app stays usable

**Originality rules (do not copy existing franchises)**
- No yellow-sponge-style characters, no brown-and-yellow-plus-sea-blue palette combination
- No characters, mascots, logos, fonts or screenshots from any show or brand
- Our mascot (optional) is an original character designed by the team
- If AI image tools are used, do not prompt with any franchise or character names, and record prompts in `/design/ai-prompts.md`

## 2. Colour Palette

### Brand colours

| Role | Name | Hex | Use |
|---|---|---|---|
| Primary | Grape Pop | `#6A3DFF` | Main buttons, active tab, key actions |
| Secondary | Bubblegum | `#FF5CA8` | Secondary actions, highlights, badges |
| Accent | Lime Zap | `#B8F23A` | Record button, "new" tags, small pops of energy |
| Accent 2 | Splash Aqua | `#2ED3E6` | Info chips, links, calendar "today" marker |
| Ink | Night Ink | `#1B1535` | Outlines, text on light backgrounds, shadows |

### Status colours

| Role | Name | Fill hex (badges, backgrounds, outlines) | Text/icon hex on light theme | Text/icon hex on dark theme | Required icon |
|---|---|---|---|---|---|
| Success | Mint | `#1FCB8A` | `#0B7A52` | `#1FCB8A` | `CheckCircle` |
| Warning | Tangerine | `#FF9F1C` | `#9A5B00` | `#FF9F1C` | `Warning` |
| Danger | Tomato | `#FF4B4B` | `#C62828` | `#FF4B4B` | `XCircle` |
| Info | Splash Aqua | `#2ED3E6` | `#0B7285` | `#2ED3E6` | `Info` |

**Rule:** the bright fill hex values fail contrast when used as text or icons on the light theme (1.7 to 3.2). On light backgrounds, use the darker "text/icon" hex for any status text or icon. Bright fills are only used behind Ink text, always with the 2px outline.

### Category colours (events and tasks)

| Category | Fill | Chip text colour | Icon |
|---|---|---|---|
| School | `#6A3DFF` | White (Ink fails at 3.09) | `GraduationCap` |
| Work | `#FF5CA8` | Ink | `Briefcase` |
| Personal | `#2ED3E6` | Ink | `User` |
| Health | `#1FCB8A` | Ink | `Heart` |
| Other | `#FF9F1C` | Ink | `DotsThree` |

**Rule:** category and status are never shown by colour alone. Every chip carries its icon and a text label (see Section 14 for the colour blindness results).

### Themes

| Token | Light theme | Dark theme |
|---|---|---|
| background | `#FFF9EE` (Cream) | `#14102B` (Deep Ink) |
| surface (cards) | `#FFFFFF` | `#221C45` |
| surfaceAlt | `#F1EAFF` | `#2E2760` |
| foreground (text) | `#1B1535` | `#FFF9EE` |
| mutedText | `#5B5480` | `#B9B2E0` |
| border / outline | `#1B1535` | `#FFF9EE` |
| shadow (hard offset) | `#1B1535` | `#6A3DFF` (Grape glow; black is invisible on Deep Ink at 1.14:1) |
| primary | `#6A3DFF` | `#9B7BFF` |
| onPrimary | `#FFFFFF` | `#14102B` |
| secondary | `#FF5CA8` | `#FF7DBB` |
| onSecondary | `#1B1535` | `#14102B` |
| accent (lime) | `#B8F23A` | `#C6FF4D` |
| onAccent | `#1B1535` | `#14102B` |

**Contrast rules (tested, see Section 14):**
- Body text must meet WCAG AA (4.5:1). All text pairings in both themes were computed and pass.
- Never use lime, aqua, mint, tangerine or bubblegum as text on cream or white. Use them as fills behind Ink text.
- Every filled element keeps its 2px outline (Ink in light, Cream in dark). Light fills such as lime (1.27:1) and aqua (1.73:1) do not stand out from the cream background on their own, so the outline is what makes the shape visible. Never remove it.
- Disabled elements (40% opacity) are exempt from contrast requirements but must keep their labels.

## 3. Typography

All fonts are free (Google Fonts) and available through `@expo-google-fonts/*`.

| Role | Typeface | Weight | Use |
|---|---|---|---|
| Display / headings | **Lilita One** | Regular | Screen titles, big numbers, buttons |
| Body / UI | **Nunito** | 400, 600, 700 | Lists, forms, transcripts, notes |
| Graffiti accent | **Permanent Marker** | Regular | Small tags only: "NEW", empty-state captions, stickers. Never for body text or long labels |

### Type scale

| Style | Font | Size / line height | Use |
|---|---|---|---|
| Display | Lilita One | 32 / 38 | Splash, big empty states |
| H1 | Lilita One | 26 / 32 | Screen titles |
| H2 | Lilita One | 20 / 26 | Section headers |
| Body | Nunito 400 | 16 / 24 | Default text |
| Body strong | Nunito 700 | 16 / 24 | Event titles, emphasis |
| Caption | Nunito 600 | 13 / 18 | Times, metadata |
| Button | Lilita One | 17 / 22 | All buttons |
| Marker tag | Permanent Marker | 14 / 18 | Stickers, tags (max 3 words) |

Minimum text size: 13. Support the Android system font-size setting (do not lock font scaling).

## 4. Shape, Spacing and Effects

| Token | Value |
|---|---|
| Spacing scale | 4, 8, 12, 16, 24, 32 |
| Screen side padding | 16 |
| Corner radius (small / medium / large / pill) | 10 / 16 / 24 / 999 |
| Outline width | 2 (3 for primary buttons) |
| Hard shadow | offset x 3, y 3, blur 0, colour = shadow token |
| Min touch target | 48 x 48 |
| Slight sticker tilt | -2 to 2 degrees, on badges and tags only |

## 5. Core Components

| Component | Spec |
|---|---|
| Primary button | Grape fill, white Lilita text, 3px Ink outline, hard shadow, radius pill. On press: shift 3px down-right and remove shadow (feels like pressing a sticker) |
| Secondary button | Bubblegum fill, Ink text, same outline and shadow |
| Record button | Lime fill, Ink outline, large circle (72), pulses while recording |
| Card | Surface colour, 2px outline, radius 16, hard shadow |
| Input | Surface fill, 2px outline, radius 12, focus state: outline turns Grape and thickens to 3 |
| Tab bar | Cream or Deep Ink bar, 2px top outline, active tab shown as a Grape pill behind the icon |
| Chip / tag | Category colour fill, icon + text label always shown, Ink text (White text on the School chip), slight tilt allowed |
| Empty state | Marker caption + simple paint splat or drip illustration + one clear action |
| Toast / feedback | Status colour fill, Ink outline, slides in from top, auto-dismiss 3s |

## 6. States and Feedback

- **Loading:** bouncing dots in brand colours, or a skeleton card with a soft shimmer
- **Recording:** Lime button pulses, live timer in Lilita One, "Recording" marker tag
- **Transcribing:** progress card with steps (Uploading, Transcribing, Finding events)
- **Error:** Tomato outline, `XCircle` icon, short plain message in the danger text colour, retry button
- **Success:** Mint check with a quick pop animation
- **Disabled:** 40% opacity, no shadow

## 7. Icons

- **Library:** Phosphor Icons (`phosphor-react-native`), **Bold** weight for all UI icons, **Fill** weight for the active tab
- **Size:** 24 default, 20 in chips, 28 in the tab bar
- **Colour:** foreground token by default, onPrimary on filled buttons
- **Rule:** do not mix icon libraries. If an icon is missing, pick the closest Phosphor icon or draw a custom one at 24px, 2px stroke, rounded caps

Screen to icon mapping (starter): Calendar `CalendarBlank`, Tasks `CheckSquare`, Record `Microphone`, Transcripts `Notepad`, Settings `Gear`, Add `Plus`, Suggestions `Sparkle`

## 8. Motion

- Duration 150 to 250 ms for most transitions, bouncy easing for buttons and pop-ins
- Screen transitions: standard stack slide, tab changes: quick fade
- Respect the Android "remove animations" setting and reduce motion when it is on

## 9. Graffiti Details (use sparingly)

- Paint splats and drips: only on empty states, splash screen, and onboarding
- Marker tags: maximum one per screen
- Never place graffiti elements behind text or over controls
- Keep a calm background on dense screens (calendar, transcript) so they stay readable

## 10. App Identity (to decide as a team)

- App name: TBD (ticket: Title application)
- Logo: wordmark in Lilita One on a Grape or Lime sticker shape, with a paint-splat accent
- Launch screen: Grape background, wordmark, small splat animation (ticket: Start application)
- Android adaptive icon: 432 x 432 canvas, logo inside the centre 264 x 264 safe zone

## 11. Asset Organization

```
/design
  design-standards.md
  ai-prompts.md            (only if AI is used)
  /flows                   user flow diagrams
  /mockups                 exported screen images
  /assets
    /icons                 custom icons only (icon-<name>.svg)
    /logo                  logo-primary.svg, logo-mark.svg, logo-dark.svg
    /illustrations         empty-<screen>.svg, splat-<colour>.svg
    /fonts                 font files, if bundled
    README.md              where each asset is used
```

Naming rule: lowercase, hyphens, descriptive (`empty-transcripts.svg`, `icon-record-active.svg`).

## 12. Theme Tokens for Code

Create `theme.ts` and import tokens from it. Never hardcode hex values in screens.

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
  // text and icon colours for status (fills above fail contrast as text on light)
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
  // bright status fills already pass as text on dark backgrounds
  successText: '#1FCB8A',
  warningText: '#FF9F1C',
  dangerText: '#FF4B4B',
  infoText: '#2ED3E6',
};

export const radius = { sm: 10, md: 16, lg: 24, pill: 999 };
export const space = { xs: 4, sm: 8, md: 12, lg: 16, xl: 24, xxl: 32 };
export const shadowHard = { x: 3, y: 3 };
```

## 13. Open Decisions Checklist

- [ ] Team approves palette and fonts
- [x] Contrast check done for every colour pairing (Section 14)
- [x] Colour blindness simulation done (Section 14)
- [ ] Re-check contrast on a real Android device in sunlight and with the screen at low brightness
- [ ] Re-run the checks if any hex value changes
- [ ] App name chosen
- [ ] Logo drawn (original, no franchise references)
- [ ] Icon library confirmed with Raina (she needs it before final mockups)
- [ ] Standards copied to `/design` in the repo and linked on the Kanban tickets

## 14. Verified Accessibility Results

Method: WCAG 2.x relative luminance contrast ratios computed from the hex values in this document, and colour blindness simulated with the Machado (2009) model for protanopia, deuteranopia and tritanopia, comparing colour differences (CIELAB deltaE, under 20 treated as hard to tell apart).

### Issues found and fixed

| # | Problem found | Measured | Fix applied |
|---|---|---|---|
| 1 | Status colours used as text or icons on the light theme | Success 2.01, Warning 1.96, Info 1.73, Danger 3.15 (need 4.5) | Darker text/icon variants (Section 2), now 4.58 to 5.62 on all light surfaces |
| 2 | School chip used Ink text on Grape | 3.09 (need 4.5) | School chip uses white text, 5.64 |
| 3 | Dark theme hard shadow was black on Deep Ink, so the sticker shadow disappeared | 1.14 | Dark shadow is Grape `#6A3DFF`, 3.27 against the dark background |
| 4 | Mint (Success/Health) and Aqua (Info/Personal) look almost identical to people with tritanopia; Work and Health are close under deuteranopia | deltaE 9.5 and 17.4 | Colour is never the only signal: every status and category has its own icon and a text label |

### Results that pass (light theme)

| Pairing | Ratio | Requirement |
|---|---|---|
| Foreground on background / surface / surfaceAlt | 16.62 / 17.42 / 14.90 | 4.5 |
| Muted text on background / surface / surfaceAlt | 6.62 / 6.94 / 5.94 | 4.5 |
| White on Grape (primary button) | 5.64 | 4.5 |
| Ink on Bubblegum (secondary button) | 6.10 | 4.5 |
| Ink on Lime (record button) | 13.11 | 4.5 |
| Ink on Mint / Tangerine / Tomato / Aqua | 8.27 / 8.49 / 5.28 / 9.60 | 4.5 |
| Grape vs background (links, focus outline) | 5.38 | 3.0 |
| Ink outline vs background / surface | 16.62 / 17.42 | 3.0 |

### Results that pass (dark theme)

| Pairing | Ratio | Requirement |
|---|---|---|
| Foreground on background / surface / surfaceAlt | 17.60 / 15.18 / 12.72 | 4.5 |
| Muted text on background / surface / surfaceAlt | 9.23 / 7.96 / 6.67 | 4.5 |
| Ink on light Grape (primary button) | 5.86 | 4.5 |
| Ink on light Bubblegum / Lime | 7.82 / 15.64 | 4.5 |
| Ink on Mint / Tangerine / Tomato / Aqua | 8.75 / 8.98 / 5.59 / 10.17 | 4.5 |
| Status colours as text on dark background | 5.59 to 10.17 | 4.5 |
| Light Grape vs dark background / surface (focus outline) | 5.86 / 5.05 | 3.0 |
| Cream outline vs background / surface | 17.60 / 15.18 | 3.0 |

### Known limits (not failures)
- Bright fills on cream (lime 1.27, aqua 1.73, mint 2.01, tangerine 1.96, bubblegum 2.73) do not contrast with the background by themselves. This is accepted because every fill has a mandatory 2px Ink outline (16.62) and carries an Ink text label.
- Mint vs Tomato under protanopia and deuteranopia scored 27 to 31, which is distinguishable but close. The check and X icons are required so these two are never told apart by colour alone.
- These are calculated values. A real-device check is still on the checklist in Section 13.
