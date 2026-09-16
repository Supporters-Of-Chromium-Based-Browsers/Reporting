# SOCBB WPT Tests Igalia Status Updates

## August 24 - September 6 2026 (Weeks 35-36)

**Scope:** Improving the state of web tests in Chromium-based browsers.

**Spreadsheet:** https://docs.google.com/spreadsheets/d/14Q1zF9KocS-S94JBRbDFl3n7ymAZNMhOoFt3HMOJ9R0/edit?usp=sharing

### Summary
This is a report covering weeks 35-36. Of highlight, implementing the `side` attribute on SVGTextPathElement, scrolling anchor-positioned fixed boxes into view on focus, and resetting font orientation for canvas 2D fonts were all merged, and a large number of stale test expectations and content_shell.filter entries were cleaned up.

### Test Expectations

#### `side` attribute on SVGTextPathElement
- Implement the `side` attribute on SVGTextPathElement ("left"/"right") (crbug.com/40362379, crbug.com/499073687)
  - [Merged] https://crrev.com/c/8220847
  - Currently at the Prepare to Ship stage: https://chromestatus.com/feature/5422782593761280

#### Scroll anchor-positioned fixed boxes into view on focus
- crbug.com/469481151
  - [Merged] https://crrev.com/c/8311148
    - Reverted once due to flaky failures only in virtual/fragmented-oof-in-cb. Relanded with TestExpectations entries added for this virtual suite.

#### Canvas 2D font orientation
- Reset font orientation when resolving canvas 2D fonts (crbug.com/433324167)
  - [Merged] https://crrev.com/c/8238611

#### Stale idlharness.https.any expectations for webtransport
- Remove stale idlharness.https.any expectations for webtransport (crbug.com/430125723)
  - [Merged] https://crrev.com/c/8301393

#### Allow empty body in fetchLater()
- crbug.com/507904104
  - [Review] https://crrev.com/c/8342967

#### object-position-svg reftests fuzzy matching
- Add fuzzy match to object-position-svg reftests (crbug.com/40747033)
  - [Review] https://crrev.com/c/8343367

#### text-combine-upright-compression reftests stabilization
- Stabilize text-combine-upright-compression reftests (crbug.com/40527323)
  - [WIP] https://crrev.com/c/8357089

#### Test expectations cleanup
- [Merged] Remove redirect expectation from TestExpectations - https://chromium-review.googlesource.com/c/chromium/src/+/8281983
- [Merged] Remove view transitions tests from TestExpectations - https://chromium-review.googlesource.com/c/chromium/src/+/8342418

#### content_shell.filter cleanup
- [Merged] Remove css contain tests from content_shell.filter - https://chromium-review.googlesource.com/c/chromium/src/+/8310012
- [Merged] Remove CSS flexbox tests from content_shell.filter - https://chromium-review.googlesource.com/c/chromium/src/+/8310352
- [Merged] Remove CSS color test from content_shell.filter - https://chromium-review.googlesource.com/c/chromium/src/+/8301393
- [Merged] Remove CSS display tests from content_shell.filter - https://chromium-review.googlesource.com/c/chromium/src/+/8309374
- [Merged] Remove CSS highlight tests from content_shell.filter - https://chromium-review.googlesource.com/c/chromium/src/+/8310467

### Internal Tests

#### Internal Tests already covered by WPT (crbug.com/485677942)
- Migrate MSE multiple-attach/sourcebufferlist coverage to WPT
  - [Merged] https://crrev.com/c/8254912
- Migrate XHR reuse-after-completion tests to WPT
  - [Review] https://crrev.com/c/8174325


## Aug 10 - Aug 23, 2026 (Weeks 33-34)

**Scope:** Improving the state of web tests in Chromium-based browsers.
**Spreadsheet:** https://docs.google.com/spreadsheets/d/14Q1zF9KocS-S94JBRbDFl3n7ymAZNMhOoFt3HMOJ9R0/edit?usp=sharing


### Summary
This is a report covering weeks 33-34. Of highlight from the last two weeks, a fix to hide the scrollbar in transform-iframe-scroll-position was merged, work continued on exposing the `side` attribute on SVGTextPathElement and on resetting font orientation for canvas 2D fonts, and a large number of stale test expectations and content_shell.filter entries were cleaned up.

