# Calm (Low Stimulation) brightness

A fifth UI brightness, selectable anywhere the other four are: Preferences › Interface, the
Window › Brightness menu, or `window.brightness calm`. It persists in prefs as
`ui_brightness = "calm"`.

## Why it exists

Illustrator's four brightness levels are all the same design at different lightnesses: a
saturated blue accent, neon guides, 2 px corners, tight rows. Calm is a different tuning for
sustained use by people for whom that density is a cost — ADHD and autistic users in particular.

## What it changes

| | Dark | Calm |
|---|---|---|
| Surfaces | neutral grey (`#262626`–`#323232`) | warm near-black (`#1a1a19`–`#2c2c2a`) |
| Accent | saturated blue `#378ef0` | one soft blue `#85b7eb` |
| Smart guides | magenta `#ff3dfc` | muted violet `#b48ad0` |
| Guides | cyan `#4affff` | muted teal `#6fb2c4` |
| Selection / anchors | two blues | one, the accent |
| Corner radius | 2 px | 6 px |

Only `error` and `warning` keep a hue of their own, because they are the two cues that must never
be missed. Both are paired with an icon or a label elsewhere in the UI — **colour is never the
sole carrier of meaning**, which is the rule the rest of this theme is built around.

## Where the values come from

The surface, text and accent tokens are the dark half of the INT Digital design system
(warm-neutral greys with a faint warm bias, one semantic accent, a dark theme designed in its own
right rather than inverted from the light one), and its principles: shape + colour always, one
hue never meaning two things, and a lower-stimulation mode that keeps every shape cue intact
while taking the saturation out.

## Adding to it

`Tokens::for_brightness(Brightness::Calm)` in `crates/ui-egui/src/theme.rs` holds every override
over `base`. Widgets read `Tokens::get`, so nothing else needs touching — if a widget hard-codes
a colour, that is the bug, not the theme.
