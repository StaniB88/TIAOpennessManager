# TIA Openness Manager - Changelog

## v3.0.9 (2026-04-02)

### AI Chat
- **Task Panel** — The AI now shows a live task list when working on complex tasks. Displays progress (e.g. 3/10), collapses to a compact header, and auto-hides when all tasks are completed.
- **Plan Mode** — New toggle: the AI must submit a plan for approval before writing files. Approve or reject with optional feedback.
- **Prompt Templates** — Skills now support agent dispatch and a `/` shortcut in the chat input for quick access.
- **Instructions** — Context Folders replaced by a hierarchical instructions system (global → project → settings) with `@include` support.
- **Auto-Dream** — The AI automatically consolidates memories across sessions. Configurable in Settings → Memory.
- **Sub-Agent Improvements** — Sub-agents inherit conversation context (fork), communicate with each other, and remember results from prior agents.
- **Context Compaction** — Improved summaries for long conversations with structured boundary markers.
- **Tool Optimization** — Sub-agents only receive the tools they need. Shorter tool descriptions and tooltips in the UI.

### AI Canvas
- **Canvas → OPC UA Write Bridge** — Canvas buttons and sliders can now write values directly to OPC UA nodes. Use `canvas_bind_opcua_write` to map UI actions (onClick, onChange) to PLC variables. Supports fixed values (buttons) and dynamic payload values (sliders).
- **Canvas Reset** now also stops all write bindings alongside read bindings.

### OPC UA
- **Write Complex Tool** — New `opcua_write_complex` tool for writing individual fields of a data block or struct via OPC UA. Uses read-modify-write pattern to update specific fields without overwriting the entire struct.

### Bug Fixes

- Fixed text file attachments (`.md`, `.txt`, `.json`, `.cs`, etc.) being unreadable by the AI when dropped into the chat
- Fixed inability to send file attachments without typing a text message first
- Fixed PLC export losing the device name folder (e.g. PLC_1) when "Create Source Folder" setting was disabled

## v3.0.8 (2026-04-01)

### AI Chat
- **Auto-Save Settings** — All settings in the AI Chat Settings dialog now save immediately on change. No more Save/Cancel buttons — just change a setting and close the window.
- **Per-tool toggles** — Individual tools within a category remember their enabled/disabled state independently. Toggling a category off and back on restores each tool's individual setting.
- **Tool auto-approve persistence** — The auto-approve toggle for individual tools now persists across app restarts.
- **MCP Server stop fix** — Stopping an MCP server in Settings now properly prevents it from restarting on the next message or app launch.

### AI Canvas
- **Panel resize fix** — Canvas panel no longer disappears when collapsed after resizing. Minimum width prevents dragging to invisible size.

### File Explorer
- **Save support** — Ctrl+S saves the active file. Closing a tab with unsaved changes shows a Save / Don't Save / Cancel dialog.

## v3.0.7 (2026-03-31)

### AI Chat
- **Context Compaction** — Long conversations no longer crash with "context length exceeded" errors. When the chat approaches the model's context limit, the AI automatically summarizes older messages into a structured summary and continues seamlessly. A token usage indicator (~12K / 128K) is now shown in the chat stats.
- **Session Memory** — When switching or clearing chats, the AI automatically saves a summary of the conversation to long-term memory. Configurable in Settings → Memory: enable/disable, number of messages to include (default 15), and optional LLM-generated summaries instead of raw message logs.
- **Collapsible memory entries** — Memory entries in Settings → Memory are now collapsed by default, showing only a one-line preview. Click the chevron to expand the full content.
- **Tool call fix for parameterless tools** — Fixed an "invalid request body" error (HTTP 400) when the AI used tools without parameters (e.g. listing canvas surfaces). The tool input was sent as null instead of an empty object.

## v3.0.6 (2026-03-30)

### Hotfix
- **Canvas crash on installed version** — Fixed a crash when opening the AI Canvas in the installed application.

## v3.0.5 (2026-03-29)