### Test Expectations

#### `side` attribute on SVGTextPathElement
- Expose the `side` attribute on SVGTextPathElement, supporting "left" and "right" values — for side="right", text positions are mapped from the end of the path and the tangent direction is reversed (crbug.com/40362379, crbug.com/499073687)
  - [Review] [SVG] Implement the side attribute for textPath - https://chromium-review.googlesource.com/c/chromium/src/+/8220847
    - Currently going through Blink's Intent to Prototype process (https://chromestatus.com/feature/5422782593761280)

#### Canvas 2D font orientation
- Reset font orientation when resolving canvas 2D fonts — canvas 2D fonts must use horizontal orientation regardless of the canvas element's writing mode (crbug.com/433324167)
  - [Review] Reset font orientation when resolving canvas 2D fonts - https://chromium-review.googlesource.com/c/chromium/src/+/8238611

#### transform-iframe-scroll-position scrollbar
- Hide scrollbar in transform-iframe-scroll-position — the iframe's own scrollbar was showing up and breaking the pixel comparison against the reference, unrelated to the rotate transform (crbug.com/332572643)
  - [Merged] Hide scrollbar in transform-iframe-scroll-position - https://chromium-review.googlesource.com/c/chromium/src/+/8228246

#### Obsolete/stale test expectations cleanup
- [Merged] Remove obsolete test expectations for fenced frame anchor focus - https://chromium-review.googlesource.com/c/chromium/src/+/8235952
- [Done] Remove obsolete selectedcontent-nested test expectations - https://chromium-review.googlesource.com/c/chromium/src/+/8262708
- [Done] Remove stale TestExpectation for svg painting test - https://chromium-review.googlesource.com/c/chromium/src/+/8180969
- [Done] Remove stale TestExpectations entries for critical-ch tests on Linux - https://chromium-review.googlesource.com/c/chromium/src/+/8187834
- [Done] Remove stale TestExpectation and orphaned baseline for v8 test - https://chromium-review.googlesource.com/c/chromium/src/+/8251177
- [Done] Remove stale TestExpectations entry for table-border-1.html - https://chromium-review.googlesource.com/c/chromium/src/+/8246400
- [Reverted] Rebaseline hit-test-counts.html and remove stale expectation - https://chromium-review.googlesource.com/c/chromium/src/+/8248121
- [Done] Remove stale TestExpectation for scrolling test - https://chromium-review.googlesource.com/c/chromium/src/+/8249580
- [Done] Remove stale TestExpectations for fetch metadata test - https://chromium-review.googlesource.com/c/chromium/src/+/8249580
- [Done] Remove obsolete performance-measure-null-exception.html test - https://chromium-review.googlesource.com/c/chromium/src/+/8254358
  - This test was checking if passing 'null' to a function threw an error, but that is now an allowed value, so the test is no longer needed
- [Done] Remove stale TestExpectations entry for scrollbar-thumb-snapping - https://chromium-review.googlesource.com/c/chromium/src/+/8254358
- [Done] Remove stale TestExpectations entries for autoplay timeout tests - https://chromium-review.googlesource.com/c/chromium/src/+/8259763
- [Done] Remove stale CSP test from TestExpectations - https://chromium-review.googlesource.com/c/chromium/src/+/8264847
- [Done] Remove stale client hints test from TestExpectations - https://chromium-review.googlesource.com/c/chromium/src/+/8263084
- [Done] Remove TestExpectations entries for view-transition tests - https://chromium-review.googlesource.com/c/chromium/src/+/8252217
- [Done] Remove stale embedded content TestExpectations entry - https://chromium-review.googlesource.com/c/chromium/src/+/8260959
- [Reverted] Remove TestExpectation and baseline for wheel-event-transactions - https://chromium-review.googlesource.com/c/chromium/src/+/8243709

