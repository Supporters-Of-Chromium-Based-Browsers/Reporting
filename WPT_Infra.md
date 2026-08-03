# SOCBB WPT Infra Igalia Status Updates

## Jul 16, 2026 – Jul 30, 2026 (Weeks 29–30)

* **Spreadsheet:** [Tracking Sheet](https://docs.google.com/spreadsheets/d/14Q1zF9KocS-S94JBRbDFl3n7ymAZNMhOoFt3HMOJ9R0/edit?usp=sharing)

### Summary
Progress was made in WPT reftests for HDR and wide gamut color, page zoom / device pixel ratio testing, and mock devices for `getUserMedia()` tests.

### Topics & Tasks

#### WPT Reftests for HDR and Wide Gamut Color
* **Tracking Issue:** [Chrome Bug 483413433](https://issues.chromium.org/issues/483413433)
* **WebDriver BiDi Standardization Proposal (non-sRGB/HDR screenshots):**
  * Updated WebDriver BiDi proposal to align with an encoded-image-first approach: [WebDriver BiDi Issue 1114](https://github.com/w3c/webdriver-bidi/issues/1114). Awaiting feedback/discussion.
* **Implementation Feasibility & Integration Plan (Chromium + WPT Infra):**
  * *(Internal review in progress)* WPT-side RFC draft for runner changes needed to consume non-sRGB/HDR screenshots.
  * Incorporated Interop JPEG XL feedback ([Interop JPEG XL Issue 2](https://github.com/web-platform-tests/interop-jpegxl/issues/2)) into the main design.
  * Finalized `reftest-color-space` as root-test metadata applying to the complete reference graph.
  * Scoped `display-p3/image/png` as the first end-to-end combination.
  * Kept exact comparison for the initial path, while allowing tightly bounded fuzzy comparison for JPEG XL cases where decoding is not bit-exact.
* **Pull Requests & Commits:**
  * **[ MERGED ]** Add fuzzy matching to specific `jpegxl` tests: [WPT PR 61191](https://github.com/web-platform-tests/wpt/pull/61191)
  * **[ MERGED ]** Add fuzzy matching to `jpegxl/cmyk-basic-conversion-reftest`: [WPT PR 61407](https://github.com/web-platform-tests/wpt/pull/61407)
  * *(Not published yet)* Add support for `reftest-color-space`: [Commit e69f657](https://github.com/eerii/wpt/commit/e69f657ec01cde134379cb09bd1fc3bcd5d7175d)
  * *(Not published yet)* Pass `reftest-color-space` to WebDriver BiDi screenshots: [Commit 9dd7176](https://github.com/eerii/wpt/commit/9dd717659adb0763a4bf7955823f84bee06f6ce1)
  * Drafted a validator for color-preserving comparison.

#### Page Zoom / Device Pixel Ratio Testing
* **Tracking Issue:** [Chrome Bug 489737943](https://issues.chromium.org/issues/489737943)
* **[ IN REVIEW ]** Expose BiDi `browsingContext.setViewport` to regular WPT tests: [WPT PR 59265](https://github.com/web-platform-tests/wpt/pull/59265)
  * Addressed reviewer feedback: moved test to `infrastructure/testdriver/bidi/browsing_context/` and metadata to corresponding `infrastructure/metadata/` path.
  * Removed additional rendering wait after review discussion and updated metadata to use per-subtest expectations.
  * Declarative DPR mechanism suggested as possible follow-up work.

#### Mock Devices for `getUserMedia()` Tests
* **Tracking Issue:** [Chrome Bug 489736656](http://crbug.com/489736656)
* **[ IN PROGRESS ]** Implement virtual-device-only mode in `VirtualDeviceEnabledDeviceFactory` with unit tests: [Chromium CL 8137140](https://chromium-review.googlesource.com/c/chromium/src/+/8137140)

---

## Jul 2, 2026 – Jul 16, 2026 (Weeks 27–28)

* **Scope:** Analyzing, triaging, and fixing infrastructure issues in the WPT repository to enhance cross-platform testing for Chromium features.
* **Spreadsheet:** [Tracking Sheet](https://docs.google.com/spreadsheets/d/14Q1zF9KocS-S94JBRbDFl3n7ymAZNMhOoFt3HMOJ9R0/)

### Summary
Incorporated `interop-jpegxl` feedback into the WPT-side RFC draft and landed the mock camera backend patch.

### Topics & Tasks

#### WPT Reftests for HDR and Wide Gamut Color
* **Tracking Issue:** [Chrome Bug 483413433](https://issues.chromium.org/issues/483413433)
* **Interop JPEG XL Input:** [Interop JPEG XL Issue 2](https://github.com/web-platform-tests/interop-jpegxl/issues/2)
  * Priorities clarified: wide-gamut SDR automation starting with Adobe RGB / Display-P3 / Rec.2020; initial HDR targets focusing on PQ / HLG; gain maps reserved for later.
  * **[ DONE ]** Incorporated feedback into WPT-side RFC draft.
* **WebDriver BiDi Proposal:** [WebDriver BiDi Issue 1114](https://github.com/w3c/webdriver-bidi/issues/1114) (Awaiting feedback).

#### Page Zoom / Device Pixel Ratio Testing
* **Tracking Issue:** [Chrome Bug 489737943](https://issues.chromium.org/issues/489737943)
* **[ IN REVIEW ]** Expose BiDi `browsingContext.setViewport` to regular WPT tests: [WPT PR 59265](https://github.com/web-platform-tests/wpt/pull/59265)

#### Mock Devices for `getUserMedia()` Tests
* **Tracking Issue:** [Chrome Bug 489736656](http://crbug.com/489736656)
* **[ DONE ]** Landed mock camera backend patch: [Chromium CL 7991297](https://chromium-review.googlesource.com/c/chromium/src/+/7991297)
  * Added reusable `MockCameraDevice` and `MockCaptureDeviceController` helpers backed by Chromium's virtual device path.
  * Added browser tests for add/remove/reset, `enumerateDevices()` exposure, `devicechange`, exact `deviceId` targeting, and real video frame delivery.
* Investigating follow-up WebDriver/BiDi command integration.

---

## Jun 18, 2026 – Jul 2, 2026 (Weeks 25–26)

* **Scope:** Analyzing, triaging, and fixing infrastructure issues in the WPT repository.
* **Spreadsheet:** [Tracking Sheet](https://docs.google.com/spreadsheets/d/14Q1zF9KocS-S94JBRbDFl3n7ymAZNMhOoFt3HMOJ9R0/)

### Summary
Work continued on the main three tasks, with mock-device support progressing for `getUserMedia()`.

### Topics & Tasks

* **Mock Devices for `getUserMedia()` Tests**
  * **[ IN PROGRESS ]** Finalizing mock camera backend patch before review: [Chromium CL 7991297](https://chromium-review.googlesource.com/c/chromium/src/+/7991297)

---

## Jun 3, 2026 – Jun 18, 2026 (Weeks 23–24)

* **Scope:** Analyzing, triaging, and fixing infrastructure issues in the WPT repository.
* **Spreadsheet:** [Tracking Sheet](https://docs.google.com/spreadsheets/d/14Q1zF9KocS-S94JBRbDFl3n7ymAZNMhOoFt3HMOJ9R0/)

### Topics & Tasks

* **WPT Reftests for HDR and Wide Gamut Color**
  * WebDriver BiDi Proposal: [WebDriver BiDi Issue 1114](https://github.com/w3c/webdriver-bidi/issues/1114)
  * Refining WPT-side RFC draft for runner changes needed for non-sRGB/HDR screenshots.
* **Page Zoom / Device Pixel Ratio Testing**
  * **[ IN REVIEW ]** Expose BiDi `browsingContext.setViewport` to regular WPT tests: [WPT PR 59265](https://github.com/web-platform-tests/wpt/pull/59265)
* **Mock Devices for `getUserMedia()` Tests**
  * **[ DONE ]** Extract reusable mock camera implementation (`mock_camera_device.{h,cc}`). Passed proof tests.
  * **[ DONE ]** Added and validated `MockCaptureDeviceController` for managing add/remove/reset behavior.
  * **[ IN PROGRESS ]** Preparing mock camera backend patch for review.

---

## Apr 22, 2026 – Jun 3, 2026 (Weeks 21–22)

* **Scope:** Analyzing, triaging, and fixing infrastructure issues in the WPT repository.
* **Spreadsheet:** [Tracking Sheet](https://docs.google.com/spreadsheets/d/14Q1zF9KocS-S94JBRbDFl3n7ymAZNMhOoFt3HMOJ9R0/)

### Topics & Tasks

* **WPT Reftests for HDR and Wide Gamut Color**
  * Filed WebDriver BiDi standardization proposal: [WebDriver BiDi Issue 1114](https://github.com/w3c/webdriver-bidi/issues/1114).
  * Continued drafting WPT-side RFC for runner changes.
* **Page Zoom / Device Pixel Ratio Testing**
  * **[ IN REVIEW ]** Expose BiDi `browsingContext.setViewport` to regular WPT tests: [WPT PR 59265](https://github.com/web-platform-tests/wpt/pull/59265)
* **Mock Devices for `getUserMedia()` Tests**
  * **[ DONE ]** Confirmed Chromium runtime virtual camera path supports core mock-device behaviors.
  * **[ DONE ]** Validated runtime virtual camera lifecycle with proof tests.
  * **[ IN PROGRESS ]** Extracting reusable `mock_camera_device.{h,cc}` implementation.

---

## Apr 7, 2026 – Apr 22, 2026 (Weeks 15–16)

* **Scope:** Analyzing, triaging, and fixing infrastructure issues in the WPT repository.
* **Spreadsheet:** [Tracking Sheet](https://docs.google.com/spreadsheets/d/14Q1zF9KocS-S94JBRbDFl3n7ymAZNMhOoFt3HMOJ9R0/)

### Topics & Tasks

* **WPT Reftests for HDR and Wide Gamut Color**
  * Drafted spec direction to extend `browsingContext.captureScreenshot` with `colorSpace` + `pixelFormat` and a deterministic raw pixel output mode (`image/x-raw-rgba`).
  * Drafted WPT RFC outline for `wptrunner` plumbing.
* **Page Zoom / Device Pixel Ratio Testing**
  * **[ WIP ]** Expose BiDi `browsingContext.setViewport` to regular WPT tests: [WPT PR 59265](https://github.com/web-platform-tests/wpt/pull/59265)

---

## Mar 25, 2026 – Apr 7, 2026 (Weeks 13–14)

* **Scope:** Analyzing, triaging, and fixing infrastructure issues in the WPT repository.
* **Spreadsheet:** [Tracking Sheet](https://docs.google.com/spreadsheets/d/14Q1zF9KocS-S94JBRbDFl3n7ymAZNMhOoFt3HMOJ9R0/)

### Topics & Tasks

* **Retrieve Console Output Automatically**
  * **[ DONE ]** Convert console manual tests to BiDi-based automation: [Chromium CL 765732](https://chromium-review.googlesource.com/c/chromium/src/+/765732)
  * **[ WONTFIX ]** Fix `dirxml %s` formatting for Symbols in `entry.text`: [Chromium-BiDi PR 4123](https://github.com/GoogleChromeLabs/chromium-bidi/pull/4123) (Working as intended per BiDi spec; tracked in [WebDriver BiDi Issue 89](https://github.com/w3c/webdriver-bidi/issues/89)).
* **WPT Reftests for HDR and Wide Gamut Color**
  * Opened companion discussion in [Interop JPEG XL Issue 2](https://github.com/web-platform-tests/interop-jpegxl/issues/2).
* **Page Zoom / Device Pixel Ratio Testing**
  * Started investigating testing approaches in WPT.

---

## Mar 11, 2026 – Mar 25, 2026 (Weeks 11–12)

* **Scope:** Analyzing, triaging, and fixing infrastructure issues in the WPT repository to enhance cross-platform testing for Chromium features.
* **Spreadsheet:** [Tracking Sheet](https://docs.google.com/spreadsheets/d/14Q1zF9KocS-S94JBRbDFl3n7ymAZNMhOoFt3HMOJ9R0/)

### Topics & Tasks

* **Retrieve Console Output Automatically**
  * **[ REVIEW ]** Convert console manual tests to BiDi-based automation: [Chromium CL 7657323](https://chromium-review.googlesource.com/c/chromium/src/+/7657323)
  * Verified fix for `console.dirxml()` formatting issue in `chromium-bidi`.
* **WPT Reftests for HDR and Wide Gamut Color**
  * Scoped requirements: HDR/wide-gamut testing requires screenshot changes across specs, Chromium capture/encoding, ChromeDriver/WebDriver, and `wptrunner`.
* **Issue Triaging**
  * Reviewed open `type:untestable` WPT issues and created Chromium candidate tracking issues for script-closable session history checks and native find-in-page search results.
