
# DevTools: Omnibox Commands

Authors:
 - [Erica Draud](https://github.com/erdraud), Program Manager

## Status of this feature
This feature is a proposed experiment. To track the project status, you can see the scenario here: [[Experiment] DUX Omnibox Commands](https://dev.azure.com/microsoft/Edge/_workitems/edit/29631932)

## Introduction
Earlier this year, the Chrome team released the [Commander]( https://bugs.chromium.org/p/chromium/issues/detail?id=1014639) as a text interface that provides a shortcut for common commands for browser users. The DevTools team used this as the framework for their Omnibar hackathon project. There’s some uncertainty around the usage and discoverability of the tool, so we’re starting with a flagged experiment.
![Omnibox UI](omni.PNG)
You’ll notice that many of the commands in this feature can be found in the [Command Menu]( https://docs.microsoft.com/en-us/microsoft-edge/devtools-guide-chromium/command-menu/) in DevTools, so why have these features in the address bar (from this point forward referred to as the omnibox)? We know that users would like a faster way to complete their tasks in DevTools, and the Omnibox Commands feature enables users to do so without having to first open the Developer Tools. Additionally, we’ve included features that are specific to the browser window: Edge internal urls and last viewed pages.

## Goals
  1. To simplify DevTools users’ workflow and
  2. To test the following hypotheses:
      * Users will find this valuable in that it will save them time by minimizing the steps users need in their DevTools workflow; we'll know it's true if 20% of users are 2-week active users (returning users).
      * Users will use navigation commands more than action commands; we'll know it's true if the number of navigation commands is at least 20% more than the number of action commands.
      * Users will have trouble finding this feature without a tooltip/pop-up; we'll know it's true with overall usage (if people turn it on).
This initial experiment will run for two weeks off by default for external users and on 100% for internal users. While we will be testing all three hypotheses, we will focus on iterating for validating the feature’s value and which commands are most valuable.

## Features

### URL
To easily access internal URLs, you can type in a question mark `?`. This will pull up a list of all the Edge internal URLs. To access the existing URLs, click [here](#available-urls).
### Command
Typing `>` will pull up the available commands for DevTools. These commands were exported from those available in DevTools now. The only command added to the list that hasn’t already been added to the Commander experiment is *Device Mode: Enable Device Mode*, and we will omit this command if we don’t have time in the first iteration to add it. Most of these commands are opening panels or changing the appearance or theme of the DevTools. To access the existing commands, click [here](#available-commands).
### Search
If you type something in that isn’t a command, the Omnibox will display an option to search the text typed in the user’s preferred search engine.
### Recently closed
To get a list of the webpages you recently closed, type `#`.

## Next steps
* Design review
* Flagged rollout
* Add Documentation Search

## Things to consider
* Commands shouldn't conflict with search engine searches
* Accessibility and privacy compliance needs work
* Need to remove Chrome's petal suggestions for technical, localization, and business reasons.
* Commands are relatively easy to add, so we can always add more in the future

## Available URLs
* edge://about/
* edge://accessibility/
* edge://appcache-internals/
* edge://application-guard-internals/
* edge://apps/
* edge://autofill-internals/
* edge://blob-internals/
* edge://bluetooth-internals/
* edge://collected-cookies-dialog/
* edge://compat/
* edge://components/
* edge://conflicts/
* edge://conversion-internals/
* edge://crashes/
* edge://credits/
* edge://data-viewer
* edge://device-log/
* edge://discards/
* edge://download-internals/
* edge://downloads/
* edge://edge-dip-internals/
* edge://edge-urls/
* edge://extensions/
* edge://favorites/
* edge://flags/
* edge://floc-internals/
* edge://gcm-internals/
* edge://gpu/
* edge://help/
* edge://histograms/
* edge://history/
* edge://indexeddb-internals/
* edge://inspect/
* edge://interstitials/
* edge://invalidations/
* edge://local-state
* edge://management/
* edge://media-engagement/
* edge://media-internals/
* edge://net-export/
* edge://net-internals/
* edge://network-error/
* edge://newtab/
* edge://ntp-tiles-internals/
* edge://omnibox
* edge://password-manager-internals/
* edge://policy/
* edge://predictors/
* edge://prefs-internals/
* edge://print/
* edge://process-internals/
* edge://push-internals/
* edge://quota-internals/
* edge://sandbox/
* edge://serviceworker-internals/
* edge://settings/
* edge://signin-internals/
* edge://site-engagement/
* edge://sync-internals/
* edge://system/
* edge://terms/
* edge://tracing/
* edge://translate-internals/
* edge://ukm/
* edge://usb-internals/
* edge://user-actions/
* edge://version/
* edge://web-app-internals/
* edge://webrtc-internals/
* edge://webrtc-logs/
* edge://whats-new/

## Available commands
* Panel: Show Application
* Panel: Show Console
* Panel: Show Detached Elements
* Panel: Show Elements
* Panel: Show JavaScript Profiler
* Panel: Show Layers
* Panel: Show Lighthouse
* Panel: Show Media
* Panel: Show Memory
* Panel: Show Network Drawer
* Panel: Show Performance
* Panel: Show Security
* Panel: Show Sources
* Panel: Show Welcome
* Drawer: Focus debugger
* Drawer: Show 3D View
* Drawer: Show Animations
* Drawer: Show Changes
* Drawer: Show Console
* Drawer: Show Coverage
* Drawer: Show Developer Resources
* Drawer: Show Issues
* Drawer: Show Memory Inspector
* Drawer: Show Network Console
* Drawer: Show Network conditions
* Drawer: Show Network request blocking
* Drawer: Show Performance monitoring
* Drawer: Show Quick source
* Drawer: Show Rendering
* Drawer: Show Search
* Drawer: Show Sensors
* Drawer: Show WebAudio
* Drawer: Show WebAuthn
* Drawer: Toggle drawer
* Settings: Documentation
* Settings: Settings
* Settings: Shortcuts
* Settings: Show Devices
* Settings: Show Experiments
* Settings: Show Library Code
* Settings: Show Locations
* Settings: Show Preferences
* Settings: Show Shortcuts
* Settings: Show Throttling
* Appearance: Browser UI language 
* Appearance: Chinese (Simplified)
* Appearance: Chinese (Traditional)
* Appearance: Do not show Welcome after each update
* Appearance: French
* Appearance: German
* Appearance: Italian
* Appearance: Japanese
* Appearance: Korean
* Appearance: Portuguese
* Appearance: Russian
* Appearance: Set color format to HEX
* Appearance: Set color format to HSL
* Appearance: Set color format to RGB
* Appearance: Spanish
* Appearance: Switch to Abyss theme
* Appearance: Switch to Chromium Dark theme
* Appearance: Switch to Chromium Light theme
* Appearance: Switch to Dark+ (Default) theme
* Appearance: Switch to Kimbie Dark theme
* Appearance: Switch to Light+ (Default) theme
* Appearance: Switch to Monokai Dimmed theme
* Appearance: Switch to Monokai theme
* Appearance: Switch to Quiet Light theme
* Appearance: Switch to Red theme
* Appearance: Switch to Solarized Dark theme
* Appearance: Switch to Solarized Light theme
* Appearance: Switch to system preferred color theme
* Appearance: Use horizontal pane layout
* Appearance: Use vertical pane layout
* Console: Clear console history
* Console: Create live expression
* Console:  Do not autocomplete from history
* Console: Do not eagerly evaluate console prompt text
* Console: Do not group similar messages in console
* Console: Do not treat evaluation as user activation
* Console: Hide network messages
* Console: Only show messages from the current context (top, iframe worke…
* Console: Preserve log upon navigation
* Console: Show Console
* Console: Show timestamps
* Debugger: Disable JavaScript
* Debugger: Do not capture async stack traces
* Debugger: Pause on exceptions
* Device Mode: Enable Device Mode
* Elements: Copy styles
* Elements: Disable DOM word wrap
* Elements: Duplicate element
* Elements: Edit as HTML
* Elements: Hide HTML comments
* Elements:  Hide element
* Elements:  Redo
* Elements: Select an element in the page to inspect it
* Elements: Show Accessibility
* Elements: Show DOM Breakpoints
