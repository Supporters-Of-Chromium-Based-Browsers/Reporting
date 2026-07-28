

# SOCBB Bugfixing Igalia Status Update 

Reporting Period:  Jul 2, 2026- Jul 16, 2026

Scope: Bugfixing across Chromium codebase, focusing on UI/UX issues, web standards compliance, and platform-specific behavior

---


This is a report covering the work done during weeks 27-28.

We spent time working to finish up the overlay scrollbars and BaseAudioContext bugs. There are still a few remaining items related to these bugs but we have started to direct resourcing to the other projects per the meeting that was had about priorities.

Spreadsheet:[ ](https://docs.google.com/spreadsheets/d/1V-dIz78giXXi1VhC6ScbO8Qi716EOHl5XlofQDG6-jM/)SOCBB - Bugfixing Status (https://docs.google.com/spreadsheets/d/1V-dIz78giXXi1VhC6ScbO8Qi716EOHl5XlofQDG6-jM/)


### [Medium] Mac overlay scrollbars only show briefly when putting two fingers down on touchpad ([crbug.com/445900719](http://crbug.com/445900719))



* Done
    * Wheel events silently dropped during Pointer Lock after accumulated mouse movement ([crbug.com/497060679](http://crbug.com/497060679) - Closed)
        * Forward wheel events to main thread when pointer is locked. ([crrev.com/c/8022943](http://crrev.com/c/8022943) - Merged)
    * regressions in rendering.desktop ([crbug.com/514535246](http://crbug.com/514535246) - Closed)
        * Fixed by enabling kDeferFadeOutScrollbarUntilMouseWheelEnded ([crrev.com/c/7917390](http://crrev.com/c/7917390))
* TODO
    * regressions in system_health.memory_desktop ([crbug.com/524827663](http://crbug.com/524827663))
        * Going to unassign as it is not related to scrollbar fade-in/out but wheel event forwarding
            * CL for testing:[ crrev.com/c/7961933](http://crrev.com/c/7961933)
            * Pinpoint result:[ https://pinpoint-dot-chromeperf.appspot.com/job/13d12d51c90000](https://pinpoint-dot-chromeperf.appspot.com/job/13d12d51c90000)


### [Large] BaseAudioContext should not skip suspended state upon construction ([crbug.com/40140417](http://crbug.com/40140417))



* Done
    * Cleanup pending_resume_resolvers_ handling in AudioContext ([crrev.com/c/8000610](http://crrev.com/c/8000610) - In review)
    * Relocate script promise resolver vector for pending promises ([crrev.com/c/8001352](http://crrev.com/c/8001352) - In review)
    * Store pending suspend/resume promises in BaseAudioContext's list ([crrev.com/c/8010828](http://crrev.com/c/8010828) - In review)
* TODO
    * Merge the on-going CLs
    * Enable AudioContextAsyncStateTransitions after m151 is on stable. (after checking updated use counters)


# SOCBB Bugfixing Igalia Status Update 

Reporting Period:  Jun 18, 2026- Jul 2, 2026

 Scope: Bugfixing across Chromium codebase, focusing on UI/UX issues, web standards compliance, and platform-specific behavior

---


This is a report covering weeks 25 & 26

We continued work on the performance regressions related to the Mac overlay scrollbars and on the BaseAudioContext issue.

Spreadsheet:[ ](https://docs.google.com/spreadsheets/d/1V-dIz78giXXi1VhC6ScbO8Qi716EOHl5XlofQDG6-jM/)SOCBB - Bugfixing Status (https://docs.google.com/spreadsheets/d/1V-dIz78giXXi1VhC6ScbO8Qi716EOHl5XlofQDG6-jM/)


### [Medium] Mac overlay scrollbars only show briefly when putting two fingers down on touchpad ([crbug.com/445900719](http://crbug.com/445900719))



* Enable deferring fade-out again
    * re-enable deferring fade-out with wheel event forwarding ([crrev.com/c/7917390](http://crrev.com/c/7917390) - Merged)
    * Performance impact
        * Rendering perf. metric improvement ([crbug.com/481442206](http://crbug.com/481442206),[ crbug.com/514535246](http://crbug.com/514535246))
            * Skip main frame production throttle during pinch zoom ([crrev.com/c/7917117](http://crrev.com/c/7917117) - In review)
        * Memory perf. regression on macOS ([crbug.com/524827663](http://crbug.com/524827663))
    * Related bug
        * Wheel events silently dropped during Pointer Lock after accumulated mouse movement ([crbug.com/497060679](http://crbug.com/497060679))


### [Large] BaseAudioContext should not skip suspended state upon construction ([crbug.com/40140417](http://crbug.com/40140417))



* Count kAudioContextAsyncTransitionToSuspendedStateRead on stable ([crrev.com/c/7901980](http://crrev.com/c/7901980) - Merged)
* Relocate script promise resolver vector for pending resume promises ([crrev.com/c/7989780](http://crrev.com/c/7989780) - Merged)
* Cleanup pending_resume_resolvers_ handling in AudioContext ([crrev.com/c/8000610](http://crrev.com/c/8000610) - In review)
* Relocate script promise resolver vector for pending promises ([crrev.com/c/8001352](http://crrev.com/c/8001352) - In review)
* Store pending suspend/resume promises in BaseAudioContext's list ([crrev.com/c/8010828](http://crrev.com/c/8010828) - WIP)


### [Large] There are too many systems for configuring features ([crbug.com/469041913](http://crbug.com/469041913) - On hold)


### [Large] Seams between layers with subpixel transforms or transform animations ([crbug.com/401515597](http://crbug.com/401515597) - On hold)


# SOCBB Bugfixing Igalia Status Update 

Reporting Period:  Jun 3, 2026- Jun 18, 2026

 Scope: Bugfixing across Chromium codebase, focusing on UI/UX issues, web standards compliance, and platform-specific behavior

---


This is a report covering weeks 23 & 24.

We continued work on the performance regressions related to the Mac overlay scrollbars, and began work on the BaseAudioContext issue.

Spreadsheet: SOCBB - Bugfixing Status ([https://docs.google.com/spreadsheets/d/1V-dIz78giXXi1VhC6ScbO8Qi716EOHl5XlofQDG6-jM/](https://docs.google.com/spreadsheets/d/1V-dIz78giXXi1VhC6ScbO8Qi716EOHl5XlofQDG6-jM/)

[Medium] Mac overlay scrollbars only show briefly when putting two fingers down on touchpad ([crbug.com/445900719](http://crbug.com/445900719))



* Enable deferring fade-out again
    * trigger deferred fade-out without forwarding event ([crrev.com/c/7870415](http://crrev.com/c/7870415) - Abandoned after review)
    * re-enable deferring fade-out with wheel event forwarding ([crrev.com/c/7917390](http://crrev.com/c/7917390) - In review)
* Wheel event over spin button triggers step action with passive=true event handler on body ([crbug.com/516844151](http://crbug.com/516844151) - Fixed)
    * Skip spin button action if wheel event can scroll ([crrev.com/c/7884831](http://crrev.com/c/7884831) - Abandoned after review)
    * (by flackr@) Ensure when spin button handles wheel scroll is prevented. ([crrev.com/c/7901499](http://crrev.com/c/7901499) - Merged)
* Scrollbar fades-in over a focused number input ([crbug.com/521373842](http://crbug.com/521373842) - Won’t fix)
    * Don’t fade in scrollbar on may-begin wheel over a blocking wheel handler ([crrev.com/c/](http://crrev.com/c/) 7911343 - Abandoned after review)
* Perf metric improvement with wheel event forwarded ([crbug.com/481442206](http://crbug.com/481442206), [crbug.com/514535246](http://crbug.com/514535246))
    * Skip main frame production throttle during pinch zoom ([crrev.com/c/7917117](http://crrev.com/c/7917117) - In review)


### [Large] BaseAudioContext should not skip suspended state upon construction ([crbug.com/40140417](http://crbug.com/40140417))



* Record AudioContext async state-transition UseCounters with feature off
    * Avoid recording AudioContext state-read UseCounters when logging ([crrev.com/c/7901898](http://crrev.com/c/7901898) - Merged)
    * Count kAudioContextAsyncStateTransitions regardless of the feature ([crrev.com/c/7901426](http://crrev.com/c/7901426) - Merged)
    * Count kAudioContextAsyncTransitionToRunningStateRead on stable ([crrev.com/c/7901815](http://crrev.com/c/7901815) - Merged)
    * Count kAudioContextAsyncTransitionToSuspendedStateRead on stable ([crrev.com/c/7901980](http://crrev.com/c/7901980) - In review)


### [Large] There are too many systems for configuring features ([crbug.com/469041913](http://crbug.com/469041913) - On hold)


### [Large] Seams between layers with subpixel transforms or transform animations ([crbug.com/401515597](http://crbug.com/401515597) - On hold)


# SOCBB Bugfixing Igalia Status Update 

Reporting Period:  Apr 22, 2026- Jun 3, 2026

 Scope: Bugfixing across Chromium codebase, focusing on UI/UX issues, web standards compliance, and platform-specific behavior

---


This is a report covering weeks 21 & 22.

We have been working on some performance regressions related to a previous fix for Mac overlay scrollbars. We'll retake the work on the BaseAudioContext issue to see if we can get it shipped.

Spreadsheet: [https://docs.google.com/spreadsheets/d/1V-dIz78giXXi1VhC6ScbO8Qi716EOHl5XlofQDG6-jM/](https://docs.google.com/spreadsheets/d/1V-dIz78giXXi1VhC6ScbO8Qi716EOHl5XlofQDG6-jM/)


### [Medium] Mac overlay scrollbars only show briefly when putting two fingers down on touchpad ([crbug.com/445900719](http://crbug.com/445900719))



* Disable deferring fade-out to avoid regressions ([crrev.com/c/7835391](http://crrev.com/c/7835391) - Landed)
    * Regression on mouse wheel over focused spin button ([crbug.com/508306805](http://crbug.com/508306805) - Fixed)
    * Perf regression on Windows ([crbug.com/485669521](http://crbug.com/485669521) - Fixed)
* Re-enable deferring fade-out
    * trigger deferred fade-out without forwarding event ([crrev.com/c/7870415](http://crrev.com/c/7870415) - In Review)
* Wheel event over spin button triggers step action with passive=true event handler on body ([crbug.com/516844151](http://crbug.com/516844151))
    * Event forwarding was not the root cause.
    * Draft: Skip spin button action if wheel event can scroll ([crrev.com/c/7884831](http://crrev.com/c/7884831) - WIP)
* Performance improvement with the feature enabled
    * Issues:
        * Perf report on Linux ([crbug.com/481442206](http://crbug.com/481442206) - re-activated)
        * Perf report on macOS ([crbug.com/514535246](http://crbug.com/514535246) - new)
    * Narrowing down the root cause:
        * MainThreadEventQueue triggers BeginMainFrame with urgent = true for wheel events, which works as if the main frame throttling is skipped while pinch zooming
            * Dispatch a closure that triggers BeginMainFrame with urgent = false ([crrev.com/c/7885305](http://crrev.com/c/7885305))
                * macOS: No difference
            * Dispatch a closure that triggers BeginMainFrame with urgent = true ([crrev.com/c/7884828](http://crrev.com/c/7884828))
                * macOS: Improved (base = 26.2682 -> patched = 16.71045)
            * Skip main frame throttling while pinch zoom ([crrev.com/c/7888236](http://crrev.com/c/7888236))
                * macOS: Improved (base = 25.30415 -> patched = 16.1466)
                * Windows: Improved (base = 32.5233 -> patched = 12.4394)
                * Android: No difference (No regression)


### [Large] BaseAudioContext should not skip suspended state upon construction ([crbug.com/40140417](http://crbug.com/40140417))



* Began tracking.


### [Large] There are too many systems for configuring features ([crbug.com/469041913](http://crbug.com/469041913) - On hold)


### [Large] Seams between layers with subpixel transforms or transform animations ([crbug.com/401515597](http://crbug.com/401515597) - On hold)


# SOCBB Bugfixing Igalia Status Update 

Reporting Period:  Apr 7, 2026- Apr 22, 2026

 Scope: Bugfixing across Chromium codebase, focusing on UI/UX issues, web standards compliance, and platform-specific behavior

---


This is a report covering weeks 15 & 16. We're about to finish the hours in this contract, waiting for the renewal confirmation.

We have continued the analysis of the Enterprise Policy System, we're working on a document to share the current status and discuss the plan. We've also been investigating the issue related to seams between layers.

Spreadsheet: [https://docs.google.com/spreadsheets/d/1V-dIz78giXXi1VhC6ScbO8Qi716EOHl5XlofQDG6-jM/](https://docs.google.com/spreadsheets/d/1V-dIz78giXXi1VhC6ScbO8Qi716EOHl5XlofQDG6-jM/)

[Large] There are too many systems for configuring features



* Need to clarify the scope more precisely as the Enterprise Policy System is much more complex than expected
    * There are number of paths that forward EP to renderer
        * EP -> Prefs -> WebPreferences -> WebSettings
        * EP -> Prefs -> Command-line switch -> Runtime Enabled Features
        * EP -> Prefs -> RendererPreferences
        * EP -> Prefs -> Content Settings
        * EP -> Prefs -> RendererConfiguration
        * EP -> Prefs -> managedconfigurationchange DOM event / navigator.managed.getManagedConfiguration(keys) js call to pull from browser
    * There are number of update scope/lifecycle
        * update dynamically (per page / per renderer)
        * update at next commit navigation
        * apply once at renderer startup
    * The path variations are mostly implemented manually instead of deriving from yaml or json.
* Using Command-line switch is the only existing path of connecting EP to REF, but it has some limitations
    * Only 19 cases
    * Apply only once at renderer startup
    * There are inverted mapping between EP and switch
* Taking the above into account, the question is,
    * Is it OK to scope the task for the Command-line switch cases?
    * Or, should this task be finding a general solution for most cases?
        * If so, does it imply that this task can introduce some refactoring on forwarding Enterprise Policy status to renderer?
* Preparing a document to share the current implementation status to help communication:
    * [https://docs.google.com/document/d/1SD-8Mjx6uZrLoqKIAY7cEQjSoo0A60rEugJdSIbEBuo](https://docs.google.com/document/d/1SD-8Mjx6uZrLoqKIAY7cEQjSoo0A60rEugJdSIbEBuo)
    * List existing paths of forwarding Enterprise Policy status to renderer
    * List paths of receiving status from browser for Runtime Enabled Feature (WIP)

[Large] Seams between layers with subpixel transforms or transform animations



* Analyze 'DirectlyCompositedImage' case: trace the coordinations throughout drawing pipeline.
* Explore img at negative offset with wrapper div having will-change: opacity which makes the wrapper layer as DCI.
* Compare enable/disable gpu.


# SOCBB Bugfixing Igalia Status Update 

Reporting Period:  Mar 25, 2026- Apr 7, 2026

 Scope: Bugfixing across Chromium codebase, focusing on UI/UX issues, web standards compliance, and platform-specific behavior
 
---
This is a report covering weeks 13 & 14.


We have been working on a new large bug related to seams between layers, investigating the problem and how to reproduce it. On the configuring features issues we're exploring the new request approach by the reviewer and areas involved. Apart from that there has been some small work as follow-up of a previous fix.


# Spreadsheet: [https://docs.google.com/spreadsheets/d/1V-dIz78giXXi1VhC6ScbO8Qi716EOHl5XlofQDG6-jM/](https://docs.google.com/spreadsheets/d/1V-dIz78giXXi1VhC6ScbO8Qi716EOHl5XlofQDG6-jM/)


### [Large] There are too many systems for configuring features ([crbug.com/469041913](http://crbug.com/469041913))



* [WIP] Exploring relevant areas and feasible solutions.


### [Large] Seams between layers with subpixel transforms or transform animations ([crbug.com/401515597](http://crbug.com/401515597))



* The level of the bug has raised from Medium to Large. Took the bug and started investigation.
* Seams between tiles with non-integral zoom.
* Checked test links in the bug
    * [https://codepen.io/reesedrjones/pen/poBjJNp](https://codepen.io/reesedrjones/pen/poBjJNp) : amplifying rounding error by transform scale.
    * [https://jsfiddle.net/reesedrjones/ngcxkL1v/3/](https://jsfiddle.net/reesedrjones/ngcxkL1v/3/) : google map that has complex tile drawing scenario. Looks related to different rounding methods (ToPixelSnappedRect, ToEnclosingRect, ...) around painting, raster, compositing pipeline.
* Try to make simple test cases and check relevant code path.
* Have checked DirectlyCompositedImage cases and found one seam case with will-change: transform, which force DCI. But it looks not the all issue in the google map case.


### [Medium] Implement PRF on create for security keys ([crbug.com/420689820](http://crbug.com/420689820))



* Follow-up: Add hmac-secret-mc support to DevTools WebAuthn panel. (Done)
    * Add support to DevTools front-end ([chromium-review.googlesource.com/c/devtools/devtools-frontend/+/7683510](http://chromium-review.googlesource.com/c/devtools/devtools-frontend/+/7683510) / Landed)


### [Medium] Mac overlay scrollbars only show briefly when putting two fingers down on touchpad ([crbug.com/445900719](http://crbug.com/445900719))


* Follow-up: Windows perf regression ([crbug.com/485669521](http://crbug.com/485669521) / [crrev.com/c/7611009](http://crrev.com/c/7611009)) - No updates


# SOCBB Bugfixing Igalia Status Update 

Reporting Period:  Mar 11, 2026- Mar 25, 2026

 Scope: Bugfixing across Chromium codebase, focusing on UI/UX issues, web standards compliance, and platform-specific behavior

---


This is a report covering weeks 11 & 12.

Main part of the work continues to be on the large bug about configuring features, there has been discussion with the reviewers and some re-scope of the task. Working on the new agreed plan.

Apart from that there has been some follow-up work related to previous bugs we have fixed as part of the project.

Spreadsheet: [https://docs.google.com/spreadsheets/d/1V-dIz78giXXi1VhC6ScbO8Qi716EOHl5XlofQDG6-jM/](https://docs.google.com/spreadsheets/d/1V-dIz78giXXi1VhC6ScbO8Qi716EOHl5XlofQDG6-jM/)


### [Large] There are too many systems for configuring features ([crbug.com/469041913](http://crbug.com/469041913))



* Finished the proposal draft, shared it to the owner (masonf@), and communicated about the overall task scope and direction. ([https://docs.google.com/document/d/1fLRONQ0XFX1D6GgG7jmStDpPZHEysSMwtQeuiwVMST4](https://docs.google.com/document/d/1fLRONQ0XFX1D6GgG7jmStDpPZHEysSMwtQeuiwVMST4))
* Rescoped the task: Connecting a pure-binary Enterprise Policy to a Runtime Enabled Feature.
    * Add generate_enterprise_policy field in runtime-enabled-feature json5 definition, which provides a simple way of connecting a REF to a EP, so that a EP (which is stored in Prefs) can be propagated from browser process to renderer process and loaded as a REF to be used in renderer.
    * The field is expected to provide a trivially easy way to connect EP to a REF from json5, with all boilerplate generated.
    * Need to update the explainer based on the changed direction.
* Start investigating relevant areas:
    * How REF base_feature field works. (base::Feature -> REF)
    * Details of existing EP -> renderer propagation sequences.


### [Medium] Implement PRF on create for security keys



* Follow-up: Add hmac-secret-mc support to DevTools WebAuthn panel.
    * Add support to Chrome DevTools Protocol ([crrev.com/c/7673678](http://crrev.com/c/7673678) / Landed)
    * Add support to DevTools front-end ([chromium-review.googlesource.com/c/devtools/devtools-frontend/+/7683510](http://chromium-review.googlesource.com/c/devtools/devtools-frontend/+/7683510) / In-Review)


### [Medium] Mac overlay scrollbars only show briefly when putting two fingers down on touchpad ([crbug.com/445900719](http://crbug.com/445900719))



* Follow-up: Windows perf regression ([crbug.com/485669521](http://crbug.com/485669521) / [crrev.com/c/7611009](http://crrev.com/c/7611009))
    * Revisit the Linux perf regression case (accu_weather_pinch_2018 / thread_total_rendering_cpu_time_per_frame), as it makes the situation complicated. (regression from disabled flag)
    * Sent a mail to the reviewer(flackr@) to ask help downloading(or accessing) the trace files for the runs in the perf regression test.
        * test: [https://pinpoint-dot-chromeperf.appspot.com/job/170f1ffe090000](https://pinpoint-dot-chromeperf.appspot.com/job/170f1ffe090000)
        * trace(base): [https://storage.cloud.google.com/chrome-telemetry-output/base_chromium_17f0315_extra_browser_args_disable_features_SessionRestoreInfobar_Variant_0_20260318T080604_67933/rendering.desktop/accu_weather_pinch_2018/retry_0/trace.pb](https://storage.cloud.google.com/chrome-telemetry-output/base_chromium_17f0315_extra_browser_args_disable_features_SessionRestoreInfobar_Variant_0_20260318T080604_67933/rendering.desktop/accu_weather_pinch_2018/retry_0/trace.pb)
        * trace(flag disabled): [https://storage.cloud.google.com/chrome-telemetry-output/exp_chromium_17f0315_7bf2111_extra_browser_args_disable_features_SessionRestoreInfobar_Variant_1_20260318T080458_71459/rendering.desktop/accu_weather_pinch_2018/retry_0/trace.pb](https://storage.cloud.google.com/chrome-telemetry-output/exp_chromium_17f0315_7bf2111_extra_browser_args_disable_features_SessionRestoreInfobar_Variant_1_20260318T080458_71459/rendering.desktop/accu_weather_pinch_2018/retry_0/trace.pb)


---

# SOCBB Bugfixing Igalia Status Update 

Reporting Period:  Mar 1, 2026- Mar 11, 2026

 Scope: Bugfixing across Chromium codebase, focusing on UI/UX issues, web standards compliance, and platform-specific behavior

---

This is a report covering weeks 9 & 10.

We have continued the work on the large bug, where we shared the design doc in the issue and got some initial feedback and suggestions. We're working on the initial PoC.

Apart from that, we still got some performance regressions related to the medium bug we fixed, and we have been triaging a few issues and adding them to the candidate lists.

Spreadsheet: [https://docs.google.com/spreadsheets/d/1V-dIz78giXXi1VhC6ScbO8Qi716EOHl5XlofQDG6-jM](https://docs.google.com/spreadsheets/d/1V-dIz78giXXi1VhC6ScbO8Qi716EOHl5XlofQDG6-jM)


### [Medium] Mac overlay scrollbars only show briefly when putting two fingers down on touchpad ([crbug.com/445900719](https://crbug.com/445900719))



* follow-up: Fix perf regression on Linux ([crrev.com/c/7557877](https://crrev.com/c/7557877)): Added the bug to medium candidate list.


### [Large] There are too many systems for configuring features ([crbug.com/469041913](https://crbug.com/469041913))



* Shared [design doc](https://docs.google.com/document/d/1fLRONQ0XFX1D6GgG7jmStDpPZHEysSMwtQeuiwVMST4) in the bug: [crbug.com/469041913#comment2](https://crbug.com/469041913#comment2)
    * Review and iterate on the feedback
* [WIP] Writing an initial PoC that only generates feature definitions - [crrev.com/c/7638000](https://crrev.com/c/7638000)


### Triaging Bugs



* [crbug.com/428258024](https://crbug.com/428258024)
    * Title: Testcase adding-and-deleting iframes is 6x alower in Chrome compared to Firefox
    * Added to medium candidate
* [crbug.com/428258023](https://crbug.com/428258023)
    * Title: Testcase creating nested iframes is 525x slower in Chrome compared to Firefox.
    * Looks same to the above. Not added.
* [crbug.com/427512504](https://crbug.com/427512504)
    * Title: broken chain emoji ( &lt;200d> ) not rendering properly in canvas
    * Added to medium candidate
* [crbug.com/427424624](https://crbug.com/427424624)
    * Title: Box shadow appears in a inside of an outline during sub-pixel transform: translate()
    * Looks another pixel-snapping related issue. Not added.
* [crbug.com/485669521](https://crbug.com/485669521)
    * Title: [V8 Memory Perf Sheriff]: [3] regressions in system_health.memory_desktop
    * Added to medium candidate
    * Note: The last CL merged for schrollbar fadeout ([crrev.com/c/7230729](https://crrev.com/c/7230729)) and follow-up perf fixes continuously introduces regressions on different platforms. Reviewer (flackr) wants to dig into the exact reason of the regressions and fix it.


---


# SOCBB Bugfixing Igalia Status Update 

Reporting Period:  Feb 11, 2026- Mar 1, 2026

 Scope: Bugfixing across Chromium codebase, focusing on UI/UX issues, web standards compliance, and platform-specific behavior


---

This is a report covering weeks 7 & 8. Note that there has been some holidays in this period.

Fixing a performance regression identified in the previous work around overlay scrollbars.

Advancing on the systems for configuring features by writing a document drafting a proposal.

As mentioned in previous reports, if there are more WebAuthn issues that you consider interesting, we'll be happy to take a look to them.

Spreadsheet: [https://docs.google.com/spreadsheets/d/1V-dIz78giXXi1VhC6ScbO8Qi716EOHl5XlofQDG6-jM](https://docs.google.com/spreadsheets/d/1V-dIz78giXXi1VhC6ScbO8Qi716EOHl5XlofQDG6-jM)


### [Medium] Mac overlay scrollbars only show briefly when putting two fingers down on touchpad ([crbug.com/445900719](http://crbug.com/445900719))



* follow-up: Fix perf regression on Linux: [crrev.com/c/7557877](http://crrev.com/c/7557877)


### [Large] There are too many systems for configuring features ([crbug.com/469041913](http://crbug.com/469041913))



* Drafting the prototyping proposal:
    * Title: Migrating base::Feature-Based Feature Definitions from C++ to JSON5
    * Link: [https://docs.google.com/document/d/1fLRONQ0XFX1D6GgG7jmStDpPZHEysSMwtQeuiwVMST4](https://docs.google.com/document/d/1fLRONQ0XFX1D6GgG7jmStDpPZHEysSMwtQeuiwVMST4)
    * Collect basic patterns and variations in chrome_features.h/cc and content_features.h/cc (Section 2)
    * Propose JSON5 schema to handle the variations (Section 3)
* Will share the draft to the bug to get some feedback when Section 2/3 are ready.


---


# SOCBB Bugfixing Igalia Status Update 

Reporting Period:   Jan 28, 2026 - Feb 11, 2026

 Scope: Bugfixing across Chromium codebase, focusing on UI/UX issues, web standards compliance, and platform-specific behavior


---

We have finished the bug related to overlay scrollbars and started work on a new large bug related to the different systems for configuring features. In parallel, we have been triaging several issues and adding them to the candidate hotlists, though none has been accepted as large so far. We are currently working on one issue that will take some time, but we will continue tagging additional issues as candidates. If there is any additional WebAuthn work you believe would be suitable for this project, please let us know.

Spreadsheet:[ https://docs.google.com/spreadsheets/d/1V-dIz78giXXi1VhC6ScbO8Qi716EOHl5XlofQDG6-jM](https://docs.google.com/spreadsheets/d/1V-dIz78giXXi1VhC6ScbO8Qi716EOHl5XlofQDG6-jM)

[Medium] Mac overlay scrollbars only show briefly when putting two fingers down on touchpad (crbug.com/445900719) \
Done:



* Addressed all review comments and landed the CL (crrev.com/c/7230729).
* Identified a performance regression (crbug.com/479549167) and fixed it (crrev.com/c/7532765).
* Closed the bug as fixed.

[Large] There are too many systems for configuring features (crbug.com/469041913) \
Investigation started:



* Given the size of the task, began with base::Feature.
* Selected chrome_features.h/.cc as an initial case study and collected common usage patterns and variations that would need to be expressed in JSON5:
    * Build-time variations using BUILDFLAG().
    * Naming convention mismatches (C++ identifiers vs. field-trial keys, etc.).
    * C++ specifier variations (const, constexpr, etc.) that may affect performance or binary size.
    * Use of predefined const char[] variables for parameter names in .cc files (e.g., for testing).
    * Enum definition variations (e.g., explicit enum values).
* Started designing a JSON5 format capable of handling these variations.

Triaging bugs

Unassigned items in Large list:



* Fully implement HTTPS-RR (crbug.com/40257146)
    * Reviewed the specs and followed the bug status in detail.
    * Noted progress by Helmut Januschka; work is temporarily halted due to dependent issues requiring decisions and prior implementation.
    * The issue has been reassigned to Helmut.

Triaging for candidate lists — added bugs:



* position: sticky + display: inherit + inner display: flex (crbug.com/372503461)
    * Reviewed the test case and shared a simplified version without inherit and flex.
    * Added to MEDIUM candidate list → moved to MEDIUM list.
* LayoutBox::PixelSnapped() incorrect with pixel accumulation from ancestors or in flipped writing mode* (crbug.com/41458361)
    * Added to LARGE candidate list → moved to MEDIUM list.
* Forced breaks inside inlines are ignored (crbug.com/40075224)
    * Added to MEDIUM candidate list.
* Contenteditable: Block element joined to previous block is wrapped with a span (crbug.com/41015847)
    * Shared observations about behavior changes depending on style matching.
    * Added to MEDIUM candidate list.

Candidate bug status updates:

* Cannot call WebAuthn from an iframe hosted inside an extension (crbug.com/40282145)
    * Added to LARGE candidate → moved to MEDIUM.
* Password manager: do not fetch passkeys for forms without autocomplete="webauthn" (crbug.com/40273148)
    * Added to MEDIUM candidate → remains in MEDIUM.
* Scroll-margin does not work for an element with a parent that has non-visible overflow (crbug.com/40074749)
    * Added to LARGE candidate → removed from candidate list after being fixed.


# SOCBB Bugfixing Igalia Status Update 

Reporting Period:   - 

 Scope: Bugfixing across Chromium codebase, focusing on UI/UX issues, web standards compliance, and platform-specific behavior

---

SOCBB Bugfixing Igalia Status Update Weeks 03-04

Hello,

This is a report covering weeks 3 & 4.

Finished the WebAuthn bug, if there are other WebAuthn issues you can consider for this project please let us know. We have also been adding a few issues to the candidate hotlists.

Spreadsheet: [https://docs.google.com/spreadsheets/d/1Yjp3o3T0E9CCqihdY_-lW3RvriYAqTj5NVGgl4zslro/edit?usp=sharing](https://docs.google.com/spreadsheets/d/1Yjp3o3T0E9CCqihdY_-lW3RvriYAqTj5NVGgl4zslro/edit?usp=sharing)

[Large] Implement PRF on create for security keys ([crbug.com/420689820](http://crbug.com/420689820))



    * Done:
        * Addressed review comments and landed the CL ([crrev.com/c/7365516](http://crrev.com/c/7365516))
        * Closed the bug as fixed.

[Medium] Mac overlay scrollbars only show briefly when putting two fingers down on touchpad ([crbug.com/445900719](http://crbug.com/445900719))



    * Still in review ([crrev.com/c/7230729](http://crrev.com/c/7230729)):
    * The CL touches MouseWheelEventManager::HandleWheelEvent() to add functionality of deferring fade-out and stopping deferred fade-out while handling series of wheel event phases.
    * By design, the method builds a kind of wheel target chain (from main frame through subframes to the wheel target node) within the frame tree structure, to dispatch the wheel events to the wheel target node.
    * By design, building and clearing the wheel target chain are done while processing the recursive HandleWheelEvent() call sequences to walk through frames in the wheel target chain.
    * MouseWheelEventManager::HandleWheelEvent() was implemented and has been used with some risky points, which may not introduce any issues as it is, but are able to generate some bugs easily when we missed or doesn't care about the point.
        * The wheel target chain built at a previous wheel event phase can be updated by another following wheel event phase, but it was not implemented to guarantee clearing the previous wheel target chain perfectly as the logic only clears the wheel target of a single frame and doesn't care about clearing the wheel targets stored in subframe chains.
        * Since the updating/clearing wheel target logic implemented in HandleWheelEvent() doesn't have any missing cases, the 'out-dated' wheel targets possibly stored in some frames doesn't affect wheel event dispatching.
    * Given that the wheel target update logic is a combination of 1) the condition of updating/clearing a wheel target of a single frame, and 2) the recursive call sequences from main frame to the leaf frame, to prevent side-effects when changing HandleWheelEvent(), we need to guarantee that the change doesn't affect both.
    * Tried to workaround (not to directly touch) the issue as much as possible to focus on the functionality to be added, but as the review progresses, the hidden issue eventually comes up, and the patch is being changed to explicitly address the issue.


### Triaging bugs



* New items in Large list
    * Fully implement HTTPS-RR ([crbug.com/40257146](http://crbug.com/40257146))
        * Component: Chromium > Internals > Network > DNS
        * Need to learn the spec and relevant area
            * spec: [https://datatracker.ietf.org/doc/html/rfc9460](https://datatracker.ietf.org/doc/html/rfc9460)
            * ref.: [https://emilymstark.com/2020/10/24/strict-transport-security-vs-https-resource-records-the-showdown.html](https://emilymstark.com/2020/10/24/strict-transport-security-vs-https-resource-records-the-showdown.html)
    * There are too many systems for configuring features ([crbug.com/469041913](http://crbug.com/469041913))
        * Component: Chromium
        * Looks very large task that requires researches about features/switches/policies system from basic use cases to various variations.
* WebAuthn issues not listed in bug-bounty
    * Cannot call webauthn from an iframe hosted inside an extension ([crbug.com/40282145](http://crbug.com/40282145))
        * Need to check the test step. (Would be better to have test case to follow)
        * Added to the large candidate list
    * Password manager: do not fetch passkeys for forms without autocomplete="webauthn" ([crbug.com/40273148](http://crbug.com/40273148))
        * Need to find out the test step.
        * Added to the medium candidate list
    * Virtual authenticator attestation certificate incorrectly tagged as RSA when it uses ECDSA ([crbug.com/40916538](http://crbug.com/40916538))
        * Looks have a clear test step to reproduce, but the issue is about the virtual authentication implementation which is used for testing. (Not sure whether it matches bug-bounty program as it is not a user-facing bug)
* Scroll issues not listed in bug-bounty
    * Scroll-margin does not work for an element with a parent that has a non-visible overflow ([crbug.com/40074749](http://crbug.com/40074749))
        * Looks interesting bug(16 votes) but +7 months from last updates. It seems that it can be an interop item as well.
        * Added to the large candidate list


# SOCBB Bugfixing Igalia Status Update 

Reporting Period: Dec 16, 2025- Jan 13, 2026

 Scope: Bugfixing across Chromium codebase, focusing on UI/UX issues, web standards compliance, and platform-specific behavior



---

Hello This is a report covering more weeks than usual, anyway due to the holidays season there is not a lot to report this time.

For the large bug, the main reviewer is on holidays, so we have pinged other people to try to move things forward.

Spreadsheet: [https://docs.google.com/spreadsheets/d/1V-dIz78giXXi1VhC6ScbO8Qi716EOHl5XlofQDG6-jM/edit?usp=sharing](https://docs.google.com/spreadsheets/d/1V-dIz78giXXi1VhC6ScbO8Qi716EOHl5XlofQDG6-jM/edit?usp=sharing)


### [Large] Implement PRF on create for security keys ([crbug.com/420689820](http://crbug.com/420689820))



* Finished writing CL and activated it for review. ([crrev.com/c/7365516](http://crrev.com/c/7365516))


### [Medium] Mac overlay scrollbars only show briefly when putting two fingers down on touchpad ([crbug.com/445900719](http://crbug.com/445900719))



* In review: Got additional review comments. ([crrev.com/c/7230729](http://crrev.com/c/7230729))


# SOCBB Bugfixing Igalia Status Update 

Reporting Period:  Dec 4, 2025- Dec 16, 2025

 Scope: Bugfixing across Chromium codebase, focusing on UI/UX issues, web standards compliance, and platform-specific behavior

---
 
### [Medium] Mac overlay scrollbars only show briefly when putting two fingers down on touchpad ([crbug.com/445900719](http://crbug.com/445900719))



* Checked the bug and try an approach: defers fade-out scrollbar animation until mouse wheel event ended.
* Wrote a CL and activated it for review: [crrev.com/c/7230729](http://crrev.com/c/7230729)
* Address review comments and upload new patchset for review: [crrev.com/c/7230729](http://crrev.com/c/7230729)


### [Large] Implement PRF on create for security keys ([crbug.com/420689820](http://crbug.com/420689820))



* Started investigation
    * Read [FIDO CTAP](https://fidoalliance.org/specs/fido-v2.2-rd-20241003/fido-client-to-authenticator-protocol-v2.2-rd-20241003.html#sctn-hmac-secret-extension) and [WebAuthn](https://w3c.github.io/webauthn/#prf-extension) spec. about hmac-secret, hmac-secret-mc, prf, MakeCredential, GetAssertion.
    * Check chromium implementation under 'device/fido', 'content/browser/webauth', 'third_party/blink/renderer/modules/credentialmanagement'.
    * Check yubico user manual to understand how authenticator implements hmac-secret and hmac-secret-mc. ([link](https://docs.yubico.com/yesdk/users-manual/application-fido2/hmac-secret.html#hmac-secret-vs-hmac-secret-mc))
    * 


---


# SOCBB Bugfixing Igalia Status Update 

Reporting Period: Nov 21, 2025- Dec 4, 2025

 Scope: Bugfixing across Chromium codebase, focusing on UI/UX issues, web standards compliance, and platform-specific behavior


---
Hello, please find the biweekly update for the Bugfixing work below, covering weeks 47 and 48. While we are triaging bugs for the large hotlist, we will work on medium bugs.


### [Large] [WPT] Failures in wai-aria-roles/grid-roles.html ([https://crbug.com/341369908](https://crbug.com/341369908))



* To clarify issues and start discussion, prepared a WIP CL that reland reverted commits with some modifications
    * CL: [https://crrev.com/c/7185018](https://crrev.com/c/7185018)
    * Modifications:
        * Add expected name to the row role, following the [accessibility name computation rule](https://www.w3.org/TR/accname-1.1/#mapping_additional_nd_te) for the [roles that supports name from contents](https://www.w3.org/TR/wai-aria/#namefromcontent).
        * Solve a regression in DumpAccessibilityTreeTest.AccessibilityMinRoleInGrid by skipping group role when checking parent context from ancestors.
            * [table, grid, rowgroup, treegrid is the valid accessibility parent ofrow](https://w3c.github.io/aria/#row)
            * In the test, role=row is ignored due to the [element with draggable attribute](https://www.w3.org/TR/html-aam-1.0/#att-draggable) because the element has group role as its [minimum role](https://www.w3.org/TR/html-aam-1.0/#dfn-minimum-role).
            * Need to check whether we need spec discussion about whether skipping group is allowed or not.
                * Current draft version specifies the [rule for the accessibility parent](https://w3c.github.io/aria/#dfn-accessibility-parent) as, "the DOM ancestor of the element with only elements of role generic or none intervening".
* Followed an ongoing discussion about gridcell and row in w3c/aria
    * [Should the 'row' role really be necessary for parents of 'gridcell' and other cell role elements? (issues/2420)](https://github.com/w3c/aria/issues/2402)
    * Discussion about removing the requirement that gridcell has a row as its container.
    * Need to check whether this is a blocking issue of the bug? (Should we solve the issue before fixing this bug?)
* Check [rule for the accessibility parent](https://w3c.github.io/aria/#dfn-accessibility-parent)
    * "the DOM ancestor of the element with only elements of role generic or none intervening"
    * Followed issues about having a role intervening parent/child relationship.
        * [https://github.com/w3c/aria/issues/2423](https://github.com/w3c/aria/issues/2423)
        * [https://github.com/w3c/aria/issues/1478](https://github.com/w3c/aria/issues/1478)
* Tried to contact owners and asked some questions about the bug in slack (jocelyntran@, #accessibility), but wasn't able to get response.
* Wrote a summary: [https://docs.google.com/document/d/1rkFdgZS-DQHkrFpDJdaMnSHiDCZjRlJ6FaEPdKQGyzk](https://docs.google.com/document/d/1rkFdgZS-DQHkrFpDJdaMnSHiDCZjRlJ6FaEPdKQGyzk)
* Had internal review at Igalia, and got exact intension of the conclusion of W3C issue 2166. Decided to fix the bug as Won't fix (Obsolete)


### [High] Back button does not go back ([https://issues.chromium.org/40055627](https://issues.chromium.org/40055627))



* After trying to replicate the issue unsuccessfully, we asked in the bug for up to date steps.
* Eventually, someone from Google Chrome team mentioned that their team was actively working on the issue and reassigned it.


### [Medium] Cancelling pointerdown impact on dblclick not interoperable



* Started investigating and working on this bug


### Triage for Hotlist



* Started triaging issues (looking for large ones) off of the query provided by rbyers@ [1] to Stephanie.
* So far we have a list of issues with reported broken behavior (that seem to be working fine on other browsers). Examples:
    * [https://issues.chromium.org/issues/457794569](https://issues.chromium.org/issues/457794569) (Pointerevents shouldn't be cancelled if no panning or zooming is possible)
    * [https://issues.chromium.org/issues/457323839](https://issues.chromium.org/issues/457323839) (Selecting radio button using keyboard only is possible only the first time.)
    * [https://issues.chromium.org/issues/451355213](https://issues.chromium.org/issues/451355213) (When pressing Enter on Input box is not sending the enter key, it's just changing focus like Tab)
    * [https://issues.chromium.org/issues/449152888](https://issues.chromium.org/issues/449152888) (date input change event is fired before the user has completed entering a valid date)
    * [https://issues.chromium.org/issues/463591198](https://issues.chromium.org/issues/463591198) (Treat empty-string as an invalid value for animation-name and reject it at parse time), filed by jfernandez@igalia
    * [https://issues.chromium.org/issues/460165735](https://issues.chromium.org/issues/460165735) (Wheel event preventDefault does not work inside iframe with pointerlock (incorrect event routing))
    * [https://issues.chromium.org/issues/459088197](https://issues.chromium.org/issues/459088197) (Keyboard focus can get stuck on ::scroll-markers)

[1] [https://issues.chromium.org/u/1/issues?q=componentid:1456407%2B%20status:new%20modified:180d%20-title:%22V8%20JavaScript%20Perf%22%20type:bug%20hotlistid:5438642](https://issues.chromium.org/u/1/issues?q=componentid:1456407%2B%20status:new%20modified:180d%20-title:%22V8%20JavaScript%20Perf%22%20type:bug%20hotlistid:5438642)


---


# SOCBB Bugfixing Igalia Status Update 

Reporting Period: November 7, 2025- Nov 21, 2025

 Scope: Bugfixing across Chromium codebase, focusing on UI/UX issues, web standards compliance, and platform-specific behavior

---
Hello, please find the biweekly update for the Bugfixing work below, covering weeks 45 and 46. While we are investigating two large bugs from the hotlist, all other large bugs have been assigned on the list. We will work on triaging some bugs to suggest for the list and in the meantime will continue with medium bugs after the large bugs. 


### [Medium] Placing 2 fingers on touchpad only shows nearest scrollbar ([https://crbug.com/445523709](https://crbug.com/445523709))



* Landed the CL / closed the bug as fixed.


### [Large] [WPT] Failures in wai-aria-roles/grid-roles.html ([https://crbug.com/341369908](https://crbug.com/341369908))



* Started investigation - the problem itself doesn't seem to be super complicated. However, there seem to be lots of test results need to be updated while fixing the issue, and it seem that there are some additional hidden issues can be detected while fixing it.
* Learning the spec / Writing a prototype.
* Checked the commit history
    * There were 3 commits landed
        * [Interop] Add check for row role not in required context ([https://crrev.com/c/5538460](https://crrev.com/c/5538460))
        * [Interop] Add check for rowgroup not in required context ([https://crrev.com/c/5607828](https://crrev.com/c/5607828))
        * [Interop] Add check for rowheader, columnheader not in required context ([https://crrev.com/c/5617352](https://crrev.com/c/5617352))
    * and those were reverted by these commits:
        * Revert "[Interop] Add check for rowheader, columnheader not in required context" ([https://crrev.com/c/5627573](https://crrev.com/c/5627573))
            * reverts 5617352 to fix some bot failures introduced by the commit. (e.g. [https://logs.chromium.org/logs/chromium/buildbucket/cr-buildbucket/8745315375379956417/+/u/content_browsertests_on_Mac-11/stdout](https://logs.chromium.org/logs/chromium/buildbucket/cr-buildbucket/8745315375379956417/+/u/content_browsertests_on_Mac-11/stdout))
        * [A11y] Remove check for roles in required context ([crrev.com/c/5710051](http://crrev.com/c/5710051))
            * reverts rest of the commits (5538460, 5607828) to follow the w3c discussion about not enforcing the required accessibility parent role restriction. ([https://github.com/w3c/aria/issues/2166](https://github.com/w3c/aria/issues/2166))
* Checked the spec status:
    * Latest editor's draft of aria spec ([https://w3c.github.io/aria/#scope](https://w3c.github.io/aria/#scope)) mentions that UA should ignore the out-of-context role. \
Also, user agents SHOULD ignore the role if it occurs outside the context of a required accessibility parent role.
* Checked bot failures from 5617352
    * It seems that the bot failure is caused by incorrect expected files.
        * Expected: ++++++++row / Actual:++++++++row name='Sort illegal'
        * The actual behavior seems to be the correct behavior given that how AXNodeObject get text from descendants:
            * [Accessible Name and Description Computation](https://www.w3.org/TR/accname-1.1/)
            * AXNodeObject::TextAlternative() / AXNodeObject::TextFromDescendants()
            * content/test/data/accessibility/aria/aria-col-attr-expected-blink.txt
* Plan to move forward:
    * Share the understanding to the bug and ask about re-landing the commits with some expected result modification.


### [Medium] Android : Scrolling issue after input focus on scrollable overlay- ImplicitRootScroller ([https://issues.chromium.org/40645917](https://issues.chromium.org/40645917))



* Summary: the issue dates from 2021, and starts to happen when a runtime flag named ImplicitRootScroller was enabled.
* Status: Issue ins't reproducible to us on the latest build of Chromium/Android, tested on a Samsung Galaxy 21 FE.
    * Spent some time setting up the development environment to validate the testing:
        * checked out a chromium snapshot from early 2021.
        * fixed various build errors, eg scripts still written in python 2, missing javac dependencies, broken node.js binaries, etc.
        * put device in development mode, and got it ready for testing.
        * fixed runtime errors, including start up crashes, and renderer crashes.
* Ultimately, we were able to run test this old chromium snapshot on a real hardware, and issue isn't reproducible.
* We have commented on the bug asking (a) additional step for the report, or maybe a revalidation (b) recommended the issue for closure.


### [Large] Back button does not go back ([https://issues.chromium.org/40055627](https://issues.chromium.org/40055627))



* Started working on this bug, but still trying to replicate the original issue. If successful, will assign the bug and continue.


---


# SOCBB Bugfixing Igalia Status Update

Reporting Period: October 9, 2025 - October 23,2025 \
 Scope: Bugfixing across Chromium codebase, focusing on UI/UX issues, web standards compliance, and platform-specific behavior
 
---
Hello, please find the biweekly update for the Bugfixing work below, covering weeks 41 and 42.


### [Medium] Placing 2 fingers on touchpad only shows nearest scrollbar ([https://crbug.com/445523709](https://crbug.com/445523709))



* Start to write CL that shows all scrollbars. (Internally checked the solution works / refining changes and writing tests)
* In review ([crrev.com/c/7039800](http://crrev.com/c/7039800)): Activated CL for review / addressed comments from reviewers.


### [Medium] Seams between layers with subpixel transforms or transform animations ([https://crbug.com/401515597](https://crbug.com/401515597))



* No update since the previous report.


### [Medium] With position: sticky; bottom: 0; the element is still offset by 1px from the bottom ([https://issues.chromium.org/issues/436536717](https://issues.chromium.org/issues/436536717))



* The issue has been moved to medium hotlist 
* The element's negative offset, offset_no_snap\mathbf{offset\_no\_snap}, is correctly calculated by the sticky solver to keep the footer just inside the bottom edge of its containing block. The resulting visual 1 pixel jump is caused by a fractional layout issue: the sticky offset is combined with the layer's fractional paint offset which the system subsequently rounds to zero. This rounding effectively \mathbf{removes\ the\ small\ negative\ offset}removes the small negative offset, causing the element to move up and creating the visual "drop."
* The suggested fix is to adjust the rounding logic or prevent fractional snapping when the calculated sticky offset is very small. I still need to test this solution and discuss with christr@.


---


# SOCBB Bugfixing Igalia Status Update

Reporting Period: September 24, 2025- October 9, 2025 \
 Scope: Bugfixing across Chromium codebase, focusing on UI/UX issues, web standards compliance, and platform-specific behavior

Hello, please find the biweekly update for the Bugfixing work below, covering weeks 39 and 40. We will work on wrapping up any small and medium bugs currently in progress next week, as, like communicated previously, we will be finishing up the hours for this contract ahead of schedule.


### [Small] With position: sticky; bottom: 0; the element is still offset by 1px from the bottom ([https://issues.chromium.org/issues/436536717](https://issues.chromium.org/issues/436536717))



* Pixel snapping can cause ±1px inconsistencies when offsets (including scroll offset) are applied, and while Blink and cc differ, cc ensures consistency by subtracting the clip from the sticky box, applying the scroll/paint offset, and only then rounding. However, it's different in Blink and contents size and container rect are first pixel snapped and then values are stored. As a result, the sizes can be rounded up and rounded down for these sizes/rects introducing a 1 px gap. It's not a regression, but a long standing problem.
    * [https://issues.chromium.org/issues/436536717#comment7](https://issues.chromium.org/issues/436536717#comment7)
* Looked at other places in blink how to mitigate this post pixel snapping problem
* Searched for this solution in graphics documentation online
* Wrote a message to chrishtr@chromium.org and started the discussion
* It feels more like a medium rather than a small problem as it is not a regression, but rather pixel snapping problem, which may require broader changes than a couple of lines. Let's see what the discussion brings


### [Medium] Seams between layers with subpixel transforms or transform animations ([https://crbug.com/401515597](https://crbug.com/401515597))



* Found a hint: Calculating pixel-snapped rect without considering LocalToDevice matrix can introduce the issues:
    * [https://codepen.io/reesedrjones/pen/poBjJNp](https://codepen.io/reesedrjones/pen/poBjJNp) size diffs between original local rect and pixel-snapped local rect can exceed 1 device-pixel when the scale in LocalToDevice matrix is applied.
    * [https://jsfiddle.net/reesedrjones/ngcxkL1v/3/](https://jsfiddle.net/reesedrjones/ngcxkL1v/3/) Shows sub-pixel gaps between tiled painting rects when the translate in LocalToDevice matrix has decimal values (e.g. translate from local (0, 0) to device (10.5, 9.5) at 150% zoom).
* PoC for narrowing down the scope of investigation:
    * Approach: To check whether the decimal values in device rect offset/size are related to the issue, snap the local rect toward device-pixel boundary rather than local-pixel boundary.
    * Test result shows that the approach helps removing issues from both cases (video): [https://cloud.igalia.com/s/CBS9tXN3QTXWtap](https://cloud.igalia.com/s/CBS9tXN3QTXWtap) (e.g. [test-draw-rect.html](https://cloud.igalia.com/s/Lx6rXZ2F9bn77iA), [test-draw-tiles.html](https://cloud.igalia.com/s/4njxxmmKr8apNqW))
    * CL: [crrev.com/c/6994382](http://crrev.com/c/6994382) (NotForLanding)
        * Partially fixed #1 (closed) : still there is 1 pixel diffs at certain zoom factor (e.g. 60%, 90%, 110%)
        * Partially fixed #2 (closed) : only fixed problem in painting rect. Need to fix problem in image rect as well)
        * Removed ToPixelSnappedRect() call from blink::(anonymous namespace)::PaintFastBottomLayer() and added ToDevicePixelSnappedLocalRect() to cc::DrawRectOp::RasterWithFlags() to access LocalToDevice matrix in SkCanvas.


---


# SOCBB Bugfixing Igalia Status Update

Reporting Period: September 12, 2025 September 24, 2025 \
 Scope: Bugfixing across Chromium codebase, focusing on UI/UX issues, web standards compliance, and platform-specific behavior
 
---
Hello, please find the biweekly update for the bugfixing work below, covering weeks 37 and 38.


### [Medium] WebDriver: Correct touch events for Android ([https://crbug.com/42320346](https://crbug.com/42320346))



* Continued discussion on webdriver issue which seems to be headed towards a resolution
    * [Element click behavior on touchscreen devices](https://github.com/w3c/webdriver/issues/1925)
* Un-assigned bug as the recommendation in the [webdriver issue](https://github.com/w3c/webdriver/issues/1925) is different from the initially proposed ChromeDriver fix.


### [Medium] Seams between layers with subpixel transforms or transform animations ([https://crbug.com/401515597](https://crbug.com/401515597))



* Checked the two test links in the bug comments ([issues/401515597#comment3](https://issues.chromium.org/u/1/issues/401515597#comment3))
    * [https://codepen.io/reesedrjones/pen/poBjJNp](https://codepen.io/reesedrjones/pen/poBjJNp)
        * background color paint rect rounding issues with transform scale.
        * BoxPainterBase changes the physical rect to pixel rect by using 'ToPixelSnappedRect()', which rounds the position and size of the rect. The delta from this operation can cause a bug at compositing step that applies transform scales to the size that has the delta.
        * Looks not directly related to the bug as the bug is related to the image painting with device pixel ratio.
    * [https://jsfiddle.net/reesedrjones/ngcxkL1v/3/](https://jsfiddle.net/reesedrjones/ngcxkL1v/3/)
        * Bitmap image drawing issue. - Shows seams between tiled image with floating point device pixel ratio.
        * Checking the exact point that causes the behavior.
* Checked the second test link in the bug comments:
    * [https://jsfiddle.net/reesedrjones/ngcxkL1v/3/](https://jsfiddle.net/reesedrjones/ngcxkL1v/3/)
        * Still checking. This seems to be a similar floating point rounding issue caused by ToPixelSnappedRect(). ImagePainter::PaintIntoRect() converts the destination physical rect to pixel snapped rect for drawing image, and the rect size of each tile differs.


### [Medium] Threaded compositor: Placing 2 fingers on the trackpad does not show the overlay scrollbar ([https://crbug.com/40260134](https://crbug.com/40260134))



* Landed the CL that enables the flag ([crrev.com/c/6948546](http://crrev.com/c/6948546)) and closed the bug.
* flackr@ created two follow-up bugs and assigned those to Igalia.
    * New bugs:
        * Placing 2 fingers on touchpad only shows nearest scrollbar ([crbug.com/445523709](http://crbug.com/445523709))
        * Mac overlay scrollbars only show briefly when putting two fingers down on touchpad ([crbug.com/445900719](http://crbug.com/445900719))
    * We added those bugs to [BugBountyCandidate-Medium](https://issues.chromium.org/u/1/hotlists/6641288) as the original bug was in the medium list. But we think 445523709 is relatively simple, so it can be in small list.


### [Small] With position: sticky; bottom: 0; the element is still offset by 1px from the bottom ([https://issues.chromium.org/issues/436536717](https://issues.chromium.org/issues/436536717))



* Started investigation. There is a paint offset that is rounded differently based on viewport scale factor, which results in a 1 px artifact.


---


# SOCBB Bugfixing Igalia Status Update

Reporting Period: August 27, 2025- September 12, 2025 \
 Scope: Bugfixing across Chromium codebase, focusing on UI/UX issues, web standards compliance, and platform-specific behavior

---

Hello, please find the biweekly update for the bugfixing work below, covering weeks 35 and 36.

[Medium] Threaded compositor: Placing 2 fingers on the trackpad does not show the overlay scrollbar ([https://crbug.com/40260134](https://crbug.com/40260134))



* Found some bugs during local sanity test, and fixed those:
    * Fix crash when kPhaseMayBegin mouse wheel event on slotted text ([https://crrev.com/c/6888432](https://crrev.com/c/6888432))
    * Fix scrollbar fade-in bug for the event on slotted text ([https://crrev.com/c/6888611](https://crrev.com/c/6888611))
    * Fix scrollbar fade-in bug for the subsequent event after wheel scroll ([https://crrev.com/c/6883936](https://crrev.com/c/6883936))
* Fortunately, due to the flag added by the initial CL, there was no crash/ux-bug report. (Fixed the issues quietly)
* The landed commits looks OK and doesn't have regression so far. Will prepare a CL that enables the flag.
* Responding comments in the bug page.

[Medium] Seams between layers with subpixel transforms or transform animations



* Investigating.

[Medium] Feature request: Ability to screenshot whole tab, not just visible section (blocking issue) ([https://issues.chromium.org/issues/40402691](https://issues.chromium.org/issues/40402691))



* Working on the implementation.
* Status: We have paused this work after verifying with Rick that the main bug this is a dependency for has already been fixed.

[Medium] WebDriver: Correct touch events for Android ([https://crbug.com/42320346](https://crbug.com/42320346))



* Came up with a chromedriver fix to handle both mobile touchscreen and mobile emulation on desktop: [https://crrev.com/c/6906885](https://crrev.com/c/6906885)
* Currently discussing with chromedriver authors whether to solve it in chromedriver or wait for spec clarification.
* Opened webdriver issue to get clarification in terms of the spec: [https://github.com/w3c/webdriver/issues/1925](https://github.com/w3c/webdriver/issues/1925)

[Small] Keyboard navigation broken with popovers containing Shadow DOM components ([https://crbug.com/436071735](https://crbug.com/436071735))



* Reproduced and found the root cause.
* Working on a fix.


---


# SOCBB Bugfixing Igalia Status Update

Reporting Period: June 20 – August 27, 2025 \
 Scope: Bugfixing across Chromium codebase, focusing on UI/UX issues, web standards compliance, and platform-specific behavior

---
Hello, please find the biweekly update for the bugfixing work below, covering weeks 33 and 34.

[Medium] Mouse-wheel scrolling too fast (2x) since 109 ([https://crbug.com/40887377](https://crbug.com/40887377))



* Landed a change to enable the LimitScrollDeltaToScrollerSize feature introduced in an earlier CL, by default including a web test fix to reflect the new scroll behavior: [https://crrev.com/c/6819005](https://crrev.com/c/6819005)
* Marked the bug as fixed.
* Status: Landed


### [Medium] Unable to click on an element which is inside of iFrame with transform: scale (even after switching in frame) ([https://crbug.com/42321690](https://crbug.com/42321690))



* Performed more testing for complicated cases like nested iFrames, other transform values and more complex layout.
* Updated CL to ensure the fix works for those cases when performing mouse actions, added test case and marked it ready for review: [crrev.com/c/6829442](http://crrev.com/c/6829442)
* If Element.click() is used in the test as opposed to mouse move + click actions, that will still have the limitation as the chromedriver implementation for that uses ScrollElementRegionIntoView() where a similar fix may not be feasible.
* Chromedriver owners suggested holding off on making any fixes/workarounds for this in ChromeDriver until this is solved upstream at the webdriver spec level.
* Un-assigned bug.


### [Medium] android: Focus is lost even though pereventDefault() is called in pointerdown event handler ([https://crbug.com/433196597](https://crbug.com/433196597))



* Started doing some preliminary investigation.
* Possibly related to [crbug.com/332989701](http://crbug.com/332989701).


### [Medium] Threaded compositor: Placing 2 fingers on the trackpad does not show the overlay scrollbar ([https://crbug.com/40260134](https://crbug.com/40260134))



* Activate CL / review is in-progress: Added test cases and guarded the logic under a feature flag
* Got the first review, addressed the comments and uploaded new patchset. Waiting for the next review: [http://crrev.com/c/6772188/5](http://crrev.com/c/6772188/5)
* Landed the CL: [https://crrev.com/c/6772188](https://crrev.com/c/6772188)
* The CL contains two part:
    * event targeting & handling change: Landed directly, without additional guard, to detect unexpected regression caused by the change.
    * scrollbar behavior change: Landed behind a feature flag (FadeInScrollbarWhenMouseWheelMayBegin), disabled by default to minimize impact on user experience until the event handling change is verified.
    * Will enable the flag after some weeks.
* Status: Landed


### [Medium] Seams between layers with subpixel transforms or transform animations



* Started initial investigation.


### [Medium] Overlay scrollbars on one scroller appear when trackpad scrolling on another scroller ([https://crbug.com/402171647](https://crbug.com/402171647))



* Continued working on [https://crrev.com/c/6797805](https://crrev.com/c/6797805): Implement flashing scrollbars only once or once they become visible
* Implemented flashing on mouse enter and sent CL for review
* CL landed. Considering either enabling features by default or running a field trial
* Status: Landed


### [Medium] Feature request: Ability to screenshot whole tab, not just visible section (blocking issue) ([https://issues.chromium.org/issues/40402691](https://issues.chromium.org/issues/40402691))



* Re-iterated over the design doc.
* Pinged owners to review that
* Created a proposal to add chrome.tabs.captureTab in [https://github.com/w3c/webextensions/issues/863](https://github.com/w3c/webextensions/issues/863) to gain more visibility.
* Still no response on [https://github.com/w3c/webextensions/issues/863](https://github.com/w3c/webextensions/issues/863)


### [Medium] HTML5 drag and drop is not working([https://crbug.com/40645044](https://crbug.com/40645044))



* Studied the problem and how to run selenium and webdriver
* Reproduced the issue. After successfully running the webdriver, tried the test case that the reporter shared. Found out there was an error in the test. Reported that back, and asked if the issue is still there on their end.


### [Medium] Border of element painted in wrong place([https://crbug.com/40830128](https://crbug.com/40830128))



* Analyzing the problem and its root cause.


---


# SOCBB Bugfixing Igalia Status Update 14 August 2025

Hello, please find the biweekly update for the bugfixing work below, covering weeks 31 and 32.


### [Medium] Unable to click on an element which is inside of iFrame with transform: scale (even after switching in frame) ([https://crbug.com/42321690](https://crbug.com/42321690))



* Came up with potential fix with CL uploaded: [https://chromium-review.googlesource.com/c/chromium/src/+/6829442](https://chromium-review.googlesource.com/c/chromium/src/+/6829442)
* It reads the transform matrices for each frame leading up to the element and applies them to derive the final position
* Tested this fixes the original reported use case, doing some more tests for edge cases
* Working on unit tests, will move CL to review state after


### [Medium] Threaded compositor: Placing 2 fingers on the trackpad does not show the overlay scrollbar ([https://crbug.com/40260134](https://crbug.com/40260134))



* Will upload the new patch-set and activate it for review in this week.
* Found out that the PoC only works with js event handler registered (which triggers main thread event handler logic). Investigate the way of forwarding wheel may-begin event from compositor thread to main thread by returning DID_NOT_HANDLE in InputHandlerProxy::HandleMouseWheel().
* Addressing the review comments on the CL ([https://crrev.com/c/6772188](https://crrev.com/c/6772188) - add test, guard with a feature flag, cleanup the implementation...)


### [Medium] Overlay scrollbars on one scroller appear when trackpad scrolling on another scroller ([https://crbug.com/402171647](https://crbug.com/402171647))



* Checked review comments in [https://crrev.com/c/6656458](https://crrev.com/c/6656458)
* Agreed on another approach with the reviewer
    * Flash once
    * Flash on becoming visible on viewport
    * Flash on mouse enter
* Implemented first 2 points
    * Worked on tests
    * Sent for review: [https://crrev.com/c/6797805](https://crrev.com/c/6797805): Implement flashing scrollbars only once or once they become visible
    * Received comments on [https://crrev.com/c/6797805](https://crrev.com/c/6797805): Implement flashing scrollbars only once or once they become visible
        * Improved tracking of entered scrollbars on viewports
        * Added more tests
        * Reduced number of times that checking for entered scrollbars happens by introducing scrolling threshold
        * Landed the patch


### [Medium] Mouse-wheel scrolling too fast (2x) since 109 ([https://crbug.com/40887377](https://crbug.com/40887377))



* Fix (behind feature flag) CL landed: [https://crrev.com/c/6710973](https://crrev.com/c/6710973)


---


# SOCBB Bugfixing Igalia Status Update 30 July 2025


## Hello, please find the biweekly update for the bugfixing work below, covering weeks 29 and 30.


## We currently have multiple developers working through the hotlists and are expected to complete the contract hours ahead of schedule in September.


### [Medium] Mouse-wheel scrolling too fast (2x) since 109 ([https://crbug.com/40887377](https://crbug.com/40887377))



* Based on further feedback, updated the CL to limit the scroll delta to the size of the scroller
* Updated CL based on review and added test: [https://crrev.com/c/6710973](https://crrev.com/c/6710973)


### [Medium] chromedriver 78 double clicks the wrong position ([https://crbug.com/42322257](https://crbug.com/42322257))



* MouseMoveTo is compliant with the webdriver in-view-center point spec for an element, whereas pointerMove action tries to account for the element's parent/ancestor's overflow:hidden property and so it deviates from the spec, which was causing the inconsistency.
* Created a CL to make pointerMove action compliant with the spec and consistent with element.Click() and MouseMoveTo(): [https://crrev.com/c/6735230](https://crrev.com/c/6735230)
* The failing tests that required the original change to handle the parent's overflow seem to pass now without it.
* It is currently being discussed in the CL if there needs to be such handling still for those corner cases, even though it's not spec compliant. If so, the fix could be to make it spec compliant for most cases but calculate the in-view-center point differently only the original calculation returns a point that is not visible due to the parent's overflow.
* Landed CL to make pointerMove action compliant with the spec and consistent with element.Click() and MouseMoveTo(): [https://crrev.com/c/6735230](https://crrev.com/c/6735230)
* Closed bug as Fixed.


### [Medium] Cancelling pointerdown impact on dblclick not interoperable



* Created a test [https://jsfiddle.net/mhvwdsn8/](https://jsfiddle.net/mhvwdsn8/)
* Was unable to reproduce original issue in recent chromium build
* Found a different issue in Chrome on Android with focus being lost even with preventDefault(): [crbug.com/433196597](http://crbug.com/433196597)


### [Medium] Unable to click on an element which is inside of iFrame with transform: scale (even after switching in frame) ([https://crbug.com/c/42321690](https://crbug.com/c/42321690))



* Created a test case to reproduce locally, and it is still an issue.
* Currently investigating how to pass the scale value from outside the frame to the in-view center point calculation.
* Continued to investigate an approach of passing scale info from outside the iframe.


### [Medium] Threaded compositor: Placing 2 fingers on the trackpad does not show the overlay scrollbar ([https://crbug.com/40260134](https://crbug.com/40260134))



* Prototyping: Tried one approach that dispatches may-begin phase mouse wheel event to renderer so that the renderer makes the scrollbar fade-in by sending fake 'DidScroll()' call. This approach is just a workaround with a minimal code changes that fade-in the scrollbar at the event phase for 2 fingers on the trackpad. It doesn't touch any complex logics such as gesture scroll state and scrollbar fade-in sequences that follows compositor updates. Before moving forward, it would be good to have internal review or get feedback about adding the workaround in general.
* WIP PoC: [https://crrev.com/c/6772188](https://crrev.com/c/6772188)


### [Small] aria role menuitemcheckbox, menuitemradio should have AXMenuItemMarkChar ✓ ([https://crbug.com/41136076](https://crbug.com/41136076))



* We have checked with Mac VoiceOver and wasn’t able to find any issue in chrome compared to Firefox and Safari, and there is no response for the comment yet ([https://issues.chromium.org/u/1/issues/40581308#comment91](https://issues.chromium.org/u/1/issues/40581308#comment91)). Based on the observation, it seems that Chrome provides the attributes as expected. And my gut feeling is that, if there is any scenario that Chrome does not provide the attributes, it may be related to whether Chrome detects screen reader mode or not. (ref. skip serializing some attributes: [https://chromium.googlesource.com/chromium/src/+/refs/heads/main/third_party/blink/renderer/modules/accessibility/ax_object.cc#1430](https://chromium.googlesource.com/chromium/src/+/refs/heads/main/third_party/blink/renderer/modules/accessibility/ax_object.cc#1430)).
* It would be helpful to know the specific conditions or steps to reproduce.


---


# SOCBB Bugfixing Igalia Status Update 17 July 2025

Hello, please find the biweekly update for the bugfixing work below, covering weeks 27 and 28 of 2025.


### [Medium] Content area flashes white when changing or re-opening tabs ([https://crbug.com/40581308](https://crbug.com/40581308))



* The fallback gutter color in aura is white ([DelegatedFrameHostClientAura::DelegatedFrameHostGetGutterColor()](https://chromium.googlesource.com/chromium/src.git/+/refs/heads/main/content/browser/renderer_host/delegated_frame_host_client_aura.cc#40)), and this causes the white flashes in dark mode.
* There was [a try that sets the color to transparent](https://crrev.com/c/5598190), but it was reverted due to a regression on popup window (showing back screen until the popup frame is ready). The following step in discuss is to use transparent fallback for tab contents and use solid fallback color for popup, but it looks a bit complicated.
* We can think about an alternative of returning the window background theme color, or solid black gutter color as a fallback for dark theme. (e.g. use ColorProvider::GetColor(ui::kColorWindowBackground) or NativeTheme::ShouldUseDarkColors()). Quickly checked the feasibility internally.
* Added a comment to ask about the plans or progress of the issue ([issues/40581308#comment91](https://issues.chromium.org/u/0/issues/40581308#comment91))
* Asked the status to Blundell in Slack - he is waiting for the response from zmo as he is the one with the context.
* Waiting for the response for the comment: [https://issues.chromium.org/u/1/issues/40581308#comment91](https://issues.chromium.org/u/1/issues/40581308#comment91)


### [Small] Linux - Wacom Stylus does not register when chromium is on wayland natively w/ ozone



* Briefly looked at this but thomasanderson@ made a recent change ([https://crrev.com/c/6666637](https://crrev.com/c/6666637)) to support tablet-v2 wayland protocol which should in theory fix this issue.


### [Medium] Mouse-wheel scrolling too fast (2x) since 109 ([https://crbug.com/40887377](https://crbug.com/40887377))



* Reported originally on Linux due to a change in M109 to increase scroll delta to 120 pixels to match Windows, which was intentional but it was reopened recently due to scroll issue seen in select element, which seems platform agnostic.
* Testing on Windows revealed a scroll delta of 100 pixels being used there on recent builds.
* Found that Linux/Wayland scroll delta calculation was incorrect and landed a fix: [crrev.com/c/6700422](http://crrev.com/c/6700422)
* Identified using ui::ScrollGranularity::kScrollByPage instead of ui::ScrollGranularity::kScrollByPixel for the &lt;select> element as a potential approach to fixing the issue, which would make the scroll behavior match Firefox. Studied scrolling code paths and started working on a PoC for this.
* Prototyped scroll-by-page for &lt;select> element: [crrev.com/c/6710973](http://crrev.com/c/6710973)
* Video with the fix: [https://issues.chromium.org/action/issues/40887377/attachments/67379831?download=true](https://issues.chromium.org/action/issues/40887377/attachments/67379831?download=true)
* Question was asked on the above CL about whether we should special-case it for select element or if we should apply it everywhere.
* The PoC was done to apply scroll-by-page for the select use case because that was reported as a major pain point for users, but it could be perhaps applied more broadly, possibly using an experimental feature flag.
* One other consideration is applying scroll-by-page IFF the container size (each "page" that is scrolled) is small enough that it's less than the default scroll-by-pixel value of 120px (100px on Windows), given scroll-by-pixel maybe preferred in larger containers, so as not to jump too far ahead per wheel detent, while smaller containers could use scroll-by-page to not skip over lines.
* Waiting for further comments from reviewers about above points.


### [Small] aria role menuitemcheckbox, menuitemradio should have AXMenuItemMarkChar ✓ ([https://crbug.com/41136076](https://crbug.com/41136076))



* Checked the behavior: Chrome currently provides correct AXValue and AXMenuItemMarkChar attribute value as specified in ['core-aam'](https://w3c.github.io/core-aam/#ariaCheckedTrue) when [AXMode::kExtendedProperties](https://chromium.googlesource.com/chromium/src/+/refs/heads/main/ui/accessibility/ax_mode.h#61) mode set. (e.g. launch Chrome with --force-renderer-accessibility, switch to accessibility tree view in DevTools, or use actual screen reader)
* Posted a comment to share a test script and its result: [https://issues.chromium.org/u/1/issues/41136076#comment27](https://issues.chromium.org/u/1/issues/41136076#comment27)


### [Medium] Threaded compositor: Placing 2 fingers on the trackpad does not show the overlay scrollbar ([https://crbug.com/40260134](https://crbug.com/40260134))



* Looked at the current status: The event for 2 fingers on the trackpad is the wheel event at 'may-begin' phase (NSEventPhaseMayBegin / blink::WebMouseWheelEvent::kPhaseMayBegin). Given that scrollbar update is triggered in renderer while processing scrolls while applying compositor changes, the wheel event at 'may-begin' phase need to be dispatched to the renderer if we want to make the scrollbar visible at the point. But current wheel event handling logic in 'component/input' ignores 'may-begin' phase, and only dispatches wheel events after 'began' phases, and renderer processes scroll with those events. To fix the bug, we need to make the input component and renderer handles 'may-begin' phase.
* Adding 'MayBegin' phase to the existing wheel event handling logic looks not a trivial task. Given that its benefit is limited to a single use case (show scrollbar when two fingers are placed on macOS trackpad), I'm not confident that it is worth to add complexity, but we think at least it is worth to try PoC to clarify how much complexity it may add.


### [Medium] PageUp and PageDown in textarea moves website out of the window ([https://crbug.com/41417806](https://crbug.com/41417806))



* Not exactly reproducible in latest chrome versions. Found old versions before 94.0.4582.0 showed the drastic layout change on PageDown/PageUp, but now it seems to change only a tiny bit (see [video](https://issues.chromium.org/41417806#attachment67523690)), and is barely noticeable. So asked on the bug if there are any other examples where it looks worse on recent versions and possibly lowering the priority otherwise.
* A [bisect](https://chromium.googlesource.com/chromium/src/+log/c11b69ac397ab783521ad3ac2d130440acb1b233..edde5ea3229fc9ca26dd030c132830e8ee075d30) didn't reveal any obvious change that could've "fixed" it.
* Also, going back to versions from 123.0.6273.0 and up where CSSLightDarkColors feature flag existed, the tiny layout/margin change can only be seen if that feature is enabled and it didn't have the issue if the feature was disabled.


### [Medium] Perform Actions not correctly calculating element location in frames ([crbug.com/42321906](http://crbug.com/42321906))



* The bug was referring to an issue with one of the ChromeDriver acceptance tests which were removed as per [crrev.com/c/5812142](http://crrev.com/c/5812142) and the [webdriver repo is no longer used in chromium](https://chromium.googlesource.com/chromium/deps/webdriver/+/32215357309373c0512748c142a3e30bd612e1f5).
    * Posted a comment to confirm if it's still a valid bug.


### [Medium] chromedriver 78 double clicks the wrong position ([https://crbug.com/42322257](https://crbug.com/42322257))



* Can reproduce using test case in [crrev.com/c/6648646](http://crrev.com/c/6648646) and running the test locally.
* Started investigating.


---


# SOCBB Bugfixing Igalia Status Update 2 July 2025

Hello, please find the biweekly update for the bugfixing work below.


### Testcase calling Window.moveTo() N times is 700x slower in Chrome compared to Firefox. N=500000 ([crbug.com/411906806](http://crbug.com/411906806))



* Solution: Tried to add a flag to skip window move in a renderer class (RenderFrameHostImpl) and set the flag based on the browser process status. ([crrev.com/c/6651786](http://crrev.com/c/6651786))
* Status: Unassigned myself from the issue - I abandoned the CL due to the code complexity that the CL introduces compared to the lack of the real-world benefit. To move this forward, it seems that we need clear real-world requirement. (For example, in case that the window need to provide 'window.ismovable' or 'window.isresizable' explicitely)
* hangs when switch to window containing alert ([crbug.com/40645076](http://crbug.com/40645076))
    * Analysis: In progress. Able to reproduce both expected behavior and unexpected behavior by modifying test. Trying to understand relevant call sequences of those different behavior. (ref. [issues/3#note_289320](https://gitlab.igalia.com/p/socbb/coordination/-/issues/3#note_289320))
    * **rbyers@ closed the issue with Won't fix(infeasible) **


### Feature request: Ability to screenshot whole tab, not just visible section ([crbug.com/40402691](http://crbug.com/40402691))



* No updates. Still waiting on the document to be reviewed


### Overlay scrollbars on one scroller appear when trackpad scrolling on another scroller ([crbug.com/402171647](http://crbug.com/402171647))



* Analyzed the root cause of the issue
* Sent the CL for review
* [https://crrev.com/c/6656458](https://crrev.com/c/6656458)


### Investigating feasibility of next bugs:



* aria role menuitemcheckbox, menuitemradio should have AXMenuItemMarkChar✓
    * [issues/41136076](https://issues.chromium.org/issues/41136076)
    * Component: Chromium > Blink > Accessibility
    * Analysis: The issue looks not directly related to the browser user or web developer as the attribute AXMenuItemMarkerChar seems to be used by apple script developers or apple platform.
* ScrollIntoView not prevented with focus({ preventScroll: true }) on text fields
    * [issues/41492445](https://issues.chromium.org/issues/41492445)
    * component: Chromium > Blink > HTML > Focus
    * Analysis: The solution can be controversial because it need to touch WebContents.java interface to fix the bug related to the tricky behavior on a specific case of adjusting its viewport for OSK like Android Chrome.
* Fallback glyphs in monospace fonts render with incorrect spacing
    * [issues/41367928](https://issues.chromium.org/issues/41367928)
    * component: Chromium > Blink > Fonts
    * Analysis: There doesn't seem to be big difference between browser engines and doesn't seem to be a clear solution to handle the nature of variations on each fonts (glyph coverage, metric, shaping rules, ...) yet, so it would be better to skip it unless it is a higher priority.
* font-style: italic doesn’t activate the ital axis of variable fonts
    * [issues/40681464](https://issues.chromium.org/issues/40681464)
    * Component: Chromium > Blink > Fonts
    * Analysis: The definition of ital axis looks not clearly agreed in font spec. There is an unresolved discussion about the spec ambiguity. Looks not positive to move forward before clarifying the font spec issue.
* Some Androids reporting hover: hover
    * [issues/41445959](https://issues.chromium.org/issues/41445959)
    * Component: Chromium > Blink > Input
    * Analysis: The issue is related to some specific Android devices, especially how Android framework in the device returns the information of the input devices. It seems there's nothing we can do on the Chromium side.
* Right-click on disabled element doesn’t show context menu
    * [issues/41302618](https://issues.chromium.org/issues/41302618)
    * Component: Chromium > Blink > Input
    * Analysis: The issue looks already fixed - can see context menu shows on disabled element. It seems waiting for the interop status update, and nothing to fix at this point.
* Content area flashes white when changing or re-opening tabs
    * [issues/40581308](https://issues.chromium.org/issues/40581308)
    * Component: Internals>Compositing
    * Analysis: Need to check more history, but given that the mac implementation's initial value of the last root background color is SK_ColorTRANSPARENT, it looks worth to try applying similar approach to aura impl.


---


# SOCBB Bugfixing Igalia Status Update 20 June 2025


Hello, please find the first of the biweekly status reports for Bugfixing below.


### cloneNode(true) becomes progressively slower [(crbug.com/40874584)](https://crbug.com/40874584)



* Analysis: In case a container element contains form elements and the form elements are inserted into a collection, cloning the container element can lead to call Document::InvalidateNodeListCaches() for each form element. Then the method iterates all the registered live node list to invalidate the node list cache. This can cause n^2 calls to LiveNodeListBase::InvalidateCacheForAttribute() for a single cloneNode() call.
* Solution: introduces a stack-allocated scoping class that defers calls to the Document::InvalidateNodeListCaches() method until after the call to the Element::CloneWithChildren() method on the node being cloned has finished to avoid node list cache invalidation for each descendant node.
* Status: Done/Fixed ([https://crrev.com/c/6606312](https://crrev.com/c/6606312))


### New failures introduced in external/wpt/uievents by import [https://crrev.com/c/2158157](https://crrev.com/c/2158157) [(crbug.com/40686014)](https://crbug.com/40686014)



* Analysis: Test code itself has an issue - test cannot be finished when the test fails.
* Solution: To prevent timeout on test failure, wraps click event handler function in t.step_func() so that the test can handle the assertion inside the event handler function.
* Status: Done/Fixed ([https://crrev.com/c/6587811](https://crrev.com/c/6587811))


### Testcase calling Window.moveTo() N times is 700x slower in Chrome compared to Firefox. N=500000 (crbug.com/411906806)



* Analysis: Traced the LocalDOMWindow::moveTo() method call sequence, and found out that mojo call to LocalMainFrameHost::SetWindowRect() in   WebViewImpl::SendWindowRectToMainFrameHost() took most of the time in this case. CSSOM View Module describes steps to process window move APIs, and they are an early return step for non-auxiliary browsing context [1]. Not clearly defined yet but the auxiliary browsing context can be simply checked by whether or not the opener browsing context is null [2]. But even if the context is non-auxiliary, the behavior of window move API call depends on executable target. For example, the API call does nothing when the browser window of the web content is for normal tabbed non-app browser (e.g. chrome browser). But the API call is working (it actually moves the window position) in other cases such as content shell, headless browser, web-app, etc. We can refer the implementation for BrowserWindowInterface::Type::TYPE_NORMAL, Browser::SetContentsBounds(), Shell::SetContentsBounds(), HeadlessWebContentsImpl::Delegate::SetContentsBounds().
* Solution: Trying find a way to check non-auxiliary browsing context of normal tabbed non-app browser. We may think about adding a flag in a renderer class (e.g. RenderFrameHostImpl) and set the flag in a browser class. But the solution looks controversial. (WIP - [https://crrev.com/c/6651786](https://crrev.com/c/6651786) / Need to add tests)
* Status: WIP
* Ref.
    * [1] [https://drafts.csswg.org/cssom-view/#dom-window-moveto](https://drafts.csswg.org/cssom-view/#dom-window-moveto)
    * [2] [https://html.spec.whatwg.org/#auxiliary-browsing-context](https://html.spec.whatwg.org/#auxiliary-browsing-context)


### Feature request: Ability to screenshot whole tab, not just visible section [(crbug.com/40402691)](https://crbug.com/40402691)



* Studied the existing tab.captureVisibleTab
* Made a prototype to capture the entire area
* Reported the prototype result - [https://issues.chromium.org/issues/40402691#comment106](https://issues.chromium.org/issues/40402691#comment106)
* Initial prototype - [https://chromium-review.googlesource.com/c/chromium/src/+/6606742](https://chromium-review.googlesource.com/c/chromium/src/+/6606742)
* Wrote a design doc [https://docs.google.com/document/d/1CQXeOs-f73Dlb9sINM3zm6s4vER6SKiM3JUGEpmvJrM](https://docs.google.com/document/d/1CQXeOs-f73Dlb9sINM3zm6s4vER6SKiM3JUGEpmvJrM) and requested rdevlin.cronin@chromium.org and tjudkins@chromium.org to review


### Overlay scrollbars on one scroller appear when trackpad scrolling on another scroller ([https://crbug.com/402171647](https://crbug.com/402171647))



* Confirmed the bug. Started the investigation of the root caus
