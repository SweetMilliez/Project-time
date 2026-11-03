# Design Assets (PlanX)

This folder has the images and graphics the developers need to build the app. This README says what each file is and where it gets used. Files that are not made yet are marked (todo), so we can see what is still missing.

If you add a file, add a line for it in the tables below.

## Naming rules

- All lowercase, words split with hyphens
- The name says what it is and where it is used (`empty-transcripts.svg`, `icon-record-active.svg`)
- Use SVG when we can, and PNG when we need a picture

## Folders

| Folder | What goes in it |
|---|---|
| `icons/` | Custom icons only. Normal icons come from Phosphor Icons (Bold weight), so we do not need files for those |
| `logo/` | PlanX logo files |
| `illustrations/` | Empty screen pictures and paint splats |
| `fonts/` | Font files, only if we bundle them. Right now the fonts load from the `@expo-google-fonts` packages, so this can stay empty |

## Logo

| File | What it is | Where it is used | Status |
|---|---|---|---|
| `logo/logo-primary.svg` | PlanX wordmark in Lilita One on a Grape sticker shape with a paint splat | Launch screen, login screen | (todo) |
| `logo/logo-primary.png` | Same as above as a PNG | Places where SVG does not work | (todo) |
| `logo/logo-mark.svg` | Small square version (just the mark) | App icon, small spots in the header | (todo) |
| `logo/logo-dark.svg` | Version that still looks good on the Deep Ink background | Dark mode | (todo) |

## App icon (Android)

| File | What it is | Where it is used | Status |
|---|---|---|---|
| `logo/icon-app-adaptive.png` | 432 x 432 canvas with the logo inside the centre 264 x 264 safe zone | Android adaptive icon | (todo) |

The final copies that the Expo build uses go in the `assets` folder at the root of the repo. This `design/assets` folder is where we keep the originals.

## Illustrations

| File | What it is | Where it is used | Status |
|---|---|---|---|
| `illustrations/empty-tasks.svg` | Paint splat or drip picture | Tasks tab when there are no tasks | (todo) |
| `illustrations/empty-schedule.svg` | Paint splat or drip picture | Schedule tab when nothing is planned | (todo) |
| `illustrations/empty-transcripts.svg` | Paint splat or drip picture | Transcript list when there are no recordings | (todo) |
| `illustrations/splat-grape.svg` | Grape paint splat | Launch screen, onboarding | (todo) |
| `illustrations/splat-bubblegum.svg` | Bubblegum paint splat | Launch screen, onboarding | (todo) |
| `illustrations/splat-lime.svg` | Lime paint splat | Launch screen, record screen | (todo) |

## Icons

We use Phosphor Icons (`phosphor-react-native`), Bold weight, and Fill weight for the active tab. The icon for each screen is listed in `design/design-standards.md` (Section 7).

| File | What it is | Where it is used | Status |
|---|---|---|---|
| (none yet) | We only add a custom icon here if Phosphor does not have one | | |

## Rules for graphics

- Graffiti graphics go on empty states, the launch screen and onboarding only, never behind text or on top of buttons
- Everything has to be original. No characters, logos or pictures from any show or brand
- Use the colours from `design/design-standards.md` and nothing else
