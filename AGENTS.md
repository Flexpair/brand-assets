# Agent Guide — `brand-assets`

Binary brand assets for Flexpair: `logo.svg`, `favicons/` (many sizes/formats), `wallpapers/`, and
social banners. **No prose, no code** — there is almost nothing for an agent to author here.

This module is a Git submodule of the Flexpair umbrella repository; `AGENTS.md` is read natively by
both GitHub Copilot and Claude Code.

## Rules for agents

- **Do not hand-edit binary assets** (PNG/JPEG/ICO). The favicon set is derived from `logo.svg`; if
  the mark changes, regenerate the full set from the SVG source rather than editing individual
  rasters.
- `logo.svg` is the source of truth for the mark — read it to reference branding; edit it only with
  explicit intent.
- Reference assets from other repos by stable path (e.g. `brand-assets/logo.svg`); do not duplicate
  copies into consuming repos.
- There are currently no documented brand-usage rules (colors, clear space, typography) in this
  repo. If such guidance is needed, propose adding a `BRAND.md` rather than encoding rules here.
