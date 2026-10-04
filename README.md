<div align="center">

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/SaphiraLinux/brand/main/logos/saphira-linux-brand-icon-logo-1200.webp">
  <img alt="Saphira Linux" src="https://raw.githubusercontent.com/SaphiraLinux/brand/main/logos/saphira-linux-brand-icon-light-logo-1200.webp" width="600">
</picture>

# Saphira brand assets

Canonical Saphira Linux logo, dragon mark and mascot artwork.

**These files are the source of truth for GitHub-hosted use.** The same files
are published by the website at `https://saphira.vm2.uk/images/`. Where a
GitHub surface needs an image, reference this repository.

---

## Read this before you pick a logo file

The two logo families are inverses of each other, and **the filenames are
backwards from intuition**:

| File | Wordmark colour | Use on |
|---|---|---|
| `logos/saphira-linux-brand-icon-logo-1200.webp` | near-white, RGB(254,254,254) | **dark** backgrounds |
| `logos/saphira-linux-brand-icon-light-logo-1200.webp` | black, RGB(1,1,1) | **light** backgrounds |

The file named **without** `light` is the **dark-background** asset. The file
named **with** `light` is the **light-background** asset.

GitHub renders README files on a white background by default. **On GitHub you
almost always want the `-light-` file.** Using the other one gives you a
white wordmark on white and an apparently broken logo.

Both are transparent PNG-style WebP with a transparent background and work on
either background for the dragon and the `Linux` half of the wordmark. Only the
`Saphira` half differs.

## Using the logo on GitHub

GitHub's markdown sanitiser keeps `<picture>` elements intact, so the correct
way to get both variants is:

```html
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/SaphiraLinux/brand/main/logos/saphira-linux-brand-icon-logo-1200.webp">
  <img alt="Saphira Linux" src="https://raw.githubusercontent.com/SaphiraLinux/brand/main/logos/saphira-linux-brand-icon-light-logo-1200.webp" width="600">
</picture>
```

Two things to know:

- **Always wrap an image in an explicit `<a href>`.** GitHub auto-links a bare
  `<img>` tag to the image's own source, which sends readers to a raw asset
  instead of the page you meant.
- **`prefers-color-scheme` follows the operating system, not the GitHub theme.**
  A reader whose OS is light but whose GitHub theme is dark will get the black
  wordmark on a dark background. There is no way to query the GitHub theme from
  markdown. Most people keep the two in sync; be aware of the mismatch.

## Why the assets live here and not on saphira.vm2.uk

GitHub proxies remote README images through `camo`, and **camo refuses every
AKADATA domain**. Verified 2026-10-04:

| Source | camo verdict |
|---|---|
| `https://saphira.vm2.uk/` | 404 `Cannot proxy the given URL` |
| `https://saphira.vm2.uk/images/saphira-proof-320.webp` | 404 `Cannot proxy the given URL` |
| `https://akadata.ltd/` | 404 `Cannot proxy the given URL` |
| `https://www.akadata.co.uk/` | 404 `Cannot proxy the given URL` |
| `https://packages.akadata.ltd/` | 404 `Cannot proxy the given URL` |
| `https://github.githubassets.com/…` | **200 `image/png`, 7249 bytes** |

It is not a reachability or IPv6 problem. `saphira.vm2.uk` publishes an A record
(217.155.241.55) and an AAAA record (2a02:8012:bc57:c000::b01b) and both answer
200 from an external vantage point. Camo returns **403** for a forged signature
but **404** for these hosts, which means the signatures are valid and camo is
deliberately declining to fetch them — consistent with a domain-level image
proxy block.

`raw.githubusercontent.com` is served directly by GitHub and is **not**
camo-proxied. When GitHub's renderer is given a `raw.githubusercontent.com` URL
it emits it verbatim with no camo wrapper. That is why this repository exists.

There is a second, independent reason to self-host: **camo caches remote images
aggressively and offers no cache-busting mechanism.** A hotlinked logo would
persist on a profile page long after the brand asset changed underneath it.

## Contents

### `logos/` — the Saphira Linux logo

All are 3:1 aspect ratio, transparent background, WebP.

Each family ships at five explicit widths plus one unsized master.

