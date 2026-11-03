# Screen Template (Phase II, Template ticket)

This is the base layout every screen in PlanX starts from, so all the mockups and all the code look like the same app. The colours, fonts and shapes come from `design-standards.md`, so this file only covers the layout.

Frame size for mockups: Android phone, 360 x 800.

## Layout from top to bottom

```
+-------------------------------+
|  status bar (Android system)  |
+-------------------------------+
|  header                       |   height 56
|  Title (H1)          [icon]   |
+-------------------------------+
|                               |
|  content area (scrolls)       |   side padding 16
|  cards, lists, forms          |   gap between items 16
|                               |
|                      ( + )    |   add button, 16 from the edges
+-------------------------------+
|  Schedule Tasks Record Settings|  tab bar, height 64
+-------------------------------+
```

| Part | Spec |
|---|---|
| Background | `background` token (Cream in light mode, Deep Ink in dark mode) |
| Header | Height 56. Screen title in H1 (Lilita One 26), left aligned. One optional icon on the right (24, Bold). No outline under it |
| Content area | Scrolls. Side padding 16, space between items 16. Cards use the Card style (surface colour, 2px outline, radius 16, hard shadow) |
| Add button | Primary round button with a `Plus` icon, bottom right, 16 above the tab bar. Only on screens where the user can add something |
| Tab bar | Height 64, 2px outline on top. Four tabs: Schedule (`CalendarBlank`), Tasks (`CheckSquare`), Record (`Microphone`), Settings (`Gear`). The active tab has a Grape pill behind the icon and uses the Fill weight. Every tab has a text label under the icon |
| Safe areas | Keep content away from the status bar and the system navigation bar, so nothing is covered |
| Touch targets | At least 48 x 48 |

## Detail screens (stack screens)

Screens like Task details, Add/Edit task and Transcript review sit on top of a tab.

- The header has a back arrow (`ArrowLeft`) on the left, then the title
- The primary action (Save, Confirm) is a Primary button at the bottom of the content area
- A secondary action (Cancel, Delete) is a Secondary button or a text button next to it
- The tab bar stays visible, except on the Record screen while recording so nobody taps away by accident (proposal, team to confirm)

## States every screen needs

| State | What the user sees |
|---|---|
| Loading | Bouncing dots or skeleton cards |
| Empty | Marker caption, a paint splat or drip picture, and one clear button |
| Error | Tomato outline, `XCircle` icon, short message, retry button |
| Success | Mint check with a quick pop, or a toast that goes away after 3s |

## Checklist before a mockup is done

- [ ] Uses the 360 x 800 frame and the layout above
- [ ] Only uses colours, fonts and icons from the design standards
- [ ] Every filled shape has its 2px outline
- [ ] Status and category colours always come with an icon and a text label
- [ ] Empty, loading and error states are shown or listed in the ticket
- [ ] Light and dark versions are made, or the ticket says which one is missing
- [ ] Exported to `design/mockups` and linked on the screen's Kanban ticket

## Starter screen list

Millie's flows decide the final list. This is just so we have something to start scoping.

| Type | Screens |
|---|---|
| Tab screens | Schedule, Tasks, Record, Settings |
| Stack screens | Task details, Add/Edit task, Transcript review (confirm tasks), Recording saved |
| Before the tabs | Launch screen, Login, Sign up |
