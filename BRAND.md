# Flexpair Brand Guide

Practical brand reference for the Flexpair assets in this repository. It documents the values that
are **actually in use** today; sections marked _Not yet defined_ are gaps, not invented rules — fill
them deliberately rather than assuming a value.

> **Source of truth for the core palette:** the exact identity colors are owner-defined here and
> encoded in [`logo.svg`](logo.svg). The Astro site's
> [`src/styles/global.css`](https://github.com/Flexpair/flexpair-astro-site/blob/main/src/styles/global.css)
> owns a derived UI ramp; it does not redefine the four core colors.
> **Typography is owner-defined here** (see below): the brand typeface is Noto Sans, and
> implementations should conform to this guide, not the other way around.

## Color

The Flexpair identity uses exactly four core colors:

| Role | Hex | Typical use |
|---|---|---|
| Black | `#000000` | primary text and dark grounds |
| White | `#ffffff` | primary light ground and reversed text |
| Flexpair teal | `#157878` | subdued text, structure, and supporting information |
| Flexpair cyan | `#00ffff` | deliberate emphasis and signal accents |

For presentations and documents, use black or white for primary text, teal for intentionally
receding text, and cyan sparingly as the signal color. Cyan is not a body-text color on white;
prefer a cyan shape or line with black text when emphasis is needed on a light ground. Do not add
dark green, azure, amber, red, or other accent hues. If a quiet surface is necessary, use
transparency or a white tint derived from teal or cyan rather than introducing another hue.

The `X` path in `logo.svg` uses cyan `#00ffff` with a teal `#157878` stroke. The remaining wordmark
paths are black.

### Derived website ramp

The Astro site's `@theme` derives a teal UI ramp from the core teal for interaction states and
surface treatments. These are implementation shades, not additional identity colors and not a
presentation palette:

Brand teal ramp (from the site's `@theme`):

| Token | Hex | Typical use |
|---|---|---|
| `brand-50`  | `#e7f3f3` | subtle tint backgrounds |
| `brand-100` | `#cfe7e7` | |
| `brand-200` | `#a3d0d0` | |
| `brand-300` | `#6eb5b5` | |
| `brand-400` | `#339595` | |
| `brand-500` | `#157878` | **canonical brand color** |
| `brand-600` | `#126868` | hover / pressed |
| `brand-700` | `#0e5353` | gradient mid |
| `brand-800` | `#0a3e3e` | gradient deep |
| `brand-900` | `#062828` | gradient endpoint |

Implementation note: the site remaps Tailwind's `indigo-*` (and `violet-*` for deep gradient
endpoints) onto this teal ramp, so existing `bg-indigo-*` / `text-indigo-*` utilities resolve to
teal-derived UI shades. New presentation work must not copy this ramp as its color scheme; use the
four core colors above.

## Typography

- **Brand typeface: Noto Sans.** Recommended fallback stack:
  `"Noto Sans", ui-sans-serif, system-ui, -apple-system, "Segoe UI", Roboto, sans-serif`.
- Headings (`h1`–`h4`): weight `600`, `letter-spacing: -0.02em`, `line-height: 1.1`.
- Body: `line-height: 1.6` (tighter prose blocks use `1.65`).
- **Logo typography** — the wordmark in `logo.svg` is stored as outlined vector paths (no font is
  embedded), so these are recorded from the brand owner rather than readable from the file:
  - The **"Flexpair" wordmark (top line) is set in Syncopate.**
  - The **line beneath it is Noto Sans** _(to re-confirm against the original editable design
    source)._

> **Implementation status:** the live site at `welcome.flexpair.com` (the Hugo site) already serves
> Noto Sans — its andromeda theme hardcodes a Google Fonts load of
> `Noto+Sans:ital,wght@0,100..900;1,100..900` in
> `themes/andromeda-hugo/layouts/partials/essentials/script.html`. **Known drift:** the Astro
> successor site's `global.css` still declares `--font-display: "Inter", …`. Reconcile Astro to
> Noto Sans before it goes live at `welcome.flexpair.com`.

## Logo and icon assets

- **`logo.svg` is the master vector** and the source of truth for the mark. Reference it directly;
  edit it only with deliberate intent.
- **Favicons are derived outputs.** `favicons/` holds the generated set across sizes — PNGs
  (`favicon16px.png` … `favicon512px.png`, plus platform sizes like `114/120/144/150/152/180/192/256/310px`)
  and a few SVG sources (`favicon16.svg`, `favicon32-48.svg`, `favicon64+square.svg`,
  `favicon70+circle.svg`). **Do not hand-edit individual raster files** — if the mark changes,
  regenerate the whole set from the SVG source so all sizes stay consistent.
- `wallpapers/` contains background images (`base.png`, `clouds.png`, `waves.png`, and numbered
  variants `1.png`–`7.png`). Their current-vs-experimental status is _Not yet defined_; confirm
  before treating one as the production wallpaper.
- `LinkedIn banner.png` is the social banner (LinkedIn profile dimensions).

## Usage rules

- **Reference assets by stable path** from consuming repos (e.g. `brand-assets/logo.svg`); do not
  copy duplicates into other repos, so updates propagate from one place.
- Keep the asset filenames stable — sites and templates link to them by name.
- Binary assets are not agent-editable; changes go through regeneration from source, not pixel edits.

## Not yet defined (gaps)

These are genuinely undocumented; propose values before assuming them:

- Logo **clear space** and **minimum size**.
- **Monochrome / reversed (knockout)** logo variants and when to use each.
- Logo **misuse** rules (recoloring, stretching, effects).
- A wallpaper **status map** (which variants are production vs. experimental).