| File | Dimensions |
|---|---|
| `saphira-linux-brand-icon-logo.webp` | 2172 × 724 (master) |
| `saphira-linux-brand-icon-logo-1200.webp` | 1200 × 400 |
| `saphira-linux-brand-icon-logo-960.webp` | 960 × 320 |
| `saphira-linux-brand-icon-logo-640.webp` | 640 × 213 |
| `saphira-linux-brand-icon-logo-480.webp` | 480 × 160 |
| `saphira-linux-brand-icon-logo-320.webp` | 320 × 107 |
| `saphira-linux-brand-icon-light-logo.webp` | 2172 × 724 (master) |
| `saphira-linux-brand-icon-light-logo-1200.webp` | 1200 × 400 |
| `saphira-linux-brand-icon-light-logo-960.webp` | 960 × 320 |
| `saphira-linux-brand-icon-light-logo-640.webp` | 640 × 213 |
| `saphira-linux-brand-icon-light-logo-480.webp` | 480 × 160 |
| `saphira-linux-brand-icon-light-logo-320.webp` | 320 × 107 |

Prefer the explicitly sized variant over the master when you know the target
width. The master is 2172 px wide and 273 KB; the 320 px variant is 7 KB.
Serving the master where 320 px will do costs about thirty-eight times the
bytes for no visible gain.

### `artwork/` — the dragon artwork

Two illustrations, both portrait, both featuring Saphira the dragon and Tux the
penguin. The `-og` files are square crops intended for social previews.

| File | Dimensions | Subject |
|---|---|---|
| `saphira-proof-1122.webp` | 1122 × 1402 | developer with a slate, Saphira, Tux, laptop |
| `saphira-proof-960.webp` | 960 × 1200 | " |
| `saphira-proof-640.webp` | 640 × 800 | " |
| `saphira-proof-480.webp` | 480 × 600 | " |
| `saphira-proof-320.webp` | 320 × 400 | " |
| `saphira-proof-og.webp` | 960 × 960 | square crop |
| `saphira-d-proof-1086.webp` | 1086 × 1448 | developer with the systemd book, Saphira, Tux, laptop |
| `saphira-d-proof-960.webp` | 960 × 1280 | " |
| `saphira-d-proof-640.webp` | 640 × 853 | " |
| `saphira-d-proof-480.webp` | 480 × 640 | " |
| `saphira-d-proof-320.webp` | 320 × 427 | " |
| `saphira-d-proof-og.webp` | 960 × 960 | square crop |

The `-d-` artwork represents **Saphira-d**, the musl + systemd sibling that is
still in development. It is not the primary distribution mark.

### `icons/` — favicons

`favicon.ico`, `apple-touch-icon.png`, `android-chrome-192x192.png`,
`android-chrome-512x512.png`. Identical to the copies served by
`saphira.vm2.uk`.

### `github/` — derived GitHub assets

| File | Dimensions | Use |
|---|---|---|
| `avatar.png` | 512 × 512 | GitHub organisation avatar. Dragon mark on `#0d1117`, derived from the logo. |
| `social-preview.png` | 1280 × 640 | GitHub social preview card. |

Both are derived by cropping and compositing the logo. The avatar is the dragon
region of the logo, trimmed to its alpha bounds and centred on GitHub's dark
canvas colour. Regenerate them if the logo changes rather than re-cropping by
hand.

## Licence

Artwork in this repository is licensed under
[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) — see
[LICENSE](LICENSE). Share and adapt freely, including commercially, with
credit to AKADATA and the Saphira Linux project.

Two limits come from the licence itself and are worth stating plainly:

- **Trademark rights are excluded** (Section 2(b)(2)). The CC BY grant covers
  copyright only.
- **No endorsement** (Section 2(a)(6)). Reusing this artwork does not make you
  affiliated with, sponsored or endorsed by the Saphira Linux project.

**This licence covers artwork only.** AKADATA's Saphira source code is licensed
separately under BSL-1.1, transitioning to GPL-2.0-or-later four years after
each release. Do not assume the artwork licence applies to code.

## Related

- Saphira Linux — <https://saphira.vm2.uk/>
- Organisation profile — <https://github.com/SaphiraLinux>
- Package repository — <https://packages.akadata.ltd/saphira/main/>