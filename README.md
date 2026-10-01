# sagitogo-site

The public pages for **sagitogo**, served by GitHub Pages at **sagitogo.app**.

| Path | Page | Source of truth |
| --- | --- | --- |
| `/privacy` | Privacy policy | `docs/legal/privacy-public.html` in the app repo |
| `/support` | Help and contact | `docs/legal/support-public.html` in the app repo |
| `/` | A short landing page | `docs/legal/index-public.html` in the app repo |

**Edit the app repo, not this one.** All three pages are sourced from
`niqluong-commits/sagitogo` and copied here; `docs/legal/PRIVACY.md` there
records the full policy these are derived from. A change made only here is
a change the app repo's own tests and review process can't see.

Unlike `sagito-site`'s own split (where the landing page and support have
no source and are edited directly in that repo), sagitogo keeps all three
pages sourced from the app repo — simpler to keep in sync while there's
only one person maintaining both.

`sagitogo-logo.png` is a flat raster of `assets/brand/sagitogo-logo-horizontal.svg`
from the app repo — the same approved brand asset the in-app
`components/brand/SagitogoLogoHorizontal.tsx` is transcribed from —
rasterised (PNG over SVG, owner preference) via `qlmanage -t -s 1200`,
which composites onto an opaque white canvas rather than preserving the
SVG's own transparency. Recovered real alpha from that single white-backed
render by unmultiplying each pixel against known white
(`alpha = 255 - min(r,g,b)`, scaled; `fg = (result - white·(1-a)) / a`),
cropped to content and resized to 768 x 282 with Pillow — verified by
compositing onto both the page's paper tint and a dark colour before use,
since the unpremultiply step is the one that can go wrong silently.
Regenerate the same way if the mark ever changes, rather than re-exporting
by hand. `favicon.png` and `apple-touch-icon.png` are the app's own
`assets/favicon.png` and `assets/icon.png`.

Recopy all of these from the app repo when any of them change there; don't
hand-edit a copy here.
