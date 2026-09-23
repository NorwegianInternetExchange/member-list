# NIX member list

Live list of networks connected to the Norwegian Internet Exchange, built from
NIX's own IX-F Member Export and rendered client-side. Published via GitHub Pages
and embedded on nix.no ("Who is connected") through an `<iframe>`.

## How it works

`index.html` is fully self-contained (no build step, no dependencies). On load it
fetches the IX-F Member Export from NIX's IXP Manager instances and renders one
table per exchange (one row per network, IPs and capacity aggregated).

Data sources are configured at the top of the `<script>` block in `index.html`:

- `portal.nix.no` (IXP Manager v7) — NIX1, TIX
- `portal-old.nix.no` (IXP Manager v5.7) — NIX2, BIX, SIX, TRDIX

As exchanges are migrated to the new portal, move their shortname from the
old-portal `only:` list to the new-portal one.

## MANRS participation

Networks that participate in [MANRS](https://www.manrs.org/) are marked with a
badge next to their name, and the count is summarised above the tables. This is
what the MANRS IXP Programme calls Action 2-3 ("Promote").

The ASN list comes from `https://api.manrs.org/asns`, but that endpoint sends no
`Access-Control-Allow-Origin` header, so the page cannot fetch it from the
browser. `.github/workflows/update-manrs.yml` mirrors it into `manrs.json` once a
day (and on demand via *Run workflow*), committing only when the list actually
changes. The page then loads `manrs.json` same-origin.

If `manrs.json` is missing or fails to load the tables still render — the badges
and the summary line are simply omitted.

## Embed

```html
<iframe src="https://norwegianinternetexchange.github.io/member-list/"
        style="width:100%;height:900px;border:0"
        title="Networks connected to NIX" loading="lazy"></iframe>
```
