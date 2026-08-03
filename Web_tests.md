# SOCBB WPT Tests Igalia Status Updates

## Jul 16, 2026 – Jul 30, 2026 (Weeks 29–30)

* **Scope:** Improving the state of web tests in Chromium-based browsers.
* **Spreadsheet:** [Tracking Sheet](https://docs.google.com/spreadsheets/d/1rceYcaQiR7n6VOF59emYP1KlnGHZ3QizDlxnH-zaKYI)

### Summary
Enabling `move()` and `rename()` for directory handles in OPFS was merged, a fix for blank canvas output when chaining CSS filters with `url()` SVG filters was merged, and several internal MSE tests were either removed as redundant or migrated over to WPT.

### Topics & Tasks

#### Feature Fixes & Specs
* **Directory Handle `move()` / `rename()` in OPFS:**
  * **[ MERGED ]** FSA: Enable `move()` and `rename()` for directory handles in OPFS (crbug.com/40198034): [Chromium CL 8000010](https://chromium-review.googlesource.com/c/chromium/src/+/8000010)
* **Negative `overflow-clip-margin` Values:**
  * **[ MERGED ]** Allow `overflow-clip-margin` to accept negative length values per spec to shrink clip edge inward (crbug.com/501216032): [Chromium CL 8117433](https://chromium-review.googlesource.com/c/chromium/src/+/8117433)
* **Blank Canvas Output with CSS & `url()` SVG Filters:**
  * **[ MERGED ]** Fix blank canvas output when chaining CSS filters with `url()` SVG filters (crbug.com/533040707): [Chromium CL 8083705](https://chromium-review.googlesource.com/c/chromium/src/+/8083705)
* **Stale `HasBoxDecorationBackground` on Color-Scheme Change:**
  * **[ MERGED ]** Set `HasBoxDecorationBackground` for dynamic color-scheme mismatch in `SetUseColorAdjustBackground()` (crbug.com/494377597): [Chromium CL 8129680](https://chromium-review.googlesource.com/c/chromium/src/+/8129680)

#### Test File Fixes
* **[ MERGED ]** Fix expected ref for nested SVG sizing keyword tests (crbug.com/434975373): [Chromium CL 8084484](https://chromium-review.googlesource.com/c/chromium/src/+/8084484)
* **[ MERGED ]** Add missing `check-scheme` action in WS stash responder (crbug.com/504770562): [Chromium CL 8105315](https://chromium-review.googlesource.com/c/chromium/src/+/8105315)
* **[ MERGED ]** Fix wrong values in suggestion-picker mouse-operations tests (crbug.com/40215845): [Chromium CL 8136179](https://chromium-review.googlesource.com/c/chromium/src/+/8136179)
* **[ REVIEW ]** Add long timeout to 3 accname tests to prevent default 10s timeout (crbug.com/443203688): [Chromium CL 8129542](https://chromium-review.googlesource.com/c/chromium/src/+/8129542)

#### Obsolete Test Expectations Removals
* **[ MERGED ]** Remove obsolete DevTools insertion-order test expectations: [Chromium CL 8069257](https://chromium-review.googlesource.com/c/chromium/src/+/8069257)
* **[ MERGED ]** Remove obsolete CSP inside-worker virtual test expectations: [Chromium CL 8129337](https://chromium-review.googlesource.com/c/chromium/src/+/8129337)

#### Internal Tests Cleanup (crbug.com/485677942)
* **[ MERGED ]** Remove redundant `offset-*` `getComputedStyle` tests from `css3/motion-path`: [Chromium CL 8084382](https://chromium-review.googlesource.com/c/chromium/src/+/8084382)
* **[ MERGED ]** Remove redundant `mediasource-*` tests from `media/media-source`: [Chromium CL 8105856](https://chromium-review.googlesource.com/c/chromium/src/+/8105856)
* **[ MERGED ]** Migrate MSE preload/play-then-seek-back coverage to WPT: [Chromium CL 8123434](https://chromium-review.googlesource.com/c/chromium/src/+/8123434)
* **[ REVIEW ]** Migrate MSE `endofstream-invaliderror` tests to WPT: [Chromium CL 8129277](https://chromium-review.googlesource.com/c/chromium/src/+/8129277)

---

## Jul 2, 2026 – Jul 16, 2026 (Weeks 27–28)

* **Scope:** The main objective is to improve the state of web tests in Chromium-based browsers.
* **Spreadsheet:** [Tracking Sheet](https://docs.google.com/spreadsheets/d/1rceYcaQiR7n6VOF59emYP1KlnGHZ3QizDlxnH-zaKYI/)

### Topics & Tasks

#### TestExpectations & Feature Fixes
* **WebAuthn Failures (crbug.com/508634577):**
  * **[ MERGED ]** Fix wrong status code for invalid webauthn protocol: [Chromium CL 8042178](https://chromium-review.googlesource.com/c/chromium/src/+/8042178)
  * **[ MERGED ]** Remove invalid `signCount=-1` case from webauthn test: [Chromium CL 8043505](https://chromium-review.googlesource.com/c/chromium/src/+/8043505)
  * **[ MERGED ]** Remove obsolete webauthn test expectations: [Chromium CL 8043760](https://chromium-review.googlesource.com/c/chromium/src/+/8043760)
* **`createImageBitmap` Fixes (crbug.com/422811223):**
  * **[ MERGED ]** Fix `createImageBitmap` promise timing: [Chromium CL 8008926](https://chromium-review.googlesource.com/c/chromium/src/+/8008926)
  * **[ MERGED ]** Update `createImageBitmap` baselines for `HTMLVideoElement` pixel values: [Chromium CL 8008966](https://chromium-review.googlesource.com/c/chromium/src/+/8008966)
  * **[ MERGED ]** Fix `createImageBitmap` performance regression (crbug.com/531780534): [Chromium CL 8061406](https://chromium-review.googlesource.com/c/chromium/src/+/8061406)
* **Feature Policy & Cache Controls:**
  * **[ MERGED ]** Expose `PermissionsPolicy` as experimental alias for `FeaturePolicy` (crbug.com/493703182): [Chromium CL 7893748](https://chromium-review.googlesource.com/c/chromium/src/+/7893748)
  * **[ MERGED ]** Parse `Cache-Control: immutable` to override legacy `Pragma: no-cache` (crbug.com/416704402): [Chromium CL 7923907](https://chromium-review.googlesource.com/c/chromium/src/+/7923907)
  * **[ MERGED ]** Pass real `StyleSheetContents` to `@supports selector()` namespace check (crbug.com/40804326): [Chromium CL 8038500](https://chromium-review.googlesource.com/c/chromium/src/+/8038500)
  * **[ REVIEW ]** FSA: Enable `move()` and `rename()` for directory handles in OPFS (crbug.com/40198034): [Chromium CL 8000010](https://chromium-review.googlesource.com/c/chromium/src/+/8000010)
* **Canvas 2D & Baselines:**
  * **[ WIP ]** Fix canvas 2D stroke pruning of degenerate zero-length path segments: [Chromium CL 8057524](https://chromium-review.googlesource.com/c/chromium/src/+/8057524)
  * **[ REVIEW ]** Add missing baselines for service worker update network-id tests: [Chromium CL 8073059](https://chromium-review.googlesource.com/c/chromium/src/+/8073059)
  * **[ WIP ]** [Chromium CL 8073953](https://chromium-review.googlesource.com/c/chromium/src/+/8073953)
* **Obsolete Expectations Removals:**
  * **[ MERGED ]** Remove obsolete `set_client_window_state` expectations: [Chromium CL 8029140](https://chromium-review.googlesource.com/c/chromium/src/+/8029140)
  * **[ REVIEW ]** Remove obsolete DevTools insertion-order expectations: [Chromium CL 8069257](https://chromium-review.googlesource.com/c/chromium/src/+/8069257)

#### Internal Tests Cleanup
* **[ DONE ]** Remove redundant `css3-counter-styles-*` tests from `fast/lists`: [Chromium CL 8042177](https://chromium-review.googlesource.com/c/chromium/src/+/8042177)
* **[ DONE ]** Migrate CSS transitions crashtest to WPT: [Chromium CL 8016794](https://chromium-review.googlesource.com/c/chromium/src/+/8016794)
* **[ DONE ]** Migrate `dom/transforms/css/html` crashtests to WPT: [Chromium CL 8021270](https://chromium-review.googlesource.com/c/chromium/src/+/8021270)
* **[ DONE ]** Migrate `dom/text/normalize-crash-in-spell-checker` to `external/wpt`: [Chromium CL 8035961](https://chromium-review.googlesource.com/c/chromium/src/+/8035961)
* **[ DONE ]** Migrate `css-ruby` crashtests to `external/wpt`: [Chromium CL 8033006](https://chromium-review.googlesource.com/c/chromium/src/+/8033006)
* **[ DONE ]** Migrate misc CSS crashtests to `external/wpt`: [Chromium CL 8036480](https://chromium-review.googlesource.com/c/chromium/src/+/8036480)
* **[ DONE ]** Migrate `css-parser/large-percent-number-crash` to `external/wpt/`: [Chromium CL 8028229](https://chromium-review.googlesource.com/c/chromium/src/+/8028229)
* **[ DONE ]** Migrate `css3/flexbox/anonymous-block-merge-crash` to `wpt/css-flexbox`: [Chromium CL 8028049](https://chromium-review.googlesource.com/c/chromium/src/+/8028049)
* **[ DONE ]** Migrate `css-parser` bracket crashtests to `external/wpt/css-syntax`: [Chromium CL 8031665](https://chromium-review.googlesource.com/c/chromium/src/+/8031665)
* **[ DONE ]** Migrate `css-content` generated-content crashtests to WPT: [Chromium CL 8029795](https://chromium-review.googlesource.com/c/chromium/src/+/8029795)
* **[ DONE ]** Migrate Web Animations crashtests to WPT: [Chromium CL 8036483](https://chromium-review.googlesource.com/c/chromium/src/+/8036483)
* **[ DONE ]** Migrate CSS animations stability crashtests to WPT: [Chromium CL 8027935](https://chromium-review.googlesource.com/c/chromium/src/+/8027935)
* **[ DONE ]** Migrate `css-conditional` crashtest to `external/wpt`: [Chromium CL 8060565](https://chromium-review.googlesource.com/c/chromium/src/+/8060565)
* **[ DONE ]** Migrate `css-backgrounds` crashtests to `external/wpt`: [Chromium CL 8058464](https://chromium-review.googlesource.com/c/chromium/src/+/8058464)
* **[ DONE ]** Migrate `css-contain` `change-text-node-data` crashtests to `external/wpt`: [Chromium CL 8065605](https://chromium-review.googlesource.com/c/chromium/src/+/8065605)
* **[ DONE ]** Migrate misc layout and CSS parser crashtests to `external/wpt`: [Chromium CL 8036482](https://chromium-review.googlesource.com/c/chromium/src/+/8036482)

---

## Jun 18, 2026 – Jul 2, 2026 (Weeks 25–26)

* **Scope:** Improving the state of web tests in Chromium-based browsers.
* **Spreadsheet:** [Tracking Sheet](https://docs.google.com/spreadsheets/d/1rceYcaQiR7n6VOF59emYP1KlnGHZ3QizDlxnH-zaKYI/)

### Topics & Tasks

* **TestExpectations:**
  * **[ DONE ]** Fix sensor permissions-policy tests timing out
  * **[ DONE ]** Update `createImageBitmap` baselines for `HTMLVideoElement` pixel values
  * **[ DONE ]** Remove obsolete BiDi emulation client hints test expectations
  * **[ DONE ]** Remove stale WebCodecs PCM timeout expectations
  * **[ REVIEW ]** FSA: Enable `move()` and `rename()` for directory handles in OPFS
  * **[ REVIEW ]** Allow `Cache-Control: immutable` to override `Pragma: no-cache`
  * **[ REVIEW ]** Expose `PermissionsPolicy` alias for feature policy
  * **[ WIP ]** Fix `createImageBitmap` promise timing
* **Internal Tests:**
  * **[ DONE ]** Migrate CSS Tables crashtests to WPT
  * **[ DONE ]** Migrate animations crashtests to WPT
  * **[ DONE ]** Migrate CSS transitions crashtests to WPT
  * **[ DONE ]** Migrate Shadow DOM crash test to WPT
* **`content_shell.filter`:**
  * **[ DONE ]** Remove cookie store test from filter
  * **[ DONE ]** Remove console log test from filter
  * **[ DONE ]** Remove cookie attribute tests from filter
  * **[ DONE ]** Add fuzzy tag to CSS filter effect tests
  * **[ DONE ]** Remove compositing mix blend mode tests from filter
  * **[ DONE ]** Remove CSS2 linebox tests from filter
  * **[ DONE ]** Remove CSS pseudo tests from filter
  * **[ DONE ]** Remove Content Security Policy tests from filter
  * **[ DONE ]** Remove CSS fonts tests from filter
  * **[ DONE ]** Remove compat webkit tests from filter

---

## Jun 3, 2026 – Jun 18, 2026 (Weeks 23–24)

* **Scope:** Improving the state of web tests in Chromium-based browsers.
* **Spreadsheet:** [Tracking Sheet](https://docs.google.com/spreadsheets/d/1rceYcaQiR7n6VOF59emYP1KlnGHZ3QizDlxnH-zaKYI/)

### Topics & Tasks

* **TestExpectations:**
  * **[ DONE ]** Remove obsolete scroll-snap test expectations
  * **[ DONE ]** Remove obsolete Linux CSS pixel test expectations
  * **[ DONE ]** Remove obsolete WebDriver test expectations
  * **[ DONE ]** Fix `requestAll()` handling for multiple permission requests
  * **[ REVIEW ]** Render partial frames from truncated progressive JXL images
  * **[ WIP ]** Expose `PermissionsPolicy` alias for feature policy
  * **[ WIP ]** Remove stale WebCodecs PCM timeout expectations
* **Internal Tests:**
  * **[ DONE ]** Migrate Shadow DOM crashtests to WPT
* **`content_shell.filter`:**
  * **[ WIP ]** Add fuzzy tag to CSS filter effect tests

---

## Apr 22, 2026 – Jun 3, 2026 (Weeks 21–22)

* **Scope:** Improving the state of web tests in Chromium-based browsers.
* **Spreadsheet:** [Tracking Sheet](https://docs.google.com/spreadsheets/d/1rceYcaQiR7n6VOF59emYP1KlnGHZ3QizDlxnH-zaKYI/)

### Topics & Tasks

* **TestExpectations:**
  * **[ DONE ]** Remove obsolete `window-open-features` test expectations
  * **[ DONE ]** Allow cross-origin-isolated permission in SAB iframe test
  * **[ DONE ]** Remove obsolete selection caret test expectations
  * **[ DONE ]** Run non-integer height popup tests sequentially
  * **[ DONE ]** Remove obsolete flaky CSS test expectations
  * **[ REVIEW ]** Remove obsolete Linux CSS pixel test expectations
  * **[ REVIEW ]** Remove obsolete scroll-snap test expectations
  * **[ WIP ]** Apply `max-width` to table columns
  * **[ WIP ]** Fix `requestAll()` handling for multiple permission requests
  * **[ WIP ]** Fix atomic line breaking tests
* **Internal Tests:**
  * **[ DONE ]** Migrate `fast/mediarecorder/MediaRecorder-audio-video` to WPT
* **`content_shell.filter`:**
  * **[ DONE ]** Remove CSS writing modes `text-combine` tests from filter
  * **[ DONE ]** Remove `backdrop-filter*` tests from filter
  * **[ WIP ]** Add fuzzy tag to account for color offsets

---

## Apr 7, 2026 – Apr 22, 2026 (Weeks 15–16)

* **Scope:** Improving the state of web tests in Chromium-based browsers.
* **Spreadsheet:** [Tracking Sheet](https://docs.google.com/spreadsheets/d/1rceYcaQiR7n6VOF59emYP1KlnGHZ3QizDlxnH-zaKYI/)

### Topics & Tasks

* **TestExpectations:**
  * **[ DONE ]** Remove obsolete view transition crash test expectations
  * **[ DONE ]** Adjust fuzzy tolerance and add missing baselines for zoom picker tests
  * **[ DONE ]** Fix `querySelector` bug and update baselines for hidpi picker tests
  * **[ DONE ]** Revert "[html] Fix body margin precedence and iframe margin injection" (Landed M147)
  * **[ WIP ]** Pass viewport resolution to SVG filters for `userSpaceOnUse`
  * **[ PENDING ]** Support `closest-corner`/`farthest-corner` in `clip-path` `circle()`/`ellipse()` ([CSSWG Issue 10812](https://github.com/w3c/csswg-drafts/issues/10812))
  * **[ DONE ]** Remove obsolete mixed content plugin, audio/video, and insecure CSS tests
* **Internal Tests:**
  * **[ DONE ]** Remove internal XHR timeout tests covered by WPT
  * **[ WIP ]** Migrate `fast/mediarecorder/MediaRecorder-requestData` to WPT
  * **[ WIP ]** Migrate `fast/mediarecorder/MediaRecorder-audio-video` to WPT
* **`content_shell.filter`:**
  * **[ DONE ]** Remove `float-nowrap-*`, clipboard API, and duplicate accname tests from filter
  * **[ WIP ]** Remove CSS2 backgrounds and duplicate `css-shapes` tests from filter

---

## Mar 25, 2026 – Apr 7, 2026 (Weeks 13–14)

* **Scope:** Improving the state of web tests in Chromium-based browsers.
* **Spreadsheet:** [Tracking Sheet](https://docs.google.com/spreadsheets/d/1rceYcaQiR7n6VOF59emYP1KlnGHZ3QizDlxnH-zaKYI/)

### Topics & Tasks

* **TestExpectations:**
  * **[ DONE ]** Use `ScopedCSSName` for `animation-name` to fix cross-scope keyframes lookup
  * **[ DONE ]** Allow author stylesheets to use UA `@keyframes` for view transitions
  * **[ DONE ]** Add ancestor validation check for SMIL animations
  * Revert "[html] Fix body margin precedence and iframe margin injection" to align with updated WPT upstream ([WHATWG HTML PR 11881](https://github.com/whatwg/html/pull/11881))
  * **[ DONE ]** Remove obsolete mixed content tests (image, strict mode, CSS)
* **Internal Tests:**
  * **[ DONE ]** Migrate `fast/dom/inert/inert-focus-in-frames` to WPT
  * **[ DONE ]** Remove orphaned `fast/dom/inert` resource
  * **[ DONE ]** Remove redundant tests in `fast/dom/viewport/` and `fast/mediarecorder/`
  * **[ DONE ]** Migrate `fast/mediarecorder/BlobEvent-basic` and `MediaRecorder-requestData` to WPT

---

## Mar 11, 2026 – Mar 25, 2026 (Weeks 11–12)

* **Scope:** Improving the state of web tests in Chromium-based browsers.
* **Spreadsheet:** [Tracking Sheet](https://docs.google.com/spreadsheets/d/1rceYcaQiR7n6VOF59emYP1KlnGHZ3QizDlxnH-zaKYI/)

### Topics & Tasks

* **TestExpectations:**
  * **[ DONE ]** Use `focus()` in `inert-node-is-uneditable` test
  * **[ DONE ]** Preserve source `effectAllowed` value in drop path
  * **[ DONE ]** Update test expectation on autoscroll web test
  * **[ DONE ]** Update stale expectations for select typeahead tests
  * **[ DONE ]** Clean up `PlzServiceWorker` tests from TestExpectations
  * **[ WIP ]** Use `ScopedCSSName` for `animation-name` to fix cross-scope keyframes lookup
* **Internal Tests:**
  * **[ DONE ]** Remove redundant tests in `fast/dom/inert` [1/n & 2/n]
  * **[ DONE ]** Remove redundant internal test: `indeterminate`
  * **[ WIP ]** Migrate `fast/dom/inert/inert-focus-in-frames` to WPT

---

## Mar 1, 2026 – Mar 11, 2026 (Weeks 9–10)

* **Scope:** Improving the state of web tests in Chromium-based browsers.
* **Spreadsheet:** [Tracking Sheet](https://docs.google.com/spreadsheets/d/1rceYcaQiR7n6VOF59emYP1KlnGHZ3QizDlxnH-zaKYI/)

### Topics & Tasks

* **TestExpectations:**
  * **[ DONE ]** [css-color] Map deprecated `ActiveCaption` to `Canvas`
  * **[ DONE ]** [css-color] Make `currentcolor` inherit visited color inside visited links
  * **[ DONE ]** [html] Fix body margin precedence and iframe margin injection
  * **[ DONE ]** [Transforms] Hide scrollbars in `3d-point-mapping-deep` test
  * **[ DONE ]** Update `replaceSelectorCommand-crash` test after Mutation Events removal
  * **[ WIP ]** Preserve source `effectAllowed` value in drop path
* **Internal Tests:**
  * **[ DONE ]** Remove redundant internal tests in `editing/execCommand`
  * **[ DONE ]** Migrate TreeWalker coverage to WPT and remove redundant internal tests

---

## Feb 11, 2026 – Mar 1, 2026 (Weeks 7–8)

* **Scope:** Improving the state of web tests in Chromium-based browsers.
* **Spreadsheet:** [Tracking Sheet](https://docs.google.com/spreadsheets/d/1rceYcaQiR7n6VOF59emYP1KlnGHZ3QizDlxnH-zaKYI/)

### Topics & Tasks

* **TestExpectations:**
  * **[ DONE ]** Handle `content: url()` on `HTMLVideoElement`
  * **[ DONE ]** Update `fixed-under-composited-fixed-scrolled` expectations
  * **[ DONE ]** Remove expectations for missing tests in `lifecycle`, `mathml`, `webvtt`, `webrtc-extensions`, and `web-locks`
  * **[ DONE ]** Remove `MutationEvent` references from DOM/Window web tests & migrate to `MutationObserver`
  * **[ WIP ]** [css-color] Map deprecated `ActiveCaption` to `Canvas`
  * **[ WIP ]** [css-color] Make `currentcolor` inherit visited color inside visited links
  * **[ WIP ]** Avoid enforcing specific `white-space` serialization in join test
* **Internal Tests:**
  * **[ DONE ]** Remove and migrate internal `css3/calc` tests to WPT `css/css-values`
  * **[ DONE ]** Remove redundant test `elementsFromPoint-inline.html` (Added nested inline WPT test)
  * **[ DONE ]** Remove redundant tests in `editing/selection/`

---

## Jan 28, 2026 – Feb 11, 2026

* **Scope:** Improving the state of web tests in Chromium-based browsers.
* **Spreadsheet:** [Tracking Sheet](https://docs.google.com/spreadsheets/d/1rceYcaQiR7n6VOF59emYP1KlnGHZ3QizDlxnH-zaKYI/)

### Topics & Tasks

* **TestExpectations:**
  * Clean up missing/obsolete test expectations across `webrtc/legacy`, `clear-site-data`, `idlharness`, `css-content`, `css`, `html`, `custom-elements`, and `svg`.
  * Clean up RAB WPT expectations now passing with feature enabled.
  * Remove `MutationEvent` coverage from legacy event init tests and update `constructor.js`.
* **`content_shell.filter`:**
  * Remove `select-as-listbox-default-styles` from filter (Stopped comparing `font-family` in UA style test).
  * Remove stale `external/wpt/html` and other stale filter entries.
* **Internal Tests:**
  * Remove redundant tests across `fast/dom/elementsFromPoint/`, `fast/canvas/`, `pointerevent`, `scroll-restoration`, `domstringlist`, and `border-image-slice`.

---

## Jan 13, 2026 – Jan 28, 2026

* **Scope:** Reduce failing/flaky/crashing tests in `TestExpectations` (~7,400 target) and migrate/clean internal Blink tests (~32,919 target).
* **Spreadsheet:** [Tracking Sheet](https://docs.google.com/spreadsheets/d/1rceYcaQiR7n6VOF59emYP1KlnGHZ3QizDlxnH-zaKYI/edit?gid=1808011796#gid=1808011796)

### Topics & Tasks

* **TestExpectations:**
  * Remove expectations for missing tests in `webrtc/legacy`, `geolocation-API`, and `clear-site-data`.
* **`content_shell.filter`:**
  * Stop comparing `font-family` in select listbox UA style test.
* **Internal Tests:**
  * Remove redundant tests across `fast/canvas/`, `script-src-wildcards`, `fast/shapes/shape-outside-floats/`, `user-select-none`, `ImageData-fidelity`, and `pointerevent`.

---

## Dec 16, 2025 – Jan 13, 2026

* **Scope:** Initial setup phase for Web_test improvement project. Focusing on analyzing `TestExpectations` and internal Blink tests.

### Topics & Tasks

* **TestExpectations:**
  * **[ MERGED ]** Remove stale Linux expectation for shadow-dom focus WPT
  * **[ MERGED ]** Remove stale Linux expectation for open-features WPT
  * **[ MERGED ]** Remove stale Linux expectation for unsupported-labels WPT
  * **[ MERGED ]** Remove stale Linux expectation for spin-by-blocking-style-sheet
  * **[ WIP ]** Remove stale Linux expectation for pointerlock WPT & MathML WPT
* **`content_shell.filter`:**
  * **[ MERGED ]** Stop comparing `font-family` in select listbox UA style test: [WPT PR 57098](https://github.com/web-platform-tests/wpt/pull/57098)
