# Colours & modes

The theme is intentionally restrained: one muted steel-blue accent, a
near-neutral background, and a coordinated dark mode — all driven from a
handful of values.

## The palette

    <div style="height:3rem; background:#3f6f9f;"></div>
    <div style="padding:0.4rem 0.6rem; font-size:0.85rem;"><strong>Primary</strong><br><code>#3f6f9f</code></div>

    <div style="height:3rem; background:#7ea8d6;"></div>
    <div style="padding:0.4rem 0.6rem; font-size:0.85rem;"><strong>Primary (dark)</strong><br><code>#7ea8d6</code></div>

    <div style="height:3rem; background:#fbfcfe;"></div>
    <div style="padding:0.4rem 0.6rem; font-size:0.85rem;"><strong>Background</strong><br><code>#fbfcfe</code></div>

    <div style="height:3rem; background:#0f141b;"></div>
    <div style="padding:0.4rem 0.6rem; font-size:0.85rem;"><strong>Background (dark)</strong><br><code>#0f141b</code></div>

| Role            | Light     | Dark      |
|-----------------|-----------|-----------|
| Background      | `#fbfcfe` | `#0f141b` |
| Surface         | `#f3f7fb` | `#151c26` |
| Text            | `#1f2a37` | `#c4cdd9` |
| Primary / links | `#3f6f9f` | `#7ea8d6` |
| Border          | `#e4e9f0` | `#28323f` |

## How light & dark work

Light is the **base theme** — `bg`, `fg`, and `primary` are set as bslib
variables in `inst/pkgdown/_pkgdown.yml`, and bslib derives the full
gray ramp from them.

Dark mode rides on **Bootstrap 5.3 colour modes**. pkgdown’s light
switch (`light-switch: true`) toggles a `data-bs-theme` attribute on the
page, and the theme overrides the relevant CSS custom properties under
`[data-bs-theme="dark"]` in `inst/pkgdown/extra.scss`:

``` scss
[data-bs-theme="dark"] {
    --bs-body-bg: #0f141b;
    --bs-body-color: #c4cdd9;
    --bs-primary: #7ea8d6;
    --bs-link-color: #7ea8d6;
    /* ...and so on */
}
```

Because everything keys off CSS custom properties, components that
reference `var(--bs-primary)` or `var(--bs-border-color)` adapt
automatically — no duplicated component rules per mode.

## Typography

| Use      | Font           |
|----------|----------------|
| Body     | Inter          |
| Headings | Outfit         |
| Code     | JetBrains Mono |

All three are pulled in at build time via bslib’s Google Fonts
integration, so the rendered site has no runtime dependency on a font
CDN.
