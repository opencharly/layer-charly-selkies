# charly-selkies

The `charly-selkies` family — the owning skills for the Selkies streaming-desktop
metalayers.

The `charly-selkies` candy is a **concept candy**: it ships no install content
and owns the `selkies` family's `skill:` entities whose names have no namesake
candy. It carries two entities:

- `selkies-desktop-layer` — the metalayer composing a full Selkies Wayland
  streaming desktop: labwc, Waybar, Chrome with CDP, the `wl-*` automation
  tooling, fonts, AT-SPI2 accessibility, and XWayland support.
- `wl-overlay-layer` — the Wayland overlay-window candy (gtk4-layer-shell) used
  for screen recordings (title cards, lower-thirds, countdowns).

The engine, compositor, and per-tool skills of the same family are owned by their
own repos under the `selkies` family (`/charly-selkies:selkies`,
`/charly-selkies:selkies-core`, `/charly-selkies:labwc`,
`/charly-selkies:wl-tools`, …). `candy/plugin-marketplace` regenerates the
standalone [opencharly/marketplace](https://github.com/opencharly/marketplace)
corpus from these entities, so the skills are authored here and projected there.

## What it provides

| Property | Value |
|---|---|
| Layer / candy | `charly-selkies` (concept candy) |
| Install content | none — a `true` no-op `plan:` |
| Owns | 2 `skill:` entities: `selkies-desktop-layer`, `wl-overlay-layer` |
| Projected to | `marketplace/selkies/skills/` |
| Service / port | none (the desktop streams on port 3000 via the `selkies` engine candy) |

## How to use it

This repo is consumed as a **skill source**, not as an image layer. Edit the
`skill:` entities in `charly.yml`; the marketplace regeneration projects them
into the `/charly-selkies:*` pages. To reference the repo directly, compose it in
a box. A box is a `candy:` node carrying the box's `base:` image and a nested
`candy:` list of layer refs (the nested `candy:` is the composition list; the
outer `candy:` is the box body):

```yaml
my-box:
  candy:                  # the box body (an IMAGE is a `candy:` node carrying `base:`)
    base: fedora          # the box's base image
    candy:                # the box's composition list
      - '@github.com/opencharly/layer-charly-selkies:v2026.265.1929'
```

The streaming desktop itself is composed by the `selkies-desktop` metalayer in
the `selkies-labwc` / `selkies-kde` boxes; this concept candy carries only the
projected skill.

## Layout

- `charly.yml` — the `charly-selkies:` concept candy entity plus two `skill:`
  entities (`selkies-desktop-layer`, `wl-overlay-layer`).
- `.github/workflows/tag-on-merge.yml` — CalVer tag + `CHANGELOG/` on merge.
- `README.md` — this user overview.

## Related

- Owning skills: `/charly-selkies:selkies-desktop-layer`, `/charly-selkies:wl-overlay-layer`
- Engine / compositor skills: `/charly-selkies:selkies`, `/charly-selkies:selkies-core`, `/charly-selkies:labwc`
- Authoring reference: `/charly-image:layer`
- [`opencharly/marketplace`](https://github.com/opencharly/marketplace) — the projected corpus
- [`opencharly/charly`](https://github.com/opencharly/charly) — the charly CLI and image builder
- [`opencharly/opencharly`](https://github.com/opencharly/opencharly) — the umbrella
