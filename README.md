# Url Shortener — Mobile

> **Template copy.** This repo is one of the name-substituted Expo SDK 53 / Expo Router
> template copies in `bookchaowalit-mobile`. The canonical template is
> [`bookchaowalit-mobile/community-hub-mobile`](https://github.com/bookchaowalit-mobile/community-hub-mobile);
> this copy keeps its own code (no shared package). Consolidation/archive is pending
> owner decision D5 (BD-033) per `repository-catalog/portfolio/MOBILE-CONSOLIDATION-2026-10.md`
> in solo-empire.

React Native mobile app (Expo) for **Url Shortener**.

Part of [Chaowalit Greepoke](https://bookchaowalit.com)'s 101 Portfolio Projects.

## Features

- **Link shortener** (Links tab): paste a URL (scheme optional) and get a short
  code — a deterministic 6-character base62 hash, or your own alias. Only
  http(s) URLs are accepted (`javascript:`/`data:` and credentialed URLs are
  rejected), duplicates are reused, and alias clashes are reported. Each link
  can be opened (counted as a click) or shared. Links are in-memory for now and
  the `bkc.link` domain is a display placeholder until the redirect backend exists.
- Shortener logic lives in `lib/shortener.ts` (pure TypeScript, unit-tested).

## Tech Stack

- **Framework:** Expo SDK 53 + Expo Router
- **Language:** TypeScript
- **Navigation:** Expo Router (file-based)
- **UI:** React Native + Ionicons

## Getting Started

```bash
npm install
npx expo start
```

## Scripts

```bash
npm run typecheck   # tsc --noEmit
npm run lint        # expo lint (eslint-config-expo)
npm test            # vitest unit tests for lib/
npx expo export --platform android --output-dir dist   # JS bundle smoke check
```

CI (`.github/workflows/ci.yml`) calls the shared `bookchaowalit/platform-ci-workflows`
`ci-node.yml` and `security.yml` (v1.1.1, SHA-pinned): `npm ci`, lint, typecheck, tests,
the Android JS bundle export above, plus Gitleaks, Semgrep, OSV-Scanner and Trivy.
Failures are not masked. There is no EAS / Expo cloud build in CI: that needs an
owner-linked Expo account (owner action).

## Build

```bash
# Android
npx eas build --platform android --profile preview

# iOS
npx eas build --platform ios --profile preview
```

## Related

- **Frontend:** [bookchaowalit-website/url-shortener-frontend](https://github.com/bookchaowalit-website/url-shortener-frontend)
- **Portfolio:** [bookchaowalit.com](https://bookchaowalit.com)

## License

MIT
