# Change Log

### 1.12.0

#### Improvements

- Added a [public GitHub issue tracker](https://github.com/Infineon/modustoolbox4vscode/issues) for bug reports, feature requests, and usage questions
- Improved AI Assistant status and guidance, including distinct disabled and uninstalled states, updated iconography, and direct documentation links
- Improved the Add AI Enhancements button with an explanatory tooltip and persistent per-project completion status across window reloads

#### Bug Fixes

- Fixed false AI Assistant installation notifications when the extension is installed but disabled
- Fixed the Getting Started guide link
- Fixed macOS clangd diagnostics for non-FPU targets by applying `-mfpu=none` only to affected project configurations
- Fixed bootloader setup failures in MAC OS
- Fixed stale project metadata, and delayed Application tab refresh after adding a bootloader

### 1.10.0

#### Improvements

- Added command palette entries for common ModusToolbox actions: opening projects, running tools, switching tabs, showing the main page, showing the output log, and toggling the peripheral-viewer read-batching override
- Added an AI creation workflow explainer webview and planning-workspace toast to guide users into the AI-assisted project flow
- Added an "Install AI Assistant" affordance in the Create Project view; when Python 3 is missing, the fix action now opens the python.org download page directly instead of showing a warning message
- Project Creator now launches the external Project Creator GUI from the Create Project view; the inline in-webview project creation flow has been removed
- Removed the "Install LLVM" warning card and the `disableLLVMNag` setting from the application page
- Duplicate-install detector warns users when multiple copies of the extension are installed
- Installer pages now scroll properly with themed scrollbars; the Configuration dropdown was widened so the label is no longer clipped
- Updated extension branding icons

#### Bug Fixes

- Fixed issue with importing project zip file in vs code .
- Fixed the extension hanging silently when `make vscode` failed; failures are now surfaced to the user 
- Fixed Windows builds by normalizing `CY_TOOLS_PATHS` to forward slashes
- Fixed User Guide table-of-contents anchor links not navigating
- Workspace-trust flow hardened: clangd/cortex-debug are now declared via `extensionPack`, the AI tile is gated by a `trustNeeded` state with a "Manage Workspace Trust" affordance
- Dropped the unused `vscode.git` extension dependency

### 1.8.0

#### Infineon ModusToolbox™ AI Assistant Integration

- Added detection and version-compatibility check for the Infineon ModusToolbox™ AI Assistant extension
- Create Project page now offers two paths: the guided wizard, and an AI-assisted path that opens a planning workspace and guides the user through project creation with Copilot Chat (with landing buttons and an Edge-only note guiding users into the AI flow)
- Prerequisite checks for the ModusToolbox™ AI Assistant surface a greyed tile with actionable buttons when the AI Assistant is disabled, uninstalled, needs to be updated, is missing GitHub Copilot Chat, or is missing Python dependencies
- New "Add AI Enhancements" task in the application view generates AI planning instructions; the task is shown with a state-aware tooltip explaining why it is disabled when the AI Assistant is not ready
- New "Plan" subtab renders the project's `mtb-application-plan.md` when present
- Updated extension icon

### 1.6.0

#### Improvements

- Bundled Source Sans 3 fonts and Infineon-style SVG icons in the extension so webview UI no longer depends on external resources
- LLVM versions list is now bundled with the extension instead of fetched from mewserver.org 
- Bootloader final-steps document is now bundled with the extension and accessible via a new show-doc command and button in application page.
- TRAVEO™ support added to the extension description; PSOC™ capitalization normalized throughout 
- Project creation now shows a BSP summary and description for all BSPs
- Clangd is now the default C/C++ IntelliSense provider for ModusToolbox projects; Microsoft cpptools is suppressed via `unwantedRecommendations` and the clangd/cpptools conflict popup no longer appears
- On macOS, `clangd.path` is automatically set to a valid LLVM clangd ≥ 17 (from the clangd extension's bundled download, Homebrew, or MacPorts) so Apple's Xcode-bundled clangd no longer breaks ARM bare-metal IntelliSense

#### Bug Fixes

- Fixed invisible/low-contrast text in the extension UI
- Fixed icons not centered or aligned in extension tabs and buttons
- Fixed UI issues on the LCS tab
- Fixed compiler tasks failing when the compiler path contains spaces
- Fixed `tools_min_version` / `tools_max_version` not being enforced for BTSDK code examples 
- Fixed code examples being filtered to a narrower BSP version range than the project-creator displays
- Removed tool version numbers from the Applications status panel
- Fixed the custom tools path field: it now validates the directory (rejecting non-existent paths and empty/aborted installs), shows inline errors, and appears under the Tools Version dropdown only when "Custom" is selected
- Fixed the tools version not honoring the user's choice: the selected version now persists across workspaces instead of silently falling back to the newest installed tools
- Fixed a custom tools path with Windows backslashes breaking project creation: the path is now normalized to forward slashes so make no longer reports "Unable to find any of the available CY_TOOLS_PATHS"

### 1.4.0

#### Improvements

- Improved VS Code extension startup experience by changing autodisplay default from "Always" to "When ModusToolbox Project Loaded"

#### Bug Fixes

- Fixed incorrect font rendering in the extension UI
- Fixed graphical glitches on Steps 2 and 3 of the Software Installer wizard
- Fixed unreadable white text on white background in the project creation completion message
- Fixed places where "ModusToolbox" was misspelled throughout the extension

### 1.2.0

#### Branding & Appearance

- Renamed extension to **Infineon ModusToolbox™ for VS Code** for Visual Studio Marketplace availability
- Updated extension icon to the Infineon logo
- Refreshed icons throughout the UI with the Infineon design language

#### Improvements

- Connected dev kits that support multiple BSPs (e.g., PSOC™ Edge E84) now display a separate entry for each valid BSP in the kit list

#### Bug Fixes

- Fixed Memory Usage view showing incorrect data for multi-core projects where different core types share the same bus master index (e.g., PSOC™ Edge with CM33 + CM55)
- Fixed Memory Usage view errors when an application contains multiple projects targeting the same core, or when the target device lacks external memory resources
- Fixed manifest URI resolution that could prevent BSP and middleware discovery in certain configurations
- Fixed the Software Installer page not showing the "Select Tools Location" option when the ModusToolbox tools package is the only missing prerequisite
- Improved robustness of XML configuration file parsing to handle variant element formats

#### Security

- Access tokens are no longer written to diagnostic logs

### 1.0
First version of ModusToolbox™ for VS Code