### AI Chat — Complete Redesign
The AI Chat has been rebuilt from the ground up with a new architecture based on Semantic Kernel.
- **New provider system** — Switch between Anthropic, OpenAI, Google, Ollama, OpenRouter, and GitHub Copilot with provider icons and per-provider settings (temperature, top-p, timeout, custom endpoints)
- **Skills** — Quick-access prompt templates with the scroll icon in the chat input bar. Includes built-in skills (Explore Project, Explain Block, Generate SCL, Compare Blocks) and supports custom user-created skills
- **File attachments** — Drag and drop files directly into the chat. The AI reads text files (Markdown, JSON, source code) via the built-in file read tool
- **Visual Context** — The AI can see and interact with your screen: list windows, capture UI elements, read visual trees, and automate clicks and keyboard input
- **AI Connect** — The AI can connect to TIA Portal on its own via `tia_connect`, running the exact same connection flow as the manual Connect button (tree refresh, profile loading, HMI detection)
- **Chat history** — Conversations are persisted in a local SQLite database with branching (edit/retry), session list, and token usage stats
- **Database cleanup** — Configurable retention period (30/60/90 days) in Settings → Storage. Automatic cleanup on startup, manual "Cleanup Now" button with database size display
- **Reasoning model support** — Models with reasoning/thinking tokens (e.g. DeepSeek, QwQ) are now displayed correctly with collapsible thinking sections

### AI Chat — Essential Tools
- **To-Do List** — The AI can create and manage a task checklist during complex multi-step operations, tracking progress with status icons
- **Sub-Agent Dispatching** — The AI can delegate focused sub-tasks to an isolated agent with its own conversation context, preventing context pollution during complex workflows
- **MCP Server Connections** — Connect external MCP (Model Context Protocol) servers to extend the AI with additional tools. Supports Stdio and HTTP transports. Configure, start/stop, and manage servers in Settings → MCP Servers

### AI Canvas
- **Interactive Canvas** — The AI can create interactive HTML/JavaScript canvases with live previews. Build dashboards, visualizations, and custom UIs directly in the app.
- **Real-time OPC UA binding** — The AI can bind OPC UA variables to canvas elements using `canvas_bind_opcua`. Values update live, enabling real-time process visualization dashboards.
- **TIA custom Web Components** — Five ready-to-use components for automation: SignalChart (live trending), Gauge (radial indicator), VariableDisplay (tag monitor), BlockDiagram (process flow), and AlarmTable (alarm list).
- **Popout window** — Detach the canvas to a separate window for multi-monitor setups.
- **Save & Load** — Export canvas content as JSONL files and reload them later.

### WinCC Unified — Screen Editor
- **Visual Screen Editor** — New canvas-based editor for WinCC Unified screens. Drag, resize, and inspect screen items visually with a property grid. Zoom with Ctrl+Scroll or Ctrl+/-, pan with middle mouse button.
- **AI-powered screen creation** — The AI Chat can create, modify, and manage WinCC Unified screens using dedicated MCP tools. Ask the AI to build screens with buttons, I/O fields, text boxes, and other elements — it creates them directly in the canvas editor.
- **Export to TIA / Import from TIA** — Transfer screens between the canvas editor and TIA Portal in both directions.

### New Features
- **WinCC Unified screen export/import** — Full export and import of WinCC Unified HMI screens via the TIA Portal Openness property-level API. Exports all screen items (buttons, I/O fields, text boxes, graphics, list boxes, etc.) with positions, colors, fonts, texts, compositions, dynamizations, and events as JSON files. Import recreates screens with all properties. Supports TIA Portal V19 and later.
- **WinCC Unified HMI Tags and Scripts** — Export and import HMI tag tables (YAML format via Siemens directory-based API) and export JavaScript script modules from WinCC Unified devices. Each tag table and script module exports to its own folder.
- **WinCC Unified extended project tree** — The project tree now shows HMI Alarms (Discrete/Analog), Alarm Classes, Scripts, Logs (Data Logs/Alarm Logs), Text Lists, and Graphic Lists for WinCC Unified devices — matching WinCC Classic's coverage.
- **OPC UA multi-select and multi-drag** — Select multiple OPC UA nodes in the tree and drag them to the Watch Table in one operation.
- **OPC UA settings** — New gear icon for OPC UA configuration with logging toggle.
- **Openness Firewall auto-whitelist** — The installer automatically registers the application in the Siemens TIA Portal Openness Firewall whitelist (V15–V21). No more manual confirmation dialog when connecting to TIA Portal.

