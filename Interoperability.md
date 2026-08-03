# SOCBB Interop Igalia Status Updates

## Jul 16, 2026 – Jul 30, 2026 (Weeks 29–30)

* **Scope:** Improving standards compliance and resolving interoperability issues across CSS features.

### Summary
Normalizing IIRFilter coefficients in double precision for WebAudio and painting `::marker` symbols with `-webkit-text-fill-color` for `css-lists` were both merged. Work began on making blob URLs opaque when they have a non-http/https/file inner scheme, and the work for preserving invalid selectors in `:is()` and `:where()` is under review alongside a related CSSWG spec discussion.

### Topics & Tasks

#### Preserving Invalid Selectors in `:is()` and `:where()`
* Update `CSSSelector`, `CSSSelectorList`, and `CSSSelectorParser` so invalid selectors in forgiving selector lists can be serialized instead of dropped.
* **Standard Discussion:** [CSSWG Drafts Issue 8356](https://github.com/w3c/csswg-drafts/issues/8356) ([Comment](https://github.com/w3c/csswg-drafts/issues/8356#issuecomment-5042919620)). Needs spec edit to close issue.
* **CLs:**
  * **[ REVIEW ]** Preserve invalid selectors in `:is()` and `:where()` (Got +1, needs fix-up): [Chromium CL 8068106](https://crrev.com/c/8068106)
  * **[ REVIEW ]** Fix-up: [Chromium CL 8061514](https://crrev.com/c/8061514)

#### Make Blob URL Opaque When Inner Scheme is Non-http/https/file
* Apply blob URL rule from the [URL Specification](https://url.spec.whatwg.org/#origin) using inner origin as origin when inner scheme is `http`, `https`, or `file`.
* **Explainer:** [Blob URL Opaque Origin Explainer](https://github.com/Igalia/explainers/tree/main/blob-url-opaque-origin)
* **Feature & Intent:** [Chrome Status Feature](https://chromestatus.com/feature/5079000453087232) | [Intent to Prototype](https://groups.google.com/a/chromium.org/g/blink-dev/c/mS87yfDEzxU)
* **CLs:**
  * **[ REVIEW ]** [Chromium CL 8090107](https://crrev.com/c/8090107)
* > **Note:** The CL fixes behavior of both `url::Origin` and `blink::SecurityOrigin` behind two separate flags (a base feature in `url/url_features` and an experimental runtime feature in Blink). While states can theoretically diverge until enabled by default, this does not block the CL as it introduces no regressions.

#### URL Host Parsing
* Incorrect asterisk (`*`) escaping while parsing URL host: Identified issue and exploring feasible solutions.
  * **[ WIP ]** [Chromium CL 8116847](https://crrev.com/c/8116847)

#### WebAudio IIRFilter Coefficients
* **[ MERGED ]** WebAudio, Normalize IIRFilter coefficients in double precision: [Chromium CL 8082300](https://chromium-review.googlesource.com/c/chromium/src/+/8082300)

#### `css-lists` Marker Symbols
* **[ MERGED ]** Paint `::marker` symbols with `-webkit-text-fill-color`: [Chromium CL 8083120](https://chromium-review.googlesource.com/c/chromium/src/+/8083120)

#### Namespaces in `attr()`
* **[ IN PROGRESS ]** Support namespaces in `attr()` (Large change, working on reviewer feedback): [Chromium CL 7931006](https://chromium-review.googlesource.com/c/chromium/src/+/7931006)

#### CSS Typed OM Interop Issues
* **[ REVIEW ]** Export `CSSStyleValue` hierarchy to Workers: [Chromium CL 8085260](https://chromium-review.googlesource.com/c/chromium/src/+/8085260)
  * Submitted WPT PR to adapt current window-only tests to `any.js` format: [WPT PR 61330](https://github.com/web-platform-tests/wpt/pull/61330/)
  * Preparing [Intent to Ship](https://chromestatus.com/feature/5114591051907072) as requested by reviewer.
* **[ MERGED ]** Interop failures related to `cssmath-serialization`: [Chromium CL 8085260](https://chromium-review.googlesource.com/c/chromium/src/+/8085260)
* **[ WIP ]** Investigate `calc` expression simplification when serializing `CSSMathValues`.
* **[ MERGED ]** Wrapping out-of-range values into `CSSMathValues` issue: [Chromium CL 8085614](https://chromium-review.googlesource.com/c/chromium/src/+/8085614)
* **[ ANALYSIS ]** Allow custom-ident values in `StylePropertyMap.set` method: Preliminary analysis ([Chrome Bug 40682424](https://issues.chromium.org/issues/40682424)). WebKit has supported this since [Safari Technology Preview 161](https://developer.apple.com/documentation/safari-technology-preview-release-notes/stp-release-161).

#### CSS Background Interop Issues
* **[ MERGED ]** Avoid collapsing `background-size` shorthand values unless both are `auto`: [Chromium CL 8034084](https://chromium-review.googlesource.com/c/chromium/src/+/8034084)

---

## Jul 2, 2026 – Jul 16, 2026 (Weeks 27–28)

* **Scope:** Improving standards compliance and resolving interoperability issues across CSS features.
* **Spreadsheet:** [Tracking Sheet](https://docs.google.com/spreadsheets/d/1V-dIz78giXXi1VhC6ScbO8Qi716EOHl5XlofQDG6-jM/)

### Summary
There was work in many areas related to interop over the last two weeks. Of highlight, implementing `shadowrootslotassignment` for declarative shadow roots was merged, we began investigating a new regression related to CSS Typed OM, a few MediaSource issues were merged, and the work for preserving invalid selectors in `:is()` and `:where()` is under review.

### Topics & Tasks

#### Declarative Shadow Roots (`shadowrootslotassignment`)
* **[ MERGED ]** Implement `shadowrootslotassignment` for declarative shadow roots
  * [Chromium CL 7893946](https://chromium-review.googlesource.com/c/chromium/src/+/7893946)
  * [Intent to Ship](https://chromestatus.com/feature/5178682139344896)

#### Namespaces in `attr()`
* **[ IN PROGRESS ]** Support namespaces in `attr()`
  * Large change, reviewer had a lot of feedback, working on it.
  * [Chromium CL 7931006](https://chromium-review.googlesource.com/c/chromium/src/+/7931006)

#### Editing / Run Interop Issues
* Continue working on the editing/run interop issues: [WPT Results](https://wpt.fyi/results/editing/run?label=master&max-count=2&aligned&view=test&q=seq%28status%3A%21pass%20status%3A%21pass%20status%3A%21pass%20status%3A%21pass%20status%3Apass%20status%3Apass%20status%3Apass%20status%3Apass%29)
* Completed the analysis, but we don't think it's worth continuing work on these issues. Most of the tests are focused on the `execCommand` spec, which is no longer pursued by any major browser engine.

#### Service Worker Interop Issues
* Continue working on Service Worker interop issues: [WPT Results](https://wpt.fyi/results/service-workers?label=master&label=experimental&aligned&q=chrome%3A%21PASS%20edge%3A%21PASS%20firefox%3APASS%20safari%3APASS%20none%28is%3Atentative%29%20none%28is%3Aoptional%29%20%21path%3A%2Fthird_party%2F%20idl)
* Completed analysis, but not sure the task fits into the project's scope.
* Issues are already tracked in [Chrome Bug 422940475](https://issues.chromium.org/issues/422940475) and [Chrome Bug 40364838](https://issues.chromium.org/issues/40364838) (Microsoft engineers appear to be working on 40364838).

#### CSS Background Interop Issues
* Triage additional interop issues in CSS Background test suite.
* **[ REVIEW ]** Avoid collapsing background-size shorthand values unless both are `auto`: [Chromium CL 8034084](https://chromium-review.googlesource.com/c/chromium/src/+/8034084)

#### CSS Typed OM Regression
* Investigating a new regression in CSS Typed OM related folders:
  * **[ MERGED ]** Wrap out-of-range values into a `CSSMathSum` value: [Chromium CL 8024972](https://chromium-review.googlesource.com/c/chromium/src/+/8024972)
  * **[ MERGED ]** Extending Typed OM support to other properties and values: [Chromium CL 8035200](https://chromium-review.googlesource.com/c/chromium/src/+/8035200)
  * **[ WIP ]** The `CSSPositionValue` CSSOM interface should not be exposed: [Chromium CL 8032682](https://chromium-review.googlesource.com/c/chromium/src/+/8032682) | [Chrome Bug 530292679](https://issues.chromium.org/issues/530292679)
  * Core CSS Typed OM interfaces not exposed in Worker context: Preliminary analysis.

#### MediaSource Interop Issues
* **[ MERGED ]** The `activeCue` attribute should return an empty list if no cue is available: [Chromium CL 8004691](https://chromium-review.googlesource.com/c/chromium/src/+/8004691)
* **[ MERGED ]** Automatic text track selection task is not fired at the right moment: [Chromium CL 8005418](https://chromium-review.googlesource.com/c/chromium/src/+/8005418)
* **[ WIP ]** Autoplay hidden is ignored despite `kHiddenAttr` value: [Chromium CL 8008308](https://chromium-review.googlesource.com/c/chromium/src/+/8008308)
* **[ WIP ]** `HTMLTrackElement` should not allow percent-encoded URLs: [Chromium CL 8008327](https://chromium-review.googlesource.com/c/chromium/src/+/8008327)

#### Preserving Invalid Selectors in `:is()` and `:where()`
* Investigate and prepare fix for preserving invalid selectors in `:is()` and `:where()` (updating `CSSSelector`, `CSSSelectorList`, and `CSSSelectorParser` so invalid selectors in forgiving selector list are serialized instead of dropped).
  * **[ MERGED ]** Remove an unnecessary parameter from `ConsumeComplexSelector()`: [Chromium CL 8062612](https://crrev.com/c/8062612)
  * **[ REVIEW ]** Preserve invalid selectors in `:is()` and `:where()`: [Chromium CL 8068106](https://crrev.com/c/8068106)
  * **[ REVIEW ]** Fix silent column combinator parsing failure: [Chromium CL 8061514](https://crrev.com/c/8061514)

#### Pseudo-element Styles Using Sibling Functions
* **[ MERGED ]** Invalidate pseudo-element styles that use sibling functions: [Chromium CL 8028283](https://chromium-review.googlesource.com/c/chromium/src/+/8028283)

#### WebAudio IIRFilter Coefficients
* **[ REVIEW ]** WebAudio, Normalize IIRFilter coefficients in double precision: [Chromium CL 8082300](https://chromium-review.googlesource.com/c/chromium/src/+/8082300)

#### `css-lists` Marker Symbols
* **[ REVIEW ]** css-lists, Paint `::marker` symbols with `-webkit-text-fill-color`: [Chromium CL 8083120](https://chromium-review.googlesource.com/c/chromium/src/+/8083120)

---

## Jun 18, 2026 – Jul 2, 2026 (Weeks 25–26)

* **Scope:** Improving standards compliance and resolving interoperability issues across CSS features.
* **Spreadsheet:** [Tracking Sheet](https://docs.google.com/spreadsheets/d/1fn72b6g14VbI4G48NXWLf6qHmOM4dcRkF6J41s1nAVo/)

### Summary
Continued work across declarative shadow roots, supporting namespaces in `attr()`, MediaSource element interop issues, and began investigating Service Worker and Dedicated/Shared Worker issues.

### Topics & Tasks

* **Declarative Shadow Roots (`shadowrootslotassignment`)**
  * **[ UNDER REVIEW ]** Implement `shadowrootslotassignment` for declarative shadow roots. Code approved, requires Intent to Ship: [Chromium CL 7893946](https://chromium-review.googlesource.com/c/chromium/src/+/7893946) | [Intent to Ship](https://chromestatus.com/feature/5178682139344896)
* **Namespaces in `attr()`**
  * **[ IN PROGRESS ]** Support namespaces in `attr()`: [Chromium CL 7931006](https://chromium-review.googlesource.com/c/chromium/src/+/7931006)
* **MediaSource Element Interop Issues**
  * **[ MERGED ]** Issues in text track ordering due to errors in `activeCue` logic: [Chromium CL 8004691](https://chromium-review.googlesource.com/c/chromium/src/+/8004691)
  * **[ REVIEW ]** Issues in text track selection: [Chromium CL 8005418](https://chromium-review.googlesource.com/c/chromium/src/+/8005418)
  * **[ WIP ]** Autoplay hidden capabilities buggy (fixes `autoplay-hidden.optional.html`): [Chromium CL 8008308](https://chromium-review.googlesource.com/c/chromium/src/+/8008308)
  * **[ WIP ]** `HTMLTrackElement` should not allow percent-encoded URLs: [Chromium CL 8008327](https://chromium-review.googlesource.com/c/chromium/src/+/8008327)
* **Service Worker & Dedicated/Shared Worker Issues**
  * Initial investigation. Microsoft team working on [Chrome Bug 40364838](https://issues.chromium.org/issues/40364838). Work is incomplete and requires WPT refactoring; might be outside current project scope.

---

## Jun 3, 2026 – Jun 18, 2026 (Weeks 23–24)

* **Scope:** Improving standards compliance and resolving interoperability issues across CSS features.
* **Spreadsheet:** [Tracking Sheet](https://docs.google.com/spreadsheets/d/1fn72b6g14VbI4G48NXWLf6qHmOM4dcRkF6J41s1nAVo/)

### Summary
Continued work across several areas, with many issues under review now merged.

### Topics & Tasks

* **Editing**
  * Avoid special metadata tags removal when part of editing content: **[ REVIEW ]** [Chromium CL 7793251](https://chromium-review.googlesource.com/c/chromium/src/+/7793251)
  * Failures in `editing/run`: Initial triage on `justify*` commands algorithm and `italic` command offsets.
  * Preserve white-space style when joining blocks in `contenteditable`: **[ WIP ]** [Chromium CL 7588233](https://chromium-review.googlesource.com/c/chromium/src/+/7588233) | [Chrome Bug 40869970](https://issues.chromium.org/40869970)
* **WebCrypto Operations**
  * **[ MERGED ]** Fix bug in normalization steps of WebCrypto operations: [Chromium CL 791650](https://chromium-review.googlesource.com/c/chromium/src/+/791650)
* **Media Source**
  * **[ MERGED ]** Media source interop fix: [Chromium CL 7828889](https://chromium-review.googlesource.com/c/chromium/src/+/7828889)
* **`autocorrect` Attribute**
  * **[ REVIEW ]** [Chromium CL 7075071](https://chromium-review.googlesource.com/c/chromium/src/+/7075071)
  * **[ REVIEW ]** [Chromium CL 7902322](https://chromium-review.googlesource.com/c/chromium/src/+/7902322)
* **Italic vs. Oblique**
  * **[ MERGED ]** Distinguish italic, oblique, and oblique 14deg in computed `font-style`: [Chromium CL 7771471](https://chromium-review.googlesource.com/c/chromium/src/+/7771471)
  * **[ MERGED ]** Carry `font-style` syntax through animations and transitions: [Chromium CL 7885309](https://chromium-review.googlesource.com/c/chromium/src/+/7885309)
* **`:in-range` and `:out-of-range`**
  * **[ MERGED ]** Invalidate `:in-range` / `:out-of-range` when input `readonly` changes: [Chromium CL 7925491](https://chromium-review.googlesource.com/c/chromium/src/+/7925491)
  * **[ MERGED ]** Fix `:in-range` and `:out-of-range` for reversed time ranges: [Chromium CL 7895742](https://chromium-review.googlesource.com/c/chromium/src/+/7895742)
* **Qualified Names**
  * **[ MERGED ]** [DOM] Split qualified names on the first colon: [Chromium CL 78832988](https://chromium-review.googlesource.com/c/chromium/src/+/78832988)
* **`U+000B` (VT)**
  * **[ MERGED ]** Do not treat `U+000B` (VT) as ASCII whitespace in CSP: [Chromium CL 7862660](https://chromium-review.googlesource.com/c/chromium/src/+/7862660)
* **Declarative Shadow Roots**
  * **[ UNDER REVIEW ]** Implement `shadowrootslotassignment`: [Chromium CL 7893946](https://chromium-review.googlesource.com/c/chromium/src/+/7893946)
* **Namespaces in `attr()`**
  * **[ IN PROGRESS ]** Support namespaces in `attr()`: [Chromium CL 7931006](https://chromium-review.googlesource.com/c/chromium/src/+/7931006)

---

## Apr 22, 2026 – Jun 3, 2026 (Weeks 21–22)

* **Scope:** Improving standards compliance and resolving interoperability issues across CSS features.
* **Spreadsheet:** [Tracking Sheet](https://docs.google.com/spreadsheets/d/1fn72b6g14VbI4G48NXWLf6qHmOM4dcRkF6J41s1nAVo/)

### Topics & Tasks

* **Editing**
  * **[ MERGED ]** Wrap elements with default `white-space` behavior: [Chromium CL 7705494](https://chromium-review.googlesource.com/c/chromium/src/+/7705494)
  * **[ REVIEW ]** Avoid removing special elements from metadata section: [Chromium CL 7793251](https://chromium-review.googlesource.com/c/chromium/src/+/7793251)
  * **[ WIP ]** Preserve `white-space` style when joining blocks in `contenteditable`: [Chromium CL 7588233](https://chromium-review.googlesource.com/c/chromium/src/+/7588233) | [Chrome Bug 40869970](https://issues.chromium.org/40869970)
* **Media Source**
  * **[ REVIEW ]** Do not pause player when moved to different document: [Chromium CL 7828889](https://chromium-review.googlesource.com/c/chromium/src/+/7828889)
* **`autocorrect` Attribute**
  * **[ REVIEW ]** [Chromium CL 7075071](https://chromium-review.googlesource.com/c/chromium/src/+/7075071) (I2S approved).
* **CSSWG Discussions**
  * Clarify `:lang()` behavior when language range is not well-formed BCP 47 code: [CSSWG Issue 8720](https://github.com/w3c/csswg-drafts/issues/8720)
  * Serialization of `font-style: oblique`: Resolved `oblique 14deg` computes and serializes to `oblique 14deg` ([CSSWG Issue 8291](https://github.com/w3c/csswg-drafts/issues/8291)).
* **Italic vs. Oblique**
  * **[ UNDER REVIEW ]** Distinguish italic, oblique, and oblique 14deg: [Chromium CL 7771471](https://chromium-review.googlesource.com/c/chromium/src/+/7771471)
* **Qualified Names**
  * **[ UNDER REVIEW ]** Split qualified names on first colon: [Chromium CL 7883298](https://chromium-review.googlesource.com/c/chromium/src/+/7883298) | [Chrome Bug 490251709](https://issues.chromium.org/issues/490251709)
* **`U+000B` (VT)**
  * **[ UNDER REVIEW ]** Do not treat `U+000B` (VT) as ASCII whitespace in CSP: [Chromium CL 7862660](https://chromium-review.googlesource.com/c/chromium/src/+/7862660) | [Chrome Bug 479873900](https://issues.chromium.org/issues/479873900)
* **First Contentful Paint (FCP)**
  * **[ WIP ]** Suppress FCP for non-invertible transforms: [Chromium CL 7734583](https://chromium-review.googlesource.com/c/chromium/src/+/7734583)

---

## Apr 7, 2026 – Apr 22, 2026 (Weeks 15–16)

* **Scope:** Improving standards compliance and resolving interoperability issues across CSS features.
* **Spreadsheet:** [Tracking Sheet](https://docs.google.com/spreadsheets/d/1fn72b6g14VbI4G48NXWLf6qHmOM4dcRkF6J41s1nAVo/)

### Topics & Tasks

* **Editing**
  * **[ MERGED ]** WebDriver issue fix for WPT infrastructure: [Chromium CL 7642806](https://chromium-review.googlesource.com/c/chromium/src/+/7642806)
  * **[ REVIEW ]** Editing commands losing original `white-space` behavior: [Chromium CL 7705494](https://chromium-review.googlesource.com/c/chromium/src/+/7705494) | [Chrome Bug 500638465](https://issues.chromium.org/issues/500638465) | [WPT Issue 59067](https://github.com/web-platform-tests/wpt/issues/59067)
* **Control Characters**
  * **[ MERGED ]** Render Cc control characters as visible glyphs: [Chromium CL 7656490](https://chromium-review.googlesource.com/c/chromium/src/+/7656490)
* **SVG `animateMotion`**
  * **[ MERGED ]** Respect CSS `d` property on path elements: [Chromium CL 7665902](https://chromium-review.googlesource.com/c/chromium/src/+/7665902)
* **`lang`**
  * **[ MERGED ]** Reject `:lang()` matches for ill-formed lang attributes: [Chromium CL 7761523](https://chromium-review.googlesource.com/c/chromium/src/+/7761523)
* **WPT Upstream Fixes**
  * **[ MERGED ]** Fix tests matching lang tags: [WPT PR 59296](https://github.com/web-platform-tests/wpt/pull/59296)
  * **[ MERGED ]** Correct Korean mappings: [WPT PR 56554](https://github.com/web-platform-tests/wpt/pull/56554)
  * **[ MERGED ]** Correct interpolation accumulation results: [WPT PR 58497](https://github.com/web-platform-tests/wpt/pull/58497)

---

## Mar 25, 2026 – Apr 7, 2026 (Weeks 13–14)

* **Scope:** Improving standards compliance and resolving interoperability issues across CSS features.
* **Spreadsheet:** [Tracking Sheet](https://docs.google.com/spreadsheets/d/1fn72b6g14VbI4G48NXWLf6qHmOM4dcRkF6J41s1nAVo/)

### Topics & Tasks

* **Editing**
  * **[ WIP ]** Wrap inserted node in span to preserve `white-space`: [Chromium CL 7705494](https://chromium-review.googlesource.com/c/chromium/src/+/7705494)
  * **[ REVIEW ]** Fix WebDriver focus/testing infra issue: [Chromium CL 7642806](https://chromium-review.googlesource.com/c/chromium/src/+/7642806)
* **Control Characters**
  * **[ WIP ]** Render Cc control characters as visible glyphs: [Chromium CL 7656490](https://chromium-review.googlesource.com/c/chromium/src/+/7656490)
* **SVG `animateMotion`**
  * **[ WIP ]** SVG `animateMotion` respects CSS `d` property: [Chromium CL 7665902](https://chromium-review.googlesource.com/c/chromium/src/+/7665902)
* **CSS Ruby**
  * **[ WIP ]** Investigating display values (`ruby-base`, `ruby-base-container`, `ruby-text-container`): [Chromium CL 7725437](https://chromium-review.googlesource.com/c/chromium/src/+/7725437) | [WPT Results](https://wpt.fyi/results/css/css-ruby)

---

## Mar 11, 2026 – Mar 25, 2026 (Weeks 11–12)

* **Scope:** Improving standards compliance and resolving interoperability issues across CSS features.
* **Spreadsheet:** [Tracking Sheet](https://docs.google.com/spreadsheets/d/1fn72b6g14VbI4G48NXWLf6qHmOM4dcRkF6J41s1nAVo/)

### Topics & Tasks

* **HTML5Lib**
  * **[ MERGED ]** Removal of `<command>` HTML element: [Chromium CL 7633305](https://chromium-review.googlesource.com/c/chromium/src/+/7633305)
  * **[ MERGED ]** Missing step in Agency Adoption algorithm: [Chromium CL 7535115](https://chromium-review.googlesource.com/c/chromium/src/+/7535115)
* **Editing**
  * **[ REVIEW ]** WebDriver focus bug: [Chromium CL 7642806](https://chromium-review.googlesource.com/c/chromium/src/+/7642806)
* **Translate Serialization**
  * **[ MERGED ]** Fix translate serialization in `GetTypeForTranslate()`: [Chromium CL 7637894](https://chromium-review.googlesource.com/c/chromium/src/+/7637894)
* **`scroll-margin` and `padding-margin` Inheritance with Zoom**
  * **[ MERGED ]** Correct inheritance with CSS zoom: [Chromium CL 7665362](https://chromium-review.googlesource.com/c/chromium/src/+/7665362)
* **Resource Timing Metrics**
  * **[ MERGED ]** Fix resource timing metrics when Service Worker fetches subresources: [Chromium CL 7665682](https://chromium-review.googlesource.com/c/chromium/src/+/7665682)
* **Control Characters & Font Updates**
  * **[ WIP ]** Render Cc control characters as visible glyphs (Updating NotoSansSymbols2 font): [Chromium CL 7656490](https://chromium-review.googlesource.com/c/chromium/src/+/7656490)
* **SVG `animateMotion`**
  * **[ WIP ]** Respect CSS `d` property: [Chromium CL 7665902](https://chromium-review.googlesource.com/c/chromium/src/+/7665902)
* **CSS Ruby**
  * **[ WIP ]** Investigating missing features in CSS Ruby.

---

## Mar 1, 2026 – Mar 11, 2026 (Weeks 9–10)

* **Scope:** Improving standards compliance and resolving interoperability issues across CSS features.
* **Spreadsheet:** [Tracking Sheet](https://docs.google.com/spreadsheets/d/1fn72b6g14VbI4G48NXWLf6qHmOM4dcRkF6J41s1nAVo/)

### Topics & Tasks

* **Editing Related Issues**
  * **[ MERGED ]** [Chromium CL 7511015](https://chromium-review.googlesource.com/c/chromium/src/+/7511015)
* **HTML Parsing Issues**
  * **[ REVIEW ]** [Chromium CL 7535115](https://chromium-review.googlesource.com/c/chromium/src/+/7535115)
  * **[ REVIEW ]** Remove `<command>` element: [Chromium CL 7633305](https://chromium-review.googlesource.com/c/chromium/src/+/7633305)
* **ChromeDriver Issue**
  * Filed upstream bug: [Chrome Bug 490318105](https://issues.chromium.org/issues/490318105)
  * Patched WPT infra: [WPT PR 58290](https://github.com/web-platform-tests/wpt/pull/58290)
  * **[ ABANDONED ]** [Chromium CL 7638650](https://chromium-review.googlesource.com/c/chromium/src/+/7638650)
  * **[ REVIEW ]** [Chromium CL 7642806](https://chromium-review.googlesource.com/c/chromium/src/+/7642806)
* **Iteration Accumulation for CSS Transforms**
  * **[ MERGED ]** Add `AccumulateN` for CSS transform operations: [Chromium CL 7614089](https://chromium-review.googlesource.com/c/chromium/src/+/7614089)
  * **[ MERGED ]** Implement iteration composite accumulation for CSS transforms: [Chromium CL 7572602](https://chromium-review.googlesource.com/c/chromium/src/+/7572602)
  * **[ UNDER REVIEW ]** Fix bug in `GetTypeForTranslate()`: [Chromium CL 7637894](https://chromium-review.googlesource.com/c/chromium/src/+/7637894)
* **Control Characters**
  * **[ WIP ]** Render Cc control characters as visible glyphs: [Chromium CL 7637351](https://chromium-review.googlesource.com/c/chromium/src/+/7637351)

---

## Jan 28, 2026 – Feb 11, 2026

* **Scope:** Improving standards compliance and resolving interoperability issues across CSS features.
* **Spreadsheet:** [Tracking Sheet](https://docs.google.com/spreadsheets/d/1Yjp3o3T0E9CCqihdY_-lW3RvriYAqTj5NVGgl4zslro/)

### Topics & Tasks

* **`onanimationcancel` Global Handler**
  * **[ WONTFIX ]** Closed non-reproducible regressions: [Chrome Bug 468000581](https://issues.chromium.org/issues/468000581) | [Chrome Bug 477993725](https://issues.chromium.org/issues/477993725)
* **Empty String in `css-animation-name`**
  * **[ MERGED ]** Treat empty string as invalid: [Chromium CL 7067893](https://chromium-review.googlesource.com/c/chromium/src/+/7067893) | [Spec PR 13151](https://github.com/w3c/csswg-drafts/pull/13151) | [WPT PR 56260](https://github.com/web-platform-tests/wpt/pull/56260)
* **Malformed HTML Tags**
  * **[ WIP ]** Bug in adoption algorithm: [Chromium CL 7535115](https://chromium-review.googlesource.com/c/chromium/src/+/7535115)
* **`font-variant-alternates` Precedence**
  * **[ MERGED ]** Fix precedence over `@font-face` descriptor: [Chromium CL 7509466](https://chromium-review.googlesource.com/c/chromium/src/+/7509466)
* **`text-transform: full-size-kana`**
  * **[ MERGED ]** Implement full-size-kana for Japanese text: [Chromium CL 7525629](https://chromium-review.googlesource.com/c/chromium/src/+/7525629)
* **Multi-keyword `text-transform`**
  * **[ WIP ]** Support multi-keyword values: [WPT Test](https://wpt.fyi/results/css/css-text/text-transform/text-transform-multiple-001.html)
* **`iterationComposite` for CSS Animations**
  * Initial implementation in [Chromium CL 7047878](https://chromium-review.googlesource.com/c/chromium/src/+/7047878).

---

## Jan 13, 2026 – Jan 28, 2026 (Weeks 03–04)

* **Scope:** Improving standards compliance and resolving interoperability issues across CSS features.
* **Spreadsheet:** [Tracking Sheet](https://docs.google.com/spreadsheets/d/1V-dIz78giXXi1VhC6ScbO8Qi716EOHl5XlofQDG6-jM/edit?usp=sharing)

### Executive Summary
Progress was made on closing major interop tasks, stabilizing prior changes, and advancing alignment with web specifications. Completed WebAudio tasks (specifically `AudioContext` async state transitions), resolved CSS Images gradient regressions, fixed animation/ASAN crashes, and improved standards compliance in text emphasis and font feature precedence.

### Topics & Tasks

* **CSS Images Gradient Regression**
  * **[ MERGED ]** Fix regression in gradient computed values: [Chromium CL 7508374](https://chromium-review.googlesource.com/c/chromium/src/+/7508374) | [Chrome Bug 476742109](https://issues.chromium.org/issues/476742109)
* **Editing Interop**
  * **[ WIP ]** Paragraph merging/deletion style handling: [Chromium CL 7511015](https://chromium-review.googlesource.com/c/chromium/src/+/7511015)
* **WebAudio Transitions**
  * **[ MERGED ]** `AudioContext` async state transitions to "running" and "suspended": [Chromium CL 7266845](https://chromium-review.googlesource.com/c/chromium/src/+/7266845) | [Chrome Bug 40140417](https://issues.chromium.org/issues/40140417)
* **Animations / Crash Fixes**
  * **[ MERGED ]** Fix CHECK failure in `InterpolableLength::ScaleAndAdd`: [Chromium CL 7478868](https://chromium-review.googlesource.com/c/chromium/src/+/7478868) | [Chrome Bug 467366440](https://issues.chromium.org/issues/467366440)
  * **[ MERGED ]** Fix Use-After-Free in `OffsetMapping`: [Chromium CL 7483830](https://chromium-review.googlesource.com/c/chromium/src/+/7483830)
* **CSS Text Emphasis**
  * **[ MERGED ]** Auto value of `text-emphasis-position` in Chinese: [Chromium CL 7510164](https://chromium-review.googlesource.com/c/chromium/src/+/7510164)
  * **[ MERGED ]** Fix `text-emphasis-style` default shape to circle: [Chromium CL 7508985](https://chromium-review.googlesource.com/c/chromium/src/+/7508985)

---

## Dec 16, 2025 – Jan 13, 2026 (Weeks 51–02)

* **Scope:** Improving standards compliance and resolving interoperability issues across CSS features.
* **Spreadsheet:** [Tracking Sheet](https://docs.google.com/spreadsheets/d/1Yjp3o3T0E9CCqihdY_-lW3RvriYAqTj5NVGgl4zslro/edit?usp=sharing)

### Topics & Tasks

* **`AudioContext` Async Transitions:** Working on rollout strategies and UseCounters for [Chromium CL 7266845](https://chromium-review.googlesource.com/c/chromium/src/+/7266845).
* **Fuzzer Bugs Triaged:**
  * Interpolation CHECK failure: [Chrome Bug 467366440](https://issues.chromium.org/issues/467366440)
  * Full-width CHECK failure: [Chrome Bug 470442749](https://issues.chromium.org/issues/470442749)
  * Full-width NULL read: [Chrome Bug 472414704](https://issues.chromium.org/issues/472414704)
* **Editing Interop Analysis:** Investigating [WPT Test Failures](https://wpt.fyi/results/editing/other/join-different-white-space-style-left-line-and-right-paragraph.html%3Fmethod%3Dselect-boundary%26left-white-space%3Dnowrap%26right-white-space%3Dpre-wrap?label=master&max-count=2&aligned&view=test&q=seq%28status%3A%21pass%20status%3A%21pass%20status%3A%21pass%20status%3A%21pass%20status%3Apass%20status%3Apass%20status%3Apass%20status%3Apass%29).

---

## Dec 4, 2025 – Dec 16, 2025 (Weeks 49–50)

* **Scope:** Improving standards compliance and resolving interoperability issues across CSS features.

### Topics & Tasks

* **Selection API:** `getSelection().anchorNode` side-effects fix: [Chromium CL 7083656](https://chromium-review.googlesource.com/c/chromium/src/+/7083656)
* **Web Animations:**
  * **[ MERGED ]** Support `iterationComposite: accumulate`: [Chromium CL 7047878](https://chromium-review.googlesource.com/c/chromium/src/+/7047878)
* **CSS Selectors:**
  * **[ MERGED ]** Extended language ranges in `:lang()`: [Chromium CL 7048363](https://chromium-review.googlesource.com/c/chromium/src/+/7048363)
* **Text Transforms & Color Parsing:**
  * Correct Korean character expectations: [WPT PR 56554](https://github.com/web-platform-tests/wpt/pull/56554)
  * Full-width collapsed space handling: [Chromium CL 7234894](https://chromium-review.googlesource.com/c/chromium/src/+/7234894)
  * Color parsing fixes: [Chromium CL 7261315](https://chromium-review.googlesource.com/c/chromium/src/+/7261315)
* **Media & Animations:**
  * **[ MERGED ]** Expose `onanimationcancel`: [Chromium CL 7172354](https://chromium-review.googlesource.com/c/chromium/src/+/7172354)
  * **[ WIP ]** `MediaElement` move across documents: [Chromium CL 7210785](https://chromium-review.googlesource.com/c/chromium/src/+/7210785)

---

## Nov 21, 2025 – Dec 4, 2025 (Weeks 47–48)

* **Scope:** Improving standards compliance and resolving interoperability issues across CSS features.

### Topics & Tasks

* **`css-animation-name`:** Drafted spec change ([CSSWG PR 13151](https://github.com/w3c/csswg-drafts/pull/13151)) and WPT tests ([WPT PR 56260](https://github.com/web-platform-tests/wpt/pull/56260)). **[ WIP ]** [Chromium CL 7067893](https://chromium-review.googlesource.com/c/chromium/src/+/7067893).
* **Dialog Element WPT Failures:** Addressed focus-on-startup issues in tests: [WPT PR 56270](https://github.com/web-platform-tests/wpt/pull/56270), [WPT PR 56288](https://github.com/web-platform-tests/wpt/pull/56288), and [Chromium CL 7205407](https://chromium-review.googlesource.com/c/chromium/src/+/7205407).
* **Canvas 2D Color Parsing:**
  * **[ MERGED ]** Support unresolved `calc()` values in Canvas 2D: [Chromium CL 7182583](https://chromium-review.googlesource.com/c/chromium/src/+/7182583) | [Chrome Bug 459135661](https://issues.chromium.org/issues/459135661)

---

## Nov 7, 2025 – Nov 21, 2025 (Weeks 45–46)

* **Scope:** Improving standards compliance and resolving interoperability issues across CSS features.

### Topics & Tasks

* **CSS Animation Interop:** Split animation serialization work into 3 patches:
  * **[ MERGED ]** Allow `<string>` in `css-animation-name`: [Chromium CL 7067893](https://chromium-review.googlesource.com/c/chromium/src/+/7067893)
  * **[ MERGED ]** Omit default values in `animation` shorthand computed style: [Chromium CL 7122294](https://chromium-review.googlesource.com/c/chromium/src/+/7122294)
  * **[ MERGED ]** Allow `<string>` in `@keyframes-name` style rule: [Chromium CL 7128859](https://chromium-review.googlesource.com/c/chromium/src/+/7128859)
* **CSS Backgrounds:**
  * **[ MERGED ]** Enable 2-value syntax for `background-position-x/y` by default: [Chromium CL 7130739](https://chromium-review.googlesource.com/c/chromium/src/+/7130739)

---

## Oct 23, 2025 – Nov 7, 2025

* **Scope:** Improving standards compliance and resolving interoperability issues across CSS features.

### Topics & Tasks

* **Selection API:** Landed fix returning `direction: "none"` for collapsed selections. Caching live range in `SelectionController`: [Chromium CL 7083656](https://crrev.com/c/7083656).
* **Gamepad API:** Shipped `ongamepadconnected` and `ongamepaddisconnected` event handlers.
* **`text-transform: full-width`:** Relanded in two steps:
  * **[ MERGED ]** Implementation: [Chromium CL 6875479](https://chromium-review.googlesource.com/c/chromium/src/+/6875479)
  * **[ MERGED ]** Enable in experimental mode: [Chromium CL 7030343](https://chromium-review.googlesource.com/c/chromium/src/+/7030343)
* **Extended Language Ranges:** Re-landed parser fix with extra validation: [Chromium CL 7048363](https://chromium-review.googlesource.com/c/chromium/src/+/7048363).
* **Web Animations `iterationComposite`:** Intent to Prototype sent ([Chrome Status](https://chromestatus.com/feature/5198590821662720)). Initial patch: [Chromium CL 7047878](https://chromium-review.googlesource.com/c/chromium/src/+/7047878).

---

## Oct 9, 2025 – Oct 23, 2025

* **Scope:** Improving standards compliance and resolving interoperability issues across CSS features.

### Topics & Tasks

* **Selection API Fixes:**
  * **[ MERGED ]** `removeRange()` throw `NotFoundError`: [Chromium CL 7026953](https://chromium-review.googlesource.com/c/chromium/src/+/7026953)
  * **[ MERGED ]** `onselectionchange` support in `HTMLElement`s: [Chromium CL 7031196](https://chromium-review.googlesource.com/c/chromium/src/+/7031196)
  * **[ MERGED ]** Collapsed selection direction handling: [Chromium CL 7055926](https://chromium-review.googlesource.com/c/chromium/src/+/7055926)
* **CSS Gradients:** Computed style and parsing interpolation fixes: [Chromium CL 7021757](https://chromium-review.googlesource.com/c/chromium/src/+/7021757).

---

## Sep 24, 2025 – Oct 9, 2025 (Weeks 39–40)

* **Scope:** Improving standards compliance and resolving interoperability issues across CSS features.

### Topics & Tasks

* **Gamepad API:**
  * **[ MERGED ]** Implement `WindowEventHandlers` extensions for gamepad: [Chromium CL 6984681](https://crrev.com/c/6984681) | [Chrome Status](https://chromestatus.com/feature/5109540852989952)
* **SVG Backgrounds:**
  * **[ MERGED ]** Sizing and positioning fixes for SVG documents in backgrounds: [Chromium CL 6915855](https://chromium-review.googlesource.com/c/chromium/src/+/6915855)
* **Background Position Syntax:**
  * **[ MERGED ]** Side-relative syntax implementation: [Chromium CL 6811401](https://chromium-review.googlesource.com/c/chromium/src/+/6811401)
  * **[ MERGED ]** Computed style fixes for background position: [Chromium CL 6804463](https://chromium-review.googlesource.com/c/chromium/src/+/6804463)

---

## Sep 12, 2025 – Sep 24, 2025 (Weeks 37–38)

* **Scope:** Improving standards compliance and resolving interoperability issues across CSS features.

### Topics & Tasks

* **Battery Status API:** Drafted Permissions Policy implementation: [Chromium CL 6945228](https://crrev.com/c/6945228) | [Chrome Bug 40100229](https://issues.chromium.org/issues/40100229).
* **White Space Handling:** Collapsing with control characters and ZWJ/ZWNJ: [Chromium CL 6946846](https://chromium-review.googlesource.com/c/chromium/src/+/6946846).
* **CSS Backgrounds & Gradients:**
  * **[ MERGED ]** Apply `CSSGradient` changes to other properties: [Chromium CL 6722514](https://chromium-review.googlesource.com/c/chromium/src/+/6722514)

---

## Aug 27, 2025 – Sep 12, 2025 (Weeks 35–36)

* **Scope:** Improving standards compliance and resolving interoperability issues across CSS features.

### Topics & Tasks

* **SVG in `<object>` / `<embed>`:**
  * **[ MERGED ]** Treat SVG as replaced elements: [Chromium CL 6884274](https://chromium-review.googlesource.com/c/chromium/src/+/6884274)
* **CSS Color Serialization:**
  * **[ MERGED ]** Fix CSS color space serialization: [Chromium CL 6858231](https://chromium-review.googlesource.com/c/chromium/src/+/6858231)
* **CSS Gradients & `calc()`:**
  * **[ MERGED ]** Simplify `calc()` expressions in gradients: [Chromium CL 6714636](https://crrev.com/c/6714636)
  * **[ MERGED ]** Fix angle values in gradients: [Chromium CL 6881685](https://crrev.com/c/6881685)

---

## Jun 20, 2025 – Aug 27, 2025 (Period Summary & Biweeklies)

* **Scope:** Improving standards compliance and resolving interoperability issues across CSS features.

### Executive Summary of Completed Work
* **CSS Gradient Resolution:**
  * **[ MERGED ]** Computed values resolution in gradient functions: [Chromium CL 6676851](https://chromium-review.googlesource.com/c/chromium/src/+/6676851)
  * **[ MERGED ]** Simplified `calc()` single-literal math: [Chromium CL 6714636](https://chromium-review.googlesource.com/c/chromium/src/+/6714636)
* **CSS Selectors Level 4:**
  * **[ MERGED ]** Extended language ranges support in `:lang()`: [Chromium CL 6677873](https://chromium-review.googlesource.com/c/chromium/src/+/6677873)
* **Text Alignment:**
  * **[ MERGED ]** `text-align: match-parent` implementation: [Chromium CL 6721711](https://chromium-review.googlesource.com/c/chromium/src/+/6721711) | [Chrome Status](https://chromestatus.com/feature/5133972077805568)
* **SVG Embedding:**
  * **[ MERGED ]** SVGs inside `<object>`/`<embed>` treated as replaced elements (fixes 62 WPT tests).

---

### Archive: Biweekly Breakdown (June – August 2025)

#### Aug 14 – Aug 27, 2025 (Weeks 33–34)
* **CSS Gradients:** Work expanding resolution logic to other properties ([Chromium CL 6722514](https://chromium-review.googlesource.com/c/chromium/src/+/6722514)) and angle serialization ([Chromium CL 6811401](https://chromium-review.googlesource.com/c/chromium/src/+/6811401)).
* **`text-transform: full-width`:** [Chromium CL 6790585](https://chromium-review.googlesource.com/c/chromium/src/+/6790585) merged, reverted due to Win10 failure ([Chromium CL 6867371](https://chromium-review.googlesource.com/c/chromium/src/+/6867371)), and reland prepared ([Chromium CL 6875479](https://chromium-review.googlesource.com/c/chromium/src/+/6875479)).
* **Color Serialization:** Fix for HSL, HWB, Lab, RGB spaces ([Chromium CL 6858231](https://chromium-review.googlesource.com/c/chromium/src/+/6858231)).

#### Jul 30 – Aug 14, 2025 (Weeks 31–32)
* **[ MERGED ]** Extended language ranges in `:lang()` ([Chromium CL 6677873](https://chromium-review.googlesource.com/c/chromium/src/+/6677873)).
* **[ MERGED ]** `text-align: match-parent` ([Chromium CL 6721711](https://chromium-review.googlesource.com/c/chromium/src/+/6721711)).
* **[ MERGED ]** SVG as replaced elements in `<object>`/`<embed>`.
* **CSS Images Interop:** Fallback to `image-rendering: pixelated` agreed with WPT ([WPT PR 53930](https://github.com/web-platform-tests/wpt/pull/53930) & [Chromium CL 6794665](https://chromium-review.googlesource.com/c/chromium/src/+/6794665)).

#### Jul 17 – Jul 30, 2025
* **Image Rendering & WPT Fuzzy Tags:** Discussions on pixelated fallback and WPT annotation infrastructure ([Chrome Bug 434057608](https://crbug.com/434057608)).
* **CJK Text Transforms:** Initial implementation for `text-transform: full-width` ([Chromium CL 6790585](https://chromium-review.googlesource.com/c/chromium/src/+/6790585)).

#### Jul 2 – Jul 17, 2025 (Weeks 27–28)
* **CSS Backgrounds:** **[ REVIEW ]** Omit default values & resolve `calc()` stop offsets in Gradient CSS Values ([Chromium CL 6676851](https://chromium-review.googlesource.com/c/chromium/src/+/6676851)).
* **Language Selectors:** **[ REVIEW ]** Extended language ranges parser ([Chromium CL 6677873](https://chromium-review.googlesource.com/c/chromium/src/+/6677873)).
* **Text Alignment:** **[ REVIEW ]** `text-align: match-parent` ([Chromium CL 6721711](https://chromium-review.googlesource.com/c/chromium/src/+/6721711)).

#### Jun 20 – Jul 2, 2025
* **[ MERGED ]** Omit default values in Gradient CSS Values serialization: [Chromium CL 6638812](https://chromium-review.googlesource.com/c/chromium/src/+/6638812/).
* **Language Selectors:** Created patch implementing extended language ranges for `:lang()` ([Chromium CL 6677873](https://chromium-review.googlesource.com/c/chromium/src/+/6677873)).

#### Initial Kickoff (Jun 20, 2025)
* **Baseline Content-Alignment:** Prototype created for `align-content: last-baseline` ([Chromium CL 6625778](https://chromium-review.googlesource.com/c/chromium/src/+/6625778)). Raised implementation gaps with CSSWG.
* **Gradient Serialization:** Filed [Chrome Bug 424157326](https://issues.chromium.org/issues/424157326) and submitted initial fix ([Chromium CL 6638812](https://chromium-review.googlesource.com/c/chromium/src/+/6638812/)).
