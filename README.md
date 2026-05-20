# Edgeless OTel Plugin Registry

The community index for [Edgeless OTel Command](https://github.com/thedavidmurray/edgeless-otel-command) plug-ins.

The app fetches `plugins.json` from this repo to populate its "Browse Plug-ins" UI. Plug-ins themselves live in their own repos and ship via GitHub Releases — this registry is just a flat list pointing at them.

## What is a plug-in?

A folder with a `manifest.json` and `index.js` that extends Edgeless OTel Command. Plug-ins can register:
- **Panels** — new visualizations on the dashboard
- **Anomaly rules** — custom detectors that fire alerts
- **Themes** — visual reskins

Read the [plug-in development guide](https://github.com/thedavidmurray/edgeless-otel-command/blob/main/PLUGINS.md).

## How to submit your plug-in

1. Build your plug-in. The [example](https://github.com/thedavidmurray/edgeless-plugin-example) is a working starting point.
2. Publish it to a public GitHub repo. Cut at least one release (`gh release create v0.1.0 plugin.zip` or attach the source as a tag).
3. Fork this registry.
4. Add an entry to `plugins.json`:
   ```json
   {
     "id": "yourorg.plugin.coolthing",
     "name": "Cool Thing",
     "description": "One-line summary of what it does.",
     "author": "yourorg",
     "repo": "yourorg/edgeless-plugin-coolthing",
     "latestVersion": "0.1.0",
     "minAppVersion": "1.2.0",
     "tags": ["panel", "your-category"],
     "license": "MIT",
     "homepage": "https://github.com/yourorg/edgeless-plugin-coolthing",
     "screenshot": "https://raw.githubusercontent.com/yourorg/edgeless-plugin-coolthing/main/screenshot.png"
   }
   ```
5. Bump `lastUpdated`.
6. Open a PR. We'll review and merge.

## Review criteria

Submissions are accepted if:

- `manifest.json` is valid and `id` matches your namespace
- The plug-in does what its description says (we install it and check)
- License is permissive (MIT, Apache 2.0, BSD, ISC)
- No obfuscated or minified code in `index.js` (so users can audit it)
- No outbound HTTP unless declared in the description (this becomes mandatory in v2 via a `permissions` field)
- Reasonable name and description — no SEO spam, no copy of an existing plug-in

We do not host plug-in binaries here. Each plug-in is downloaded from its own GitHub repo at install time.

## Versioning

The registry index is versioned (`"version": 1` at the top of `plugins.json`). If we need a breaking change to the format we'll bump it and the app will negotiate. Individual plug-in versions follow semver and are tracked in the `latestVersion` field.

## Found a malicious or broken plug-in?

Open an issue here with `[REMOVE]` in the title. We'll investigate within 48h and pull it from the index if confirmed. The plug-in's own repo isn't ours to take down, but it stops being discoverable.

## License

The registry index itself is MIT. Individual plug-ins carry their own licenses (declared in each manifest).