### Bug Fixes
- **GitHub Copilot provider** — Sign-in, model fetching, and token handling for GitHub Copilot now work correctly.
- **Ollama timeout** — Default request timeout increased from 20s to 120s, fixing cold start timeouts with large Ollama models.
- **Connect dialog resizable** — The Connect to TIA Portal dialog can now be resized, preventing cut-off text with long instance names.
- **Import All: Safety deletion now stops immediately** — When deleting a group containing safety elements fails, the import now stops immediately and rolls back the transaction. Previously, the operation continued after the safety error, causing TIA Portal to become exposed.
- **Error dialogs no longer cut off** — Message dialogs (e.g. Git fetch/pull errors) now resize to fit their content instead of using a fixed height. The OK button is always visible and clickable.

## v3.0.4 (2026-03-26)

### New Features
- **Multi-select in project tree and file tree** — Ctrl+Click toggles selection, Shift+Click selects a range. Works in both the left project tree and the right import/export file tree. Selected items can be exported, dragged, or deleted in bulk — no checkboxes required.

### Git — New Features
- **Auto-refresh local changes** — File changes are now detected automatically via FileSystemWatcher. No more manual refresh needed — changes appear within ~1 second, just like in SourceGit.
- **Auto-fetch from remotes** — Enable in Repository Settings with configurable interval (minutes). Fetches from the default remote automatically in the background.
- **Merge conflict resolution** — Use Theirs / Use Mine per conflicted file directly from the Working Copy context menu. Full 3-way merge editor for line-by-line conflict resolution with Ours/Theirs/Result panels.
- **In-progress operation handling** — Cherry-pick, Rebase, Revert, and Merge in-progress states are now detected and shown in the Working Copy. Continue, Skip, or Abort directly from the UI.
- **Reword HEAD** — Edit the most recent commit message without changing the code. Auto-stashes staged changes if needed.
- **Squash / Fixup HEAD** — Combine HEAD commit with a previous commit. Choose between squash (edit message) or fixup (discard message).
- **Drop HEAD** — Remove the most recent commit entirely. Working copy changes are auto-stashed and restored.
- **Stash detail view** — Selecting a stash now shows its changed files with diff preview. Search stashes by message. Clear all stashes with one click.
- **Add Remote dialog** — Dedicated dialog with name/URL validation, SSH key support, and automatic fetch after adding.
- **Edit Remote dialog** — Rename, change URL, and configure SSH key for existing remotes.
- **Submodule: De-initialize** — De-init submodules with optional force flag.
- **Submodule: Change URL** — Change the remote URL of a submodule with URL validation.
- **Submodule: Set Branch** — Set the tracking branch for a submodule.
- **Submodule: Move** — Move a submodule to a different directory path.
- **Reset branch without checkout** — Move a non-current branch pointer to a different commit without switching to it.
- **Edit branch description** — Add or edit a branch description note via git config.
- **Delete multiple tags** — Batch delete tags with optional push-delete to all remotes.
- **Push specific revision** — Push a specific commit SHA to a remote branch with optional force push.
- **Directory history** — View commit history filtered to a specific directory.
- **Revision file browser** — Browse all files of any commit as a tree with search, content viewer, and binary file detection.
- **Command palettes** — Quick keyboard-driven access to Checkout Branch, Merge Branch, Blame File, File History, and Open File operations with instant search filtering.
- **Commit message history** — Last 10 commit messages are saved and can be reused. Messages persist across sessions.
- **Commit template variables** — Templates now support `${branch_name}`, `${files}`, `${pure_files}`, slicing (`${files:3}`), and regex transforms.

