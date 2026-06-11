# Flexpair Brand Guide

Practical brand reference for the Flexpair assets in this repository. It documents the values that
are **actually in use** today; sections marked _Not yet defined_ are gaps, not invented rules — fill
them deliberately rather than assuming a value.

> **Source of truth for the palette:**
> [`flexpair-astro-site/src/styles/global.css`](https://github.com/Flexpair/flexpair-astro-site/blob/main/src/styles/global.css)
> (`@theme` block) is the canonical implementation of the color ramp; this file mirrors it in prose.
> If the site palette changes, update this guide in the same change.
> **Typography is owner-defined here** (see below): the brand typeface is Noto Sans, and
> implementations should conform to this guide, not the other way around.

## Color

**Primary brand color: Flexpair teal `#157878`** (the `--color-brand-500` token; also the teal
accent inside `logo.svg`). The brand is monochromatic teal on near-black ink over a white ground.

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

Neutrals:

| Token | Hex | Use |
|---|---|---|
| `ink`      | `#0b1020` | body text |
| `ink-soft` | `#1a2140` | secondary text, soft headings |
| background | `#ffffff` | page ground |

Implementation note: the site remaps Tailwind's `indigo-*` (and `violet-*` for deep gradient
endpoints) onto this teal ramp, so existing `bg-indigo-*` / `text-indigo-*` utilities resolve
on-brand. Do not introduce a second accent hue without a deliberate brand decision — gradients are
intentionally kept monochromatic teal.

## Typography

- **Brand typeface: Noto Sans.** Recommended fallback stack:
  `"Noto Sans", ui-sans-serif, system-ui, -apple-system, "Segoe UI", Roboto, sans-serif`.
- Headings (`h1`–`h4`): weight `600`, `letter-spacing: -0.02em`, `line-height: 1.1`.
- Body: `line-height: 1.6` (tighter prose blocks use `1.65`).

> **Known drift — fix in implementation, not here:** the Astro site's `global.css` currently
> declares `--font-display: "Inter", …`, and the Hugo site sets no explicit font family (it falls
> back to the theme default). Neither matches the Noto Sans brand intent. Reconcile the sites to
> Noto Sans; until then, treat this guide as the brand standard.

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
