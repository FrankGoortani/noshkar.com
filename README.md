# noshkar.com

Landing page for **Noshkār** (نشخوار) — a modern Persian brand built around the idea of *rumination as transformation*. Music, podcast, and ideas at the intersection of AI, philosophy, and creative synthesis.

Deployed via **GitHub Pages** to [noshkar.com](https://noshkar.com).

---

## Structure

```
├── index.html           # landing page (hero, album teaser, singles grid)
├── nimeh-khab/          # album page + per-song lyric pages
├── moohat/              # single · نشخوار 013
├── roshan-bemoon/       # single · نشخوار 014
├── baghlavayi/          # single · نشخوار 015
├── laate-kooche-khalvat/ # single · نشخوار 016
├── nakoneh-pir-beshim/  # single · نشخوار 017
├── starlight/           # single · نشخوار 018
├── styles/main.css      # brand tokens + layout
├── assets/noshkar.png   # primary ouroboros mark (also used for favicon / OG)
├── assets/singles/      # single cover art (480 / 1200 jpg)
├── assets/nimeh-khab/   # album cover art
├── CNAME                # tells GitHub Pages the custom domain
├── .nojekyll            # disables Jekyll processing (serves files as-is)
└── LICENSE              # MIT (code); brand marks reserved
```

Each single page is self-contained static HTML: cover art, catalog number,
Persian + Latin title, SoundCloud/YouTube links, and the full lyric in RTL.

The brand system, guidelines, and design tokens live in a separate private repo: `noshkhar` (project deck). This repo holds only the public-facing landing implementation.

---

## Local preview

No build step. Any static server works:

```bash
# python
python3 -m http.server 8080

# or node
npx --yes serve -l 8080 .
```

Open <http://localhost:8080>.

---

## Deploy

Pushes to `main` auto-deploy via GitHub Pages.

### DNS (GoDaddy → GitHub Pages)

Configure these records at GoDaddy for `noshkar.com`:

**Apex A records** (point `noshkar.com` at GitHub's servers):

| Type | Host | Value           | TTL |
|------|------|-----------------|-----|
| A    | @    | 185.199.108.153 | 600 |
| A    | @    | 185.199.109.153 | 600 |
| A    | @    | 185.199.110.153 | 600 |
| A    | @    | 185.199.111.153 | 600 |

**AAAA records** (IPv6, optional but recommended):

| Type | Host | Value                        | TTL |
|------|------|------------------------------|-----|
| AAAA | @    | 2606:50c0:8000::153          | 600 |
| AAAA | @    | 2606:50c0:8001::153          | 600 |
| AAAA | @    | 2606:50c0:8002::153          | 600 |
| AAAA | @    | 2606:50c0:8003::153          | 600 |

**CNAME for www subdomain:**

| Type  | Host | Value                      | TTL |
|-------|------|----------------------------|-----|
| CNAME | www  | frankgoortani.github.io.   | 600 |

**Remove** any parked / forwarding records GoDaddy added by default (they interfere).

### GitHub Pages settings

In the repo, go to `Settings → Pages`:

1. Source: `Deploy from a branch`
2. Branch: `main` / `root`
3. Custom domain: `noshkar.com`
4. Enforce HTTPS: on (enable after DNS verifies — usually within an hour)

The `CNAME` file in this repo already tells Pages about the custom domain; the settings UI is the mirror of that file.

---

## Attribution

[GetSongBPM](https://getsongbpm.com) — BPM and key data. Required attribution per their API terms.

---

## License

MIT for code. See `LICENSE`. Brand assets (logo, wordmark نشخوار / Noshkār) are not covered by the MIT license and remain reserved.
