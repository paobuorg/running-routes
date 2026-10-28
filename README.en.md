# RunMap · Route content

[中文](README.md) · English

This repository holds the route records, bilingual articles, sources and review data used by the RunMap main site. It is a content-only repository: it has no site runtime code, `package.json`, `node_modules` or build output.

## Status

- The initial 16-route set covers Boston, UTMB, Tokyo, London, Berlin, Chicago, New York, Sydney, Cape Town, Beijing, Shanghai, Western States, Hardrock, Hong Kong 100, Diagonale des Fous and Tor des Géants.
- All 16 routes were **AI-assisted editorially reviewed** and published on 2026-10-28 (`published`, with bilingual `approve` records and matching digests). The reviewer is `runmap-editorial`, explicitly AI-assisted, not independent or professional review. The initial route list is covered 16/16.
- There is no remote repository, public issue tracker or deployed site yet. This repository does not claim professional review.

## Scope

The main site profiles fixed, verifiable editions of classic road marathons and trail ultramarathons. It does not maintain registration, current-year dates, live results, prices or real-time access conditions. A course edition is pinned with `courseVersion` (for example `2024-baa-published-course`); no single year is treated as the permanent route.

## Layout

```text
data/entities/{slug}.json          Shared facts, course version, source refs and geometry rights
data/sources/{sourceId}.json       Sources, locations and the claims they support
data/contributors/{personId}.json  Public author and reviewer identities
data/reviews/{slug}.{locale}.json  Content digest and decision after review
content/zh-CN/{slug}.md            Chinese article and frontmatter
content/en/{slug}.md               English article and frontmatter
assets/                            Redistributable tracks and small assets
```

Entity IDs look like `route:boston`; slugs use lowercase English hyphens. The two languages are paired by `entityId`, and shared facts live only in `data/entities/`.

## Data rules

- Distance and elevation need a locatable source. When elevation is not trustworthy, `elevationGainMeters` stays `null`; it is never set to `0`.
- `mapAnchor` is a globe anchor, not a start point or a full track.
- `geometryAccess` is `redistributable`, `official-link` or `unavailable`. Only `redistributable` geometry may be stored and offered as a download, and it requires a licence, attribution and source.
- A visible route page does not imply permission to redistribute its track. Official pages support fact-checking but do not grant rights to images, logos, GPX files or databases.
- When a source changes, both language versions must be checked again. `reviewedAt` is filled only after a substantive review.

## Local use

The content is read by `site-www` at build time. When the six projects sit in the same parent directory, the build finds this repository automatically; `ROUTES_CONTENT_DIR` can override the path. This repository has no install or build command of its own.

See [site-www](../site-www/README.md) for preview commands. The build validates bilingual pairing, sources, licences, review dates and content digests; a failure blocks publication.

## Licence and corrections

- New article text: CC BY 4.0, attributed to “RunMap 跑地图”.
- Tracks, images and third-party assets: under each source's terms, recorded per entity or source. Material without confirmed rights does not enter the repository.
- Site code: MIT, in the three `site-*` repositories.

Once the repository is hosted, report factual or source problems through an issue or pull request that names the paragraph, source and proposed change. No public issue URL or email address exists yet, and none is invented here. See [CONTRIBUTING.md](CONTRIBUTING.md), whose second half is in English.

Last checked: 2026-10-28.
