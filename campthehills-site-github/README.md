# campthehills.net

The official site of **campthehills** — Campbell Rolston-Clemmer, artist, record producer and samplemaker. From Missoula, Montana; based in Los Angeles.

Two static pages, no build step, no framework, no dependencies. Each page is self-contained: its own inline `<style>` and `<script>`, nothing shared between them.

```
index.html      the site — music, the music video, shows, about, credits, contact
watch.html      short-form clips and the lyric videos
assets/         artwork, photography, video
assets/watch/   the clips and their poster frames
assets/flyers/  past-show flyers
```

`index.html` is a single page. The header jumps to its sections rather than loading anything, and `watch.html` carries the same header so it never reads as a different site.

## Running it locally

Open `index.html` in a browser and it works — with one exception. The YouTube embed on `watch.html` refuses to load from a `file://` page, because there is no origin for it to check; the page detects this and opens the video on youtube.com in a new tab instead.

To see it exactly as it is served, run any static server from the project root:

```
python3 -m http.server 8000
```

then visit `http://localhost:8000`.

## Deploying

Built for **GitHub Pages**. `CNAME` points the site at `campthehills.net` and `.nojekyll` stops Pages from trying to process it as a Jekyll blog. After the first push: **Settings → Pages**, set the source branch, and confirm the custom domain. The DNS records at the registrar have to point at GitHub's Pages IPs before the domain will resolve.

Any static host works equally well — there is nothing to build.

## Two things to configure

- **The contact form** posts nowhere until `BOOK_ENDPOINT` is filled in near the foot of the script in `index.html`. Formspree, Basin and Web3Forms all work; Web3Forms also needs `BOOK_ACCESS_KEY`. Left empty, the form validates and then falls back to opening the visitor's email client, so nothing is broken in the meantime.
- **The mailing list** runs on Laylo, drop id `nK8jU`. The SDK is deliberately not loaded on page load — it is fetched the first time someone actually presses a signup link, so the site makes no third-party requests for anyone who never signs up.

## Privacy

No analytics, no tracking, no cookies, no consent banner. The only third-party request any page makes on load is Google Fonts, for Archivo.

## Credits

Design and development by [Riss Creative Co.](https://risscreativeco.com)
Photography by [Max Durante](https://www.instagram.com/max.dur/)
*down with the snow* directed by [Jaxon Ray](https://youtu.be/s6Ya5daiqHo)
All cover artwork painted by campthehills.

## Rights

© 2026 Campbell Rolston-Clemmer. **This repository is not open source.** The code is published so the site can be served from it. The music, artwork, photography and video are not licensed for reuse, and the cover art appearing on the credits page belongs to the respective labels and artists.
