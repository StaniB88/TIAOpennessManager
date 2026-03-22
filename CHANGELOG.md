# TIA Openness Manager - Changelog

## v3.0.2 (Unreleased)

### Bug Fixes
- **Exit button not working in license dialog** - Clicking Exit/Close had no effect
- **Manage Subscription button text truncated** - Button text was cut off in the license dialog
- **License status shows Free on startup** - Status bar showed "Free" despite active license until dialog was opened

---

## v3.0.1 (2026-03-22)

### Improvements
- **License status in status bar** - Clickable license indicator shows current tier (Free/Trial/Professional/Enterprise) with color coding
- **License access in Help menu** - "Manage License" is now directly accessible from the Help menu

### Bug Fixes
- **Trial button text truncated** - "Start 30-Day Trial" button in the license dialog was cut off

---

## v3.0.0 (2026-03-02)

### Major Release - Complete Rewrite

- **New Architecture** - Two-process design: .NET 10 Avalonia UI app + .NET 4.8 Bridge (COM proxy) via Named Pipes
- **Cross-Platform UI** - Migrated from WPF to Avalonia 11.x with dark theme
- **MediatR Pipeline** - Command/Query separation for all business logic
- **MCP Server** - Built-in Model Context Protocol server for AI assistant integration
- **OPC UA Client** - Browse and read OPC UA server address spaces with struct support
- **Improved Localization** - Runtime language switching (EN, DE, FR, IT) without restart
- **Velopack Auto-Updates** - In-app update mechanism via GitHub Releases
- **Password Vault** - Encrypted credential storage for TIA Portal connections
- **Enhanced Export** - Source code generation, structured export paths, fingerprint caching
- **.NET Reactor Obfuscation** - Three-tier protection (App, Bridge, MCP Bridge)
- **Code Signing** - Certum SHA-256 signed binaries and installer

---

## v1.2.2 (2026-01-02)

### Bug Fixes
- **Remove V21 from Settings** - Removed TIA Portal V21 option from API version dropdown to prevent crashes (V21 support not yet stable)

---

## v1.2.1 (2026-01-01)

### New Features
- **Privacy Policy & EULA Integration** - Added direct access to legal documents from About Window
  - New "Privacy Policy" button opens Privacy.md
  - New "EULA" button opens EULA.md
  - Documents automatically included in installer and build output