#### content_shell.filter cleanup
- [Done] Remove background fetch test from content_shell.filter - https://chromium-review.googlesource.com/c/chromium/src/+/8184836
- [Done] Remove compositing tests from content_shell.filter - https://chromium-review.googlesource.com/c/chromium/src/+/8187699
- [Done] Remove css anchor position tests from content_shell.filter - https://chromium-review.googlesource.com/c/chromium/src/+/8259126
- [Done] Specify failing css break test in content_shell.filter - https://chromium-review.googlesource.com/c/chromium/src/+/8264250
- [Done] Remove CSS backgrounds tests from content_shell.filter - https://chromium-review.googlesource.com/c/chromium/src/+/8265745
- [Done] Mark inline formatting context tests NeverFix on all platforms - https://chromium-review.googlesource.com/c/chromium/src/+/8269721
- [Done] Remove CSS2 tests from content_shell.filter - https://chromium-review.googlesource.com/c/chromium/src/+/8263451
- [Done] Remove CSS conditional tests from content_shell.filter - https://chromium-review.googlesource.com/c/chromium/src/+/8272492

### Internal Tests

#### Internal Tests already covered by WPT (crbug.com/485677942)
- Migrate internal tests to WPT
  - [Merged] Migrate MSE endofstream-invaliderror tests to WPT - https://chromium-review.googlesource.com/c/chromium/src/+/8129277
  - [Review] Migrate MSE multiple-attach/sourcebufferlist coverage to WPT - https://chromium-review.googlesource.com/c/chromium/src/+/8254912
  - [Review] Migrate XHR reuse-after-completion tests to WPT - https://chromium-review.googlesource.com/c/chromium/src/+/8174325


## July 27, 2026 - Aug 7, 2026 (Weeks 31-32)

