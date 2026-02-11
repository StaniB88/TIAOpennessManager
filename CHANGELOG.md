# TIA Openness Manager - Changelog

## v1.2.12 (2026-02-11)

### New Features
- **Connect Dialog** - New "Connect to TIA Portal" dialog replaces the old Browse and Attach buttons. Two tabs: "Attach to Running" lists running TIA instances, "Open Project" lets you browse for a project file
- **Folder Path Overlay** - Shows the selected right folder path at the bottom of the right panel

### Changes
- Removed TIA Project path bar from toolbar
- Removed Browse and Attach buttons from toolbar (replaced by Connect dialog)

### Bug Fixes
- **Headless TIA Portal cleanup** - Disconnecting from a headless project now fully closes the TIA Portal process, preventing it from interfering with subsequent Attach operations

---

## v1.2.11 (2026-02-10)

- General bug fixes and improvements

---

## v1.2.10 (2026-01-29)

- Reduced subscription prices (Pro CHF 9.99/mo, Enterprise CHF 29.99/mo)

---

## v1.2.9 (2026-01-27)

### New Features
- **User Guide Button** - Added "User Guide" button in toolbar to open built-in documentation
- **Indeterminate Progress Bar** - Progress bar now shows marquee animation during Browse/Attach until project tree is fully loaded

### Bug Fixes
- **Language Change Crash** - Fixed application crash when changing language in Settings
- **Tooltip Correction** - Fixed TIA Project tooltip referencing non-existent "Open Project" button (now "Browse")
- **Project Path Behavior** - TIA Project path no longer persists between sessions; shows only currently connected project

---

## v1.2.8 (2026-01-23)

### New Features
- **Protection Checkboxes for OBs** - AllowCodeUpdates and AllowAttributeUpdates options for protected Organization Blocks
- **Browse Profiles Folder** - Button to open profiles folder for easy sharing

---

## v1.2.7 (2026-01-21)

### Bug Fixes
- **Protection Logic** - Fixed path-based protection matching to prevent false positives
  - Removed name fallback that could incorrectly protect unrelated items with same name
  - Protection now uses strict path-only matching
- **Settings Persistence** - Fixed settings not being saved correctly
- **Compare Window Format Matching** - Fixed file format mismatch in manual compare
  - Left side (TIA export) now matches the format of the right side file (SCL↔SCL, XML↔XML, AWL↔AWL)
  - Fixed issue where selecting an XML file would silently load SCL content if both existed

### New Features
- **Export Fingerprints Option** - New setting to toggle fingerprint extraction during export
  - Disable to speed up exports when change detection is not needed

---

## v1.2.6 (2026-01-20)

### New Features
- **Per-Type Export Options** - Export settings (WithDefaults, WithReadOnly, None) now configurable separately for:
  - Data Blocks (DBs)
  - User Defined Types (UDTs)
  - Tags
  - Provides granular control over export behavior per element type

### Improvements
- **SCL Comment Normalization** - NormalizeWhitespace setting now also normalizes SCL source files
  - Ensures exactly one space after `//` in VAR section comments
  - Reduces Git diff noise from inconsistent comment formatting
  - Only processes VAR/VAR_INPUT/VAR_OUTPUT/VAR_IN_OUT/VAR_TEMP sections (code comments unchanged)
- **Uninstall License Cleanup** - Installer now prompts during uninstall whether to remove license data
  - Choosing "No" preserves license activation for easy reinstallation
  - Choosing "Yes" performs a clean removal including Trial and License registry keys

---

## v1.2.5 (2026-01-18)

### Bug Fixes
- **Instance DB Folder Placement** - Fixed Instance DBs landing in wrong folder during Import All
  - Instance DBs now correctly placed in their original subfolder structure
- **Folder Name Detection** - Improved detection of block folder names
  - Now uses configured folder names from Settings instead of hardcoded fallbacks
  - Supports projects with localized folder names (Program blocks, Programmbausteine, etc.)
- **HMI Item Deletion** - Fixed "Delete" context menu for all HMI item types
- **AML Import Performance** - Fixed performance issue where project tree was rebuilt after each file

### Improvements
- **Extended Trial Period** - Trial period increased from 7 days to 30 days
- **Project Library Tree** - Added Project Library (Master Copies & Types) to tree building
- **UI Tooltips** - Added helpful tooltips throughout the application:
  - Preview Diff button: Clarifies that exported fingerprints are required
  - Offline Folder path: Explains offline browsing mode
  - And many more tooltips for better discoverability

---

## v1.2.4 (2026-01-17)

### New Features
- **Compare Files** - Added file comparison feature for exported projects (same-side comparison)
- **Open Exported Project** - Left tree now supports opening exported project folders

### Bug Fixes
- **Instance DB Import** - Fixed import errors ("Element cannot be found") when importing Instance DBs after SCL compilation

### Improvements
- **Compare Tab** - Removed auto-tab-jump behavior, added green highlight for Graphic tab selection

---

## v1.2.3 (2026-01-16)

### Security
- **Enhanced Clock Manipulation Detection** - Now detects both backward and forward system clock manipulation attempts
- **Server-Time Validation** - Additional check compares local time against server expiry date to prevent bypass attempts

### Improvements
- **Installer: Extended TIA Version Check** - Installer now checks for TIA Portal V15-V20 (previously only V18-V20)

---

## v1.2.2 (2026-01-02)

### Bug Fixes
- **Remove V21 from Settings** - Removed TIA Portal V21 option from API version dropdown to prevent crashes (V21 support not yet stable)

---

## v1.2.1 (2026-01-01)

### New Features
- **Legal Document Access** - Quick access to Privacy Policy and EULA directly from the About Window
- **Website Link** - Clickable website link in About Window opens [tiaopenessmanager.ch](https://tiaopenessmanager.ch)

### Bug Fixes
- **Find Unused** - Fixed incorrect detection of Instance DBs

### Improvements
- About Window redesigned with action buttons for better usability
- Updated User Guides with latest documentation 

## v1.2.0 (2025-12-30)

Various bugfixes, performance optimizations, and stability improvements.

---

## v1.1.7 (2025-12-30)

### New Features
- **Import/Export Settings Window** - New dialog for configuring import and export behavior
- **SPL Export Support** - Export SCL/AWL/LAD/FBD blocks as SIMATIC Source Documents (.spl format, V20+)
- **Export Options** - Configure export with defaults and read-only attributes
- **Import Options** - Ignore structural changes and missing references during import

### Improvements
- **Safety Block Detection** - Improved detection of Safety blocks in S7DCL format (V20 Update 4+)

### Technical
- Added ExportBlockToSplAsync method for SIMATIC Source Document export
- Updated documentation with V21 references for future releases

---

## v1.1.6 (2025-12-22)

### New Features
- **7-Day Full Trial** - New users get a 7-day trial with ALL features unlocked (Enterprise-level)

## v1.1.5 (2025-12-21)

### Bug Fixes
- **Language Switching Fixed** - Language switching now works correctly in the installed version
  - Added missing language satellite assemblies to installer