### Git — Improvements
- **Amend loads previous message** — Toggling Amend now automatically loads the last commit message into the editor.
- **Settings are persisted** — Auto-fetch, interval, default remote, and other repository settings are saved to `.git/sourcegit.settings` and restored when reopening.
- **Sidebar state remembered** — Which sidebar sections (Branches, Remotes, Tags, Submodules, Worktrees) are expanded is saved per repository and restored on next open.
- **Last commit message preserved** — Your uncommitted commit message is saved when switching tabs and restored when you return.
- **Cherry-pick extended** — Now supports multi-commit cherry-pick, merge commit handling with parent selection, and "Append source to message" option.

### Bug Fixes
- **Connect dialog shows all running TIA Portal versions** — Previously only the highest version was shown when multiple TIA Portal versions were running simultaneously (e.g., V19 + V20). Now all instances are listed.
- **Improved error messages when connecting to TIA Portal** — The generic "Exception has been thrown by the target of an invocation" error is now unwrapped to show the actual Siemens error message, making connection issues easier to diagnose.
- **Tree scrolling fixed** — Scrolling in the project tree and file tree no longer conflicts with drag & drop.
- **Drag & drop works with filtered tree items** — Blocks found via tree search can now be dragged as expected; checkbox selections are preserved during filtering.
- **Log and Git Output now support text selection and copy** — Text in the Application Log and Git Output panels can be selected with the mouse and copied via Ctrl+C.
- **Drag & drop to Compare no longer blocks subsequent drags** — Previously, dragging a block to Compare caused it to stay selected, preventing other blocks from being dragged. Now dragging always uses the block under the cursor unless it is part of a checked group.
- **Folder checkboxes in file tree** — Folders now show checkboxes for selection. Checking or unchecking a folder cascades to all children, matching the project tree behavior.
- **Folder selection state consistent** — In both trees, unchecking a parent now correctly unchecks all children. Previously the file tree did not cascade deselection.

## v3.0.3 (2026-03-25)

### Git — New Features
- **Stash Changes dialog** - Full stash dialog with message, mode selection (Discard/Keep Index/Keep All), selective file stash, staged-only option
- **Apply Patch dialog** - Apply .patch/.diff files with whitespace handling options (No Warn, Warn, Error, Error All)
- **Archive dialog** - Create zip or tar.gz archives from any commit
- **Interactive Rebase dialog** - Reorder commits and assign actions (Pick, Reword, Edit, Squash, Fixup, Drop) with drag-and-drop
- **Conventional Commit builder** - Structured commit message helper with type, scope, breaking change, body, and footer fields
- **Add to .gitignore** - Right-click files to add ignore patterns (by file, extension, folder)
- **Assume Unchanged manager** - Mark/unmark files as assume-unchanged, list dialog to manage entries
- **Repository Settings dialog** - Per-repo configuration for user name, email, HTTP proxy, GPG signing, fetch prune
- **Worktree Remove/Prune** - Remove individual worktrees (with force option) and prune stale entries
- **Submodule management** - Add, Update (init/recursive), and Remove submodules with dedicated dialogs
- **GitFlow support** - Initialize GitFlow, Start/Finish Feature/Release/Hotfix branches with sidebar integration
- **LFS management** - Track patterns, Fetch, Pull, Push, Prune, and manage Locks via toolbar dropdown
- **Commit context menu icons** - All menu items now show SourceGit-style SVG icons
- **Copy submenu** - Commit context menu Copy with SHA-Subject, SHA, Subject, Message, Author, Committer
- **Git Working Copy context menus** - Right-click on staged/unstaged files for Stage, Discard, Stash, Save as Patch, Open in Editor, Reveal in Explorer, Copy Path
- **Discard Changes dialog** - Confirmation dialog with options to include untracked/ignored files and "can't undo" warning
- **Discard All button** - One-click discard of all local changes in the unstaged header
- **Commit History context menu** - Right-click on commits for Create Branch, Create Tag, Reset, Rebase, Merge, Cherry-Pick, Revert, Checkout, Save as Patch, Copy SHA
- **Checkout Commit dialog** - Double-click a commit to checkout with Stash & Reapply or Discard options and detached HEAD warning
- **Commit Detail tabs** - INFORMATION, CHANGES, and FILES tabs for inspecting commits
- **Information tab** - Author/Committer with avatar, SHA with copy button, clickable parent commits, Refs badges, full message, inline changed files list
- **Files tab** - Browse all files of a commit as tree with syntax-highlighted content viewer
- **Changes tab with diff** - Changed files list with search, embedded diff viewer that auto-scrolls to first change
- **Branch context menu extensions** - Pull, Push, Fast-Forward, and Create Tag actions directly from branch right-click
- **Branch tooltip** - Hover over branches to see tracking remote, ahead/behind status, and invalid upstream warnings
- **Tag context menu extensions** - Push Tag to remote and Create Branch from Tag
- **Commit detail file menu** - Open in Editor, Reveal in Explorer, Copy Path on changed files in commit detail view
- **Multi-branch commit graph** - All branches, remotes, and tags shown with colored merge lines
- **Commit decorator badges** - Icons for HEAD, Branch, Remote, and Tag with colored borders
- **Compare with HEAD / Worktree** - Right-click a commit to compare changes against HEAD or working tree
- **Operation dialogs** - Proper dialogs for Create/Delete/Rename Branch, Merge (mode selection), Rebase (auto-stash), Reset (Soft/Mixed/Hard), Cherry-Pick, Revert, Checkout Branch (stash/discard options), Fetch (remote/prune), Pull (rebase option), Push (force push), Create/Delete Tag

