# Aranim Assets

Puzzle artwork for the [Aranim](https://github.com/anggastudio/aranim) game,
hosted here so the app can stream pictures on demand instead of bundling all of
them in the APK/IPA.

- `images/` - the puzzle pictures (`puzzle_001.png` .. `puzzle_100.png`), 512x512.
- `manifest.json` - version, count, CDN base URL, and the image file list.

## How the app uses these

The app ships a small starter pack inside the build (so it works offline from
the first launch) and downloads the rest from jsDelivr, caching each image on
device after the first fetch:

```
https://cdn.jsdelivr.net/gh/anggastudio/aranim-assets@main/images/puzzle_050.png
```

jsDelivr is a free public CDN that serves any public GitHub repo. No account or
configuration is required.

## Adding more pictures

1. Generate new images with `tool/generate_images.py` in the main repo.
2. Copy them here, update `manifest.json` (`count` + `images`), commit, push.
3. New `@main` URLs go live after jsDelivr's cache TTL (up to ~12h). For an
   instant, permanently-cached release, tag a version (e.g. `v2`) and point the
   app's CDN base at `@v2`.

These images are generated, royalty-free, and may be reused freely.
