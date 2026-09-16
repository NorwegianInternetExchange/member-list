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

## Embed

```html
<iframe src="https://norwegianinternetexchange.github.io/member-list/"
        style="width:100%;height:900px;border:0"
        title="Networks connected to NIX" loading="lazy"></iframe>
```
