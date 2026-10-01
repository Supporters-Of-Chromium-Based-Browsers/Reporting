# SOCBB Metadata status updates

## 2026-W38/W39

_Reporting period_: 14 September 2026 – 27 September 2026

### Team Heck B.V.

- Released [v3.39.0](https://github.com/web-platform-dx/web-features/releases/tag/v3.39.0), [v3.40.0](https://github.com/web-platform-dx/web-features/releases/tag/v3.40.0)
- Infrastructure and tools:
  - Switch from Mocha to `node:test` test runner ([#4364](https://github.com/web-platform-dx/web-features/pull/4364))
  - Switch from c8 to Node's built-in coverage reporter ([#4390](https://github.com/web-platform-dx/web-features/pull/4390))
- Statistics generation:
  - `stats.ts`: add commit hash and timestamp to output ([#4346](https://github.com/web-platform-dx/web-features/pull/4346))
  - Statistics: generate a markdown report from `stats.ts` ([#4294](https://github.com/web-platform-dx/web-features/pull/4294))
  - Statistics: add GitHub Actions workflow ([#4295](https://github.com/web-platform-dx/web-features/pull/4295))
  - `stats-report.ts`: improve date and commit range formatting ([#4395](https://github.com/web-platform-dx/web-features/pull/4395))
  - `stats-report.ts`: fix typo in comparison URL ([#4401](https://github.com/web-platform-dx/web-features/pull/4401))
  - Statistics: post stats weekly ([#4396](https://github.com/web-platform-dx/web-features/pull/4396))
  - `stats-report.ts`: fix incorrect change in total caniuse IDs ([#4419](https://github.com/web-platform-dx/web-features/pull/4419))
- Added and revised feature entries
  - Revise performance timing entries' names and descriptions ([#4278](https://github.com/web-platform-dx/web-features/pull/4278))
  - Add `initialPermissionStatus` discouraged feature ([#4365](https://github.com/web-platform-dx/web-features/pull/4365))
  - `import-defer`: include `import.defer()` as part of this feature ([#4385](https://github.com/web-platform-dx/web-features/pull/4385))
  - Add `named-feature()` feature ([#4272](https://github.com/web-platform-dx/web-features/pull/4272))
  - `uint8array-base64-hex`: revise description ([#4254](https://github.com/web-platform-dx/web-features/pull/4254))
  - Add discouraged feature for `trimLeft()` and `trimRight()` ([#4386](https://github.com/web-platform-dx/web-features/pull/4386))
  - Disambiguate container size queries feature ([#4310](https://github.com/web-platform-dx/web-features/pull/4310))
  - Add name-only container queries feature ([#4311](https://github.com/web-platform-dx/web-features/pull/4311))
  - `symbols()` CSS function: revise ID and description ([#4400](https://github.com/web-platform-dx/web-features/pull/4400))
  - Add gamut mapping feature ([#4392](https://github.com/web-platform-dx/web-features/pull/4392))
  - Add feature for `Iterator.prototype.join()` ([#4403](https://github.com/web-platform-dx/web-features/pull/4403))
- Grouped feature entries
  - Add an `anchor-positioning` group ([#4313](https://github.com/web-platform-dx/web-features/pull/4313))
  - Group more CSS text features ([#4407](https://github.com/web-platform-dx/web-features/pull/4407))
- Backfilled compat keys:
  - `select`: add `HTMLOptionsCollection` compat keys ([#4367](https://github.com/web-platform-dx/web-features/pull/4367))
  - `outline`: assign `auto` value compat key ([#4408](https://github.com/web-platform-dx/web-features/pull/4408))
  - `background-position`: backfill compat keys ([#4414](https://github.com/web-platform-dx/web-features/pull/4414))
  - `clip-path`: backfill `none` value compat key ([#4416](https://github.com/web-platform-dx/web-features/pull/4416))
  - `font-size`: backfill keyword values compat keys ([#4417](https://github.com/web-platform-dx/web-features/pull/4417))
  - `text-shadow`: backfill `none` value compat key ([#4409](https://github.com/web-platform-dx/web-features/pull/4409))
  - `pointer-events`: backfill compat keys ([#4411](https://github.com/web-platform-dx/web-features/pull/4411))
  - `svg`: backfill compat keys ([#4412](https://github.com/web-platform-dx/web-features/pull/4412))
- Browser compat data:
  - `api.HTMLGeolocationElement.initialPermissionStatus`: mark as deprecated ([#30519](https://github.com/mdn/browser-compat-data/pull/30519))
  - `javascript.builtins.String.trimStart` and `trimEnd`: break out `trim{Left,Right}` ([#30520](https://github.com/mdn/browser-compat-data/pull/30520))
  - Unmark `css.selectors.-webkit-meter-bar` as deprecated ([#30610](https://github.com/mdn/browser-compat-data/pull/30610))
  - `api.MouseEvent.layer{X,Y}`: add spec URLs and mark as standard ([#30651](https://github.com/mdn/browser-compat-data/pull/30651))
  - Add guideline for handling A/B tests and feature rollouts ([#30486](https://github.com/mdn/browser-compat-data/pull/30486))
- Noteworthy reviews:
  - Add feature for extended-lifetime shared workers ([#4341](https://github.com/web-platform-dx/web-features/pull/4341)) by @jgraham
  - Add caniuse links where the IDs are different ([#3301](https://github.com/web-platform-dx/web-features/pull/3301)) by @foolip
  - Split out type=week|month input types from input-date-time ([#4371](https://github.com/web-platform-dx/web-features/pull/4371)) by @jgraham
  - Update webdriver-bidi with the new BCD keys ([#2777](https://github.com/web-platform-dx/web-features/pull/2777)) by @captainbrosset
  - Add HTML setters features ([#4318](https://github.com/web-platform-dx/web-features/pull/4318)) by @tunetheweb
  - Make CSS animatable data consistent (https://github.com/mdn/browser-compat-data/pull/30417) by @chrisdavidmills
  - Remove partial_implementation from ariaNotify() for Chromium ([#30571](https://github.com/mdn/browser-compat-data/pull/30571)) by @captainbrosset
  - fix(lint): apply link replacements at exact offsets ([#30657](https://github.com/mdn/browser-compat-data/pull/30657)) by @caugner

## 2026-W36/W37

_Reporting period_: 31 August 2026 – 13 September 2026

### Team Heck B.V.

- Releases: [v3.36.0](https://github.com/web-platform-dx/web-features/releases/tag/v3.36.0), [v3.37.0](https://github.com/web-platform-dx/web-features/releases/tag/v3.37.0), [v3.38.0](https://github.com/web-platform-dx/web-features/releases/tag/v3.38.0)
- Added responsive iframes feature ([#4077](https://github.com/web-platform-dx/web-features/pull/4077))
- Reviewed `<template for>` (out of order patching) feature ([#4265](https://github.com/web-platform-dx/web-features/pull/4265))
- Added anchor positioning animations and transitions feature ([#4270](https://github.com/web-platform-dx/web-features/pull/4270))
- Added `window-drag` feature ([#4273](https://github.com/web-platform-dx/web-features/pull/4273))
- Added `flex-wrap: balance` feature ([#4274](https://github.com/web-platform-dx/web-features/pull/4274))
- Added `alpha()` CSS function feature ([#4275](https://github.com/web-platform-dx/web-features/pull/4275))
- Marked `xslt` as discouraged ([#4271](https://github.com/web-platform-dx/web-features/pull/4271))
- Fixed bugs and did table setting for statistics generation ([#4281](https://github.com/web-platform-dx/web-features/pull/4281), [#4289](https://github.com/web-platform-dx/web-features/pull/4289), [#4290](https://github.com/web-platform-dx/web-features/pull/4290), [#4291](https://github.com/web-platform-dx/web-features/pull/4291), [#4291](https://github.com/web-platform-dx/web-features/pull/4291))
- Filed ten issues to create new feature entries for things not yet tracked, but where certain data consumers (see [#4287](https://github.com/web-platform-dx/web-features/issues/4287 "web-features consumers report for 2026-09-01")) are expecting them to exist already ([#4302](https://github.com/web-platform-dx/web-features/issues/4302 "Iterator Includes"), [#4303](https://github.com/web-platform-dx/web-features/issues/4303 "Import Bytes (Bytes Modules)"), [#4304](https://github.com/web-platform-dx/web-features/issues/4304 "Iterator Join"), [#4305](https://github.com/web-platform-dx/web-features/issues/4305 "`initialPermissionStatus` (discouraged feature)"), [#4306](https://github.com/web-platform-dx/web-features/issues/4306 "`CSSPseudoElement`"), [#4307](https://github.com/web-platform-dx/web-features/issues/4307 "`path-length` CSS property"), [#4308](https://github.com/web-platform-dx/web-features/issues/4308 "`Iterator.zip()` and `zipKeyed()` (joint iteration)"), [#4309](https://github.com/web-platform-dx/web-features/issues/4309 "Web Haptics (API)"), [#4324](https://github.com/web-platform-dx/web-features/issues/4324 "`trimLeft` and `trimRight` (discouraged)"), [#4325](https://github.com/web-platform-dx/web-features/issues/4325 "`substr()` string method (discouraged)")).
- Added `import defer` JavaScript proposal data ([mdn/browser-compat-data#30425](https://github.com/mdn/browser-compat-data/pull/30425))
- Unblocked `attr()`'s status block on `<url>` type ([#4334](https://github.com/web-platform-dx/web-features/pull/4334))
- Added `container-anchor-position-queries` to `container-queries` group ([#4312](https://github.com/web-platform-dx/web-features/pull/4312))

## 2026-W34/35

_Reporting period_: 17 August 2026 – 28 August 2026

### Team Heck B.V.

- Releases: [web-features@v3.35.0](https://github.com/web-platform-dx/web-features/releases/tag/v3.35.0), [web-features@v3.35.1](https://github.com/web-platform-dx/web-features/releases/tag/v3.35.1)
- Updated stats script ([#4030](https://github.com/web-platform-dx/web-features/pull/4030 "web-platform-dx/web-features#4030"))
- `fencedframe`: marked privacy sandbox as discouraged, pending removal ([#4260](https://github.com/web-platform-dx/web-features/pull/4260 "web-platform-dx/web-features#4260"))
- Added stats to release artifacts ([#4264](https://github.com/web-platform-dx/web-features/pull/4264 "web-platform-dx/web-features#4264"))
- Discovered and fixed a bug in the BCD release notes with Florian ([mdn/browser-compat-data#30299](https://github.com/mdn/browser-compat-data/pull/30299 "Exclude &quot;next&quot; tags in release notes script"), [mdn/browser-compat-data#30298](https://github.com/mdn/browser-compat-data/pull/30298 "Don&#x27;t use `next` as basis for generating regular releases"))

## 2026-W32/33

_Reporting period_: 3 August 2026 – 14 August 2026

### Team Heck B.V.

- Releases: [web-features@v3.34.3](https://github.com/web-platform-dx/web-features/releases/tag/v3.34.3)
- Added a discouraged `anchors-valid` and `anchors-visible` feature ([#4227](https://github.com/web-platform-dx/web-features/pull/4227 "web-platform-dx/web-features#4227"))