### Git — Improvements
- **ChangeCollectionView in Working Copy** - Unstaged/Staged file lists now use the rich ChangeCollectionView with tree/list/grid modes and search
- **CommitSubjectPresenter** - Rich commit subject rendering with highlighted conventional commit prefixes, issue links, and inline code
- **GitFlow branch detection** - Right-click GitFlow branches to finish them directly
- **Resizable history columns** - Drag column headers in commit history to resize (Graph, Author, SHA, Commit Time)
- **Full date+time in history** - Commit time column shows date and time instead of date only
- **Multi-selection in Working Copy** - Select multiple files for bulk Stage, Discard, or Stash operations
- **File search/filter** - Filter staged and unstaged file lists by filename
- **Keyboard shortcuts** - Enter/Space to stage/unstage, Delete to discard, Ctrl+C to copy path
- **Push error display** - Failed push operations now show error messages in the commit area
- **Stash context menu** - Copy stash message to clipboard
- **Navigate from Information to Changes** - Double-click a changed file in Information tab to jump to its diff

### AI Chat — New Features
- **Inline Diff Preview** - When AI modifies code via the editor, changes are shown as an inline diff (red/green highlighting) with Accept/Reject buttons instead of being applied directly. Keyboard shortcuts: Tab to accept, Escape to reject
- **Follow-up Suggestions** - AI responses now include 2-3 clickable follow-up suggestions as pill-shaped buttons below each response
- **Code Block Copy & Apply** - Each code block in AI responses gets individual Copy and Apply buttons (previously only one Apply button per message)
- **Inline Chat (Ctrl+I)** - Inline chat directly in the code editor. Select code, press Ctrl+I, type a question or request — AI responds and proposes changes inline
- **Embedded Diff Viewer in Chat** - When AI suggests code that differs from the current editor content, an inline diff view is shown in the chat message
- **Implicit Context Chip** - When a block is opened in the editor, it automatically appears as a context chip above the chat input. Click to add/remove it from AI context
- **Question Carousel** - AI can present multi-step questionnaires with text input, single-select, and multi-select questions for guided interactions
- **Context shortcuts** - Type `@` in chat input to open the attachment menu, `#editor` to share the current editor with AI

### AI Chat — Improvements
- **Rotating Thinking Indicator** - Thinking display now cycles through "Thinking...", "Analyzing...", "Reasoning..." with animated pulse dots
- **Streaming Progress** - Live elapsed time counter and prominent Stop button during AI response generation
- **Per-code-block language labels** - When AI response contains multiple code blocks, each shows its language tag

---

## v3.0.2 (2026-03-22)

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