- **Website Link in About Window** - Added clickable website link (https://tiaopenessmanager.ch)
  - Opens in default browser when clicked
  - Matches existing GitHub link functionality

### Changes
- About Window now displays three buttons: "View Full Licenses", "Privacy Policy", and "EULA"
- Privacy.md and EULA.md copied from Software Dokumente folder to project root for distribution

### Technical
- AboutWindow.xaml: Added Privacy and EULA buttons in horizontal stack panel
- AboutWindow.xaml.cs: Added `BtnViewPrivacy_Click()` and `BtnViewEula_Click()` handlers
- TiaOpennessManager.csproj: Configured Privacy.md and EULA.md to copy to output directory
- Software Dokumente folder now tracked in repository (11 legal/product documentation files)

---

## v1.2.0 (2025-12-30)

### New Features
- **Swiss Franc (CHF) Currency Support** - Automatic IP-based region detection for Switzerland
  - Swiss users automatically see CHF prices (Professional: CHF 25/250, Enterprise: CHF 40/400)
  - IP geolocation service (ip-api.com) detects user location on startup
  - All other regions continue to see EUR prices
- **Centralized Pricing Configuration** - New `PricingConfiguration.cs` with single source of truth for all prices and payment links
- **8 Stripe Payment Links** - Complete coverage for EUR/CHF, Professional/Enterprise, Monthly/Yearly combinations

### Changes
- **Enterprise Price Reduction** - EUR Enterprise pricing reduced from €50/€500 to €40/€400 (CHF 40/CHF 400)
- **Removed Manual Currency Toggle** - Currency is now fully automatic based on IP location (no user override)
- **Updated EULA Files** - VERSION line now automatically updated during releases

### Fixed
- **EUR Price Flash** - Fixed brief EUR price display on dialog open (removed hardcoded XAML defaults)
- **IP Detection Always Runs** - Ignores cached currency preference to ensure fresh detection

### Technical
- New `RegionService.cs` - IP geolocation singleton with 5-second timeout and caching
- New `Currency` enum (EUR, CHF) and `LicenseTier` enum (Professional, Enterprise)
- Enhanced debug logging for currency detection troubleshooting
- Release script now updates `LICENSE_EN.txt` and `LICENSE_DE.txt` version numbers automatically

---

## v1.1.7 (2025-12-30)

### New Features
- **Import/Export Settings Window** - New dialog for configuring import and export behavior
- **SPL Export Support** - Export SCL/AWL/LAD/FBD blocks as SIMATIC Source Documents (.spl format, V20+)
- **Export Options** - Configure export with defaults and read-only attributes
- **Import Options** - Ignore structural changes and missing references during import

### Improvements
- **V21 Infrastructure** - Prepared codebase for future TIA Portal V21 support
- **MCP Server** - Updated code generation tools for V21 compatibility
- **Safety Block Detection** - Improved detection of Safety blocks in S7DCL format (V20 Update 4+)

### Technical
- Enhanced TiaPortalApiResolver with V21 assembly resolution logic
- Added ExportBlockToSplAsync method for SIMATIC Source Document export
- Updated documentation with V21 references for future releases

---

## v1.1.6 (2025-12-22)

### New Features
- **7-Day Full Trial** - New users get a 7-day trial with ALL features unlocked (Enterprise-level)
- **Server-Side Trial Tracking** - Trial period is tracked on our server using hardware fingerprint
- **Anti-Reinstall Protection** - Reinstalling the app does NOT reset your trial period

### Changes
- **Trial = Enterprise** - During trial, all features are available: Safety blocks, Bulk Import, Protection Profiles, MCP Server, Find Unused
- **After Trial** - Falls back to Basic tier (limited features) or purchase a license to continue

### Technical
- New backend endpoint for trial registration and status checking
- Hardware-ID based tracking prevents trial abuse

---

## v1.1.5 (2025-12-21)

### Bug Fixes
- **Language Switching Fixed** - Language switching now works correctly in the installed version
  - Fixed ConfuserEx obfuscation encrypting resource files
  - Added missing language satellite assemblies (de/, fr/, it/) to installer

### Improvements
- **Settings Dialog Translations** - Added missing translations for Folder Names and License Information sections in all languages (DE/FR/IT)
- **Smaller Installer** - Reduced installer size by ~3MB (removed bundled Siemens.Engineering DLLs that are loaded from TIA Portal at runtime)

---

## v1.1.4 (2025-12-21)

### New Features
- **Online License Activation** - New activation system using activation codes (ACT-XXXX-XXXX-XXXX format)
- **Hardware-Bound Licenses** - Licenses are now bound to your machine for added security
- **Free Basic Tier** - Basic tier is now permanently free (no trial expiration)
- **Monthly/Yearly Toggle** - Switch between monthly and yearly billing directly in the app
- **Direct Stripe Checkout** - Subscribe buttons now open Stripe checkout directly (no website redirect)

### Improvements
- **Simplified Activation** - Enter your activation code received via email to unlock Pro/Enterprise features
- **License Server Integration** - Licenses are validated against our secure server
- **Manage Subscription Button** - Improved visibility with accent color styling
- **Dynamic Pricing Display** - Prices update automatically when switching between monthly/yearly

---

## v1.1.3 (2025-12-20)

### Bug Fixes
- **Auto-Update not working** - Added missing AutoUpdater.NET.dll to installer package (update feature was broken since v1.1.0)

---

## v1.1.2 (2025-12-20)

### Bug Fixes
- **FindUnused false positives on some machines** - Removed debug code that caused XML parsing to fail silently on machines without a specific folder structure

---

## v1.1.1 (2025-12-20)

### New Features
- **Clear Code Button** - New button to clear the code editor content
- **Clear Results Button** - New button to clear Find Unused results
- **Auto-Clear on Project Close** - Code editor and Find Unused results are automatically cleared when project is closed

### Bug Fixes
- **Instance DBs marked as unused** - FindUnused now correctly detects Instance DB references from FB calls (prevents false positives)
- **ObjectDisposedException after detach** - Fixed stale facade reference when detaching from attached TIA Portal instance

### Improvements
- **Import Progress Display** - Progress label now shows current file name being imported
- **About Dialog** - Added clickable GitHub link for easy access to the repository
- **Third-Party Licenses** - Added AutoUpdater.NET to the licenses list in About dialog and THIRD_PARTY_NOTICES.txt

---

## v1.1.0 (2025-12-20)

### New Features
- **Auto-Update Check** - Application now checks for updates at startup and notifies when a new version is available
- **Update Settings** - New checkbox in Settings to enable/disable automatic update checks

### Bug Fixes
- **Progress bar not fully filled** - Progress bar now shows 100% when operations complete (Analysis, Export, HMI Export)

---

## v1.0.1 (2025-12-18)

### Bug Fixes

- **Checkbox state lost during search/filter** - Checkboxes in left and right tree now persist when filtering or searching multiple times
- **Selection count incorrect with filter** - Import/Export selection count now correctly reflects checked items even when filter is active
- **Delete Selection fails with filter** - Delete operation now works correctly when tree is filtered
- **Single block import progress bar** - Progress bar now updates correctly for imports with less than 5 files
- **Right-click doesn't select item** - Right-clicking on a tree item now selects it before showing context menu
- **Missing Import button in right tree** - Added Import option to right tree context menu
- **FindUnused false positives** - Fixed reference detection for FC calls with direct Component pattern in XML
- **Fingerprint export progress** - Progress bar now includes fingerprint cache update phase after export
- **MCP Generate FC fails** - Fixed VAR section removal regex to only remove standalone VAR, not VAR_INPUT/VAR_OUTPUT/VAR_TEMP