* **Scope:** Improving the state of web tests in Chromium-based browsers.
* **Spreadsheet:** [Tracking Sheet](https://docs.google.com/spreadsheets/d/1rceYcaQiR7n6VOF59emYP1KlnGHZ3QizDlxnH-zaKYI)

### Summary
This is a report covering weeks 31-32. There was work in many areas related to WPT test expectations over the last two weeks. Of highlight, fixes for captureStream() tracks not restarting after playback ends and for execute_async_script crashing with a null timeout were both merged, fuzzy matching was added to several reftests, and internal XMLHttpRequest and MSE tests continued to be removed or migrated to WPT.

### Test Expectations

#### `side` attribute on SVGTextPathElement
- [WIP] Expose the `side` attribute on SVGTextPathElement, supporting "left" and "right" values - for side="right", text positions are mapped from the end of the path and the tangent direction is reversed (crbug.com/40362379, crbug.com/499073687)
  - [WIP] [SVG] Implement the side attribute for textPath - https://chromium-review.googlesource.com/c/chromium/src/+/8220847

#### captureStream() tracks not restarting after playback ends
- Fix captureStream() tracks not restarting after playback ends - the captured tracks never fired an "ended" event, so now their sources are stopped via DidStopMediaStreamSource() instead of stopTrack(), and the tracks are recreated when playback restarts (crbug.com/484258336)
  - [Merged] Fix captureStream() tracks not restarting after playback ends - https://chromium-review.googlesource.com/c/chromium/src/+/8184757

#### execute_async_script crash when script timeout is null
- Fix execute_async_script crash when script timeout is null - a null timeout maps to base::TimeDelta::Max(), which can't be stored in a base::Value, so the JS timeout argument is now omitted in that case since undefined is treated as no timeout (crbug.com/479872440)
  - [Merged] Fix execute_async_script crash when script timeout is null - https://chromium-review.googlesource.com/c/chromium/src/+/8190774

#### Fix bugs in the test files themselves
- [Merged] Preserve CRLF in meta charset boundary tests - https://chromium-review.googlesource.com/c/chromium/src/+/8198964 (crbug.com/40834455)
  - Git's EOL normalization was stripping intentional CR bytes, shifting the meta charset position relative to the 1024-byte boundary - disabled Git text conversion for these files and restored the CR bytes
- [Merged] Fix clipboard permissions-policy tests timing out - https://chromium-review.googlesource.com/c/chromium/src/+/8185536 (crbug.com/492280259)
  - The tests sent `{enabled: true/false}`, but `test_feature_availability()` filters on `evt.data.type === 'availability-result'`, so `test.done()` was never called - added the missing `type` field
- [Merged] Add long timeout to 3 accname tests - https://chromium-review.googlesource.com/c/chromium/src/+/8129542 (crbug.com/443203688)
  - These tests generate many dynamic test cases and can exceed the default 10s testharness timeout

#### Canvas 2D stroke pruning
- [Merged] Fix canvas 2D stroke pruning of degenerate zero-length path segments - https://chromium-review.googlesource.com/c/chromium/src/+/8057524
  - Code fix in 2d canvas in the renderer that accounts for zero-length segments by pruning them

#### Fragmentation test baseline
- [Merged] Add missing baseline for fragmentation test - https://chromium-review.googlesource.com/c/chromium/src/+/8073953

#### Fuzzy matching for reftests
- [Merged] Add fuzzy match to jpegxl reftest for JXL's rounding difference - https://chromium-review.googlesource.com/c/chromium/src/+/8173443 (crbug.com/507903802)
- [Merged] Add fuzzy match to rotate keyframes animation reftest - https://chromium-review.googlesource.com/c/chromium/src/+/8173664 (crbug.com/499073688)

#### Obsolete test expectations cleanup
- [Merged] Remove obsolete MathML anchor test expectations - https://chromium-review.googlesource.com/c/chromium/src/+/8138000
- [Merged] Remove obsolete Application panel sidebar test expectations - https://chromium-review.googlesource.com/c/chromium/src/+/8162042
- [Merged] Remove obsolete mixed-content audio/video-tag test expectations - https://chromium-review.googlesource.com/c/chromium/src/+/8198005
- [Merged] Remove obsolete vertical-alignment-slr test expectations - https://chromium-review.googlesource.com/c/chromium/src/+/8206247
- [Merged] Remove obsolete cross-origin fullscreen test expectations - https://chromium-review.googlesource.com/c/chromium/src/+/8200047
- [Merged] Remove stale TestExpectations for prerender same-origin subframe test - https://chromium-review.googlesource.com/c/chromium/src/+/8170045
- [Merged] Remove stale Linux-only scroll-animations TestExpectations entries - https://chromium-review.googlesource.com/c/chromium/src/+/8169783
- [Merged] Remove stale TestExpectations for http test failures - https://chromium-review.googlesource.com/c/chromium/src/+/8089256
- [Merged] Remove stale Linux canvas-imageSmoothing TestExpectations entry - https://chromium-review.googlesource.com/c/chromium/src/+/8089061
- [Merged] Remove windows scroll animations from TestExpectations - https://chromium-review.googlesource.com/c/chromium/src/+/8182328
- [Merged] Remove TestExpectations entries for threaded composited iframe tests - https://chromium-review.googlesource.com/c/chromium/src/+/8181047
- [Merged] Remove stale Mac scroll-animations tests from TestExpectations - https://chromium-review.googlesource.com/c/chromium/src/+/8178986
- [Merged] Remove stale TestExpectations entry for CSS image animation test - https://chromium-review.googlesource.com/c/chromium/src/+/8179287

#### content_shell.filter cleanup
- [Merged] Remove css2 borders tests from content_shell.filter - https://chromium-review.googlesource.com/c/chromium/src/+/8183972

### Internal Tests

#### Internal Tests already covered by WPT (crbug.com/485677942)
- Remove redundant internal tests
  - [Merged] Remove redundant XMLHttpRequest tests from xmlhttprequest/web-apps - https://chromium-review.googlesource.com/c/chromium/src/+/8173803
- Migrate internal tests to WPT
  - [Review] Migrate XHR reuse-after-completion tests to WPT - https://chromium-review.googlesource.com/c/chromium/src/+/8174325
  - [Review] Migrate MSE endofstream-invaliderror tests to WPT - https://chromium-review.googlesource.com/c/chromium/src/+/8129277

#### WPT crashtest migrations
- [Merged] Migrate css-syntax atrule-with-escape-character crashtest to WPT - https://chromium-review.googlesource.com/c/chromium/src/+/8169945
- [Merged] Migrate CSS2 float-append-child crashtest to WPT - https://chromium-review.googlesource.com/c/chromium/src/+/8187614


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
