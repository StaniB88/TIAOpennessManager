# TIA Openness Manager - User Manual

**Version:** 4.0
**Date:** May 2026

---

## 0. Welcome Tab

### What is the Welcome Tab?

The Welcome tab is the first thing you see when you start TIA Openness Manager. It gives you a single place to start a new session, learn the app's core concepts, and jump back into a recent project. The tab is non-modal — you can leave it open alongside your work, or close it and open it again later from the Help menu.

### When it opens

- **On first launch** the Welcome tab opens automatically.
- **On every launch** after that, it keeps opening until you uncheck *"Show welcome page on startup"* at the bottom of the page.
- **Anytime** you can reopen it from **Help → Welcome Guide**. Reopening it this way does not turn the startup setting back on.

### Quick Start actions

The left column offers eight shortcuts for the most common first steps:

- **Connect to TIA Portal…** — attach to a running TIA Portal instance.
- **New TIA Project…** — open the New Project Wizard to create a TIA project with CPU, optional modules, network and initial blocks. Pick the TIA Portal version inside the wizard — no prior connection required. See [User Manual → New Project Wizard](#4-project-management).
- **Open TIA Project…** — pick a `.ap1x` / `.ap2x` project file from disk.
- **Browse Export Folder…** — choose the folder where exported blocks are written.
- **Clone Git Repository…** — clone a repository directly into the app.
- **New SCL File…** — open a blank SCL editor tab.
- **Unit Testing…** — open the Unit Testing workspace.
- **Configure AI Assistant…** — open the AI Chat settings so you can add an API key or sign in.

### Get Started walkthrough

The centre of the tab has an interactive **Get Started** card with four steps. The steps check themselves off as you use the app:

1. **Connect to TIA Portal** — checks itself off when you successfully connect.
2. **Learn the Project Explorer** — explains per-row checkboxes, *Export Selected* vs. *Export All*, the Protection column, Protection Profiles bound to Import/Export folders, and drag-and-drop import. An inline button opens the Protection-Profile save dialog; the step completes as soon as you save a profile (either from this button or from your normal Project Explorer workflow).
3. **Export your first block** — completes when any block export succeeds.
4. **Choose your next step** — four buttons (Git, AI Chat, Unit Testing, OPC UA) open the corresponding tab and complete this step.

A progress bar at the top of the card shows how many steps are done. A **Reset walkthrough progress** link at the bottom of the card clears all four checkmarks if you want to run through them again.

### Feature cards

Five cards on the right describe the app's main areas. Click a card to jump to that feature:

- **AI Chat** — opens the AI Chat workspace and the settings dialog.
- **Git Version Control** — opens the Git workspace.
- **Unit Testing** — opens the Unit Testing workspace.
- **OPC UA Browser** — opens the OPC UA workspace.
- **What's New in 3.x** — opens the bundled `CHANGELOG` with the latest user-visible changes.

### Recent projects

The **Recent** list shows up to five recently opened TIA projects, newest first. Click an entry to reconnect straight to it. Entries pointing to projects that have been moved or deleted are hidden automatically. The list updates after every successful connection, whether you opened a project file or attached to a running TIA Portal instance. If the list is empty, a single inline link offers to start a connection.

### Hiding the Welcome tab

Uncheck **Show welcome page on startup** at the bottom of the tab. The app will no longer auto-open the Welcome tab on launch. You can always bring it back from **Help → Welcome Guide**.

---

## 1. Introduction

### What is TIA Openness Manager?

TIA Openness Manager is a desktop application that uses the Siemens TIA Portal Openness API to export, import, and manage PLC program blocks. It provides a user-friendly alternative to manual export/import operations directly in TIA Portal.

### Main Use Cases

- **Version Control** - Export blocks as XML for Git/SVN
- **Project Migration** - Transfer blocks between projects
- **Backup** - Create regular backups of your program blocks
- **Code Review** - Compare changes with the Preview Diff function
- **Cleanup** - Find and remove unused blocks

---

## 2. Installation & System Requirements

### System Requirements

| Component | Requirement |
|-----------|-------------|
| Operating System | Windows 10/11 (64-bit) |
| TIA Portal | V15, V16, V17, V18, V19, V20, or V21 |
| TIA Portal Openness | Windows user must be in "Siemens TIA Openness" group |
| .NET | .NET 10 Runtime (bundled with installer) |
| RAM | Minimum 4 GB (8 GB recommended) |
| Disk Space | 500 MB |

### Installation

1. Download the TiaOpennessManager archive
2. Extract the archive to a folder of your choice (e.g., `C:/Tools/TiaOpennessManager`)
3. Run `TiaOpennessManager.V3.exe`

> **Note:** No separate installation is required. The application is portable and includes all necessary runtimes. TIA Portal must be installed on the system.

### TIA Portal Openness Setup

Your Windows user must be a member of the **"Siemens TIA Openness"** user group. Without this, TIA Portal will deny the connection.

1. Press `Win + R`, type `lusrmgr.msc`, press Enter
2. Click **Groups** on the left side
3. Double-click **"Siemens TIA Openness"**
4. Check if your user is listed. If not, click **Add**, type your username, click **Check Names** → **OK**
5. Click **Apply** → **OK**
6. **Log off and log back in** for the change to take effect

> **Windows 11 Home:** `lusrmgr.msc` is not available. Use an elevated command prompt instead:
> ```
> net localgroup "Siemens TIA Openness" %USERNAME% /add
> ```

### Launching the Application

Only one instance of TIA Openness Manager runs per Windows session. Opening a file or folder from Windows Explorer while the application is already running activates the existing window and opens the item there, instead of starting a second copy. Double-clicking the application icon or launching the executable a second time also just brings the running window to the front.

If another program has claimed the name the application uses internally, startup is refused with a warning. Close the other program (or sign out and back in) and try again.

### Signing in

The first time you launch the application a Sign-In dialog opens before the main window. Click **Sign in via browser** — your default browser opens `tiaopenessmanager.ch/sign-in`, where you enter your email address and the 6-digit verification code we mail you. Once the browser confirms, the dialog closes automatically and the application unlocks.

You stay signed in across application restarts; the next launch goes straight to the main window. The license is anchored to your account, not to a specific machine. You can sign in on up to three different machines per 30-day window.

To sign out, open **Settings → License**. The License panel shows the email address you signed in with, the active tier, and a **Sign out** button. Pressing it opens a confirmation dialog ("Sign out and release this machine?") so an accidental click does not release the binding — choose **Sign out** to confirm or **Cancel** to stay signed in. Signing out releases the current machine's binding so a teammate can pick it up. The application requires an active sign-in to be usable: immediately after signing out, the Sign-In dialog re-opens. Sign in again to continue working, or close the dialog to exit the application.

If sign-in fails repeatedly, check that your network can reach `tiaopenessmanager.ch`. Corporate firewalls that intercept TLS may need an exception (see "Cert pin bypass" in the troubleshooting section).

If the licensing server is unreachable when the application starts (no internet, VPN not connected, server outage), a dialog appears with three choices: **Retry** re-attempts the connection, **Continue offline** opens the application using the cached license and the 14-day grace period (some features may be unavailable until the next successful sign-in), and **Close application** exits. Continue offline never grants more rights than your last successful online check; subscription access is capped at 14 days, and you cannot start a new trial or activate a new license while offline.

---

## 3. User Interface

### Main Window Overview

The application is divided into several areas:

```
┌─────────────────────────────────────────────────────────────┐
│  Title Bar                              [_] [□] [X]         │
├─────────────────────────────────────────────────────────────┤
│  Menu: File | Project | View | Help                         │
├─────────────────────────────────────────────────────────────┤
│  Toolbar: [Archive] [Disconnect] [Rescan] [Save]    TIA:V20 │
├─────────────────────────────────────────────────────────────┤
│  Protection Profiles: [Name] [Save] | [Profiles ▼] [Apply]  │
├─────────────────────────────────────────────────────────────┤
│  Tree Controls: [F-Signature] [Safety Printout]              │
├─────────────┬───────────────────────────────────────────────┤
│             │  [Project] [Import/Export] [Compare]           │
│  Project    │  [Find Unused] [Find in Project] [Hardware]    │
│  Tree       │  [Vault]                                       │
│             ├───────────────────────────────────────────────┤
│  (Left)     │              Tab Content                      │
│             │                                               │
├─────────────┴───────────────────────────────────────────────┤
│  Bottom Panel: [Log Output] [Terminal] [Git Output] …       │
├─────────────────────────────────────────────────────────────┤
│  Status Bar: ● Connected | Status Message | License: ● Pro   │
└─────────────────────────────────────────────────────────────┘
```

### Left Panel - Project Tree

- Shows the structure of the opened TIA Portal project
- Hierarchy: Project → Hardware → Source → PLC → Blocks/Datatypes/Tags
- Checkboxes enable multiple selection for export

### Right Panel - Tabs

- **Project** - Code editor for selected blocks
- **Import/Export** - Main workspace for file operations
- **Compare** - Side-by-side block comparison viewer
- **Find Unused** - Dead code detection and cleanup
- **Find in Project** - Project-wide symbol and reference search
- **Hardware** - Device list with PROFINET names and IP configuration
- **Vault** - Encrypted credential storage

### Menu Bar

| Menu | Key Items |
|------|-----------|
| File | Connect, Browse Folder, Archive Project, Disconnect, Exit |
| Project | Rescan PLC, Save, Compile, Safety Login/Logoff |
| View | Settings, Terminal, Import/Export Settings, Protection Profiles Folder, Fullscreen, Keyboard Shortcuts |
| Help | Documentation, Release Notes, Report Issue, About |

### User Guide window

Open this manual from **Help → Documentation**. The User Guide window matches the rest of the app's theme, includes a sticky table of contents on the left, and supports:

- **Find** — click the Find button (or press Ctrl+F) to search the current page. Enter jumps to the next match; Shift+Enter to the previous; Esc closes the bar.
- **Zoom** — `−` / `+` step through 50–200% in 25% increments.
- **Language switch** — the dropdown swaps between English and German without leaving the page.
- **Code highlighting** — code blocks render with syntax highlighting tuned to the active theme.

### Toolbar

| Button | Function |
|--------|----------|
| Archive | Creates a compressed archive of the project |
| Disconnect | Disconnects from TIA Portal |
| Rescan | Rescans the PLC for changes |
| Save | Saves the TIA Portal project |
| Compile | Compiles the project |
| Safety Login | Logs in with Safety credentials |
| Safety Logoff | Logs off Safety credentials |

The TIA Portal version (e.g., V20) is displayed on the right side of the toolbar.

### Bottom Panel

The bottom panel contains:
- **Log Output** - Application log messages with color-coded severity
- **Terminal** - Integrated terminal for command-line operations
- **Git Output** - Output stream of Git operations
- **Problems** - Diagnostics aggregated across open editor files; every row shows the file name with line and column, and a click jumps the editor to that exact location
- **References** - Symbol references found by the language service

The panel can be collapsed, expanded, or maximized using the controls in the top-right corner. The side-by-side block comparison viewer (**Compare**) now lives in the workspace dock next to **Import/Export** — open it from the workspace View menu.

### Copying Values from Data Fields

Read-only data fields throughout the application can be selected with the mouse and copied with **Ctrl+C** like any text input. This includes CPU identity (MLFB, serial number, firmware), OPC UA diagnostics (server build, session counters, capabilities), license information (account email, hardware ID, expiry date), connection details (endpoint URL, IP address, security mode), MCP session IDs, and error or status messages. Static field labels are not selectable; values are.

### Copying Rows from Tables

Tables in the OPC UA panels (Node Attributes, References, Struct Fields, Diagnostics Buffer, Event Log, Server Diagnostics, Type Definitions, Watch Table, Endpoint List) support row-level copy: click a row to select it, hold **Shift** or **Ctrl** to select multiple rows where supported, and press **Ctrl+C** to copy the selected rows as tab-separated values including the column headers. Paste into a spreadsheet, text editor, ticket, or chat to share the data.

---

## 3a. Quick Open Bar

### What is the Quick Open Bar?

The Quick Open Bar is a search box in the application title bar. It is the fastest way to jump to anything in the app — a command, a PLC or HMI symbol, a file in the working directory, a Git branch, or a specific line in the open code editor — without leaving the keyboard or hunting through menus and trees.

### Opening the Quick Open Bar

- Press **Ctrl+Shift+P** anywhere in the application. The search box receives focus and is prefilled with **`>`** so the Commands list populates immediately.
- Click into the search box in the title bar. No prefix is preselected; type a prefix (or `?`) to choose a category.

The popup with results opens as soon as the search box has focus and stays open while you type. Press **Esc** to close it; click anywhere outside the popup also closes it.

### Discovery list (click into the bar)

When you click the search bar without using the keyboard shortcut, the popup opens with a **discovery list** that shows seven entries — one per category — each labelled with what it searches and which prefix triggers it:

- **Go to File** — no prefix, recent files and workspace files reachable from the working directory
- **Show and Run Commands** — prefix `>`
- **Go to Symbol in Active Tab** — prefix `@`
- **Go to Symbol in Workspace** — prefix `#`
- **Switch Git Branch** — prefix `git:`
- **Go to Line in Editor** — prefix `:`
- **More** — prefix `?` (opens the full help list)

Below the discovery list you also see your **recently opened files** so the result you reach for most often is one click away. Click any discovery row to fill the search box with its prefix and keep typing under that category, or press Enter on a recent file to open it directly.

### Prefixes

The first character of your search selects which category is searched. Type `?` and press Enter on a row to fill the prefix in for you, then keep typing.

| Prefix | Searches | Example |
|--------|----------|---------|
| `>` | **Commands** — any action exposed in the app menus, toolbars and global shortcuts | `>compile`, `>save` |
| `@` | **Symbols in the active context** — PLC symbols when on the TIA workspace, HMI items on the Screen Editor, test cases in Unit Testing, signals in Trace, OPC UA nodes when connected | `@motor`, `@start` |
| `#` | **Symbols across the whole workspace** — same sources as `@`, not filtered by the active tab | `#fb_motor` |
| `git:` | **Git branches** — local and remote in the open repository | `git:main`, `git:feature/x` |
| `?` | **Help** — lists all the prefixes above with a one-line description; pressing Enter prefills the search box with the chosen prefix and keeps the popup open for the next term | `?` |
| `:` | **Go to line** — jumps to the given line in the active code editor; only available when an editor tab has focus | `:42` |

Without a prefix the bar searches recently opened files and any other workspace files reachable from the currently configured working directory.

### Keyboard navigation

- **Up / Down arrows** — move the selection through the result list.
- **Enter** — execute the selected row.
- **Esc** — close the popup.
- **Mouse single-click** — executes a row immediately (the same as selecting it and pressing Enter).

Pressing Enter immediately runs the top match — the first result is preselected on every search update.

### What happens when you select a result

Each result type has its own action. Most actions also switch the active workspace if the target lives elsewhere.

| Result type | What happens on Enter / single-click |
|-------------|--------------------------------------|
| Command | Runs the command (e.g. opens a dialog, triggers an export). |
| Go-to-line | Jumps to the given line in the active code editor. |
| Help | Prefills the search box with the chosen prefix; popup stays open so you can keep typing. |
| PLC symbol | Switches to the TIA Manager workspace and selects the symbol in the project tree. |
| Screen symbol | Switches to the Screen Editor and selects the matching item. |
| Unit test symbol | Switches to Unit Testing and opens the test suite document. *Per-test-case selection inside the suite is coming in a later release.* |
| OPC UA node | Switches to the PLC Online workspace. *Selecting the matching node in the address-space tree is coming in a later release.* |
| Git branch | Checks out the branch (local non-current branches only). Remote branches and the currently checked-out branch use the existing checkout dialog. |
| Trace signal | Switches to the Trace workspace. *Selecting the matching signal in the list is coming in a later release.* |
| Recent file / cross-project file | Opens the file in a code editor tab. |

### Recently used results

The Quick Open Bar remembers your recent selections across application restarts so the things you reach for most are at the top of the list. The list keeps up to 50 entries and prunes anything older than 30 days automatically.

### Relationship to the Git workspace command palette

The Git workspace has its own **Ctrl+Shift+P** command palette (see [Git Client](#14a-git-client) → *Command Palette*) with 14 Git-specific actions. Both shortcuts coexist: the Git workspace palette is workspace-scoped and takes precedence when the Git tab has focus; the global Quick Open Bar lives in the title bar and is reachable from every other workspace.

---

## 3b. Keyboard Shortcuts

### Opening the shortcut overview

Press **Ctrl+K, Ctrl+S** anywhere in the application to open the **Keyboard Shortcuts** dialog. It lists every binding the app responds to, grouped by area:

- **Global** — application-wide bindings: project save, settings, terminal, workspace switching, find in project, the shortcut overview itself.
- **Editor** — bindings that act on the active code editor and its inline-edit overlay.
- **Git** — bindings used inside the Git workspace (tabs, branches, working copy, history, diff).
- **AI Chat** — quick-switch shortcuts inside the AI Chat panel.
- **Compare** — bindings inside the Compare workspace.

Each row shows the key combination and a short description; a search box at the top filters by either part. The same dialog is reachable from **View → Keyboard Shortcuts**.

### Frequently used shortcuts

| Shortcut | Action |
|----------|--------|
| **Ctrl+1 … Ctrl+8** | Switch workspace (TIA Manager, Version Control, PLC Online, Explorer, Screen Editor, Unit Testing, Trace, AI Agent) |
| **Ctrl+Alt+1 … Ctrl+Alt+9** | Quick-switch the active assistant inside the AI Chat panel |
| **Ctrl+S** | Save the active editor; in the Git diff view, stage the focused hunk; in Compare, save the focused side |
| **Ctrl+Shift+S** | Save the TIA Portal project |
| **Ctrl+K, Ctrl+S** | Open this Keyboard Shortcuts dialog |
| **Ctrl+R** (Git tab) | Refresh the active Git repository |
| **Ctrl+Ö** | Toggle the integrated terminal |
| **F1** | Open the user manual |
| **F5** | Rescan the TIA Portal project |
| **F11** | Toggle full-screen window |
| **Ctrl+Shift+F** | Find references in the current project |

If a key combination is shown for two different areas (for example **Ctrl+S** for *Save project* and *Stage hunk*), the binding that fires depends on which workspace and panel currently has the keyboard focus.

---

## 3c. Right-Click Context Menus

Every table, selectable text label, and tree view in the application responds to a right click with a context menu. The menus are localised in the application language (English / German / French / Italian).

### Shared defaults (work on any table, text label, or tree)

| Surface | Entries |
|---------|---------|
| Any table | Copy Cell · Copy Row · Copy All as CSV · Select All |
| Any selectable text label | Copy · Copy (Quoted) · Select All |
| Any tree view | Copy Name · Expand All · Collapse All |

- **Copy Cell** — copies the value of the cell under the pointer to the clipboard.
- **Copy Row** — copies all columns of the selected row as tab-separated text.
- **Copy All as CSV** — copies every visible row including the header row in RFC-4180 CSV format. Truncated to 10 000 rows for very large grids; the log records the truncation.
- **Copy (Quoted)** — wraps the selected text (or full label) in double quotes; useful for pasting an email or path into a sentence.

### Feature-specific entries

In addition to the shared defaults, several surfaces expose actions that fit their content:

- **OPC UA — References table** (PLC Online → References dock): Copy NodeId · Copy BrowseName · Copy as JSON · Subscribe (adds the referenced node to the watch list).
- **Compare — file lists** (left and right panes): Copy Full Path · Copy Filename · Open Folder (Windows Explorer / Finder reveal) · Remove from comparison.
- **Project Tree** (TIA Manager): Copy Name · Copy Number directly after Open in Editor / Find References on the existing menu.
- **Git Blame** — the SHA badge offers Copy SHA (short, first 8 characters) and Copy SHA (full); the subject offers Copy.
- **Git Commit detail** — the SHA offers the same short/full pair; the author block offers Copy Name · Copy Email · Copy "Name &lt;Email&gt;".

Right-click in code editors (the SCL editor, diff view, blame body, and Git command output) keeps the editor's own cut/copy/paste menu — the new menus do not override it. Text boxes (input fields) keep the operating-system native cut/copy/paste flyout.

---

## 3d. File Explorer

The Explorer workspace (Ctrl+4) is the file tree on the left side. It opens any folder on disk, shows files and subfolders, and lets you create, rename, delete, move and search items — and when the folder is a Git working copy, it shows the same status decorations you would see in a Git client or in VS Code.

### Open a folder

- Click the folder icon in the toolbar (right side) or the "Open Folder" button in the empty state.
- The Explorer remembers nothing else about the folder — it walks the file system each time and refreshes automatically when files change on disk.

### Toolbar

| Icon | Action |
|------|--------|
| ➕📄 | New file in the selected folder (or in the root if nothing is selected) |
| ➕📁 | New folder in the selected folder (or in the root) |
| ↻ | Refresh the tree |
| ⌃ | Collapse all folders |
| 👁 | Show / hide Git-ignored files |
| 📄 | Open a single file in the editor without changing the open folder |
| 📁 | Open a different folder |

### File and folder icons

Each row gets an icon that matches the file extension or the folder name:

- Code files (`.cs`, `.scl`, `.xml`, `.axaml`, `.json`, `.html`, `.js`, `.ts`, `.py`, …) and well-known config files (`.csproj`, `.sln`, `.yaml`, `.toml`, `.ini`) get distinct icons.
- Media (`.png`, `.jpg`, `.svg`, `.mp4`, `.wav`), archives (`.zip`, `.tar`, `.7z`), scripts (`.exe`, `.dll`, `.bat`, `.ps1`, `.sh`) and Git config files (`.gitignore`, `.gitattributes`, `.gitmodules`) each have their own glyph.
- Folders with names like `src`, `lib`, `docs`, `tests`, `node_modules`, `.git`, `.vscode`, `scripts`, `assets`, `.worktrees` also pick up matching icons.

### Git status

When the open folder is inside a Git repository, the Explorer displays the working-tree status for every visible file and folder:

- **Glyph badge** on the right edge of the row shows the change type with a colored 14×14 icon: `±` modified, `+` added, `−` deleted, `➜` renamed, `❏` copied, `★` untracked, `!` conflicted, `T` type-changed. The badge tooltip names the state in your UI language.
- **Folder bubble-up:** a folder inherits the *worst* status of any file inside it and shows the same badge at reduced opacity, so a single modified file deep inside a tree is visible from the root.
- **File names** stay in the regular text color so the status is carried by the badge alone.
- **Ignored files** (matched by `.gitignore`) appear in a muted colour. Use the 👁 toolbar toggle to hide them entirely — the choice is remembered between sessions.
- The Explorer watches `.git/index` and `.git/HEAD` and refreshes the decorations automatically when you stage, commit, switch branch or run any other Git operation outside of TIA Openness Manager.

### Solution panel

When the opened folder contains a `.sln` file, a **Solution** panel appears below the file tree and lists each C# project in the solution:

- **Frameworks** — every target framework the project compiles for (multi-targets are split out).
- **Packages** — every NuGet `<PackageReference>` with its declared version.
- **Analyzers** — packages contributing analyzers / source generators, detected from explicit `<Analyzer>` items, `PrivateAssets="all"` plus a name suffix like `.Analyzers`, or a curated whitelist (StyleCop, .NET Analyzers, Roslynator, xUnit Analyzers, …). Transitive analyzers pulled in by SDKs are not listed; the empty-state explicitly notes this is a best-effort detection.
- **Projects** — every `<ProjectReference>` resolved to its project name.

A refresh button in the panel toolbar re-parses everything on demand; the panel also re-parses automatically whenever a `.sln` or `.csproj` changes on disk (debounced to 500 ms). If the opened folder has no `.sln`, the panel is hidden entirely and the file tree gets the full panel height; the panel reappears as soon as a `.sln` is detected. Double-click the solution row or any project row to open the matching `.sln` / `.csproj` file in the editor.

### Language-aware file icons

Files in both the Explorer tree and the Solution panel draw the actual brand glyph of their language — the C# logo for `.cs` / `.csproj` / `.sln`, the TypeScript logo for `.ts` / `.tsx`, the JavaScript / Python / Rust / Go / Java / Kotlin / Swift / C / C++ / Ruby / PHP / Lua / R logos for the matching extensions, the HTML5 / CSS3 / Sass marks for web sources, JSON / YAML / XML / Markdown badges for data and docs, the shell / Bash / PowerShell prompts for scripts, the Docker whale for `Dockerfile` and `.dockerignore`, and the Git logo for `.gitignore` / `.gitattributes` / `.gitmodules`. Each glyph is tinted in its language's brand color (C# purple, TS blue, JS yellow, Python blue, Rust orange, Go cyan, SCL/AWL/STL Siemens orange, …). Files without a registered language fall back to the generic file glyph in the neutral secondary text color; ignored files stay dimmed regardless of their language.

### Multi-select

- **Click** selects one row.
- **Ctrl+Click** toggles selection of one more row.
- **Shift+Click** selects a continuous range.
- Selected rows participate together in Delete and Drag operations.

### Open a file

- **Double-click** a file in the tree to open it in the editor.
- Folder rows expand or collapse on double-click instead.

### Create new file or folder

- Click the ➕📄 or ➕📁 button, or right-click and choose **New File** / **New Folder**.
- A small dialog asks for the name. The new item is created in the currently selected folder (or in the root if nothing is selected) and opens immediately in the editor if it is a file.

### Rename

- Select a row and press **F2**, or right-click and choose **Rename**.
- The name turns into an inline text box. For files with an extension the cursor pre-selects only the base name, so typing immediately overwrites it without disturbing the extension.
- Press **Enter** to commit the new name, **Escape** to cancel, or click somewhere else to commit.
- Empty names, names containing invalid path characters, and names that would collide with an existing sibling are rejected silently.

### Delete

- Select one or more rows and press **Delete**, or right-click and choose **Delete**.
- A confirmation dialog appears with the number of items and the total entry count inside (e.g. "Delete 3 items (47 entries)?"), so a recursive delete never surprises you with an unexpected blast radius.
- Confirming sends the files and folders to the Windows Recycle Bin (on Windows) so a wrong delete can be restored. Symlinks and junctions are deleted as the link itself, never as the link target.
- The tree refreshes automatically after the operation.

### Move via drag and drop

- Press and hold on a row, then drag it onto a folder *in the same tree* to move it there.
- The drop highlight only activates when the target is a folder, not the source itself, and not inside the source's own subtree, so a folder cannot be accidentally dragged into its own children.
- Multiple selected rows move together; the destination file or folder must not already exist.

### Drag out to another window

- Dragging from the Explorer out to the chat input area attaches the selected files to the next message.
- Dragging out to the Windows Explorer creates copies in the target folder.

### Search and filter

- Press **Ctrl+F** with the Explorer focused to slide the search bar in above the tree; the box receives focus and its text is pre-selected.
- Press **Esc** in the search box, or click the **X** button, to close the bar and clear the query.
- The match runs against the file or folder name, case-insensitively, anywhere in the name. Folders stay visible whenever any descendant matches, and matching descendants are auto-expanded so the hits land in view.
- Clearing the field restores the full tree.
- The `.gitignore` filter and the search filter combine: when "Show Git-ignored files" is off, ignored files are excluded from search results too.

### Right-click context menu

| Entry | Action |
|-------|--------|
| New File | Create a file in this folder |
| New Folder | Create a subfolder |
| Rename | Start inline rename (same as F2) |
| Delete | Remove the file or folder (with confirmation) |
| Reveal in File Explorer | Open the parent folder in Windows Explorer with the file selected |
| Copy Path | Copy the absolute path to the clipboard |
| Copy Relative Path | Copy the path relative to the open folder root |

---

## 3e. Workspace Layout

The workspace shows tools (Project Explorer, File Explorer) and documents (Editor, Import/Export, Find Unused, Find in Project, Hardware, Vault) in a flexible dock arrangement. You can rearrange every panel and persist the result to a file you can re-load later or share with a colleague.

### Rearranging panels

- **Drag a tab header** to dock the panel to a new edge of the workspace, to split an existing region, or to combine it with another panel as a tab group.
- **Drag a tab header outside the main window** to float it as an independent window. The floating window stays in sync with the project and can be redocked by dragging its title bar back into a docking guide.
- **Drag the splitter between two regions** to change their proportions.
- **Click the pin icon** on a tool tab to collapse it into a side strip; click again to restore the full panel.
- **Close a tab** with the close button or middle-click. Closed documents and tools are hidden, not destroyed — re-open them from the **View** dropdown in the workspace toolbar (top-right of the workspace area).

### View dropdown

The **View** dropdown (top-right of the workspace toolbar) toggles individual panels. Selecting an entry shows a hidden panel or hides a visible one:

| Group | Items |
|-------|-------|
| Tools | Project Explorer, File Explorer |
| Documents | Editor, Import / Export, Find Unused, Find in Project, Hardware, Vault |

### Workspace dropdown

The **Workspace** dropdown (next to **View**) groups three actions that operate on the entire dock arrangement of the main workspace:

| Item | Action |
|------|--------|
| Save Workspace As… | Saves the current dock layout (panel positions, splitter proportions, tab order, floating windows) to a `.tiamgr-workspace` file. The file is a small JSON document that you can copy between machines or commit to source control as part of a team setup. |
| Load Workspace… | Opens a `.tiamgr-workspace` file and applies it to the current main window. Open documents are reused; their visual placement matches the file. |
| Reset Workspace | Restores the factory-default dock arrangement. A confirmation dialog asks before the layout changes. Open documents and tools remain available — only their position is reset. |

The Workspace dropdown acts on the layout only. Project content (files, blocks, settings) is never affected by Save, Load, or Reset.

### What is and is not saved

Saved to the `.tiamgr-workspace` file:

- Position and orientation of every tool and document panel
- Width / height proportions between regions
- Tab grouping and active tab in each region
- Whether a tool is pinned, floated, or docked
- Active document and active tool at the time of saving

Not saved:

- Document contents (those live in your TIA Portal project and source files)
- Editor scroll position or selection inside a document
- The contents of the AI Chat sidebar
- Connection state, license, or settings

---

## 4. Project Management

### New Project Wizard

The New Project Wizard creates a complete TIA Portal project — with CPU, optional modules, network and initial program blocks — without leaving TIA Openness Manager.

**Open the wizard:**

- From the **Welcome** tab, click **New TIA Project…** in the Quick-Start column.
- The wizard opens directly. You do not need to be connected to TIA Portal beforehand — pick the version on Step 1 and the matching TIA Portal instance is started for you when you leave Step 1 by clicking **Next**. The wizard shows a "Starting TIA Portal V…" overlay while the instance comes up; the catalog search on Step 2 works as soon as the overlay disappears.

**Step 1 — Project info:**

1. Pick the **TIA Portal version** (V15…V21) — pre-filled with the currently connected version when applicable.
2. Enter a **Project name** (up to 60 characters; the usual filesystem characters `\\ / : * ? " < > |` are not allowed).
3. Click **Browse…** to choose a **Target directory** (must be an absolute path on a local drive — UNC paths are rejected).
4. Optionally enter an **Author** and a **Comment**.

If you are already connected to a different TIA Portal version when you click **Next**, the wizard asks for confirmation before disconnecting the current session and starting the version you picked.

**Step 2 — CPU:**

1. Type a search term in the **Hardware catalog** field (for example `1516` or `S7-1500`).
2. Pick the CPU you want from the result list. F-CPUs are listed but cannot be selected — Safety configuration is not supported by the wizard and must be done manually in TIA Portal.
3. Enter a **Device name** (defaults to `PLC_1`).

**Step 3 — Modules (optional):**

Add I/O modules, communication processors or other rack-pluggable items:

1. Click **Add module**, search the catalog and pick the module.
2. Enter a **Slot** number.
3. Repeat for additional modules. Names within the list must be unique.
4. If you go back to Step 2 and change the CPU, the modules list is cleared because the previously chosen modules may no longer fit the new rack.

**Step 4 — Network (optional):**

Configure a single Ethernet subnet:

1. Enter a **Subnet name** (for example `PN/IE_1`).
2. Enter the **Interface path** of the CPU's PROFINET interface inside the device tree (for example `Rack_0/PROFINET interface_1`).
3. Enter the **IPv4 address** in four numeric fields (each 0–255).

PROFIBUS, MPI and AS-i subnets are not supported by the wizard.

**Step 5 — Initial blocks (optional):**

Pre-create empty program blocks:

1. Click **Add block**.
2. Pick a **Kind** (FB, FC, OB or Global DB).
3. Enter a **Name** and optionally a **Number** (leave the number empty for auto-numbering).
4. Pick a **Programming language** (SCL, LAD, FBD, STL, GRAPH or ProDiag).
5. Repeat for additional blocks. F-block names (`F_*`, `Failsafe_*`, `Safety_*`, `F-…`) are rejected.

**Step 6 — Review and create:**

1. Review the summary (project name, target directory, CPU, modules, network, blocks).
2. Click **Create project**.
3. Progress is shown at the bottom of the wizard. The wizard runs the entire creation as one atomic operation in TIA Portal — if any step fails, the whole project is rolled back.
4. After success the wizard closes and the new project is opened automatically in the application.

> **Note:** F-CPU + Safety configuration, multiple CPUs in one project, and PROFIBUS/MPI/AS-i networks are not supported by the wizard. Use TIA Portal directly for these scenarios.

### Connect to TIA Portal

Click **Connect** from the File menu to open the Connect Dialog.

The Connect Dialog has two tabs:

#### Tab 1: Attach to Running Instance

1. Open your project in TIA Portal first
2. Click **Connect** to open the Connect Dialog
3. Switch to the **Attach to Running** tab
4. Click **Refresh List** to find running TIA Portal instances
5. Select the desired instance
6. Click **Connect**

**Advantages of Attach Mode:**
- Faster connection (no project loading)
- You can work in TIA Portal simultaneously
- Changes are immediately visible

#### Tab 2: Open Project File

1. Click **Connect** to open the Connect Dialog
2. Switch to the **Open Project** tab
3. Click **Browse** to navigate to the project file (`.ap15` through `.ap21`)
4. Select the file - connection starts automatically

This starts TIA Portal in the background (headless mode) without a visible user interface. This is faster for pure export/import operations.

**Recent Projects:** The dialog remembers your recently opened projects (up to ten, newest first) for quick access. Entries pointing to projects that have been moved or deleted are hidden automatically.

**Note:** For large bulk operations (25+ files), the application automatically uses ExclusiveAccess for better stability.

### Archive Project

Creates a compressed archive (.zap file) of the current project:

1. Click **Archive Project** in the toolbar
2. Select a destination folder
3. The project is archived with all associated files

**Note:** The project must be saved before archiving.

### Safety Printout

Generates a safety documentation printout for F-blocks:

1. Ensure you are logged in with Safety credentials (click **Safety Login** first)
2. Click **Safety Printout** in the Tree Controls area
3. Select a destination folder
4. A PDF is generated with all safety-relevant documentation

**Note:** This feature requires an active Safety login and is only available for projects with F-blocks.

### Disconnect

Click **Disconnect** in the toolbar or select **File → Disconnect** to close the connection. In Headless Mode, TIA Portal will be terminated.

---

## 5. Import/Export Tab

The Import/Export Tab is the heart of the application.

### Layout

```
┌──────────────────┬──────────────────┬───────────────────────┐
│   TIA Project    │    Actions       │   Working Directory   │
│   (Left)         │    (Center)      │   (Right)             │
├──────────────────┼──────────────────┼───────────────────────┤
│ □ Blocks         │ Export Selected→ │ [Refresh] [Path: ...] │
│   □ Main [OB1]   │ Export All →     │ □ Main.xml            │
│   □ Motor [FB1]  │                  │ □ Motor.xml           │
│   □ Calc [FC1]   │ ← Import Selected│ □ Calc.xml            │
│ □ Datatypes      │ ← Import All     │                       │
│ □ Tags           │                  │                       │
└──────────────────┴──────────────────┴───────────────────────┘
```

### Right Directory (Export/Import Directory)

The Right Directory is the folder on your file system where exported XML files are stored and from which files are imported.

**Setting:**
1. Click **...** next to the "Right directory" field
2. Select a folder
3. The folder is saved with the Profile and loaded on each start

**Tip:** Use a Git repository folder for automatic version control.

When the chosen folder is inside a Git repository, the Right Directory tree decorates each row with the same Git status badges and dimming as the Explorer workspace:

- Coloured status glyph (M, +, −, ➜, ❏, ★, ! or T) next to the file name (Modified, Added, Deleted, Renamed, Copied, Untracked, Conflicted, Type-changed). Hover for a tooltip with the change type.
- Folders show a dimmed version of the worst status of any file inside them, so you can spot uncommitted work without expanding the tree.
- `.gitignore`-matched files stay visible but are rendered in muted grey.
- Badges refresh automatically after commits, checkouts, merges, and rebases — no manual reload needed.

> **Note:** The "Working Directory" in Settings refers to the "Find Unused Blocks" function and is a separate folder.

### File Tree Search (Right)

The search field above the right file tree filters the file list as you type. The same syntax as the [Project Tree Search](#project-tree-search) is supported:

- Substring (`motor`), fuzzy (`fbmtr`), multiple terms (all must match), quoted phrase (`"my block"`), exclusion (`!safety`).
- Matching characters in each visible result are highlighted in bold accent color.
- Filtering is debounced (250 ms) so very long lists stay responsive while you type.
- Clearing the search field restores your manually expanded folders exactly as they were before you started typing.

### Right-click on Folders and Files (Right Tree)

Right-clicking any node in the right file tree opens a context menu with **Open in Editor**, **Import**, and **Delete**:

- **Open in Editor** loads the selected file into the Editor workspace (disabled for folders).
- **Import** runs the same import as the *Import Selected* sidebar button against the checked rows.
- **Delete** removes the selected file *or folder* from disk. Selecting **Delete** on a folder removes the folder recursively (all files and subfolders inside it). A confirmation prompt appears first.

Files whose names start with a dot (for example the delta-import fingerprint cache that *Preview Diff* maintains alongside your exports) are now shown in the tree so you can see and manage them. Files that the operating system has marked as Hidden or System are still excluded.

### Export Operations

#### Export Selected
1. Check the boxes next to the desired blocks in the left tree
2. Click **Export Selected**
3. The selected items are exported as XML. Existing files with the same name are overwritten; all other files in the export folder are kept.

#### Export All
1. Click **Export All**
2. The PLC export folder is cleared first, then ALL blocks, data types, tag tables, technology objects, and software units are exported — a full project export

### Import Operations

#### Import Selected
1. Check the boxes next to the desired XML files in the right tree
2. Click **Import Selected**
3. The selected files are imported. Existing blocks with the same name are overwritten; all other PLC content is left untouched.

#### Import All
1. Click **Import All**
2. The entire PLC program is cleared first (all blocks, data types, and tag tables are deleted), then ALL XML files in the Working Directory are imported — a full project re-import

**Important:** Import All replaces the complete PLC content with what is in the Working Directory. Blocks marked in the Protection Profile are preserved.

### Import/Export Options

The toolbar above the right tree provides options to customize import and export behavior:

**Import Options:**

| Option | Description |
|--------|-------------|
| Ignore Structural Changes | Ignores structure modifications when importing |
| Ignore Missing References | Continues import even if referenced objects are missing |

**Export Options:**

| Option | Description |
|--------|-------------|
| Export With Defaults | Includes default values in the exported XML |
| Export With Read Only | Marks exported blocks as read-only |
| Export Protected Files | When unchecked, items marked as protected are excluded from export. Folder structure is always preserved. |

These options help resolve common import issues and customize export behavior for version control.

**S7DCL Export Options (TIA Portal V20+ only):**

The S7DCL (SIMATIC 7 Declaration Language) export feature provides additional text-based exports alongside the standard XML and source code files.

| Option | Description | Export Result |
|--------|-------------|---------------|
| SCL + S7DCL | Additionally export SCL blocks as S7DCL format | `.xml` + `.scl` + `.s7dcl` |
| AWL + S7DCL | Additionally export AWL/STL blocks as S7DCL format | `.xml` + `.awl` + `.s7dcl` |
| LAD/FBD + S7DCL | Additionally export LAD/FBD/GRAPH blocks as S7DCL format | `.xml` + `.s7dcl` |

**Why use S7DCL export?**
- **Better readability:** Text-based format ideal for code review
- **Version control:** Perfect for diff comparison in Git/SVN
- **Multi-format:** Keep both standard formats AND S7DCL for maximum compatibility
- **Graphical languages:** Enables text export for LAD/FBD blocks (normally only XML)

**Important Notes:**
- S7DCL files (`.s7dcl`) are **export-only** - they **cannot be re-imported** into TIA Portal
- The checkboxes enable **additional** exports, not replacements - you always get the standard formats
- For LAD/FBD blocks, S7DCL provides a text representation that would otherwise not exist
- S7DCL export requires TIA Portal V20 or higher

**Access S7DCL Settings:**
Select **View → Import/Export Settings** from the menu bar.

### Preview Diff

The Preview Diff function shows differences between the TIA Portal project and the Working Directory:

1. Click **Preview Diff**
2. The PLC is compiled first so any unsaved edits are included, then the application compares TIA Portal fingerprints and file hashes against the cached state from the last export
3. The Compare panel opens with a summary header (`X changed · Y added · Z protected · N unchanged`) and one row per differing block:
   - **Changed** - Block content in TIA or source file differs
   - **New in TIA** - Block only exists in the project
   - **Deleted** - Block only exists in the Working Directory
4. Tick the checkbox next to each block you want to push back into the PLC (Changed and Added rows are pre-selected, Protected blocks are disabled)
5. Click **Import** to re-import the selected files

Preview Diff detects both XML-side changes (block interface edits in TIA) and source-file changes (SCL, AWL, DB edits on disk). Re-imports run in a single transaction — if any block fails, all changes are rolled back so the project stays in its original state. Unticked rows and protected blocks are left untouched.

**First-time use:** Preview Diff works on a fresh working directory even if you have never run Export All. On the first click the application silently builds a baseline by temporarily exporting the PLC, comparing the temporary files against what is already on disk, and then saving the baseline (`.fingerprint-cache.json`) so subsequent runs use the fast path. The first run takes longer than follow-up runs.

**Left and right file lists:** The Compare panel shows a file list on the left for the TIA side and a matching file list on the right for the disk side. Both lists, the diff toolbar, and the side panes are visible from the moment you open the Compare tab — even before you load anything — so you can see where everything will appear. When the panel is empty, a subtle drop-files watermark sits in the diff area; it disappears as soon as content is loaded. Modified blocks appear in both lists; blocks that only exist in TIA (or that still need compiling) show only on the left, blocks that only exist on disk show only on the right. Each list has its own show/hide toggle in the Compare toolbar, so you can focus on either side or keep both visible.

**Multiple formats per block:** When a block is present in more than one representation on disk (for example an SCL block stored as both `Block_2.scl` and `Block_2.xml`), each format gets its own row in the file list. Click the row of the extension you want to see — the diff loads immediately. There is no separate SCL/XML toggle; the extension of the clicked row decides which representation the editor renders.

**Change strip at the row edge:** Every row in both file lists carries a thin colored bar at its right edge that tells you the change type without reading the label: green for added, red for deleted, orange for modified, yellow for inconsistent (needs compiling), and blue for blocks that only exist on one side (left or right). Unchanged rows show no bar.

### Section-by-section merge

When two files differ, arrow buttons (`←` / `→`) appear in the middle column between the editors — one pair per change-section. Click `→` to copy the left section into the right buffer, or `←` for the opposite direction. Changes are applied to the in-memory buffer; click **Save** to persist them. For TIA-side buffers (left side in Sync mode against a temp-export), saves are skipped — re-import the block to apply the change back to TIA.

### Identical files

When both sides have identical content, both editors show the file with no `+`/`-` markers and no merge arrows. Identity is visually clear from the absence of change markers; no separate banner is shown.

### Ad-hoc Compare (Drag and Drop)

For quick side-by-side checks without scanning the whole project, drag items directly into the Compare panel. Both sides accept drops independently — whichever half you drop onto is the half the item lands in:

1. Drag one or more blocks from the TIA project tree and drop them onto the left or right half of the Compare panel. Dropped items appear in the matching file list (left or right).
2. The PLC is compiled, the blocks are exported with your current Import/Export Settings (the same strip rules that apply to a normal "Export Selected"), and each exported file becomes its own row in the corresponding file list — an SCL block produces both a `.xml` and a `.scl` row, an InstanceDB produces `.xml` and `.db`.
3. Click the row for the format you want to see.
4. You can mix sources on either side: drag a TIA block to one side and a Windows file onto the other, or drop two files directly for a file-to-file compare without a TIA export.
5. The diff viewer shows differences line by line.

**Notes:**

- The TIA side is compiled and stripped the same way a regular export would be, so the comparison is apples-to-apples against a file that was exported earlier to your working directory.
- Additional drops on the same side append to the existing list instead of replacing it — one block in TIA can be checked against several candidate files without re-exporting, and the other side keeps whatever is already loaded.
- Hover over a row in either file list to reveal an `X` button at the right end; click it to remove just that file without affecting the rest of the comparison.
- The file list splitters are resizable between 180 and 500 pixels and remember the widths you picked.

For project-wide comparison with selective re-import back into the PLC, use **Preview Diff** instead (hash-based, produces Modified / Only in TIA / Only on Disk categories and a Sync-Mode Import button).

### Diff Editor Toolbar

The diff editor has a built-in toolbar with the following controls:

- **Change navigation** — First / Previous / Next / Last change buttons plus a `1/N` counter jump through all hunks in the current file.
- **Context lines** — The `+=` and `-=` buttons increase or decrease how many unchanged lines are shown around each change (default 3, minimum 1). The stretches between hunks are folded behind a `@@ -a,b +c,d @@` header.
- **Show entire file** — Expand every line of the file, no context folding.
- **Syntax highlighting** — Toggle on/off (SCL, AWL, DB, XML, and other languages are recognised by extension).
- **Word wrap** — Wrap long lines in unified view.
- **Ignore whitespace** — Treat whitespace-only differences as unchanged.
- **Hidden symbols** — Reveal spaces, tabs, and line-ending markers.
- **Side-by-side / Unified** — Switch layout.

On the left of that toolbar you'll find the TIA-specific actions:

- **Edit** — Unlock both sides for direct editing. When enabled the view switches to side-by-side and expands the entire file so the edits aren't broken up by the context-lines fold. Typed changes are tracked per side.
- **Save Left / Save Right** — Write the edited side back to its source (file on disk or block in TIA).
- **Discard** — Drop unsaved edits.
- **Merge All →** / **Swap** / **Merge All ←** — Overwrite one side with the other, or flip which side is "original".
- **Clear** — Close the current comparison.

### HMI Export/Import

For projects with HMI devices (WinCC Unified, Comfort Panels, etc.):

**Export HMI Selected:**
1. Select HMI elements in the left tree (under the HMI device node)
2. Click **Export HMI Selected**
3. Selected screens, templates, tags, scripts are exported

**Export HMI All:**
1. Click **Export HMI All**
2. All HMI elements from all HMI devices are exported

**Supported HMI Elements:**
- Screens and Popups
- Screen Templates
- HMI Tag Tables
- VB Scripts
- Connections
- Text Lists
- Graphic Lists

#### WinCC Unified Screen Export/Import

WinCC Unified screens are exported as JSON files (not XML like Classic HMI). The export includes all screen items with their properties, positions, colors, fonts, texts, compositions (e.g., ListBox entries), dynamizations, and events.

- **Export Selected:** Select screens in the HMI tree, click Export HMI Selected
- **Export All:** Click Export HMI All — automatically exports all screens preserving the folder structure (e.g., `Screens/Device PopUp/DCM.json`)
- **Import:** Select JSON files in the file tree, click Import HMI Selected. Existing screens with the same name are deleted and recreated.

> **Note:** For WinCC Unified screens, all elements will be placed in **Layer 0** after import. The Siemens TIA Portal Openness API does not support reading or writing layer assignments. Positions and all other properties are preserved correctly.

### Hardware Export

Export the device configuration as an AutomationML (.aml) file:

1. Switch the category in the Import / Export tab to **Hardware**.
2. Click **AML Export →** in the right column. The file is written into the configured export folder.
3. Use **← AML Import** in the same column to bring an `.aml` file back into the project.

**Note:** AML export covers the full hardware configuration of the selected PLC. The resulting `.aml` file can be re-imported or kept for documentation.

---

## 6. Project Tab

### Code Display

When you select a block in the project tree, its source code is displayed in the code editor.

**Supported Languages:**
- SCL (Structured Control Language)
- STL (Statement List)
- LAD/FBD/GRAPH (rendered inline as networks)

### Graphical block view

LAD, FBD and GRAPH blocks open in the **Graphical** tab next to the Code tab. Networks render directly in the manager — no external Compare or Visualizer tool is required, and no separate Siemens utility needs to be installed. Each network shows its title, comment and the LAD/FBD layout exactly as it appears in TIA Portal. Data blocks, UDTs and tag tables likewise display their structure inline.

The view is read-only; edits are made through the Code tab or the inline chat. Switch back to the Code tab at any time to see or modify the SCL/STL source.

### Interface Tab

When a Data Block (DB), Function Block (FB), Function (FC), User Data Type (UDT), or PLC tag table is loaded, an **Interface** tab appears next to the **Code** tab. It renders the block's interface in the same tabular layout TIA Portal uses, with one row per member and the columns:

- **Name** — member name; nested struct or UDT members appear indented under their parent and can be collapsed via the chevron in front of the name.
- **Data type** — the SIMATIC type as TIA exports it (e.g. `Bool`, `Int`, `Array[0..9] of "myUdt"`).
- **Start value** — the initial value if defined, otherwise empty.
- **Retain** — `Non-retain`, `Retain`, or `Set in DB`.
- **Accessible from HMI / Writable from HMI / Visible in HMI** — the three external-access flags. On data blocks, function blocks, functions and PLC tag tables, toggling **Accessible from HMI** carries **Writable** and **Visible** along (switching it off clears both, switching it back on restores both); on user data types the three flags stay independent. **Writable** and **Visible** can always be flipped individually without affecting the other two.
- **Setpoint** — editable checkbox marking the member as a setpoint.
- **Supervision** — read-only text showing the linked ProDiag supervision reference (empty when none is assigned).
- **Comment** — the comment in the current UI language; if it is missing, the English (`en-US`) text is used; otherwise the first available language.

For PLC tag tables the same tab shows two tables stacked vertically: the **Tags** list (Name · Data type · Logical address · Retain · HMI flags · Supervision · Comment) on top and the **User constants** list at the bottom. The **Supervision** column is read-only and shows the linked ProDiag supervision reference, matching the same column on block interfaces. Array-typed and UDT-typed tags expand inline: each array element appears as its own row with the computed address, and each UDT member appears underneath the tag down to the primitive level. When no TIA Portal connection is active the UDT definitions cannot be fetched; a yellow banner above the Tags list explains that opening the project in TIA Portal will reveal the full hierarchy.

An **Edit / Discard / Save / Save As / Upload to TIA** toolbar above the Tags list offers the same workflow as block interfaces: rename tags, change data types or logical addresses, toggle Retain and the HMI flags, and edit comments inline. **Save** writes the modified tag-table XML to the configured Working Directory (`{Working Directory}/{PLC}/{Tags folder}/{TableName}.xml`); **Save As…** lets you choose any path; **Upload to TIA** stays available when a TIA Portal connection is active and re-imports the edited tag table into the project.

#### Editing the Interface offline (file drop or File Explorer)

Both **drag-and-drop onto the editor / Welcome tab** and **File Explorer right-click → Open in Editor** open files with the Interface tab populated. Two file shapes are supported:

- **Source files** — `.scl`, `.stl`, `.udt`, `.db`. The parser reads the declaration sections (`VAR_INPUT` / `VAR_OUTPUT` / `VAR_IN_OUT` / `VAR_TEMP` / `VAR` / `VAR_STAT` / `STRUCT` / DB members) directly from the file. No TIA Portal connection is required.
- **SimaticML XML** — `.xml` exports from TIA Portal. The block type is detected from the root element: `<SW.Blocks.FB>` / `<SW.Blocks.FC>` / `<SW.Blocks.OB>` / `<SW.Blocks.GlobalDB>` / `<SW.Blocks.InstanceDB>` / `<SW.Blocks.ArrayDB>` / `<SW.Types>` open into the block-interface editor; `<SW.Tags.PlcTagTable>` opens directly into the Tags table editor with the Edit / Discard / Save / Save As / Upload toolbar enabled.

**Save** writes back to the dropped or opened file path; **Save As…** writes to a chosen path; **Upload to TIA** stays disabled until a TIA Portal connection is active.

In edit mode you can:

- Rename a member.
- Change a member's data type (using the SCL syntax TIA Portal exports, including arrays and UDT references).
- Edit a start value.
- Edit the comment in the current UI language.
- Add a new member, remove a member, or reorder members via the drag handle to the left of each row.

**Save (Ctrl+S** or the **Save** button**)** writes the changes atomically back to the original source file. The header attributes, decorations (`VERSION`, `NON_RETAIN`, `READ_ONLY`, `KNOW_HOW_PROTECT`, `AUTHOR`, `FAMILY`, `NAME`), body code and untouched declaration sections are preserved byte-for-byte; only the sections you actually edited are re-emitted. Line endings (CRLF or LF) are preserved per file.

If the source file is read-only on disk, the Save command automatically switches to **Save As…** with a localized info banner explaining the fallback. **Save As…** lets you write the contents to a new path; subsequent saves target that new path.

**Upload to TIA** stays available as a separate action and is only visible when a TIA Portal connection is active. Save and Save As work regardless of connection state.

#### Editing the Interface online (TIA-connected)

When a block is opened from the project tree of a connected TIA Portal project, the Interface tab supports the same set of edits as the offline path (rename, change data type, edit start value, edit comment, add, remove and reorder members). Uploading the edits back to TIA Portal goes through three guards:

- **Cross-reference impact preview** — before the upload starts, renames, removals and data-type changes are checked across the project for call sites that the edit would break. A confirmation dialog reports the affected count, a sample of up to ten callers, and a cap indicator if the search was capped. Clicking **Cancel** aborts the upload; clicking **Proceed** requires acknowledging the change and continues.
- **Automatic compile after upload** — once the edits land, the PLC is compiled automatically. Any compile messages are listed in an expandable **Compile diagnostics** panel above the table with a severity glyph (× / ⚠ / ⓘ) and the failing block name. Clicking a row jumps to that block in the project tree and opens it in the editor for fixing.
- **Edit-mode gate** — if TIA Portal reports the block as know-how-protected, read-only, or the capability probe could not determine its state, the **Enter edit mode** toggle is disabled and the tooltip explains why. The same gate applies before any upload attempt — read-only or protected blocks cannot be modified through the Interface tab regardless of the project's online state.

Editing a Safety (F-) block still surfaces a separate warning that must be acknowledged before the upload proceeds. Re-validation of the Safety program after an interface edit is a manual step in TIA Portal — TIA Openness does not expose a "validate Safety program now" call, so the manager cannot automate it.

Closing a tab whose Interface has unsaved changes prompts to **Save**, **Discard** or **Cancel** — the same dialog used for unsaved code edits. Save writes the file; Discard closes without writing; Cancel keeps the tab open.

### Saving and closing

- **Ctrl+S** saves the file or block currently shown in the editor. For files this writes to disk. For TIA Portal blocks Ctrl+S asks for confirmation ("Upload to TIA Portal?") before sending changes back to the project; clicking the *Upload to TIA* toolbar button asks the same question.
- **Ctrl+Shift+S** saves the entire TIA Portal project (the previous Ctrl+S behavior).
- Closing a tab or the application with unsaved changes shows a confirmation dialog. The dialog lets you save all, discard all, or cancel.
- Disconnecting from TIA Portal closes any editor tabs that were opened from TIA. If those tabs have unsaved changes you are prompted to save (upload), discard, or cancel the disconnect.

### Drag & Drop from the Project Explorer

You can drag any block (FB, FC, OB, DB, UDT, Tag Table) from the TIA tree directly onto the editor or the Welcome tab, or drag source files from the offline folder. Each dropped item opens as its own editor tab; the editor loads the content exactly as it would on double-click. Items that can't be resolved or opened are reported in the status bar.

### Block Details Panel

Metadata is displayed next to the code:
- **Block Type:** OB, FB, FC, DB
- **Number:** e.g., OB1, FB10
- **Language:** Reflects the actual programming language reported by TIA Portal (`SCL`, `STL`, `LAD`, `FBD`, `GRAPH`, `F_LAD`, …). For files dropped from the file explorer, the label shows the file's language (`C#`, `Python`, `Markdown`, `TypeScript`, …) — unknown extensions show `Text`.
- **Author:** If available
- **Last Modified:** Timestamp

### Inline Chat (Ctrl+I)

The Inline Chat lets you ask the AI questions or request code changes directly in the code editor — without switching to the AI Chat sidebar.

**How to use:**

1. Open the **Project** tab with a block selected (or an empty editor)
2. Optionally select the code you want to modify or ask about
3. Press **Ctrl+I** — a small chat input appears at the top of the editor
4. Type your question or instruction (e.g., "add error handling", "what does this section do?")
5. Press **Enter** to send

**Handling AI responses:**

- The AI streams its response directly in the inline chat widget
- If the AI proposes a code change, **Accept/Reject** buttons appear:
  - Press **Tab** or click **Accept** to apply the change
  - Press **Escape** or click **Reject** to discard it
- Press **Escape** at any time to close the inline chat

> **Tip:** The inline chat works even without a block loaded — useful for asking general SCL questions.

### Project Tree Search

Use the search field above the project tree to quickly find blocks:
- **Substring match** — `motor` finds `FB_Motor`, `MotorController`, `drive_motor`.
- **Fuzzy match** — `fbmtr` finds `FB_Motor` by matching the characters in order.
- **Multiple terms** — separate terms with a space. All terms must match. `motor plc1` finds only items whose name contains both `motor` and `plc1`. Order of terms does not matter.
- **Quoted phrase** — wrap a phrase in double quotes to match it verbatim, including spaces: `"my block"` matches the literal substring `my block`.
- **Exclusion** — prefix a term with `!` to exclude matches that contain it: `motor !safety` finds items whose name matches `motor` but does **not** contain `safety`.
- **Scope filter** — use `kind:VALUE` to restrict matches to a node kind. Known values: `fb`, `fc`, `db`, `ob` (include safety variants), `udt`, `tag`, `plc`, `block` (any block kind), `safety` (only safety blocks), `folder`, `screen`. Example: `kind:fb motor` lists only function blocks whose name matches `motor`.
- **Ranking** — exact matches rank first, then prefix matches, then matches at word boundaries (`FB_Motor` ranks above `CalibrateMotor`), then general substring matches, then fuzzy matches. Next / Previous Match jumps through the results in rank order.
- **Highlighting** — matching characters in each visible result are shown in bold accent color so you can see at a glance what the search matched.
- **Case-insensitive** — `MOTOR` and `motor` behave identically.

Clearing the search field restores the tree exactly as it was before you started typing, including any nodes you had manually expanded.

---

## 7. Protected Items Tab

### Concept

The protection system prevents important blocks from being accidentally overwritten.

### Protecting Blocks

1. Switch to the **Protected Items** tab
2. Navigate to the desired block
3. Check the box next to the block

Protected blocks will:
- Be skipped during import
- Be skipped during export (when "Export Protected Files" is unchecked in Import/Export Settings)
- Be marked with a green padlock badge in the project tree (red padlock = unprotected, click to toggle)
- Appear in the protection list

> **Tip:** Even when protected blocks are excluded from export, folder structure is always preserved.

### Profiles

Profiles save your protection configuration:

**Save Profile:**
1. Configure your protected blocks
2. Click **Save Profile**
3. Enter a name

**Load Profile:**
1. Click **Load Profile**
2. Select a saved profile

---

## 8. Password Vault Tab

### Overview

The Password Vault securely stores TIA Portal know-how protection passwords. It uses AES-256-GCM encryption with a master password to protect all entries. The vault enables bulk protect and unprotect operations on assigned blocks.

### Creating a Vault

1. Switch to the **Vault** tab
2. Click **New Vault**
3. Choose a location and file name (`.vault` extension)
4. Enter a master password

> **Important:** Remember your master password. It cannot be recovered.

### Opening an Existing Vault

1. Click **Open Vault**
2. Select a `.vault` file
3. Click **Unlock** and enter your master password

### Managing Entries

**Add Entry:**
1. Click **Add Entry**
2. Enter a name (e.g., "Production PLC Password")
3. Enter the know-how protection password

**Edit Entry:**
- Right-click an entry and select **Edit**, or select it and click **Edit**

**Remove Entry:**
- Right-click an entry and select **Remove**

### Assigning Passwords to Blocks

**Via Context Menu (single block):**
1. In the **Project Tree**, right-click a block or folder
2. Select **Assign Vault Password**
3. Choose a vault entry from the dropdown
4. The password is now linked to that block path

**Via Vault Toggle (bulk assignment):**
1. Enable the vault toggles (key icons appear next to each block in the tree)
2. Check the vault toggle for the blocks you want to assign
3. Select a vault entry when prompted
4. Checked blocks are assigned to that vault entry

### Bulk Protect/Unprotect

1. Assign vault passwords to blocks using the vault toggle checkboxes or context menu
2. Right-click and choose **Bulk Protect (Vault)** or **Bulk Unprotect (Vault)**
3. All blocks with assigned vault passwords are protected or unprotected in one operation

> **Note:** Protected blocks remain assigned to their vault entry even if you uncheck the vault toggle. To remove a protected block from the vault, you must unprotect it first.

### Protecting Safety (F-) Blocks

Before any Safety block (F_FB, F_FC, F_DB, F_OB) can be know-how-protected through the vault, the F-program in TIA Portal must be **fully built and consistent**. The Bulk Protect operation calls the same Siemens API that TIA Portal uses internally — and Siemens rejects that call for any F-block that is not currently referenced from a compiled F-runtime group.

**Required step before vault-protecting Safety blocks:**

1. In TIA Portal, right-click the F-CPU's program folder
2. Select **Software → Rebuild all** (also labelled **Software → Compile → Software (rebuild all)** depending on TIA Portal version and language)
3. Wait for the rebuild to finish without errors
4. Switch back to TIA Openness Manager and run **Bulk Protect (Vault)**

If you skip the rebuild and try to protect a freshly added or changed F-block, the vault surfaces a Safety-block error listing the four most common Siemens rejection reasons (block not used in the safety program, safety-offline-program login missing, block inconsistent, block open in the editor). The rebuild closes the inconsistency case for new or modified blocks.

> **Why "rebuild all" and not just "compile"?** A normal compile only touches changed blocks. Adding or modifying an F-block invalidates the Siemens-generated F-runtime-group glue blocks (`F_PLK`, `F_RTG_OB`, etc.) that chain F-OBs into the safety program. Until those glue blocks regenerate, the Openness API does not see the new F-block as "called" and Protect is refused. **Rebuild all** forces full regeneration of every glue block.

### Crash Recovery

If the application crashes while blocks are unprotected:
1. On next project open, a recovery dialog appears
2. It lists blocks that were left unprotected
3. Click **Yes** to re-protect them automatically

### Locking the Vault

- Click **Lock** to lock the vault (entries remain in memory but encrypted)
- Click **Close Vault** to completely unload the vault
- Click **Change Password** to change the master password

### Exporting the Vault to CSV

The CSV Export feature allows you to create a backup of all vault entries in a text format:

**Exporting:**
1. Open and unlock your vault
2. Click **Export CSV** in the toolbar
3. Select a destination folder for the backup file
4. A CSV file is created with all vault entries

**CSV Format:**
- Metadata header with vault information (app version, vault file path, export date, entry count)
- Column headers: Name, Password, Paths, ProtectedPaths
- UTF-8 encoding with BOM (for Excel compatibility)
- RFC 4180 compliant CSV formatting

**Security Note:**
The CSV file contains passwords in plaintext for backup purposes. Store the exported CSV file securely, just like you would protect the vault file itself. Delete the CSV after verifying the backup is complete.

**When Export is Available:**
- Export CSV button is only active when the vault is unlocked
- Lock the vault when you're done to prevent accidental exports

---

## 9. MCP Server (AI Integration)

### What is MCP?

The Model Context Protocol (MCP) lets external AI assistants — Claude Desktop, Claude Code, Gemini CLI, Cursor, LM Studio, Continue.dev — access your TIA Portal project through TIA Openness Manager.

### How it works

There is no MCP tab inside the application. The MCP server runs as a background subprocess that the AI client launches on demand by spawning `TiaOpennessManager.V3.exe` with the `--mcp-stdio` argument. As long as TIA Openness Manager is open and connected to a TIA Portal project, the subprocess transparently relays each tool call to the running instance, so all 47 MCP tools (project queries, code reading, exports, comparisons, AI-aware analyses, OPC UA, Canvas, Git, PowerShell, Trace, etc.) operate against the project you currently have open.

### Setup with an AI assistant

1. Open and connect TIA Openness Manager to your TIA Portal project as usual.
2. In your AI client's MCP server settings, register a new server with command `TiaOpennessManager.V3.exe` and argument `--mcp-stdio`. The exact configuration block depends on the client (each vendor publishes its own MCP server format) — see the snippets below.
3. Start a chat with the AI assistant. It can now query project structure, read block code, perform analyses, drive OPC UA reads/writes, and run any other tool the active license tier allows.

### Capabilities

| Capability | Methods | What it gives the AI client |
|------------|---------|-----------------------------|
| Tools | `tools/list`, `tools/call` | 47 tools — TIA project & PLC operations (project queries, project creation, code reading, exports, compares, hardware device management, network/subnet, tag tables, screen tools, OPC UA, Canvas, Trace, Unit Testing, Git) plus general-purpose helpers: `fs` (filesystem read/write/search), `web_fetch` (outbound HTTP), `web_search`. All gated per call by license tier and the permission filter |
| Resources | `resources/list`, `resources/read`, `notifications/resources/list_changed` | A live `tia://project` resource and 4 URI templates; clients receive a list-changed notification when the project changes (per-URI subscribe is deliberately not advertised) |
| Sampling | `sampling/createMessage` | The TIA Portal-aware tool `tia_ai_analyze` asks the AI client to run a model — the client controls the model and its credentials |
| Prompts | `prompts/list`, `prompts/get` | 4 ready-made prompts: `analyze-block`, `generate-unit-tests`, `compare-blocks`, `review-safety-function` |
| Logging | `logging/setLevel`, `notifications/message` | The AI client can ask the server to forward its own log stream at a chosen verbosity |

### Configuration examples

Replace `C:\Program Files\TIA Openness Manager\TiaOpennessManager.V3.exe` with your actual install path. The path must point at a write-protected location — the default install directory under `Program Files` requires admin to modify, which is what you want. Pointing the AI client at a user-writable directory turns the MCP server entry into a code-execution sink for any process running as your user.

**Claude Desktop** (`%APPDATA%\Claude\claude_desktop_config.json`):

```json
{
  "mcpServers": {
    "tia-openness-manager": {
      "command": "C:\\Program Files\\TIA Openness Manager\\TiaOpennessManager.V3.exe",
      "args": ["--mcp-stdio"]
    }
  }
}
```

**Claude Code** — register the server with the CLI:

```
claude mcp add tia-openness-manager "C:\Program Files\TIA Openness Manager\TiaOpennessManager.V3.exe" -- --mcp-stdio
```

Claude Code stores MCP server entries in its root settings file (`~/.claude.json` under the `mcpServers` key); use the CLI rather than editing the file directly.

**LM Studio** — Settings → MCP Servers → Add Server:

- Name: `tia-openness-manager`
- Command: `C:\Program Files\TIA Openness Manager\TiaOpennessManager.V3.exe`
- Arguments: `--mcp-stdio`

**Gemini CLI** (`~/.gemini/config.json`), **Cursor** (Settings → MCP Servers), and **Continue.dev** (`~/.continue/config.json` under `experimental.modelContextProtocolServer`) all accept the same shape — `command` plus `args: ["--mcp-stdio"]`.

### License gating

MCP tool calls require a license tier that includes MCP server access (Trial, Professional, or Enterprise). The Basic tier does not include MCP — calls from the AI client are rejected per-call by the SDK with a tier-not-licensed error. The check runs at the SDK filter chain on every tool invocation; there is no app-level toggle.

### Diagnostics

Subprocess logs land in `%LocalAppData%/TiaOpennessManager/Logs/mcp-subprocess.log` (daily rotation, 3-file retention). Use it to troubleshoot connection issues or unexpected rejections.

### Session indicator

The status bar at the bottom of the main window shows `MCP: <n>` whenever an AI client is connected via the proxy path. The plug icon turns active-color when at least one client is online. Click the indicator to open a dialog that lists each connected session (client name, version, connect time, session id) and includes a Setup Guide with copy-ready configuration snippets for Claude Desktop, Claude Code, LM Studio, and Continue.dev. The Desktop App tab also has an Open Folder button that takes you straight to `%APPDATA%\Claude` so you can drop the snippet into `claude_desktop_config.json`.

---

## 9a. AI Chat

The built-in AI Chat panel provides a conversational interface to an AI assistant that is aware of your project and environment. Configure it via **View → AI Chat Settings**.

### Chat Providers

Choose a provider per agent in the provider dropdown. Each one uses its own API key, which you paste into the Settings dialog once.

| Provider | How to get an API key |
|----------|-----------------------|
| xAI (Grok) | <https://console.x.ai/> |
| Groq | <https://console.groq.com/keys> |
| Cerebras | <https://cloud.cerebras.ai/> |
| DeepSeek | <https://platform.deepseek.com/api_keys> |
| Perplexity | <https://www.perplexity.ai/settings/api> |
| Together AI | <https://api.together.ai/settings/api-keys> |
| Hugging Face | <https://huggingface.co/settings/tokens> |
| Z.AI | <https://z.ai/manage-apikey/apikey-list> |
| MiniMax | <https://www.minimax.io/platform/user-center/basic-information/interface-key> |
| Fireworks AI | <https://fireworks.ai/account/api-keys> |
| Moonshot AI | <https://platform.moonshot.ai/console/api-keys> |
| Vercel AI Gateway | <https://vercel.com/dashboard/ai-gateway/api-keys> |
| SGLang (self-hosted) | No API key required by default — point the endpoint at your SGLang server (e.g. `http://localhost:30000/v1`) |
| vLLM (self-hosted) | No API key required by default — point the endpoint at your vLLM server (e.g. `http://localhost:8000/v1`) |
| Qwen | <https://home.qwencloud.com/api-keys> |
| Alibaba Model Studio | <https://home.qwencloud.com/api-keys> |
| Baidu Qianfan | <https://qianfan.baidubce.com/> |
| Volcano Engine (Doubao) | <https://console.volcengine.com/ark> |
| BytePlus (Doubao Global) | <https://console.byteplus.com/ark> |
| Arcee AI | <https://app.arcee.ai/> |
| Kimi Coding | <https://platform.moonshot.cn/console/api-keys> |

**Cloudflare AI Gateway** works differently from the providers above: it is a proxy that routes chat requests through your own Cloudflare account. Select it in the provider dropdown, then enter your **Account ID**, **Gateway ID**, and pick a **Sub-Provider** (OpenAI, Anthropic, Groq, Mistral, Google, or Workers AI). Cloudflare caching, analytics, and rate limits apply in front of the chosen downstream LLM. Get started: <https://dash.cloudflare.com/?to=/:account/ai/ai-gateway>.

**Region option for Qwen, Z.AI, MiniMax, and Moonshot** — When you select one of these four providers, the settings panel shows an additional **Region** picker. Pick **Global** to route through the international endpoint or **China** to route through the mainland-China endpoint; Qwen and Z.AI also offer **Global (Coding Plan)** and **China (Coding Plan)** for the dedicated coding-subscription endpoints. Leave it on **Auto** to keep the provider's default.

Additional providers available out of the box: Anthropic, OpenAI, Google Gemini, Mistral, OpenRouter, GitHub Copilot, Azure OpenAI, Google Vertex, AWS Bedrock, Ollama (local), LM Studio (local), **Google Antigravity** (sign in with your Google account — same flow as Gemini CLI — to use Claude Opus/Sonnet, Gemini 3 Pro/Flash, and GPT-OSS 120B in the Antigravity sandbox).

### Context Folders

Register folders on your file system that the AI is allowed to browse. Once registered, the AI can use the `fs_read_file`, `fs_list_directory`, and `fs_search_files` tools to inspect those folders on your behalf.

**Setup:**
1. Open **View → AI Chat Settings**
2. Navigate to the **Context Folders** section
3. Click **Add Folder** and select a directory (e.g., your export working directory or a Git repository)
4. The AI will be able to read and search files within that folder during chat sessions

### Instruction Files

Instruction files are Markdown (`.md`) files whose content is automatically injected into the AI's system prompt at the start of every conversation. Use them to give the AI standing instructions, project conventions, or context it should always be aware of.

**Setup:**
1. Open **View → AI Chat Settings**
2. Navigate to the **Instruction Files** section
3. Click **Add File** and select a `.md` file
4. The file content is prepended to the AI's system prompt for every new chat session

### Git Integration

The AI Chat is git-aware. When a git repository is detected in any of your configured context folders (or the current working directory), the AI can:

- View the current branch and repository status
- View staged and unstaged changes
- Stage files
- Create commits (using the active commit template if configured)
- Push and pull changes

**Mutating operations** (stage, commit, push, pull) require explicit user approval before they are executed.

### Commit Templates

Define commit message templates that the AI follows when generating commit messages. The active template is used whenever the AI creates a commit.

**Setup:**
1. Open **View → AI Chat Settings**
2. Navigate to the **Commit Templates** section
3. Click **Add Template**, give it a name, and write the template text
4. Select a template as active using the radio button next to it
5. The AI will adhere to this format for all commits made during the chat session

**Example template:**
```
<type>: <short description>

<optional body>
```

### Skills

Skills are Markdown files that appear as commands in the chat input's `/` command palette. They let you define reusable prompts or instructions you can invoke by name.

**Location:** `%LocalAppData%\TiaOpennessManager\skills\`

#### Built-in Skills

Default skills are included and automatically deployed on first launch:

| Skill | Description |
|-------|-------------|
| Explore Project | Analyzes the connected TIA Portal project and generates a context file |
| Explain Block | Reads a block's source code and explains its logic |
| Generate SCL | Generates SCL code following Siemens programming standards |
| Compare Blocks | Compares block versions between project and export folder |
| Optimize SCL | Suggests refactorings to make a block faster or easier to read |
| Safety Check | Inspects a block (or selection) for safety-relevant patterns |
| Export Blocks | Walks the export workflow with the user, including selection and folder handling |
| Document Block | Generates a block-level documentation file |
| Document Project | Generates project-wide documentation |
| Describe Block | Produces a short, plain-language summary of a block |
| Describe Project | Produces a short, plain-language project summary |
| Git Commit | Drafts a commit message from the current diff using the active commit template |
| Convert AWL → SCL | Converts an AWL block to SCL following the Siemens conversion rules |
| Review SCL | Reviews SCL against the Siemens style guide and reports findings |
| Write Unit Tests | Generates a Unit-Testing suite skeleton for the selected block |

Built-in skills can be edited. To restore them to their original content, click **Open Skills Folder**, delete the modified files, and use the **Reload** button (↻) — the defaults will be re-deployed automatically.

#### Creating Custom Skills

To create a new skill, place a `.md` file in the skills folder. The simplest skill is just a plain text file:

```markdown
Please analyze the current PLC program and suggest improvements.
```

For more control, add YAML frontmatter at the top to set a name, description, and icon:

```markdown
---
name: Export Summary
description: Summarize the last export operation
icon: 📊
---

Please summarize the blocks that were exported in the last operation, including counts by type.
```

All frontmatter fields are optional. If no `name` is specified, the filename is used. If no `icon` is specified, a default icon (📄) is shown.

After adding or editing skill files, click the **Reload** button (↻) in the Skills palette header to refresh the list.

**Frontmatter fields:**

| Field | Required | Description |
|-------|----------|-------------|
| `name` | No | Display name (defaults to filename if omitted) |
| `description` | No | Short description shown in the command palette |
| `icon` | No | Emoji icon displayed next to the skill name (defaults to 📄) |
| `action` | No | Comma-separated action IDs for automated behavior (see below) |
| `save-path` | No | File path where the AI response is saved (used with `save-response` action) |

#### Variable Substitution

Skill content supports variables that are replaced at runtime with project information:

| Variable | Replaced With |
|----------|---------------|
| `{ProjectName}` | Name of the connected TIA Portal project |
| `{ProjectDir}` | Directory path of the TIA Portal project |
| `{PlcName}` | Name of the first PLC in the project |
| `{TiaVersion}` | Connected TIA Portal version (e.g., "V20") |
| `{Date}` | Current date in `yyyy-MM-dd` format |
| `{ContextDir}` | Path to the context files directory |

#### Action Skills

Skills can include an `action` field in the frontmatter to trigger automated behavior when executed:

| Action | Behavior |
|--------|----------|
| `auto-send` | Automatically sends the prompt without requiring the user to press Enter |
| `save-response` | Saves the AI response to the file specified by `save-path` |
| `explore-project` | Combines auto-send + save-response, and saves the response as the project's AI context file (requires a connected TIA Portal project) |

Multiple actions can be combined with commas: `action: auto-send, save-response`

**Example action skill:**
```markdown
---
name: Document Project
description: Generate and save project documentation
action: auto-send, save-response
save-path: {ProjectDir}\ProjectDocumentation.md
---

Generate complete documentation for the TIA Portal project {ProjectName}.
```

#### Usage

1. In the chat input, type `/`
2. The command palette lists all available skills (built-in and custom)
3. Select a skill to insert its content as the prompt
4. For action skills with `auto-send`, the prompt is sent automatically

### Agent Configs

Agents define a persona for the AI, including a custom system prompt and a specific set of allowed tools. Switch agents to change the AI's behavior for different tasks.

**Location:** `%LocalAppData%\TiaOpennessManager\agents\`

**Format:** Each `.json` file defines one agent. The following built-in agents ship with the application and are deployed on first launch:

| Agent | Purpose |
|-------|---------|
| Standard Agent | All-purpose chat with full tool access |
| Git Assistant | Focused on git operations; file tools restricted |
| SCL Expert | Specialized for writing and reviewing SCL/PLC code |
| TIA Analyzer | Read-only analysis of the connected TIA project (no write tools) |
| TIA Modifier | Project-modifying agent (export, import, edit) with explicit write permissions |
| Canvas Creator | Builds and edits the AI Canvas (A2UI) layouts |
| File Worker | Filesystem-focused agent (read/write/search across registered context folders) |
| AWL Converter | Drives the AWL → SCL conversion workflow with the user |
| Unit Test Author | Generates Unit-Testing suites and test cases for the selected blocks |

**Switching agents:**
Use the agent dropdown in the AI Chat header to select the active agent. The change takes effect for the next message sent.

**Creating a custom agent:**
Place a `.json` file in `%LocalAppData%\TiaOpennessManager\agents\` with the following structure:

```json
{
  "name": "My Custom Agent",
  "description": "A short description shown in the dropdown",
  "systemPrompt": "You are an expert in ...",
  "allowedTools": ["fs_read_file", "fs_list_directory", "git_status"]
}
```

**Responses API for reasoning models (Azure):** If your Azure deployment hosts a reasoning model such as `o1`, `o3`, or `gpt-5`, enable the "Use Responses API (for reasoning models)" toggle in the agent's Azure section. This switches the request flow to Azure's Responses endpoint, which is required for `reasoning_effort` to take effect. Standard (non-reasoning) deployments should leave this off.

**Additional Azure deployments per agent:** A single Azure OpenAI agent can serve multiple deployments. In the agent's Azure section, the **Additional deployments** list holds one row per extra deployment name; click **Add deployment** to append a new row, type the deployment name, or click the × button on a row to remove it. Each registered deployment surfaces as its own row in Manage Language Models; pick any of them as the active deployment via **Use in active agent**. The primary deployment above is always included in the list.

**Knowledge & References (Settings → AI Chat → Agents → Edit):** Every agent has a Knowledge & References section under its Name / Description / System Prompt block. It controls what reference material the AI sees when the agent runs.

- **Eager-load instruction files** (toggle) — When on, the files listed under **Instruction files (eager)** are concatenated into every dispatch of this agent. When off, the agent reads the **Available references (lazy)** list as a short index and loads the full text on demand via a tool call (typically saves 30 + seconds per dispatch).
- **Instruction files (eager)** — A list of paths or `builtin:<name>.md` entries that the agent loads up front. **Add instruction file** opens a file picker; **Insert built-in…** offers the five shipped references (Siemens styleguide, AWL → SCL, SCL language, Canvas, Unit testing).
- **Migrate to lazy** (button, shown only when the instruction-files list is non-empty) — Opens a confirmation dialog. Confirming moves every listed instruction file into the **Available references** list with a pre-filled name and description, then turns the eager-load toggle off. A status line under the button reports how many references were added and how many were skipped as duplicates so you can see at a glance whether the existing list absorbed everything. You can switch back to eager mode any time by re-enabling the toggle; nothing is lost.
- **Available references (lazy)** — One row per reference. Each row has a name (used as the lookup key), a source path, and a free-form description (shown to the AI as a hint of when to load the reference). Buttons per row: move up / down, **Browse…** to pick a Markdown file, **Insert built-in…** to seed a known reference, and × to remove. The validation banner warns about duplicate names and about rows that have only a name or only a source — those rows are dropped on save.
- **Source paths** — Use `builtin:<name>.md` for the built-in catalog. For custom files, pick any Markdown file under `%LocalAppData%\TiaOpennessManager\instructions\` or `%LocalAppData%\TiaOpennessManager\references\` (other directories are rejected as a safety measure). Files are capped at 1 MiB per reference.

Changes save automatically with a short debounce, take effect on the next dispatch, and survive application updates: built-in agents continue to receive new system-prompt and capability updates, but your customised reference list is preserved across version bumps.

**Reasoning effort (Low / Medium / High):** For agents whose model supports deep thinking, pick how hard the model should think before replying. Set it per agent in **Settings → Agents → Capabilities → Reasoning Effort**, or switch it on the fly via the brain chip next to the tool-call button in the composer bar. Higher levels produce better reasoning at the cost of latency and tokens. Selecting **Use app default** clears the per-agent override so the agent follows the global default configured elsewhere.

**Provider settings tab (Settings → Providers):** A cross-agent overview of the AI providers the app can talk to. The GitHub Copilot card shows sign-in status, every enterprise domain used by a Copilot agent, the reasoning-model policy state, and buttons to retry the policy enablement or verify the Copilot model catalog without leaving Settings. Placeholder cards for Anthropic, OpenAI, Google Gemini, Azure OpenAI, AWS Bedrock, Ollama, and OpenRouter link through to the Manage Language Models browser. Copilot sign-in and enterprise domain still live on each Copilot agent in the Agents tab — the Providers tab is a read-only console for those values.

**Manage Language Models window:** Click the gear icon next to the assistant selector in the composer bar to open a cross-provider catalog of every model the app knows about. The window combines three kinds of rows: GitHub Copilot's live server-discovered list (fetched directly from the Copilot `/models` endpoint when the window first opens or Refresh is pressed — no offline fallback, so Copilot rows appear once the discovery call returns); the OAuth catalogs shipped for OpenAI Codex, Google Gemini CLI, and Antigravity; and — new — a **live-fetched** list of models for every agent you have configured with an API key. The app asks each vendor's `/models` endpoint directly, so Anthropic, OpenAI, OpenRouter, Mistral, XAI, Groq, Cerebras, DeepSeek, Perplexity, Together, HuggingFace, Z.AI, MiniMax, Fireworks, Moonshot, Vercel AI Gateway, SGLang, vLLM, Qwen, Alibaba Model Studio, Arcee, Cloudflare AI Gateway, Ollama, LM Studio, and Custom OpenAI-compatible endpoints surface whatever their vendor is offering right now. AWS Bedrock rows remain static because AWS has no public model-discovery endpoint. Search by model name or ID and filter by provider. The **Source** column distinguishes the three kinds. The status bar shows a live count (e.g. *120 of 240 models · 75 live*) when at least one visible row was fetched live. The **Capabilities** column shows per-model Tool, Vision, and Reasoning badges; the **Request Multiplier** column shows the Copilot premium-request cost for Copilot models (`0x`, `0.33x`, `1x`, `3x`, `7.5x`, …). The **Policy** column is Copilot-specific: it shows *Enabled* for models your account has successfully turned on, *Failed* for models the last enablement attempt rejected (hover the badge to read the exact error), or *Admin-managed* when your Copilot plan lets the tenant administrator control model availability. When a row shows *Failed*, right-click it and choose **Retry Copilot model policy** to kick off a fresh enablement pass against your Copilot tenant. Right-click a row or press **Use in active agent** to switch the active agent's model in one step (enabled only when the row's provider matches the agent's provider). The **Refresh** button invalidates the 5-minute model-list cache and re-queries every endpoint — use it after adding a new API key or after a vendor announces a new model.

**Numeric parameters (Request Timeout, Max Retries, Context Window Override, Temperature, Top-P, Session Memory Count):** Type the value directly. Press **Enter** to apply, **Escape** to revert, or click away to apply automatically. Values outside the allowed range are clamped to the nearest bound. Leaving **Max Retries**, **Context Window Override**, **Temperature**, or **Top-P** empty means the provider SDK default (typically 2–3 retries with exponential backoff for **Max Retries**) or the catalog/provider default is used (no override sent). **Max Retries** accepts 0–10 and applies to Anthropic, OpenAI, OpenAI Responses, and Azure OpenAI agents.

**GitHub Copilot provider:** Sign in via the Device Flow in **Settings → Agents → GitHub Authentication**. For corporate accounts, enter your **GitHub Enterprise Domain** (e.g. `company.ghe.com`) before signing in — OAuth and API calls then go to your enterprise instance. After signing in, use **Re-enable models** if Claude or Grok models report a policy error. Model selection automatically shows per-model context-window limits; Copilot routes each model to its correct upstream API.

**Global Copilot enterprise domain:** If every Copilot agent in your setup uses the same GitHub Enterprise instance, set the domain once in **Settings → Providers → GitHub Copilot → Global GitHub Enterprise Domain**. Any Copilot agent without its own domain will inherit the global value automatically; agents that set their own domain still win. The agent card shows a hint *"Inherits global GitHub Enterprise domain: …"* when the inherited value is active.

### File Attachments

Drag and drop files directly into the AI Chat to attach them to your message. The AI can see the content of attached files and respond accordingly.

**Supported file types:**

| Category | Extensions |
|----------|-----------|
| Images | `.png`, `.jpg`, `.jpeg`, `.bmp`, `.gif`, `.webp` |
| Text | `.cs`, `.xml`, `.json`, `.txt`, `.md`, `.yaml`, `.yml`, `.csv`, `.log`, `.scl`, `.cfg` |

**How to attach files:**
1. Drag one or more files from your file explorer onto the chat area
2. A drop overlay appears confirming the drop target
3. Images appear as thumbnails in the input area; text files appear as chips
4. Click the **X** button on any attachment to remove it before sending
5. Send your message as usual; attachments are included automatically

Images are automatically resized to a maximum of 1024px (longest side) to stay within API limits.

### Dropping folders

Drag any folder from Windows Explorer (or the Manager's built-in file tree) onto the chat input area. The folder is attached as a directory listing of its immediate children (entries sorted alphabetically, case-insensitive). Larger folders are truncated; the entry cap defaults to 1000 and can be adjusted in AI Chat settings (range 100–10000). Truncated listings are marked with an `… and N more entries` hint. The assistant receives the listing as a structured directory block — nested files are not auto-expanded. To inspect deeper, re-drop the specific subfolder or use the file-mention `@` syntax.

### Restricted folders

The assistant will not accept drops or `@`-mentions pointing into well-known sensitive locations: your SSH key directory (`~/.ssh`), AWS credentials directory (`~/.aws`), Windows credentials stores, the TIA Openness Manager vault, and the Windows system configuration directory. Attempts are silently rejected with a transient hint at the bottom of the chat indicating which class of path was blocked.

### Folder attachment labels

Attached folder chips show their path relative to the currently open repository root when possible. Dragging two same-named folders from different parents (e.g. `src/utils/` and `tests/utils/`) produces visually distinct chips. Folders outside any repository show their leaf name with a trailing slash.

### Line-range and PDF mentions

When typing an `@`-mention, append a line range to focus on a specific slice: `@src/utils/helper.cs#L10-20` attaches the file with the start/end line range carried into the assistant's context. PDF files larger than 25 MB are attached as lightweight references (path + size only); smaller PDFs and other binaries are inlined as usual.

### Clipboard Paste

Paste a screenshot directly from the clipboard into the chat.

**How to paste:**
1. Take a screenshot (e.g., Win+Shift+S)
2. Click in the chat input box
3. Press **Ctrl+V** — if the clipboard contains an image, it is attached automatically
4. Alternatively, click the **paperclip** icon and select **Paste from Clipboard**

If the clipboard contains text (not an image), normal text paste occurs.

### Chat Sessions

Conversations are saved automatically as sessions. You can create new chats, switch between sessions, and resume previous conversations.

**Header buttons:**
- **+** (New Chat) — Creates a new empty session and switches to it
- **Clock** (History) — Toggles the session list panel

**Session list:**
- Click any session to load its messages and resume the conversation
- Session titles are auto-generated from the first message (editable via double-click)
- Hover over a session to see the archive and delete buttons

**Archive:**
- Click the archive icon on a session to move it to the collapsed "Archived" section
- Archived sessions can be restored or permanently deleted
- The archived section shows a count badge and expands on click

Sessions are stored in a local SQLite database under `%LocalAppData%\TiaOpennessManager\` (`chat.db`); attached files and large message payloads land in a content-addressed blob store next to it. Both files are user-private and never leave the workstation.

### Agent Memory

The AI agent can store and recall information across chat sessions. Each agent has its own private memory store that persists between conversations, with scope isolation to control memory visibility.

**How it works:**
- The agent automatically saves important facts, decisions, and preferences during a conversation (auto-memory)
- At the start of each session, memories that are semantically relevant to the current question are injected into the agent's context automatically
- Sub-agent results are automatically stored as memories for future reference
- You can also ask the agent explicitly to remember, update, or forget specific information

**Memory Scopes:**

| Scope | Description |
|-------|-------------|
| **Local** (default) | Only this agent sees its memories |
| **Project** | Memories tied to a specific project (shared across agents with the same scope) |
| **User** | Global memories visible to all agents |

Configure the memory scope in each agent's configuration file.

**Memory tools available to the agent:**

| Tool | Description |
|------|-------------|
| `memory_store` | Save a fact, decision, or preference for later recall |
| `memory_search` | Find stored memories by keyword or semantic similarity |
| `memory_list` | List all memories stored for the current agent |
| `memory_update` | Update the content of an existing memory |
| `memory_delete` | Delete a specific memory |

**Memory Snapshots (Team Initialization):**

You can pre-seed agents with shared knowledge by placing a JSON file named `{agent-id}.memories.json` in the agents directory (`%LocalAppData%/TiaOpennessManager/agents/`). The file is automatically imported on the agent's first use:

```json
[
  { "content": "Project uses ExclusiveAccess for bulk imports", "tags": "project,import" },
  { "content": "PLC_1 runs firmware V4.5", "tags": "plc,hardware" }
]
```

When the snapshot file is updated, the new version is imported automatically at the next agent start.

**Memory Settings panel:**

Open **View → AI Chat Settings** and navigate to the **Memory** section for the selected agent:

- **View memories** — Browse all stored memories for the current agent
- **Delete memories** — Remove individual entries or clear all memories
- **Export (JSON)** — Export all memories to a JSON file for backup
- **Import** — Restore memories from a previously exported JSON file
- **Cleanup old memories** — Remove memories older than a configurable age

**Embedding provider (semantic search):**

Each agent can be configured with an embedding provider for semantic memory search. When configured, the agent finds memories by meaning rather than keyword matching:

| Provider | Setup |
|----------|-------|
| OpenAI | API key required |
| Google | API key required |
| Ollama | Local Ollama instance |
| LM Studio | Local LM Studio instance |

If no embedding provider is configured, the agent falls back to keyword-based search automatically.

### Sub-Agent Steering

The AI agent can dispatch sub-tasks to independent sub-agents and manage them during a conversation. This allows the agent to run parallel or long-running tasks without blocking the main conversation.

**Sub-agent tools available to the agent:**

| Tool | Description |
|------|-------------|
| `run_subagent` | Dispatch a sub-task to a new agent (blocking or non-blocking) |
| `manage_subagents list` | View all currently running sub-agents and their status |
| `manage_subagents kill` | Terminate a running sub-agent |
| `manage_subagents steer` | Redirect a running sub-agent with new instructions |

**Key behaviors:**
- Up to 5 sub-agents can run concurrently
- Non-blocking sub-agents run in the background; the main agent can continue working and check results later
- Blocking sub-agents pause the main agent until the sub-task completes
- The main agent can redirect a running sub-agent with new instructions using `manage_subagents steer`

**Example use cases:**
- Analyzing multiple PLC blocks in parallel
- Running a long export operation in the background while answering questions
- Delegating documentation generation to a sub-agent while reviewing code

**Approval prompts from sub-agents.** When a sub-agent needs your permission to run a tool (for example, connecting to an OPC UA server or pushing a Git branch), the prompt now appears in the main chat flow — you don't have to expand the sub-agent panel to find it. Each prompt clearly shows which sub-agent triggered it. After you decide, the prompt shows one of three statuses: a green check ("Allowed"), a red X ("Denied" — you actively rejected the action), or an orange alert ("Interrupted" — the app closed or the request was cancelled before you could decide). Tool arguments named like `password`, `api_key` or `token` are shown as `[redacted]` so they aren't stored in the chat history on disk.

**Tool call transparency.** When the assistant runs a tool, the chat shows the operation and target at a glance — for example *"Read (src/main.cs · lines 1-50)"* for a file read, or *"Git Status"* for a git command. Successful completions show a green check with a short summary, errors show a red X, and rejected approvals show an amber shield — so you always know what the assistant did without expanding the bubble. File paths in these lines are clickable: a click opens the file in the code editor tab so you can review what the assistant read or wrote without typing the path yourself. Destructive tools such as deleting a block or importing external code render their name on a red background as a second confirmation cue before you approve.

### Hooks

Hooks are event-driven interceptors that run before or after AI tool calls. They allow you to add custom validation, formatting, logging, or control flow to the AI's tool execution.

**Built-in hooks** (always active):
- **Safety Confirmation** — Blocks AI modification of safety blocks (F_-prefix) automatically
- **Compile After Import** — Reminds the AI to compile after importing blocks
- **Audit Log** — Logs all TIA Portal tool operations

**User-configurable hooks:**

You can add custom hooks in `ai_chat_settings.json` under the `Hooks` array:

```json
{
  "Hooks": [
    {
      "Event": "PreToolUse",
      "Matcher": "tia_delete_*",
      "Type": "command",
      "Command": "node validate-delete.js",
      "TimeoutSeconds": 30,
      "IsBackground": false,
      "Enabled": true
    },
    {
      "Event": "PostToolUse",
      "Matcher": "tia_export_*",
      "Type": "http",
      "Url": "http://localhost:8080/hooks/post-export",
      "TimeoutSeconds": 10,
      "IsBackground": true,
      "Enabled": true
    }
  ]
}
```

| Field | Description |
|-------|-------------|
| `Event` | When to run. One of: `PreToolUse`, `PostToolUse`, `PostToolUseFailure`, `SessionStart`, `SessionEnd`, `SubagentStart`, `SubagentStop`, `PreCompact`, `PostCompact`, `Stop`, `UserPromptSubmit`, `PlanModeExit`. (`Stop` fires alongside `SessionEnd` for backwards compatibility.) |
| `Matcher` | Tool name pattern (e.g. `tia_*`, `tia_delete_*\|tia_import_*`, `Bash(git *)`) |
| `Type` | `command` (shell) or `http` (POST callback) |
| `Command` | Shell command to execute (receives JSON on stdin, returns JSON on stdout) |
| `Url` | HTTP endpoint for `http` type hooks |
| `TimeoutSeconds` | Maximum execution time (default 60s) |
| `IsBackground` | If `true`, runs fire-and-forget (PostToolUse only) |
| `Enabled` | Set to `false` to disable without removing |

**Shell hook protocol:** The hook receives a JSON object on stdin with `tool_name`, `tool_input`, `tool_output`, `session_id`, and `agent_id`. It should return JSON on stdout with `decision` (`allow`/`deny`/`ask`), optional `reason`, `additionalContext`, or `updatedInput`. Exit code 2 blocks execution.

### Command Queue

You can type and send messages while the AI agent is actively processing. Messages entered during streaming are placed into a priority queue and processed automatically after each turn completes.

**Sending while busy:** Simply type your message and press Enter while the agent is streaming. The message appears as "queued" and the input field clears so you can continue typing. A small indicator next to the input area shows how many messages are waiting (e.g. "2 messages queued").

**Priority levels:**

| Priority | When used | Behavior |
|----------|-----------|----------|
| Next | User messages (default) | Processed after current turn ends |
| Later | Agent notifications | Processed after user messages |

**Queue controls:**

- **ESC while streaming:** Cancels the current AI response and clears all queued messages
- **UP-Arrow with an empty input field:** Pulls every queued message back into the input field so you can edit or discard them before sending. Any text already in the input stays — queued messages are appended after it.
- **Stop button while idle with queued messages:** Same as UP-Arrow — pulls the queue back into the input field.

**Queue indicator:** The text next to the input area shows how many messages are waiting and what the assistant is currently doing — for example "2 queued — running tia_import", "1 queued — running sub-agent scl-expert", or "3 queued — ESC to cancel last" when the assistant is idle.

**Sub-agent approval prompts:** When a sub-agent wants to run a tool that requires your approval, the Allow/Deny buttons appear in the main conversation and are labeled "via sub-agent X" so you know which agent raised the request.

**Moving a sub-agent to the background:** When a blocking sub-agent has the main assistant waiting, press **Ctrl+B**. The sub-agent is detached and keeps running in the background while the main assistant is free to answer new messages. A small "(background)" badge appears on the sub-agent block. When the backgrounded sub-agent finishes, its result arrives in the chat as a notification, and the main assistant picks up from there. If more than one sub-agent is currently blocking, Ctrl+B sends all of them to the background at once.

**Queue processing:** After each AI turn completes, the system automatically checks the queue and processes the next message. If multiple messages are queued, they are processed one at a time in priority order (higher priority first, FIFO within the same priority).

**Steer mode (default):** In **AI Chat Settings → When typing during a response**, the default is *Send into running response (steer the model)* — a message typed while the AI is working is handed to the model at the next safe boundary inside the current response so it can react immediately. Steered messages keep their normal bubble plus a small "↪ steered into running response" indicator. Sub-agent and notification entries continue to follow the regular queue rules. If you prefer the legacy behaviour, switch the setting to *Wait for current response to finish*.

**Interrupt (Shift+Enter):** While a response is streaming, press **Shift+Enter** to cancel the current response and immediately start a fresh turn with the message you typed. ESC alone cancels without sending; Shift+Enter cancels *and* sends — useful when the AI heads in the wrong direction and you want to restart with new instructions in one gesture.

---

### Multi-Session

Run multiple AI chat sessions simultaneously. Each session has its own conversation context, canvas state, and model override.

**Sidebar layout:** Click the sidebar toggle icon (PanelLeftOpen/PanelLeftClose) in the chat header to toggle the Agent Sidebar. It slides out as an overlay from the left without pushing the chat content. Sessions are grouped under a header for each workspace (TIA project, Git repository, or manually added folder). Each group is sorted newest-first by the most recent activity in the group; sessions whose workspace is unknown or has been removed land in a trailing **OTHER** group. Each group shows up to five sessions, with a `+N more` row to expand and a `Show less` row to collapse again.

**Workspace picker:** Click the `▾` button next to the `+` in the sidebar header to open the workspace picker flyout. Three tabs:

- **Local** — Lists all recent workspaces with a folder icon, name, and dimmed full path. Click any row to make that workspace active (new sessions land in its group, the chat picks up its file-system scope). The leading **(None)** row clears the active workspace. Hover a row to reveal an X button that removes it from the recent list. The trailing **Select…** row opens a folder picker for any directory you want to add manually.
- **GitHub** — Coming soon. Will let you browse and pick GitHub repositories.
- **Remote** — Coming soon. Will let you pick SSH-tunnelled remote workspaces.

Workspaces are auto-tracked when you open a TIA project or open a folder in the Git sidebar; up to 30 entries are kept, deduplicated by path, with the most recently opened on top.

**Creating sessions:** Click the **+** button in the sidebar header to create a new session under the currently active workspace. New sessions appear at the top of their workspace group.

**Switching sessions:** Click any session row to switch to it. The chat context, canvas, and model override all switch to the selected session.

**Closing sessions:** Click the **X** button on a session row. If the session is still running, a confirmation dialog appears. Closing cancels active streaming, kills sub-agents, and cleans up the session context.

**Unread badges:** When another session receives a message while you are viewing a different session, an unread badge appears on the session row with a brief blink animation.

**Renaming sessions:** Double-click a session name to edit it. Press Enter or click away to save.

**Canvas per session:** Each session maintains its own canvas state. When switching sessions, the WebView is reset and the target session's canvas content is automatically replayed.

**Live model switch:** Use the model picker button in the chat header to change the AI model for the current session only. Other sessions and the global setting are not affected.

### Workspace — File System Access Control

The AI chat's `fs` tool (read, write, create, edit, delete, list, search) is gated by a layered access policy. Configure scope in **AI Chat Settings → Workspace**.

**Automatically allowed:**
- The currently open TIA project's directory
- Your Desktop, Documents, and Temp folders (defaults)

**Adding folders:** In Settings → Workspace, click **Add Folder…** to grant the AI persistent access to additional directories (e.g. shared project drives, common SCL libraries). Folders inside system locations (Windows, Program Files, AppData root, drive root) are rejected.

**Per-request prompt:** When the AI requests a path outside the allowed scope, a dialog appears with the operation type (read / write / delete) and the path:

- **Allow Once** — grants this single operation only
- **Allow This Session** — grants the path's parent directory until the app closes
- **Allow Permanently** — adds the parent directory to your saved Workspace roots (warning shows the exact directory that will be persisted)
- **Deny** — refuses the request

**Always refused, regardless of scope:** vault, license, chat database, agent memory, app settings, SSH/AWS/Azure/Kubernetes credentials, Windows/Program Files/AppData internals, browser/OS lock files. The AI cannot bypass this list even by requesting allow-permanent on a parent that contains them.

### MCP Server Plugins (External Tool Integrations)

The AI Chat can also connect **outward** to external MCP servers — Figma Remote, Notion, Linear, Atlassian, GitHub-MCP, your own internal services — and surface their tools alongside the built-in TIA tools. Configure them in **AI Chat Settings → MCP Servers**.

**Adding an MCP server:**

1. Click **+ Add** in the MCP Servers section.
2. Pick a transport: **Stdio** (local subprocess) or **HTTP** (remote URL).
3. For Stdio, fill in **Command**, **Arguments**, **Working Directory**, and any **Environment Variables** (one `KEY=VALUE` per line).
4. For HTTP, fill in the **Endpoint** URL and pick an **Auth Mode**.
5. Tick **Auto-start when AI Chat opens** if you want the server to come up with the chat.
6. Click **Save**.

**HTTP Auth Modes:**

- **None** — no authorization header. Use only for trusted local MCP servers that do not gate access.
- **Static header** — send a fixed `Authorization` header (or other custom header) you fill into the Headers field. Use for personal-access-token servers (e.g. self-hosted MCP gateways with a bearer token you already have).
- **OAuth 2.1** — full OAuth 2.1 + PKCE login flow. Use for hosted MCP servers (Figma Remote, Notion, Linear, Atlassian, GitHub-MCP) that advertise an authorization server via `WWW-Authenticate` or the `.well-known/oauth-protected-resource` document.

**OAuth Client Mode (only when Auth Mode = OAuth 2.1):**

When you select **OAuth 2.1**, a second radio group appears: **OAuth Client Mode**. The default — **Dynamic registration** — works with any server that supports automatic client registration and needs no extra setup. The other three modes are for servers that do not support, or where you do not want, automatic client registration:

- **Dynamic registration** (default) — TIA Openness Manager registers itself with the server automatically via Dynamic Client Registration. No extra fields. Use this whenever it works — it is the simplest option.

- **Static (pre-registered)** — The server does not allow automatic client registration; you must register the client once in the server's developer portal and paste the credentials here.
  1. Open the server's developer portal and create a new OAuth client. Set the redirect URI to `http://127.0.0.1` (any port).
  2. Copy the **Client ID** the server gave you into the **Client ID** field.
  3. If the server also issued a **Client Secret**, paste it into the **Client Secret** field. The secret is encrypted and stored in the Windows Credential Manager — only its key reference is kept in the app config. Leave the field blank for public clients (PKCE-only).
  4. In the **Edit MCP Server** dialog, the secret field starts blank with a placeholder — leave it blank to keep the previously stored secret, or type a new value to replace it.

- **Use a hosted client metadata document** — The server supports the Client Identifier Metadata Document profile (the URL itself acts as the OAuth client identifier). TIA Openness Manager hosts a default document at `https://tiaopenessmanager.ch/.well-known/tiaom-mcp-client-metadata` that covers most use cases.
  1. Leave the **Metadata document URL** field blank to use the built-in default.
  2. Power users may host their own metadata document and paste an absolute `https://` URL — it must follow the URL rules from the OAuth Client Identifier Metadata Document specification (no fragment, no userinfo, no port if the scheme's default applies).

- **Cross-app authorization (XAA)** — One central OpenID Connect identity provider (Azure AD, Okta, Auth0, Keycloak, or any OIDC-compliant IdP) issues a single sign-on token that several MCP servers accept. Configure the IdP once for the whole app, then mark each XAA-capable server with this mode.
  1. Click **Configure…** in the warning border (or open **AI Chat Settings → MCP Servers → Cross-app authorization → Configure…**).
  2. In the **Cross-app authorization identity provider** dialog, fill in:
     - **Issuer URL** — the OIDC issuer (must be `https://`, no loopback). For Azure AD multi-tenant the issuer is `https://login.microsoftonline.com/{tenant}/v2.0`; for Okta it is `https://<your-org>.okta.com/oauth2/<authServerId>`; for Keycloak it is `https://<host>/realms/<realm>`.
     - **Client ID** — the OAuth client identifier from the IdP's app registration.
     - **Client Secret** *(optional)* — leave blank for a public client (PKCE-only). If the IdP requires a confidential client, paste the secret; it is encrypted in the Windows Credential Manager.
     - **Callback port** *(optional)* — fixed loopback port between 1024 and 65535. Leave blank to allocate dynamically.
  3. Click **Save**. The Configured / Not configured pill in the AI Chat settings flips to **Configured**, and any MCP server set to **Cross-app authorization** can now use it.
  4. Back in the MCP Server dialog, optionally enter an **Audience** value if the IdP requires `aud`-binding for that server. Leave blank if the server does not require it.
  5. Click **Authorize…** — the same browser-based sign-in flow as Dynamic mode, but the token comes from the central IdP instead of the MCP server's own authorization server.

**OAuth flow:**

When you select **OAuth 2.1**, an Authorization status row appears:

1. Click **Authorize…** — your default browser opens to the server's login page.
2. Sign in and approve the requested scopes.
3. The browser is redirected to a local callback (`http://127.0.0.1:<port>/callback`) and reports back to TIA Openness Manager.
4. The status row flips to **Authorized** (or **Authorized as &lt;your-name&gt;** if the server returned an OpenID `id_token`).
5. The button becomes **Sign out** — clicking it revokes the local token and the row returns to **Not authorized**.

If the flow fails, the status row shows a localized hint:

- **Discovery failed** — the server did not advertise its OAuth metadata. Check that the endpoint URL is correct and that the server actually requires authentication.
- **Server accepts unauthenticated requests** — the server replied without ever asking for a token. Switch **Auth Mode** to **None**.
- **Client registration failed** — the server's Dynamic Client Registration endpoint rejected our request. The server may not allow public-client registration; contact the server operator.
- **Authorization canceled** — you closed the browser window or hit Cancel.
- **State mismatch — possible CSRF** — the callback's state did not match what we sent. Try again from a fresh dialog.
- **Token exchange failed** — the server's token endpoint returned an error during the code-for-token swap. Try again; if it persists, check the subprocess log.
- **Network error** — the browser-redirect or token endpoint could not be reached.
- **Not authorized — click Authorize first** — internal: a tool tried to use the server before you completed the Authorize step.
- **Authorization failed** — generic fallback for any other error class.

**Tokens are stored in Windows Credential Manager** (per server, indexed by the server's GUID). Sign out wipes the local credential; existing tokens are also rolled back automatically if you cancel the **Add MCP Server** dialog after authorizing (Edit-flow re-authorizations keep their new tokens).

**License gating:** External MCP server plugins follow the same tier rules as the built-in MCP Server feature — Trial, Professional, and Enterprise tiers are licensed; the Basic tier rejects them.

---

### Scheduled Tasks

The **Scheduled Tasks** tab in **AI Chat Settings → Scheduled tasks** lets you schedule autonomous AI agent runs on a cron expression. Each scheduled run starts a fresh chat session that appears in the sidebar with a clock icon and tinted background.

#### Creating a scheduled task

1. Open **AI Chat Settings** (gear icon in the chat input area).
2. In the left sidebar select **Scheduled tasks**.
3. Click **New task**.
4. Fill in:
   - **Name** — 1-100 characters, unique per agent.
   - **Agent** — the AI agent that runs the task. The picker is locked when editing an existing task; to switch agents, delete the task and recreate it.
   - **Task prompt** — the instruction sent to the agent at run time (max 16 000 characters).
   - **Schedule** — pick a preset (Every 5/15/30 min, Hourly, Daily, Weekly, Monthly) or switch to **Advanced (raw cron)** and enter a 5-field POSIX cron expression.
   - **Timeout** — 30 to 3600 seconds, default 300.
   - **Run history retention** — 1 to 100 runs, default 10.
   - **Enabled** — on/off toggle.
5. Click **OK**. The task appears in the list and runs at its next scheduled occurrence.

#### Cron expression syntax

The **Advanced (raw cron)** field accepts a 5-field cron expression of the form `minute hour day-of-month month day-of-week`. Each field accepts `*` (any value), comma-lists (`1,15,30`), ranges (`1-5`), and step values (`*/15`). Day-of-week values `0` and `7` both mean Sunday. Months and weekdays also accept 3-letter names (`JAN-DEC`, `SUN-SAT`).

| Field | Range | Notes |
|-------|-------|-------|
| Minute | 0-59 | |
| Hour | 0-23 | 24-hour clock |
| Day-of-month | 1-31 | |
| Month | 1-12 or JAN-DEC | |
| Day-of-week | 0-6 or SUN-SAT | 0 and 7 = Sunday |

Examples:

| Expression | Meaning |
|------------|---------|
| `*/15 * * * *` | every 15 minutes |
| `0 * * * *` | every hour at :00 |
| `0 9 * * 1-5` | weekdays at 09:00 |
| `30 7 * * MON` | every Monday at 07:30 |
| `0 0 1 * *` | first day of every month at midnight |
| `0 22 * * 0,6` | Saturdays and Sundays at 22:00 |

Times are evaluated in the local time zone of the machine running the application. Daylight-saving transitions are handled automatically — runs that fall inside a skipped hour shift to the next valid occurrence.

#### Per-row actions

- **Run now** — triggers an immediate manual run. If another run is already in progress, the request is rejected with the message *Scheduler is busy — another run is already in progress*.
- **Edit** — opens the same dialog with the current values pre-filled.
- **Delete** — removes the task and its run history (cascade delete).

#### Auto-disable on repeated failures

If a task fails three runs in a row (timeout counts as failure), the scheduler **automatically disables it** and a warning marker appears on the row. To resume, open the task and toggle **Enabled** back on — the failure counter resets.

#### Headless tool restrictions

Scheduled runs execute the agent in **headless mode**. Only read-only or query-style tools are available (TIA query/explore, OPC UA browse/read, Git status/log/diff, file-system list/read, web fetch/search, scheduled-task introspection). Write tools (`tia_delete`, `tia_import`, `editor_write`, `manage_schedule`, etc.) are denied at two layers — the catalog filter hides them from the LLM definition list and a runtime guard rejects any call that bypasses the filter.

#### Catch-up after restart

If the application was offline when a scheduled time passed, on the next start a single catch-up run fires for each task whose most recent missed slot is younger than 24 hours. Older missed slots are recorded as **Skipped** with the reason *grace expired (24h cutoff)* and the cursor advances to the next future occurrence.

#### Sidebar group

Every scheduled run starts a new chat session titled `[Scheduled] {task name} — {timestamp}`. Sessions appear in the chat-history sidebar with a clock icon prefix and a subtle tinted background to distinguish them from interactive chats. Clicking a scheduled session opens it normally — full conversation history is preserved.

---

## 9b. OPC UA Tab

The OPC UA Tab provides a built-in OPC UA client for connecting to, browsing, and monitoring PLCs and other OPC UA servers directly from TIA Openness Manager. Access it via the ActivityBar on the left sidebar (third icon from the top).

### Overview

OPC UA (Open Platform Communications Unified Architecture) is an industrial communication standard supported by Siemens S7-1500 and S7-1200 PLCs with firmware 4.1 and later. The tab lets you read and write live PLC values, subscribe to changes for real-time monitoring, and export watch table data for analysis.

### Connecting to an OPC UA Server

#### Manual Connection

1. Click the **OPC UA** icon in the ActivityBar (left sidebar, third from top)
2. Enter the **Endpoint URL** in the connection field (e.g., `opc.tcp://192.168.0.1:4840`)
3. Select the **Authentication Mode**:
   - **Anonymous** - No credentials required (if the server allows it)
   - **Username/Password** - Enter the OPC UA user credentials configured on the PLC
   - **Certificate** - Select a client certificate for secure authentication
4. Click **Connect**

The status indicator in the tab header turns green when the connection is established.

#### Auto-Discover from TIA Project

When a TIA Portal project is open, TIA Openness Manager can automatically detect OPC UA endpoints configured in the project:

1. Click **Auto-Discover** in the connection panel
2. The application reads the network configuration from the connected TIA project
3. Detected PLC endpoints are listed in a dropdown
4. Select the desired endpoint and click **Connect**

This eliminates manual entry of IP addresses and port numbers.

### Browsing the Address Space

The left panel of the OPC UA tab shows a TreeView of the server's address space:

- The root shows the server's top-level nodes
- Expand any node to browse its children
- PLC variables, data blocks, and tag groups appear as nodes
- Icons indicate the node class: Object, Variable, Method, View

**Searching nodes:**
Use the search field above the tree to filter nodes by name. The tree collapses to show only matching nodes and their parents.

**Refreshing a node:**
The orange-arrow Refresh button on the Address Space toolbar (top-right of the panel) re-fetches the children of the currently selected node directly from the server, bypassing the local cache. Use it when the server-side address space has changed since the last expand — for example after adding tags in TIA Portal — and the cached children no longer match. The button is disabled when no node is selected, when no OPC UA connection is active, or when the active connection uses the S7 Native protocol.

### Node Information

Selecting a node in the address space fills the **Node Information** panel on the right with every OPC UA attribute of that node: Node Id, Browse Name, Display Name, Node Class, Description, Write Mask, and User Write Mask. Variables show additional rows — Data Type, Value Rank, Array Dimensions, Access Level, User Access Level, Minimum Sampling Interval, Historizing, current Value, Status Code, and Source / Server Timestamp. All cells are selectable with Ctrl+C.

### References

Next to Node Information, the **References** panel shows every incoming and outgoing reference of the selected node:

| Column | Description |
|--------|-------------|
| Direction | In (inverse) or Out (forward) |
| Reference Type | Resolved name of the reference type (e.g. `HasComponent`, `Organizes`, `HasTypeDefinition`) |
| Browse Name | Browse name of the target node |
| Node Class | Node class of the target node |
| Target Node Id | Full node id of the referenced node |

### Event Log

The **Event Log** panel sits as a tab next to the Watch Table at the bottom of the OPC UA workspace. It receives live event notifications from a server-side notifier object.

| Toolbar control | Purpose |
|-----------------|---------|
| Notifier Node | The Node Id of the OPC UA object that emits events. Defaults to `i=2253` (Server). Locked while a subscription is active. |
| Severity range | Two number boxes that constrain incoming events by severity (0–1000). Events outside the range are dropped before reaching the grid. |
| Subscribe to Events | Starts the subscription against the configured notifier. |
| Stop Event Subscription | Cancels the active subscription. |
| Export CSV | Saves the visible events to a CSV file. Cells whose content starts with `=`, `+`, `-`, `@`, tab, or carriage return are prefix-quoted to defang spreadsheet formula injection. |
| Clear Event Log | Empties the grid without affecting the active subscription. |

The grid keeps the most recent 5000 events with the newest at the top. Server-controlled fields are capped at 8 KB per cell to bound memory; under heavy event flood, additional events are silently discarded and a debug-log line records the dropped count once per second.

### History Chart

The **History Chart** panel sits as a third tab next to the Watch Table and Event Log at the bottom of the OPC UA workspace. It loads raw historical values for a variable node over a time range and plots them on a scatter chart with a date-time X-axis.

| Toolbar control | Purpose |
|-----------------|---------|
| Source | Read-only label that tracks the currently selected variable node in the address space tree. |
| Start | Start of the time range (UTC). Defaults to one hour ago. |
| End | End of the time range (UTC). Defaults to now. |
| 1h / 6h / 24h / 7d | Quick presets that set End to now and Start to now minus the chosen window. |
| Aggregate | Selects the value-shape returned by the server: **Raw** (default — every recorded sample) or one of **Average**, **Minimum**, **Maximum**, **Count**, **Total** computed in fixed-width bins across the time range. |
| Interval (s) | Width of each aggregate bin in seconds. Visible only when Aggregate is not Raw. Default 60 s, range 1..86400 s. |
| Read History | Fetches values for the source node between Start and End. With Raw selected the chart shows every sample; with an aggregate selected the chart shows one point per bin. The button is disabled while a read is in progress. |
| Export CSV | Saves the loaded values to CSV (Source Timestamp / Server Timestamp / Value / Status Code). Formula-injection defanging is identical to the Event Log export. |
| Clear Chart | Empties the chart and frees the in-memory buffer. |

Non-numeric values, values with `Bad` status, and samples with out-of-range timestamps are omitted from the chart but remain in the CSV export. Raw reads are capped at 100,000 values per call and 1,000,000 values total; if the server returns more, the chart shows what fits and a warning is logged. The chart clears automatically on protocol switch or disconnect but keeps its content while you browse the address tree, so you do not lose loaded history just because you select a different node.

When an aggregate is selected the application log records how many bins came back marked **partial** (the bin straddles the time-range boundary or contains incomplete data). Partial bins still appear in the chart; the count is informational. Aggregate support depends on the server: Siemens S7-1500 CPUs typically expose Average, Minimum, Maximum, Count and Total when historizing is enabled; less common functions (Standard Deviation, Range, …) are also wired in the service layer but not exposed in the toolbar.

The variable must have `Historizing = true` on the server, and the session must have HistoryRead access. Siemens S7-1500 CPUs do not enable historizing by default — most variables need to be flagged for historical access in the PLC configuration.

### Server Diagnostics

The **Server Diagnostics** panel sits as a fourth tab next to the Watch Table, Event Log, and History Chart at the bottom of the OPC UA workspace. It surfaces the standardized OPC UA server-object hierarchy (Part 5 §6) so you can monitor session counters, subscription health, and server build information without leaving the application.

| Toolbar control | Purpose |
|-----------------|---------|
| Poll interval | Numeric spinner from 1 to 60 seconds (default 5). Persisted per connection endpoint. |
| Refresh | Triggers an immediate read regardless of the timer. |
| In-flight indicator | Indeterminate progress bar visible while a read is in flight. |
| Last updated | Timestamp of the last successful response (HH:mm:ss, local time). |
| Inline error | Surfaces the server-reported status code if the read fails. |

The body shows five collapsible sections:

- **Server Status** — server state, start time, shutdown countdown, build info (product name, URI, manufacturer, software version, build number, build date).
- **Server Capabilities** — max array / string / byte-string lengths, plus operation limits (max nodes per Read / Write / Browse).
- **Diagnostics Summary** — current and cumulated session count, rejected sessions, session timeouts, current subscription count, rejected requests.
- **Subscriptions** — sortable, resizable grid with one row per active subscription (id, publishing interval, publishing enabled flag, notifications count).
- **Sessions** — sortable, resizable grid with one row per session (session id, name, connect time, last contact time, total request count, read count, write count).

If the server explicitly does not expose the `Server.ServerDiagnostics` subtree (security policy, capacity), a "Server diagnostics are not exposed by this server" placeholder is shown instead of empty rows. Transient communication errors do **not** trigger the placeholder — they appear in the inline error strip so you can tell a "policy denial" apart from a "transient outage". After repeated failures the panel automatically backs off the poll interval to avoid hammering a struggling server; on the next success, the back-off resets.

Per-row strings (session name, product name, ...) are sanitized at projection time so that hostile servers cannot tear the grid layout with embedded control characters.

### Connection polish

The connection header and Address Space tree expose UaExpert-style polish for everyday use:

**Auto-reconnect banner.** When the keep-alive watchdog detects a lost connection, the SDK starts reconnecting in the background. While that runs, the connection header shows a yellow banner that updates once per second with the elapsed time ("Reconnecting… (12 seconds)"). A **Cancel** button on the banner stops trying and returns to disconnected state — useful when you know the server is gone for good and want to skip the 5-minute timeout.

**Recent endpoints.** The Endpoint URL field is an autocomplete dropdown of the last 10 successful connections. Type to filter, or click the down-arrow to pick one. The list is per-installation (not per-project) and survives application restart. Different URL forms that resolve to the same scheme + host + port are merged into a single entry — typing `OPC.TCP://Host:4840/` after a previous `opc.tcp://host:4840` connection updates the existing entry rather than creating a duplicate.

**Keyboard shortcuts.** Within the OPC UA tab, the following keys are bound to the active connection:

| Shortcut | Action |
|----------|--------|
| Ctrl+Enter | Connect |
| Ctrl+D | Disconnect |
| F5 | Refresh selected node (re-browse from server, bypass cache) |
| Ctrl+W | Write the currently selected Watch Table row |

The Write shortcut acts on the row you have highlighted in the Watch Table — select the row first (single click), edit the value cell (double-click or F2), then Ctrl+W to send. Without an active edit it is a no-op.

**Copy NodeId / Copy Browse Path.** Right-click any node in the Address Space tree to copy either the canonical Node Id (e.g. `ns=2;s=DB1.MyTag`) or the human-readable browse path (e.g. `Objects/DeviceSet/PLC_1/DB1/MyTag`) to the clipboard. Useful for pasting Node Ids into Canvas bindings, MCP tool calls, or external scripts.

**View menu.** A "View" button at the top of the OPC UA toolbar opens a menu with one toggle entry per tool tab (Address Space, Type Definitions, Node Attributes, References, Struct Fields, CPU Protection, Watch Table, Event Log, History Chart, Server Diagnostics). Click an entry to close the corresponding tool if it is currently open, or re-open it at its home dock if it was closed. Useful for getting back a tool you accidentally closed via its tab × button without resetting the whole workspace.

### Call Method dialog

Right-click a **Method node** in the Address Space Browser and pick **Call Method...** to open a modal dialog that drives an OPC UA method call end-to-end.

The dialog first fetches the method's input and output argument list from the server and renders one editor per input:

| Argument shape | Editor |
|----------------|--------|
| Scalar (boolean, integer, float, string, DateTime) | Single text box with the expected data type as watermark |
| Array | A list of single-value rows with **+ Row** / **− Row** buttons to match the desired array length |

Each card shows the argument's name, data type, and description (if provided by the server). After filling the inputs, click **Call** — the dialog invokes the server, clamps oversized payloads, and populates the Output arguments section with the returned values and a status line. Closing the dialog cancels any call still in flight.

Method calls write to the PLC — make sure the method's effect is understood before calling on a running machine.

### Edit Matrix dialog

Right-click a **Variable node** whose value is a two-dimensional matrix (for example a `Double[3,4]` setpoint table or a calibration grid) in the Address Space Browser and pick **Edit Matrix...** to open a spreadsheet-style editor. The menu entry only appears when the selected variable actually has matrix shape on the server.

The dialog loads the current value and renders every cell as an editable text box with row (`R0`, `R1`, ...) and column (`C0`, `C1`, ...) headers. Change values cell by cell — changed cells are tracked as dirty. Press **Save** to write the whole matrix back to the server (only cells you actually changed are re-parsed; untouched cells are preserved as-is) or **Reload** to throw away your edits and pull a fresh copy from the server.

If the server declares the variable as read-only (no write access for your session), the dialog shows a **Read-only** badge and the Save button stays disabled. Matrices with more than two dimensions are not editable — the dialog reports "rank not supported" instead of silently flattening the data. Invalid cell values (for example text in a numeric matrix) are flagged when you press Save; fix the cell and try again.

When you press Save the dialog re-reads the current value from the server first. If any cell has changed on the server while you were editing — for example because another client or the PLC itself updated the matrix — a warning banner appears with two options: **Overwrite** writes your edits anyway (and clobbers the server-side change), **Reload** discards your edits and pulls the fresh server values into the editor. If the server reports a different matrix shape (more rows or columns than when you opened the dialog), Overwrite is disabled and you must Reload before continuing.

### Certificate Management

Open the settings flyout (gear icon next to the endpoint URL in the connection bar) and click **Certificate Management...** to review and manage the OPC UA certificates this client uses and trusts. The dialog shows three tabs:

| Tab | What it shows | Actions |
|-----|---------------|---------|
| Own | Your client certificate(s) — the one the PLC sees when you connect | Regenerate (creates a fresh keypair; ends all active OPC UA sessions), Remove |
| Trusted | Server certificates this client has accepted | Reject (moves to the Rejected tab), Remove |
| Rejected | Server certificates this client has refused or received while Auto-accept was off | Trust (moves to the Trusted tab), Remove |

Each row shows Subject, Issuer (for server certs), Thumbprint, Valid from, Valid to. Select a row and use the tab's action buttons.

Directly above the button sits the **Auto-accept server certificates** toggle:

- **On (default)** — Any new server certificate is trusted on first connect. Fastest, most convenient; matches the previous behaviour.
- **Off** — New server certificates are routed to the Rejected tab instead of being accepted automatically. You must open the dialog and click Trust before the next connect succeeds. Use this mode on networks where you want explicit per-server approval.

### Connection Status Indicators (S7 Native)

When connected to an S7-1200 or S7-1500 PLC over the native S7 Comm+ protocol, the PLC Online tab shows three live status indicators that react immediately to what the PLC is doing:

- **Tab header dot** — a small coloured circle next to the tab title. Hover the dot to see what it means:
  - **Grey** — not connected yet
  - **Green** — online, CPU is running
  - **Yellow** — online but the CPU is stopped (Stop, Startup, Hold, ...), or the app is currently reconnecting
  - **Red** — the PLC is unreachable
- **Reconnecting banner** — a yellow strip under the connection bar saying "Reconnecting..." appears while the app is trying to restore a lost connection. It clears automatically when the PLC comes back.
- **Faded watch values** — when the PLC becomes unreachable, the values in the Watch Table fade to half opacity and switch to `???` to show they are no longer current. As soon as the PLC is back, new live values replace them on their own. No restart or manual reconnect needed.
- **Operating-state pill** — `RUN`, `STOP`, `STARTUP` etc. next to the IP address, coloured to match the CPU state.
- **Access-level badge** — sits next to the operating-state pill and reflects what the PLC granted on legitimate-step:
  - **Green `Full access`** — the supplied password (or anonymous if the PLC permits it) was accepted with full read/write permission.
  - **Amber `Read access` / `HMI access`** — the PLC granted a degraded level. Reads work for the categories the level allows; writes will be rejected.
  - **Red `No access`** — the PLC requires a password and none was supplied. The connection stays open but the post-connect browse, watch-table subscribe and CPU-protection probe are skipped on purpose. Supply the correct password in the connection form and click Connect again to re-attempt with credentials.

### TLS encryption and certificate pinning (S7 Native)

S7-1500 firmware V2.9 and later activates TLS unconditionally on the OMS+ port — the unencrypted plain S7-CommPlus path is rejected by current PLCs. The S7 Native transport mirrors that contract: TLS is on by default, the unencrypted InitSsl handshake runs first, and the channel is upgraded to TLS for every operation that follows. The connection settings expose three options:

- **Use TLS** — historical toggle preserved on the connection form. The S7 Native driver mirrors the legacy S7-CommPlus contract and always performs the TLS upgrade after the unencrypted InitSsl handshake; the toggle no longer disables that upgrade.
- **Server-certificate fingerprint (SHA-256)** — paste the SHA-256 thumbprint of the CPU's device certificate (lowercase or uppercase hex, with or without `:` separators). When set, the client accepts that one certificate only; any mismatching certificate is rejected. Pinning is the recommended production setting because S7-1500 device certificates are typically self-signed and not enrolled into a public PKI.
- **Accept any certificate** — explicit diagnostics toggle. When enabled the client trusts whatever certificate the server presents and a one-shot warning is written to the app log on every connect.

Selection precedence:
1. If a fingerprint is set → only that certificate is accepted, regardless of the *Accept any certificate* toggle.
2. Else, if *Accept any certificate* is on → any certificate is accepted, with an explicit-diagnostics warning.
3. Else (TLS on, no fingerprint, accept-any off) → the client accepts any certificate and emits a one-shot warning recommending fingerprint pinning. This mirrors the behaviour of the legacy S7-CommPlus client and matches what TIA Portal does over the same channel; it is also the only way to talk to a stock S7-1500 without first extracting the device certificate.

For Wireshark-side diagnostics of the encrypted handshake, the `SSLKEYLOGFILE` mechanism described under *Unit Testing → Troubleshooting* applies to PLC Online connections as well.

### CPU Protection panel

A `CPU Protection` tab in the right-hand tool dock shows the live protection state of the connected S7-1500 / S7-1500F CPU:

- **Protection level** — `No protection` / `Read protection` / `Write protection` / `Full protection` / `Unknown`. The values mirror what TIA Portal Online & Diagnostics shows for the same CPU.
- **Password required** — `Yes` if the granted level requires a password to authenticate, `No` otherwise.
- **Refresh** — re-reads the CPU memory-and-protection block on demand. The value also refreshes automatically once after every successful S7 connect (so the field is populated by the time the tab is opened).

The values display as an em-dash (`—`) when no PLC is connected. If the read fails (for example because the CPU rejected the request), an inline red error message appears below the rows and the previous cached value is kept until the next successful refresh.

### Diagnostic Buffer panel

A `Diagnostic Buffer` tab in the right-hand tool dock lists the most recent CPU diagnostic events read from the SSL `0xA0` partial-list, mirroring what TIA Portal Online & Diagnostics shows under "Diagnostics buffer":

- **Columns** — `Timestamp` (UTC, millisecond precision), `Event ID` (hex `0xXXXX`), `Class`, `Priority`, `OB` (organization-block reference).
- **Refresh** — re-reads the diagnostic buffer on demand. The value also refreshes automatically once after every successful S7 connect on supported firmware.
- **Empty state** — when the CPU reports zero events, a `No diagnostic events on this CPU.` placeholder is shown.
- **Firmware requirement** — the SSL DS-248 SubrangeRead used here is a CPU **firmware V3.0 or newer** feature. On V2.x CPUs the tab shows `Diagnostic buffer requires CPU firmware V3.0 or newer.` instead of the table; the auto-refresh skips the wire call so no log spam is produced.

### CPU Identity panel

A `CPU Identity` tab in the right-hand tool dock shows the device-identification record (PROFINET I&M0) read from the active S7-1500 / S7-1500F CPU. Works on both V2.x and V3.0+ firmware.

- **MLFB / Order number / Serial / Hardware version / Firmware version** — five rows extracted from the I&M0 record on the CPU's `theCPUProxy` submodule.
- **Refresh** — re-reads the I&M0 record on demand. The value also refreshes automatically once after every successful S7 connect.

### Memory Usage panel

A `Memory Usage` tab in the right-hand tool dock shows live load/work/retain memory utilization for the connected S7-1500 / S7-1500F CPU, mirroring what TIA Portal Online & Diagnostics shows under "Memory":

- **Load memory** — used/total in megabytes plus a horizontal progress bar (0–100 %, clamped).
- **Work memory** — same shape.
- **Retain memory** — same shape.
- **Refresh** — re-reads the CPU memory-and-protection block on demand. The value also refreshes automatically once after every successful S7 connect.

When no PLC is connected the rows show an em-dash (`—`) and the progress bars sit at zero. Read failures surface a localized error string below the rows; the previous cached value is cleared so stale numbers cannot mislead.

### Protocol-Aware Tool Tabs

The tool tabs surrounding the connection workspace adapt to whichever protocol the active connection uses:

- **OPC UA connection** — Address Space, Type Definitions, Node Attributes, References, Struct Fields, Event Log, Watch Table, History Chart, Server Diagnostics. No CPU Protection / Diagnostic Buffer / CPU Identity / Memory Usage / Cycle Time tabs (those are S7-only).
- **S7 Comm+ connection** — Address Space, Watch Table, History Chart, CPU Protection, Diagnostic Buffer, CPU Identity, Memory Usage, Cycle Time. The OPC-UA-only tabs (Type Definitions, Node Attributes, References, Struct Fields, Event Log, Server Diagnostics) are hidden because they need NodeIds, OPC events or other server-side surfaces that S7 Comm+ does not expose.

Tabs that are hidden retain their state — switching the active tab to an S7 connection and back to OPC UA restores the OPC-UA-only tabs in their previous places. Switching the protocol radio in the connection form mid-session re-applies the filter immediately.

### Watch Table

The watch table on the right displays variables you have selected for monitoring.

#### Adding Variables

- **Double-click** a variable node in the address space tree to add it to the watch table
- **Click the + button** next to a node to add it without navigating away
- Drag a node from the tree and drop it onto the watch table

Each row in the watch table shows:

| Column | Description |
|--------|-------------|
| Name | Display name of the variable |
| Node ID | OPC UA Node ID (e.g., `ns=3;s="DataBlock1"."Speed"`) |
| Data Type | OPC UA data type (e.g., Int16, Float, Bool) |
| Value | Current value — scalars render as typed strings (`True`, `12345`, `1.5`); arrays render with a size-prefix and element list (`[16] True, False, …`); byte arrays render as hex (`[4] DE AD BE EF`). Long arrays truncate after 32 elements. |
| Status | OPC UA status code (Good, Bad, Uncertain) |
| Timestamp | Server timestamp of the last value |

#### Reading Values

- Click **Read All** to refresh all values in the watch table with a single server request
- Click the **Read** button on an individual row to refresh only that variable

#### Writing Values

1. Double-click the **Value** cell of a row in the watch table
2. Enter the new value
3. Press **Enter** or click outside the cell to confirm
4. The value is written to the PLC immediately

> **Note:** Write operations require the OPC UA user to have write permissions configured on the PLC.

#### Write Errors

If a write fails, the row stays in edit mode (your value remains visible) and a small red error message appears below the value cell explaining why the write was rejected:

- **Variable is read-only** — the server rejected the write because the variable does not allow writes (`BadNotWritable` / `BadWriteNotSupported`).
- **Permission denied** — the OPC UA user is connected but does not have write rights for this variable (`BadUserAccessDenied`).
- **Type mismatch** — the value cannot be converted to the variable's data type (`BadTypeMismatch`).
- **Value out of range** — the value is outside the valid range for the variable (`BadOutOfRange`).
- **Server returned no result** — the server accepted the request but returned no per-item status; the write may not have taken effect.
- **Write failed: {reason}** — generic fallback for any other server response or connection problem.

To clear the error, edit the cell again or click another row. A successful write also clears the message.

The same feedback appears as a banner above the **Struct Fields** panel for failed struct writes.

#### Struct Write — No Changes

If you press **Write** on the Struct Fields panel without having edited any field, the panel shows a **"No changes to write"** banner instead of silently doing nothing. As soon as you edit any field, the banner clears automatically and the next press of **Write** sends the changes to the server.

### Live Monitoring (Subscriptions)

Subscriptions let the OPC UA server push value changes to TIA Openness Manager automatically, without repeated polling.

#### Starting a Subscription

1. Set the **Subscription Interval** (in milliseconds) using the interval field — the default is `500` ms
2. Click **Subscribe** to start monitoring all variables in the watch table
3. Values update automatically as changes occur on the PLC
4. A pulsing indicator shows that a subscription is active

> **Note:** The accepted range is 100 – 60000 ms. Values below 250 ms are not recommended for production CPUs — they can overload PLCSIM Advanced and may exceed the communication-load budget on real S7-1200 / 1500 PLCs (see CPU comm-load setting in TIA Portal). Use 100 – 200 ms only for short, targeted measurements.

#### Stopping a Subscription

Click **Unsubscribe** to stop receiving updates. Values in the watch table remain at their last received values.

#### Per-Variable Subscriptions

To subscribe to only specific variables:
1. Select the rows you want to subscribe to (hold Ctrl for multi-select)
2. Right-click and select **Subscribe Selected**

### Saving and Loading Watch Table Configurations

Watch table configurations (the list of monitored variables and the endpoint URL) can be saved and restored:

**Save:**
1. Click **Save Watch Table** (floppy disk icon)
2. Choose a file name and location
3. The configuration is saved as a `.opcua-watch` JSON file

**Load:**
1. Click **Load Watch Table** (folder icon)
2. Select a previously saved `.opcua-watch` file
3. The variables are restored; click **Connect** then **Read All** or **Subscribe** to resume monitoring

### Saving and Restoring the Whole Workspace

The entire OPC UA workspace — panel layout (which tabs are active), open connections (without passwords) and the watch table — is also captured automatically and restored the next time you open the app. No setup is needed; just close the app and reopen it.

Every open connection tab now gets its own saved state — watches, subscriptions, event filter, and history range — not just the active tab. When you reopen the app or load a workspace file, each tab comes back with the variables, alarms and history range you left it with.

For named snapshots that you can hand to a colleague or stash for a specific commissioning trip, use the **Workspace** menu in the dock toolbar at the top of the OPC UA tab:

- **Save Workspace As…** writes the current state to a `.opcua-workspace` file you choose. Passwords are never written to the file — operators have to re-enter them on reconnect.
- **Load Workspace…** opens any previous `.opcua-workspace` file and applies it. The picker also accepts the older `.json` watch-table files saved with the floppy-disk icon, so legacy workspaces keep loading.
- **Reset Workspace** clears the auto-saved snapshot and the active connection's watch list after a confirmation prompt — useful before sharing your screen for a presentation, or when a stale workspace keeps restoring stale state.

To keep a confidential endpoint out of the workspace entirely, open the connection's Settings flyout (the gear icon in the connected connection bar) and enable **Don't persist this connection in workspace**. While the toggle is on, that tab's endpoint, watches, subscriptions, event filter and history range stay out of the workspace file and the auto-restore. Turn it back off whenever you want the tab to be remembered again.

The saved workspace also remembers how you arranged the panes — whether the Watch Table sits at the bottom or the right, whether Type Definitions is pinned, where you placed the splitters, and which tabs were active. Loading the workspace puts every pane back exactly where you left it.

### Exporting Watch Table Data

Export the current watch table values for documentation or further analysis:

**CSV Export:**
1. Click **Export → CSV**
2. Choose a destination file
3. A CSV file is created with all rows including Name, Node ID, Data Type, Value, Status, and Timestamp columns

**JSON Export:**
1. Click **Export → JSON**
2. Choose a destination file
3. A structured JSON file is created with full metadata for each variable

### OPC UA MCP Tools (AI Integration)

When the MCP server is running, AI assistants have access to OPC UA and Canvas tools via two consolidated tools:

| Tool | `what` subcommand | Description |
|------|-------------------|-------------|
| `opcua` | `connect` | Connect to an OPC UA endpoint with specified authentication |
| `opcua` | `disconnect` | Disconnect from the current OPC UA server |
| `opcua` | `browse` | Browse the address space starting from a given node |
| `opcua` | `read` | Read the current value of one or more variables by Node ID |
| `opcua` | `read_complex` | Read structured/complex data types (e.g., UDTs, arrays) |
| `opcua` | `write` | Write a value to a variable by Node ID |
| `opcua` | `write_complex` | Write individual fields of a data block (read-modify-write) |
| `opcua` | `get_types` | Retrieve data type definitions from the server |
| `opcua` | `subscribe` | Create a monitored item subscription for one or more nodes |
| `canvas` | `bind_opcua` | Poll OPC UA values and update the Canvas dashboard in real-time |
| `canvas` | `unbind_opcua` | Stop all Canvas OPC UA read bindings |
| `canvas` | `bind_opcua_write` | Map Canvas button clicks and slider changes to OPC UA writes |
| `canvas` | `unbind_opcua_write` | Stop all Canvas OPC UA write bindings |

**Example AI Chat usage:**

Ask the AI assistant in the chat panel things like:
- "Connect to the PLC at 192.168.0.10 anonymously and browse the data blocks"
- "Read the value of node `ns=3;s="Tank1"."Level"` and tell me if it is above 80%"
- "Subscribe to all Float variables in the 'Production' data block with a 1-second interval"
- "Write the value 1500 to `ns=3;s="Conveyor"."SetSpeed"`"

### Notes

- OPC UA connectivity does not require TIA Portal to be open or connected
- The PLC must have OPC UA enabled in its hardware configuration (General → OPC UA → Server)
- For S7-1500 PLCs, ensure the OPC UA server is activated and the relevant PLC tags are marked as "Accessible from HMI/OPC UA"
- Certificate-based authentication requires exchanging certificates between the client and the PLC

### 9c. AI Canvas with OPC UA Live Data

The AI Canvas can display interactive dashboards that connect to live OPC UA data. The AI creates visual dashboards (gauges, buttons, sliders, animations) using `canvas` (what: `eval`), and OPC UA values are bound to the dashboard for real-time updates.

#### How It Works

1. **The AI creates a dashboard** using `canvas` (what: `eval`) (HTML/CSS/JavaScript rendered in the Canvas WebView)
2. **Read bindings** (`canvas` with what: `bind_opcua`) poll OPC UA values and push them to the dashboard via `window.__tiaUpdateDashboard()`
3. **Write bindings** (`canvas` with what: `bind_opcua_write`) map Canvas button clicks and slider changes to OPC UA write operations
4. All updates happen automatically — no manual polling or subscription setup needed

#### Canvas OPC UA Tools

| Tool | `what` subcommand | Direction | Description |
|------|-------------------|-----------|-------------|
| `canvas` | `bind_opcua` | PLC → Canvas | Polls OPC UA values and updates the dashboard in real-time |
| `canvas` | `unbind_opcua` | — | Stops all read bindings |
| `canvas` | `bind_opcua_write` | Canvas → PLC | Maps button clicks and slider changes to OPC UA writes |
| `canvas` | `unbind_opcua_write` | — | Stops all write bindings |
| `opcua` | `write_complex` | Canvas → PLC | Writes individual fields of a data block (read-modify-write) |

#### Example: Process Control Dashboard

Ask the AI to create an interactive dashboard:

> "Create a process control dashboard on the Canvas with Start/Stop buttons, a speed slider (0-3000 RPM), and live gauges for Speed, Temperature, Pressure, and FlowRate. Bind it to the data block `Data_block_1` via OPC UA."

The AI will:
1. Create the visual dashboard with `canvas` (what: `eval`)
2. Set up read bindings with `canvas` (what: `bind_opcua`) for live value display
3. Set up write bindings with `canvas` (what: `bind_opcua_write`) so buttons and sliders control the PLC

#### Saving and Loading Dashboards with OPC UA Bindings

Canvas dashboards can be saved to JSONL files and loaded later. **OPC UA binding configurations are included in the saved file.**

**Save:**
1. Click the **Save** button in the Canvas toolbar
2. The JSONL file contains the dashboard layout, JavaScript, and OPC UA binding configuration

**Load:**
1. Connect to the OPC UA server first
2. Click the **Load** button in the Canvas toolbar and select the saved JSONL file
3. The dashboard is restored and OPC UA bindings are automatically re-applied
4. Live data starts flowing immediately (if OPC UA is connected)

> **Note:** OPC UA bindings are also preserved when the Canvas is docked/undocked within the same session.

#### Important Notes

- An active OPC UA connection is required before bindings can deliver data
- `canvas` (what: `bind_opcua`) uses polling (not OPC UA subscriptions) — this is more stable and avoids overloading the OPC UA server
- All values from OPC UA arrive as **strings** in the JavaScript callback (use `parseFloat()` for numbers, compare with `"True"`/`"False"` for booleans)
- The Canvas `Reset` button stops all OPC UA bindings (both read and write)

---

## 9c. Unit Testing

Integrated unit test framework for TIA blocks. Write, run and evaluate tests against a live PLCSIM Advanced instance without leaving the app.

**Requirements:**
- Enterprise license
- PLCSIM Advanced V3.0+ installed (separate Siemens license)
- A TIA project with at least one PLC open

### Opening the Unit Testing Workspace

1. Click the **Unit Testing** entry in the left sidebar (or press `Ctrl+5`)
2. The workspace has four dock panels:
   - **Left (Analysis tools + Test Explorer):** Interface, Boundary Values, Dependencies, Test Explorer (as tabs)
   - **Center (Document Dock):** Test suite editors (JSON, Visual, SCL modes)
   - **Right (Results):** Test Results panel — live progress and per-assertion details
   - **Toolbar:** PLC and block selector, Analyze, New Suite, Open Suite, Run/Stop

### Test Explorer

The Test Explorer auto-scans the `{WorkingDirectory}/.tia-tests/` folder and shows every `.json` file as a suite node with its test cases as children.

**Status icons (loaded from SQLite on startup):**
- ✓ **Pass** — green checkmark, test passed in the last run
- ✗ **Fail** — red cross, test failed in the last run
- ⚠ **Error** — orange warning, test errored (exception, timeout, S7 error)
- ⊘ **Skipped** — grey slashed circle, test was filtered out of the last run (e.g. via "Run Single")
- ○ **NotRun** — grey empty circle, no persisted result yet

**Interactions:**

| Action | Result |
|--------|--------|
| Double-click a suite | Opens the suite as a document tab in the center dock |
| Right-click a suite → Run Suite | Runs this suite only |
| Right-click a suite → Open | Same as double-click |
| Right-click a test case → Run Test | Runs this single case via TestCaseFilter (other cases marked Skipped) |
| Select a suite + **Run Selected** button | Runs this suite |
| Select a case + **Run Selected** button | Runs only that case |
| **Run All** button | Runs all visible suites sequentially |
| Type in search box | Filters suites by name (suite + test case names, case-insensitive) |
| Toggle `✗ Failed` button | Shows only suites with Fail/Error cases (button turns red when active) |
| Right-click a suite → Run Affected Only | Runs only the suites whose underlying PLC block changed since the last test run |

**Block-Change Badge:** Suites whose underlying PLC block has changed since the last test run show a small orange dot (8×8 px) next to the suite name with the tooltip "Block changed since last run". The badges refresh automatically after the project loads, after every batch run, and when the file watcher detects suite-file changes. If no suites are affected, or if change detection fails for every PLC, an inline status banner above the search box explains the result instead of a silent no-op.

### Test-Case Metadata

Each test case in the visual editor of a suite has an expandable **Metadata** pane (collapsed by default, located below the variable-watch list). Click the section header to expand it and edit the following fields per case:

| Field | Purpose |
|---|---|
| Order | Numeric run order. Leave empty to keep the natural order in the suite |
| Tags | Comma-separated labels (e.g. `safety, regression`) used for filters in HTML reports |
| Priority | One of Low / Normal / High / Critical. Drives report sort order |
| Owner | Free-text owner (team name, e-mail, etc.) |
| Requirements | Comma-separated requirement IDs (e.g. `REQ-123, REQ-456`) for traceability |

Schema-validation issues that target a specific test case (such as an out-of-range priority) are shown in a red panel directly inside the affected case's Metadata pane. Issues that target the suite as a whole still appear in the suite-level validation banner. All edits are auto-saved with the rest of the suite. Suites created before this release load with empty metadata defaults — no migration is required.

### Live Progress During a Run

While a test is running, the workspace shows:

- **Status bar:** Current phase (e.g. "Creating PLCSIM instance", "Compiling PLC", "Running: TestCase_1")
- **Test Explorer:** Status icons update live per test case (pass/fail appear as each case finishes)
- **Results panel:** Test case list fills up incrementally as results come in
- **Stop button:** Cancels the current run at the next safe point (S7 connection and PLCSIM instance are always cleaned up)

### Results Panel

After a run completes, the Results panel shows:

- **Summary:** Total passed/failed/error counts + total duration
- **Test case list:** Every case with status icon, name and duration
- **Detail grid (on case selection):** Every assertion with Variable, Operator, Expected, Actual, ✓/✗
- **Variable Timeline (on case selection):** A chart showing how each watch variable changed cycle by cycle during the run. The left column lists the variables as checkboxes — toggle one to hide or show its line in the chart. Numeric types (BOOL/INT/REAL/TIME/…) are plotted; non-numeric types still appear in the legend but aren't drawn. Hover the chart to snap a crosshair to the nearest data point with the variable name, cycle and value in the title

To fill the timeline, add a `"watch": ["Var1", "Var2"]` array to a test case in the suite JSON and set `"cycles"` greater than 1. The timeline sampling is capped at 100,000 cycles per test case.

Test results are persisted to `%LocalAppData%\TiaOpennessManager\db\test_results.db` — they survive app restarts and reappear in the Test Explorer automatically.

### Run History

The **Run History** dock-tool is a second tab in the right results panel (next to **Test Results**). It lists every run that has been persisted to the database, regardless of which suite executed.

- **Columns:** Status icon, Started At (local time), Duration, Pass / Fail / Error / Skipped counts, Suite, PLC, Hostname, TIA version
- **Status icon:** ✓ green when all cases passed, ✗ red on any failure or error
- **Filter box:** Filters the list client-side by hostname, suite name, PLC, or block name (case-insensitive)
- **Refresh:** `F5` reloads the list (or use the Refresh entry in the context menu)

**Context menu actions** (right-click a run):

| Action | Result |
|--------|--------|
| Open Results | Loads that run into the **Test Results** tab so you can inspect each case |
| Compare To… | Marks this run as the baseline and opens the **Select run to compare** dialog. Pick a second run and the **Compare Runs** dock-tool renders the diff |
| Delete Run | Permanently removes the run row plus all its test cases and provenance metadata. Block hashes survive so block-change comparisons keep working |
| Export HTML | Renders the run as a self-contained HTML report (`<run-id>.html`) with the same styling as the in-app Results panel |
| Open Manifest | Opens the SHA-256 integrity manifest for the run (when one was generated by the report pipeline) |

The list shows the most recent 100 runs by default, ordered newest-first. Provenance values such as hostname and TIA version come from the run-provenance metadata captured when the run started; the project path itself is **never** stored in plain text — only an irreversible SHA-256 hash, so you can correlate runs across machines without leaking workspace paths.

### Compare Runs

The **Compare Runs** dock-tool is the third tab in the right results panel. It is opened on demand by **Compare To…** in Run History — you pick a baseline run, the launcher dialog asks for a second run, and the Compare Runs tab activates with the diff.

- **Header:** Baseline / Current run-IDs side by side, **Swap** button reverses the comparison, **Export HTML** sends the diff to a Phase-VI report renderer (wiring lands with the CLI integration)
- **Summary pills:** Five colour-coded counters — Regressions (red), Fixed (green), New (blue), Removed (grey), Stable (muted). Stable counts only Still-Passing and Unchanged cases; Still-Failing cases stay flagged as warnings, not as stable
- **Filter bar:** Five radio buttons (All / Regressions / Fixed / New / Removed) reduce the case list in place
- **Case rows:** Each case shows a coloured bullet (red / green / blue / grey / orange) plus `<Suite> / <Case>`, the failure message (if any), the change-kind label, and the duration delta versus the baseline (`+12 ms` / `−5 ms`)

The launcher dialog lists the most recent 100 runs minus the baseline you started from, sorted newest-first. Double-click a row or click **OK** to commit the pick; **Cancel** closes the dialog without changing the comparison.

### Trend

The **Trend** dock-tool is the fourth tab in the right results panel. It visualises pass-rate, duration, and per-case status over time using historical runs from the database.

- **Filter bar (row 1):** PLC name (required), suite name (optional — narrows the duration chart), case name (optional — narrows the heatmap)
- **Filter bar (row 2):** From / To calendar pickers (clear a picker to remove the bound), **Last 30 days** / **Last 90 days** quick buttons, **Refresh** to re-query, **Export CSV** to forward the current filter to the Phase-VI CLI exporter (wiring lands with the CLI integration)
- **Pass rate chart:** Time-series scatter, X = run start time, Y = pass rate %. Visible once the project query returns at least one point; otherwise shows "No data".
- **Duration chart:** Time-series scatter, X = run start time, Y = suite duration in seconds. Requires a suite name; otherwise shows "No data".
- **Case heatmap:** Wraps cells left-to-right, one per run, colour-coded by status (green = pass, red = fail, orange = error, grey = skipped) plus a glyph (`✓`/`✗`/`!`/`—`) for accessibility. Hover any cell to see the run timestamp. Requires both suite and case names; otherwise shows "No data".

If the project trend query fails (database offline, corrupt range), the bottom banner shows the error message. Suite and case query failures show their own red banner above the affected chart so it is clear which section failed; the other charts still render normally.

### Block Analysis (before running tests)

1. Select a PLC from the dropdown
2. Select a block from the dropdown
3. Click **Analyze**
4. The three analysis tools update simultaneously (one TIA export, three analyses):
   - **Interface:** All block parameters (Input, Output, InOut, Static, Temp) with types and default values
   - **Boundary Values:** Auto-generated min/max/zero/one values per parameter type
   - **Dependencies:** Called blocks, referenced DBs, referenced UDTs

### Creating a New Test Suite

1. Select a PLC and a block (or run **Analyze** first so the interface is known)
2. Click **New Suite** — the button stays disabled until a block is selected, so you cannot accidentally create an `Unknown_Tests` suite
3. The new suite is **immediately written** to `<projectDir>/.tia-tests/{BlockName}_Tests.json` and appears in the Test Explorer without a project reload
4. The document opens with **one ready-to-edit example test case** wired up with `arrange` / `act` / `assertions` / `watch` so you can see how all four pieces fit together. If you've already run **Analyze**, the example uses the first scalar Input/Output of the block; otherwise it uses generic `Enable` / `Running` placeholders you replace with real names.
5. Switch to the **Visual** editor (form-based master-detail) to add / remove / duplicate test cases through fields and grids — Name, Description, Cycles, Tags, Priority + Arrange-Inputs grid + Assertions grid + Watch list. Edits sync back to the JSON tab in real time, so you can flip between modes freely
6. Click **Save** (`Ctrl+S`) to persist further changes; the file already exists from step 3

### Test Suite JSON Schema

Every `.tia-tests/*.json` file follows the same shape. Top-level fields:

| Field | Type | Required | Purpose |
|---|---|---|---|
| `name` | string | yes | Suite identifier (must match the file name without `.json`) |
| `blockName` | string | yes | Exact TIA block name (case-sensitive) |
| `plcName` | string | yes | PLC/CPU name in the TIA project (e.g. `PLC_1`) |
| `config` | object | yes | Connection + transport settings (see below) |
| `testCases` | array | yes | One entry per test case (see below) |

`config` (all fields optional, defaults shown):

| Field | Default | Purpose |
|---|---|---|
| `cycles` | `1` | Default PLC cycles per test case (overridable per case via `act.cycles`) |
| `cycleWaitMs` | `100` | Wait between sampled reads when `cycles > 1` |
| `timeoutMs` | `5000` | Hard timeout per test case |
| `instanceDbName` | `""` | Instance-DB to read/write; empty → `<blockName>_DB` (Siemens convention) |
| `preferFc` | `false` | Tolerate FC blocks (no Instance-DB); set when the target is a function instead of a function block |
| `transport` | `"s7CommPlus"` | `"s7CommPlus"` for real PLC / TCP-PLCSIM, `"plcSimApi"` for direct PLCSIM Tag-API |
| `s7IpAddress` | `192.168.0.1` | S7 connect target — used **only** when `preparationMode = "external"` (real PLC). For PLCSIM-backed modes (`userPreloaded`, `tiaTcpDownload`) the runner connects to `plcSimIp` instead, regardless of transport |
| `s7Port` | `102` | S7 ISO-on-TCP port. Default `102` matches every Siemens default — change only when the PLC was reconfigured to a non-standard TCP port |
| `s7User`, `s7PasswordKeyId` | `""` / null | Credentials reference (password lives in Windows Credential Manager). Required only when the PLC enforces user authentication — most projects leave this empty |
| `plcSimInstanceName` | `"TiaUnitTest"` | PLCSIM Advanced instance name. Used by both transports whenever `preparationMode != "external"` |
| `plcSimIp` | `"192.168.0.100"` | PLCSIM Virtual-Adapter IP. **This is the actual S7 connect target for `s7CommPlus + userPreloaded/tiaTcpDownload`** — set it to the IP you assigned to the Siemens PLCSIM Virtual Ethernet Adapter, not to the PLC project IP |
| `preparationMode` | `"userPreloaded"` | `userPreloaded` (default; assumes the PLCSIM instance is already running with your project loaded), `tiaTcpDownload` (compiles + downloads from the open TIA project — see prerequisites below), or `external` (real PLC; uses `s7IpAddress`) |
| `masterSecretPasswordKeyId` | null | Project master-secret password reference. Required for `tiaTcpDownload` only when the TIA project uses confidential PLC configuration protection. Password lives in Windows Credential Manager |
| `autoConnectS7` | `true` | Auto-connect S7 before run starts. Set to `false` only in advanced setups where another client (WinCC, custom HMI) already holds the session and the runner should read/write through it |
| `keepInstanceAfterRun` | `false` | Keep PLCSIM instance alive after the run. Has effect **only** in `tiaTcpDownload` mode — `userPreloaded` and `external` never manage the instance lifecycle |

Each entry in `testCases`:

| Field | Type | Required | Purpose |
|---|---|---|---|
| `name` | string | yes | PascalCase scenario name (e.g. `Start_FromIdle_Runs`) |
| `description` | string | no | One-sentence what-and-why |
| `arrange.inputs` | object | yes | `{ "MemberName": value, … }` — written to the DB before Act |
| `act.cycles` | int | no (defaults to `config.cycles`) | PLC cycles between Arrange and Assert; **must be > 1 for `watch[]` to fire**. Mutually exclusive with `act.steps` (the schema's `oneOf` rejects both on the same `act`) |
| `act.timeoutMs` | int | no (defaults to `config.timeoutMs`) | Per-case timeout. Covers the entire `steps` sequence end-to-end when `steps` is set |
| `act.steps` | array | no | Optional ordered sequence of `write` / `wait` / `assert` steps that runs *between* Arrange and the top-level `assertions`. See **Multi-phase Steps** below. Mutually exclusive with `act.cycles` |
| `assertions` | array | yes | `[ { "variable": "X", "operator": "equal", "expected": v, "tolerance": t? }, … ]` |
| `watch` | string[] | no | Variables sampled once per cycle during Act → Variable Timeline chart in the Results panel |
| `tags` | string[] | no | Free-form labels |
| `priority` | string | no | `"low"` / `"normal"` (default) / `"high"` |
| `requirements` | string[] | no | Traceability links |
| `order` | int | no | Stable sort key in the UI |

Supported `operator` values: `equal`, `notEqual`, `greaterThan`, `lessThan`, `inRange` (expects `expected: [min, max]`), `isTrue`, `isFalse`. `tolerance` is meaningful only on `Real`/`LReal` with `equal`/`notEqual` (default `0.0001`). `expected` is required by the schema for every assertion (set it to any value — `false`, `true`, `0` — for `isTrue`/`isFalse`, since the runner ignores it).

> **Safety — example values are placeholders.** When `BuildExampleTestCase` cannot infer real Input/Output names from `Analyze`, the seeded example uses safe defaults (`Enable: false`, `Running: false`) so a one-click Run cannot accidentally activate motors, valves, or other outputs on real hardware. Always review every `arrange.inputs` value and every assertion before pointing the runner at a real PLC.

> **Important — `watch[]` is the test case's diagnostic array, NOT the TIA Watch Table.**
> Variables listed in `watch` are sampled once per PLC cycle during the Act phase (provided `act.cycles > 1`) and rendered as a time-series chart in the Results panel. This is independent of TIA Portal's external Watch Table or any OPC UA subscription.

#### Complete example

A full minimal suite with one test case that exercises every block and uses `watch[]`:

```json
{
  "name": "FB_Motor_Tests",
  "blockName": "FB_Motor",
  "plcName": "PLC_1",
  "config": {
    "cycles": 1,
    "timeoutMs": 5000,
    "instanceDbName": "FB_Motor_DB",
    "transport": "s7CommPlus",
    "s7IpAddress": "192.168.0.1",
    "s7Port": 102,
    "autoConnectS7": true,
    "preparationMode": "userPreloaded"
  },
  "testCases": [
    {
      "name": "Start_FromIdle_RunsWithinThreeCycles",
      "description": "Asserting Run goes high after StartCmd is set; watch shows trajectory.",
      "arrange": {
        "inputs": {
          "StartCmd": true,
          "Reset":    false,
          "Speed":    50.0
        }
      },
      "act": { "cycles": 5 },
      "assertions": [
        { "variable": "Run",       "operator": "equal",     "expected": true },
        { "variable": "Speed_Act", "operator": "inRange",   "expected": [49.5, 50.5] },
        { "variable": "Error",     "operator": "isFalse", "expected": false }
      ],
      "watch": ["Run", "Speed_Act", "StartCmd"],
      "tags": ["happy-path", "smoke"],
      "priority": "normal"
    }
  ]
}
```

After the run, the Results panel shows pass/fail per assertion and a Variable Timeline chart for the three `watch` variables across the 5 cycles. To add more variables to watch on an existing case, append to the `watch` array and increase `act.cycles` to the smallest number that gives useful coverage (3-10 is typical).

#### Multi-phase Steps (`act.steps`)

When a single Arrange-then-Assert is not enough — for example *reset → wait → start → wait → check* — use `act.steps` instead of `act.cycles`. Three step types are available:

| `type` | Required fields | Effect |
|---|---|---|
| `"write"` | `inputs` (object, same shape as `arrange.inputs`) | Writes the listed members **additively** on top of whatever is already in the DB. Members not listed keep their value. |
| `"wait"` | `ms` (int, `0`..`3 600 000`) | Async delay. The PLC keeps cycling. When `watch[]` is non-empty and `config.cycleWaitMs > 0`, watched variables are sampled once every `config.cycleWaitMs` ms throughout the wait window. |
| `"assert"` | `assertions` (array, same shape as the top-level `assertions`) | Per-step checkpoint. A failure aborts the case immediately and reports `Step <N> (assert): <reason>` (1-based). |

**Order of operations:**

1. `arrange.inputs` is written once at case start (not replayed between steps).
2. Each entry in `steps` runs in declaration order.
3. After the last step, the **top-level** `assertions[]` runs as a final gate. Per-step asserts and top-level asserts are independent — both must pass. The schema requires `minItems: 1` on the top-level `assertions`, so author at least one trivial top-level assertion even when relying mainly on per-step asserts.
4. `watch[]` continues to sample throughout every `wait` step (under the conditions above); the time-series chart annotates step boundaries.

**Caps (enforced by the runner):**

| Limit | Value |
|---|---|
| Steps per case | `1024` |
| Inputs per `write` step | `256` |
| Assertions per `assert` step | `256` |
| `wait.ms` | `0`..`3 600 000` (1 hour) |

**Visual editor:** the case detail view shows a **Steps (optional)** section with **+ Write**, **+ Wait**, **+ Assert** buttons to append, per-step **↑ / ↓** buttons to reorder, and **−** to remove. The editor automatically omits `cycles` from the serialized JSON whenever the Steps section is non-empty (the schema rejects the `cycles + steps` combination, so the editor avoids ever producing it).

**Backwards-compatibility:** a case without `steps` runs the existing single-phase `cycles`-based path with no behavioural change. Older suites need no migration.

##### Complete example — timed motor start

`StartCmd` is set after a 500 ms reset window, then we wait 2 s for the FB to reach `Run`, plus a final speed check.

```json
{
  "name": "MotorStart_ReachesRun",
  "description": "Reset, wait, start, wait, check Run.",
  "arrange": { "inputs": { "Enable": true } },
  "act": {
    "timeoutMs": 10000,
    "steps": [
      { "type": "write", "inputs": { "Reset": true } },
      { "type": "wait",  "ms": 500 },
      { "type": "write", "inputs": { "Reset": false, "StartCmd": true } },
      { "type": "wait",  "ms": 2000 },
      { "type": "assert", "assertions": [
          { "variable": "Run", "operator": "isTrue", "expected": true }
        ]
      }
    ]
  },
  "assertions": [
    { "variable": "Speed_Act", "operator": "greaterThan", "expected": 1000 }
  ],
  "watch": ["Run", "Speed_Act"]
}
```

If the per-step `assert` fails (for example `Run` did not go true within 2 s), the runner emits `Step 5 (assert): variable Run is not true` and aborts the case. If the per-step asserts all pass but the top-level `Speed_Act > 1000` fails, the case fails with the top-level assertion message.

When in doubt, write a plain Arrange + `cycles ≥ N` + Assert case first. Convert it into a `steps` sequence only when the plain form cannot express the timing the test actually depends on.

### Opening an Existing Suite

- **From Test Explorer:** Double-click the suite in the tree
- **From menu:** **Open Suite** button in the toolbar → file picker

### Where are test suites stored?

Test suites live in a hidden folder called `.tia-tests` directly next to your TIA project file (`*.ap21`, `*.ap20`, …). When you click **Open Suite**, the dialog opens at that folder; the AI assistant writes to the same folder. If you haven't opened a TIA project yet, the Test Explorer shows "No TIA Project connected" and Open Suite is disabled — connect a project first.

The AI can read, list, and edit these test-suite files directly through the chat interface.

### Running Tests

1. Make sure PLCSIM Advanced V3.0+ is installed
2. Open the suite (via Test Explorer or Open Suite button)
3. Click **▶ Run** in the toolbar, or use a context menu action from the Test Explorer
4. Watch the live progress in the status bar and Results panel
5. When the run is complete, status icons in the Test Explorer update and results are persisted to SQLite

The runner automatically:
- Creates a PLCSIM Advanced instance (name configurable in the suite JSON)
- Powers it on and compiles the current PLC project
- Connects an S7 client to the instance
- Writes the test inputs, waits the configured cycle count, reads the outputs, evaluates the assertions
- Cleans up the S7 connection and unregisters the instance

### Choosing a Transport

The **Connection Settings** dialog lets you pick how test reads and writes travel between the app and the PLC:

- **PLCSim Advanced** — Direct access via the Siemens PLCSim API, faster and does not need an active S7 session. Best for simulator-only testing.
- **S7 Native** — Uses the S7 Communication driver over TCP/IP. Pick this when you want to run the tests against real hardware (in combination with the **Real PLC** preparation mode) or against PLCSim through the virtual Ethernet adapter with user authentication. Same protocol label as the PLC Online tab.

Both transports expose their own configuration section in the same dialog, so each suite can be targeted independently. For S7 Native, the suite owns its IP, TCP port, username, and password — no cross-tab lookup from the PLC Online view. Rack and slot are not configurable: S7-1200/1500 connect via the S7CommPlus protocol with a fixed routing handshake, and TLS is unconditional on every connection — both are taken care of by the transport.

### Simulation Workspace

Inside the Unit Testing tab, a **Simulation** sub-mode switcher at the top lets you toggle between the Test Suites view and a dedicated **Simulation** view for managing PLCSim Advanced instances. The Simulation view shows:

- API version, online-access mode (PLCSim / TCP/IP single / TCP/IP multi), strict motion timing toggle, and Runtime Manager Port.
- A **Virtual Adapter** row showing the permanent status of the Siemens PLCSIM virtual Ethernet adapter (Ready / APIPA / Disabled / Not Installed / No IPv4), its IPv4 address, and a refresh button. If the adapter is stuck in the 169.254.x.y APIPA range, downloads will be unreliable — assign a static IPv4 address in Windows network settings.
- Every registered PLCSim instance with inline action buttons: Power On, Run, Stop, Memory Reset, Power Off, Settings, Network, Delete. Each row shows the configured IP address; if the instance has more than one interface with an IP, they are listed as `X1: 192.168.0.1, X2: 10.0.0.5`.
- A **TIA PLC** combobox per instance card: pick the TIA Portal PLC that backs the instance. Use this when the PLCSim instance was loaded with a snapshot compiled from a different TIA PLC than the one it is registered under (for example: an instance named `PLC_2` actually holding the program from `PLC_1`). Without an explicit choice, the app matches by name and falls back to the only PLC in the project when there is one — which is enough for most setups but produces an empty tag tree when the names disagree. The choice is remembered per instance.
- A **New Instance** button that prompts for a name and CPU type.
- A **Tag Browser** pane that connects to any listed instance and shows all tags the running program exposes, filterable by name search, area (Input / Output / Marker / Data Block), and data type. Auto-refresh can be toggled for live value observation. Each writable tag has a **pencil button** that opens a type-aware write dialog (toggle for Bool, numeric input with type-specific range for integers and floats, one-character field for Char/WChar). String tags are read-only. Struct tags and array tags are listed with their inner members and elements as expandable rows so you can search, watch and edit individual fields like `OUT[5]` or `DI10.Channel` directly; **Expand all** and **Collapse all** toolbar buttons toggle the whole tree at once. Structured input/output tags whose layout comes from a project type definition (for example a `PNPN` block at `%I0.0` declared as `Array[0..63] of Byte`) drill down into named member rows when the app is connected to the TIA Portal project that defines them — letting you write `IN.PNPN[12]` from the same dialog that handles the rest of the tree.
- A **Saved Instances** section at the bottom listing every PLCSim Advanced instance persisted on the virtual SIMATIC memory card. The heading shows a counter with the total number of saved instances; the list shows up to three rows at a time and scrolls if there are more so the simulation area above stays visible. Click **Load** to re-register and resume one — PLCSim picks up the stored CPU type, I/O image and program automatically. Click **Delete** (with confirmation) to remove the persisted folder.

The sub-mode choice is remembered between sessions, and switching modes keeps any open suite documents intact.

### PLCSIM Preparation Mode

The **Connection Settings** dialog has a preparation-mode selector that controls how the runner brings your project online before the test run:

- **I load it myself (recommended)** — The runner expects a PLCSIM instance that you have already started and loaded manually via TIA Portal. It skips compile and download and connects directly to run the tests. Fastest option if you're iterating on the same project.
- **Automatic TCP download** — The runner compiles the project, starts a fresh PLCSIM instance and downloads via TCP over the PLCSIM Virtual Adapter. No manual TIA Portal interaction needed — just click Run.
- **Real PLC (no PLCSim)** — Skips the PLCSim lifecycle entirely. The runner connects S7 Native directly to the live S7 hardware at the IP and TCP port you configured and runs the tests there. **Use only when the plant is in a safe test state.** Selecting this mode hides the PLCSim section and locks the transport to S7 Native; PLCSim API is incompatible.

**Before using Automatic TCP download:** Four prerequisites must be met or the run will fail with a generic transport error: (1) the **PLCSIM Virtual Adapter** must be installed and have a static IPv4 address that matches the suite's `plcSimIp` (the Simulation tab shows the adapter's current status); (2) the TIA Portal **project must be open** in TIA Portal — the runner triggers a compile against the open project before the download; (3) if the project enables **Protect confidential PLC configuration data**, you must enter the master-secret password in Connection Settings (it lives in the Vault); (4) any existing PLCSIM instance with the same name is **destroyed and recreated** for every run, so other applications attached to that instance lose their session.

### Running Tests Against a Real PLC

Picking **Real PLC** in the preparation-mode selector enables tests against live S7-1200 / S7-1500 hardware without any PLCSim involvement:

1. Make sure the plant is in a **safe test state** — actuators isolated or interlocked, no production load on the PLC, operators informed.
2. Open **Connection settings…**, choose **S7 Native** as the transport, enter the PLC's real IP address and (if the PLC was reconfigured to a non-standard TCP port) the port; supply user/password if the PLC enforces authentication.
3. Switch the preparation mode to **Real PLC (no PLCSim)**. The PLCSim section disappears.
4. Click **OK**, then **▶ Run**.
5. Before the runner contacts the PLC, an acknowledgement dialog appears: *"Run tests against live PLC?"* Read the warning, tick **"I understand — the plant is in a safe test state."**, then click **Run tests**. The button stays disabled until the checkbox is ticked. Cancel aborts the run with no network traffic.

Safety blocks (F-CPU FBs marked with the safety attribute) are still hard-blocked in this mode — the runner refuses to start any test that targets a Safety block, regardless of preparation mode.

If the run fails immediately with **"S7 connection succeeded but access denied — verify username/password"**, the PLC accepted the TLS handshake but rejected the credentials. Re-check the user/password on the Connection Settings dialog and confirm the matching entry under **Vault → S7 Password**. The runner now reports this at connect time instead of letting the test fail later with a misleading "tag not found".

**Batch runs and Real PLC suites:** When you click **Run All** or otherwise trigger a batch run that contains one or more suites configured for **Real PLC** mode, those suites are skipped (the per-suite acknowledgement dialog cannot be rendered from a batch). The Test Explorer shows a dismissible banner naming the skipped suites; open each affected suite and click **Run** individually to walk through its acknowledgement dialog. Skipped suites are no longer counted as failures in the batch summary.

**CPU operating-state gate:** Real PLC runs probe the CPU's operating state right after connect. If the CPU is in **Stop**, **StartUp**, **Hold**, **Defect** or any other non-RUN state, the runner aborts immediately with `Cannot run tests against real PLC: CPU is in <STATE>, not Run. Switch the CPU to Run before retrying.` This prevents the runner from writing to DB memory while the user program isn't executing — which would otherwise cause every test to read residual data and report misleading PASS/FAIL outcomes. Set the CPU to RUN (TIA Portal Online & Diagnostics, or the CPU mode-selector switch) and click Run again.

### Running Against a Protected Project

If your TIA project has **"Protect confidential PLC configuration data"** enabled, the automatic TCP download mode shows an extra password field in the Connection Settings dialog:

1. Open **Connection settings…**
2. Select **Automatic TCP download** under PLCSIM preparation
3. Enter the project's master-secret password
4. Optional: tick **Remember password** to store it in the Windows Credential Manager, so every future run picks it up automatically without asking again. Leave unticked to use the password once and forget it after the run
5. Click **OK**, then **▶ Run**

A hint *"A password is stored for this user"* appears on the next dialog opening if you saved the password. Leave the password field blank to keep the stored value. Unticking **Remember password** and clicking OK deletes the stored entry.

The password is never written to the suite file, to any log, or to any settings file. It lives only in Windows Credential Manager under the service name `com.tiaopennessmanager` and is transferred from the UI to the runner through a user-bound DPAPI channel so a different Windows account cannot read it.

### Managing Suites and Test Cases

- **Right-click a test suite** in the Test Explorer to rename or delete it. Deleting also removes the test run history for that suite.
- **Right-click a test case** to edit its name or description, duplicate it, delete it, or move it up or down in the list.
- The **Connection settings…** button in the toolbar lets you configure the transport, PLCSim instance (selectable from the Simulation view's registry or typed by hand), IP address, cycle wait time, S7 Comm+ target (IP, port, rack, slot, TLS, user, password), and auto-connect behaviour for the active suite. Tick *Save as default* to apply the same values to newly created PLCSim suites. The dialog has a **Manage…** button on the PLCSim section that jumps to the Simulation sub-mode so you can create or tweak an instance without losing your current edits.
- **Connection Settings are saved per suite.** Clicking **OK** writes your choices — transport, instance name, IP, S7 connection details and every other field — back into the suite file. The next time you open the suite, the dialog shows exactly what you picked last, instead of snapping back to defaults. Passwords continue to live in the Windows Credential Manager — the suite file only stores a reference, never a plaintext password.
- Before running, the manager checks that every variable name in your suite exactly matches the block interface, including case. If any mismatches are found, a warning dialog shows the suggested corrections — you can still continue the run after acknowledging it.
- When a test case fails, the affected variable is **underlined in red** directly in the generated SCL code, with the error message shown on hover. **Double-click a failed test case** in the Results panel to jump straight to that variable in the suite editor.
- If a suite file is modified externally — or by one of the Rename / Delete / Edit commands above — the open editor automatically reloads, unless you have unsaved changes, in which case your edits are preserved.

### Troubleshooting

- **Status icons don't update after a run:** Make sure the suite file path is correct (absolute path under `.tia-tests/`). New unsaved suites get a unique path per click.
- **"Run" button greyed out:** A TIA project must be open, and the active suite document must be valid JSON.
- **Test Explorer is empty:** The working directory has no `.tia-tests/` folder yet. Click **New Suite** to create the first one — the folder is created automatically.
- **PLCSIM errors:** Check that PLCSIM Advanced V3.0+ is installed and licensed. The exact version is auto-detected at runtime.
- **Capture the TLS traffic for support (advanced):** If support asks for a Wireshark capture of the S7 Comm+ handshake, set the `SSLKEYLOGFILE` environment variable to an absolute file path before starting the app — for example `setx SSLKEYLOGFILE "C:\Temp\s7-keys.log"` — then restart. Point Wireshark's TLS preference *(Pre)-Master-Secret log filename* at the same file. A warning is written to the app log on every connection while this is enabled so you don't forget to unset it. Leave the variable empty in normal operation.

### AI-Authored Test Suites (Enterprise)

AI Chat can draft, refine and (optionally) run full SCL unit-test suites for you. Requires an Enterprise license.

#### Write Unit Tests skill (main chat)

1. Open **AI Chat** and pick the **Write Unit Tests** skill from the skill picker (🧪 icon), or simply ask: *"write unit tests for FB_MotorControl"*
2. The assistant reads the block interface, computes boundary values, plans test cases and summarises the plan in the chat — no giant JSON blobs
3. When it's ready to write the suite, an **Approve** / **Deny** prompt appears inline. Approve to let the assistant save the suite to `.tia-tests/`
4. If you asked the assistant to also run the suite, a second approval prompt appears for the run itself. Results come back as a pass/fail summary in the chat, and the assistant offers to refine any failing cases
5. The Test Explorer picks up the new suite automatically — open it, review it in the Visual or JSON editor, and run it yourself whenever you want
6. You can also ask the assistant to *"open that suite"* after it's been created — the suite opens as a new tab in the Unit-Testing editor without you having to switch to the Test Explorer

#### Inline chat in the suite editor (Ctrl+I)

While a test suite is open in the JSON editor:

1. Place the cursor near the test case you want to change (or select a range)
2. Press **`Ctrl+I`** — a small prompt box appears above the editor
3. Type what you want, for example:
   - *"add an overflow test for Counter_Value"*
   - *"make this test parametrized with five speed setpoints"*
   - *"tighten the tolerance on all REAL assertions to 0.01"*
4. The assistant streams the updated JSON and a diff overlay appears in the editor
5. Click **Accept** to apply the change (the file is saved and the Test Explorer reloads) or **Reject** to discard

The inline chat uses the same block interface the suite was opened with, so variable names and types are validated against the real block — mismatches are caught before you save.

#### AI badge in the Test Explorer and Visual editor

TestCases authored by the AI carry a small **AI** tag that appears:
- next to the test case name in the **Visual editor**
- in the **Test Explorer** tree

Review AI-authored test cases just like you would a colleague's pull request — read each assertion, sanity-check expected values, then run on the simulator before pointing it at real hardware.

#### Safety (F-CPU) protection

AI test authoring is gated for Safety blocks:

- **Creating tests** — The assistant refuses to author tests for an F-CPU block without an explicit, in-conversation confirmation from you. The underlying tools also reject the write if the confirmation is missing
- **Running tests** — The assistant **cannot run** tests against Safety blocks. Full stop, no override. Safety-block verification requires a certified methodology (TÜV/CE), not an AI-generated run. If you want to run a test against a Safety block, trigger the run yourself from the Test Explorer

#### Licensing

The Write Unit Tests skill and the unit-test MCP tools are Enterprise-only. On Basic or Professional tiers, the skill surfaces an "Enterprise required" message before any AI call is made.

---

## 10. Project Library Management

The Project Library stores reusable items (Master Copies and Types) that can be shared across the project.

### Available Operations

#### 1. Copy to Library (Create Master Copy)

1. Right-click a block in the PLC tree
2. Select **"Copy to Library"**
3. Creates a Master Copy of the selected block in the Project Library
4. The copy can later be instantiated in any PLC

#### 2. Instantiate from Library

1. Right-click a Master Copy in the Library tree
2. Select **"Instantiate to Project"**
3. Creates a new block in the PLC from the Master Copy
4. The original Master Copy remains unchanged

#### 3. Export Type Version

1. Right-click a Library Type
2. Select **"Export Type Version"**
3. Exports the latest committed version to an XML file

**Note:** Only committed versions can be exported; InWork versions cannot be exported.

#### 4. New Folder

1. Right-click Master Copies folder, Types folder, or any library sub-folder
2. Select **"New Folder"**
3. Creates a new organizational folder

#### 5. Rename

1. Right-click a Master Copy, Library Type, or folder
2. Select **"Rename"**
3. Allows changing the name of the selected item

#### 6. Delete

1. Right-click a library item
2. Select **"Delete"**
3. Permanently removes the item from the library (with confirmation)

#### 7. Clean Up Library

1. Right-click the "Project Library" root
2. Select **"Clean Up Library"**
3. Removes unused types and versions to keep the library organized

### Known Limitations

- Master Copies cannot be exported to XML files (Siemens API limitation)
- Only committed Library Type versions can be exported (not InWork versions)

### MCP Integration (AI Assistants)

Library Master-Copy / Type operations are exposed to AI assistants only through the project-tree context-menu actions described above. There are currently no dedicated `library_*` MCP tools — AI clients can read library contents via the standard project-resource (`tia://project`) but cannot create, instantiate, rename, delete, export, or clean up library items through MCP.

---

## 11. Hardware Tab

The Hardware Tab provides a comprehensive overview of all devices in your TIA Portal project with the ability to view and edit network configuration.

### Device List

The tab displays a table with all hardware devices:

| Column | Description | Editable |
|--------|-------------|----------|
| Device | Device name from project | No |
| Device Type | PLC, HMI, Drive, Switch, etc. | No |
| PROFINET Name | PROFINET device name | Yes |
| Article Number | Siemens order number | No |
| Firmware Version | Current firmware version | No |
| IP Address 1-4 | Up to 4 IP addresses per device | Yes |
| Input Addresses | I/O input address range | Yes |
| Output Addresses | I/O output address range | Yes |

### Actions

**Refresh Hardware:**
Reloads the device list from the TIA Portal project.

**Export to CSV:**
Exports the complete hardware list to a CSV file for documentation or further processing.

**Save Changes:**
Saves modified PROFINET names, IP addresses, and per-card I/O start addresses back to the TIA Portal project.

If you close the application or disconnect from TIA Portal while you still have unsaved hardware changes, the application asks whether to save them, discard them, or cancel the close/disconnect.

### Cards Pane

Selecting a station in the device grid loads the cards belonging to that station into a second grid below. Each row shows one card with its slot, name, article number, and the input and output address ranges as **Start / End / Length** bytes — the same byte units shown in TIA Portal Device-View, so a card displayed as `I 160...223` in TIA Portal also shows as Input Start `160`, Input End `223`, Input Length `64` here. Only the Input Start and Output Start columns are editable; End and Length are read-only and update automatically as you edit Start. Edits are tracked alongside the station-level changes — Save Changes writes both back to TIA Portal in one operation, and discarding rolls them back. Refresh reloads the stations grid and the cards pane together so any changes made elsewhere in TIA Portal show up in both views.

### Supported Device Types

- S7-1200/1500 PLCs
- WinCC Unified HMI Panels
- WinCC Comfort Panels
- SINAMICS Drives
- SCALANCE Switches
- ET 200 distributed I/O
- Other PROFINET devices

### Notes

- Changes to PROFINET names and IP addresses require the project to be saved afterward
- Some fields may be read-only depending on device type
- WinCC Unified devices are fully supported

---

## 11a. Hardware Simulation

The Hardware Simulation tab drives simulated tag values into a running PLCSim Advanced instance so PLC logic can be exercised against varying inputs without physical hardware. Available on Trial and Enterprise plans; the tab shows a "license required" overlay on Basic and Professional plans.

### Opening

Open the Hardware Simulation tab from the activity bar on the left. The workspace contains a toolbar at the top and four dockable panels: Device Panel, Override List, Linker Rules, and Function Editor.

### Connect to PLCSim Advanced

1. In the toolbar, pick a PLCSim Advanced instance from the **Instance** dropdown.
2. (Optional) Select the matching TIA Portal PLC from the **TIA PLC** dropdown so topology names resolve correctly.
3. Click **Connect**. The status text shows the established transport.
4. Click **Reload topology** to populate the Device Panel with the hardware modules and tag tree from TIA Portal.

### Engine and tick interval

The simulation engine runs all configured functions on a periodic tick. Use the **Tick** slider in the toolbar to choose an interval between 10 ms and 1000 ms. Start, Pause, and Stop buttons control the engine; the current state is shown in the status text.

### Sim functions (Function Editor)

Right-click in the Function Editor tab to add a new function or double-click an existing row to edit it. Each function drives one tag and is one of:

- **Constant** — Writes a fixed value every tick.
- **Ramp** — Linear sweep between two values over a configurable duration.
- **Sine** — Sine wave with amplitude, offset, frequency and phase.
- **Square** — Square wave with high level, low level and frequency.
- **Triangle** — Triangle wave with amplitude, offset and frequency.
- **Random** — Random value in a [min, max] range each tick.

Each kind displays a waveform icon in the dropdown so the shape is recognisable at a glance. The dialog autofills the data type from the selected tag. Use the tag picker on the right to browse the topology and select a tag; the picker covers hardware-channel tags, marker tags, system tags and data-block variables.

### Force overrides (Override List)

Force a tag to a fixed value independent of the engine functions. Right-click in the Override List tab to add a new override. An override holds priority over any engine function writing to the same tag; toggle the override active or inactive without removing it.

### Watch list

The Watch List tab shows the live values of selected tags. Use the eye icon in the Device Panel tag tree to add tags to the watch list. Values refresh on each engine tick while the engine is running, and tag-table tags receive live updates the same way hardware-channel tags do.

### Linker rules

A linker rule conditionally writes one tag's value to another tag when a boolean expression evaluates to true. Open the Linker Rules tab to add or edit rules. The tag picker covers IO-area, marker, system and data-block variables. The rule editor offers two tabs:

- **Guided builder** — Add up to eight conditions with operator, value, and AND/OR combinators between them. Pick the source tag, target tag, and the assignment value.
- **Expression text** — Free-form expression syntax `WHEN <conditions> THEN <target> := <value>` with full IEC-style operators (`=`, `<>`, `<`, `>`, `<=`, `>=`).

The expression text and the guided builder stay in sync — editing one updates the other when the expression parses cleanly.

### F-safety auto-acknowledge

PLCSim Advanced needs manual acknowledgement for forced F-channels after each PLC restart. With a hardware topology loaded, click **Acknowledge F-tags** in the device-panel toolbar to acknowledge all F-channels in one click; **Revoke** undoes it. The acknowledge state is remembered per PLC.

### Disconnect

Click **Disconnect** in the toolbar to release the PLCSim Advanced session and stop the engine. The Watch List, Override List, Linker Rules and Function Editor contents persist across reconnects.

---

## 11b. Find in Project (Cross-Reference Search)

### What it does

The "Find in Project" tab is a project-wide reference search. Type a block, tag, or UDT name and the application enumerates every cross-reference Siemens TIA Portal knows about it across the open project. Results are grouped by source PLC and source block, then by access category (Calls / Reads / Writes / Other), with the exact reference location and source line number for each hit.

Use it to answer questions like:

- "Where is `FB_Motor` called from?"
- "Which blocks read or write the tag `xStartBtn`?"
- "Which blocks reference the UDT `typ_Recipe`?"

### How to open it

| Trigger | Action |
|---------|--------|
| Right-side tabs | Click the **Find in Project** tab in the TIA Manager workspace |
| Keyboard shortcut | Press `Ctrl+Shift+F` from anywhere in the application — the workspace switches automatically and the search box is focused |
| Project tree | Right-click any block node and choose **Find References**; the tab opens pre-populated with that block's name |

### Searching

1. Type a name (or part of a name) in the search box. The search runs after a 250 ms pause so each keystroke does not trigger a full scan.
2. (Optional) Pick a **Scope**: All, Blocks, Tags, or UDTs. The default is All.
3. (Optional) Pick a **PLC** to restrict to a single PLC in multi-PLC projects.
4. Watch the progress bar — it shows how many candidates have been scanned.
5. Double-click any result row to jump to the source block and source line in the SCL editor, or right-click the row for **Open in Editor** and **Copy reference location**.

The search is case-insensitive and diacritic-insensitive: `förder` matches `Förder_DB`, `muller` matches `Müller_FB`, and `GROSSE` matches `Größe_Tag`.

When the search term itself matches a block, tag, or UDT name in the project, that object appears as its own **Definitions** group at the top of the result tree. Double-click the Definition row (or use the right-click menu) to open the block directly.

### Banners and limits

| Banner | Meaning |
|--------|---------|
| Result truncated at 2000 hits | The search found more matches than the cap. Refine your search by adding more characters or narrowing the scope or PLC. |
| Search failed: \<reason\> | The bridge or TIA Portal returned an error (project closed mid-scan, COM disposed, V15-V17 without `CrossReferenceService`). |
| No matches | The search completed and found nothing. |

### Performance and caching

- Recent identical searches are served from a 30-second in-memory cache, so re-typing the same query within that window returns instantly.
- The cache is invalidated automatically when you open or close a project, switch project, or disconnect from TIA Portal.
- Searches run on the bridge process, not the UI thread; you can keep typing or browsing while a long scan is in flight.

### Requirements

The cross-reference service is only stable on TIA Portal V18 and later. On V15–V17 you will see "Find-References requires TIA Portal V18 or later" in the error footer.

---

## 12. Find Unused Blocks

### Function

Find Unused Blocks analyzes your project and finds blocks that are never called.

### Usage

1. Open a project
2. Click **Find Unused Blocks** in the toolbar
3. The analysis starts automatically:
   - Phase 1: Collect blocks
   - Phase 2: Export to XML
   - Phase 3: Build call graph
   - Phase 4: Find unreachable blocks

### Results Window

Results are organized in 8 tabs:

**Standard Blocks:**
| Tab | Content |
|-----|---------|
| Functions (FC/FB) | Unused functions and function blocks |
| Data Blocks (DB) | Unused global data blocks |
| UDTs | Unused user-defined data types |
| Variables/Tags | Unused PLC tags |

**Safety Blocks (marked in red):**
| Tab | Content |
|-----|---------|
| Safety Functions | Unused F_FC/F_FB blocks |
| Safety DBs | Unused F_DB blocks |
| Safety UDTs | Unused safety data types |
| Safety Tags | Unused safety tags |

### Actions

**Selection:**
- **Select All** - Selects all items in current tab
- **Deselect All** - Deselects all items
- **Delete Selected** - Deletes only selected items

**Delete by Category:**
- **Standard Blocks** - Delete all unused FC/FB
- **Data Blocks (DB)** - Delete all unused DBs
- **UDTs** - Delete all unused data types
- **Tags** - Delete all unused tags

**Delete Safety (with warning):**
- **⚠ Safety Blocks** - Delete all unused F_FC/F_FB
- **⚠ Safety DBs** - Delete all unused F_DBs
- **⚠ Safety UDTs** - Delete all unused F_UDTs
- **⚠ Safety Tags** - Delete all unused F_Tags

**Export:**
- **Export to Text** - Exports the list as a text file
- **Copy All** - Copies all items to clipboard

### Settings

Click the **gear icon** in the left toolbar to open the Find Unused Settings dialog.

**Analysis Scope:**

| Setting | Default | Description |
|---------|---------|-------------|
| Include Blocks (FC/FB) | On | Include functions and function blocks in the analysis |
| Include Data Blocks (DB) | On | Include global and array data blocks. Instance DBs are always linked to their parent FB |
| Include UDTs | On | Include user-defined data types. UDTs referenced by used blocks are marked as used |
| Analyze Tags | On | Include PLC tags in the call graph analysis |
| Reuse Existing Exports | On | Reuse previously exported XML files for faster repeated analysis |

**Exclusions:**

| Setting | Description |
|---------|-------------|
| Excluded Patterns | Semicolon-separated wildcard patterns. Items matching any pattern are excluded from results. Use `*` for any characters, `?` for a single character. Example: `FB_Test*;DB_Temp*;FC_Debug*` |

All settings are saved automatically and persist across application restarts.

### Notes

- OBs (Organization Blocks) are never marked as "unused" since they are entry points
- Safety blocks require Safety login for complete analysis
- Deleting safety blocks requires confirmation due to safety implications

---

## 13. Settings

A single Settings window replaces the previous separate dialogs for app settings, Import/Export, Git Preferences and AI Chat. The window has a search bar at the top, a category tree on the left, and the matching settings on the right.

### Opening

- Menu bar: **View → Settings** (or `Ctrl+,`).
- AI Chat input bar: gear icon → opens the window directly on the AI Chat section.
- Import/Export tab: gear icon → opens on the Import/Export section.
- Git repository panel: settings gear → opens on the Git section.

Changes are saved automatically — no Save or Cancel button. A colored accent bar on the left edge of a section indicates that something inside it differs from the values that were loaded when the window opened.

### Categories

| Category | What lives inside |
|----------|-------------------|
| General | UI language, theme (Dark, Light or Midnight mode + accent color), Check-for-Updates at startup. Midnight is a true-black variant tuned for OLED displays. |
| Files & Folders | Log file directory, working folder for import/export, folder-name customization, "Create Source folder" toggle. |
| Import/Export | Import options (ignore structural changes, ignore missing references, fault-tolerant), Export options per type (DBs / UDTs / Tags / Technology Objects / HMI), additional S7-DCL export (V20+), Fingerprint Cache, Version Control normalization. |
| Git | Date format, default clone directory, history limits, appearance fonts, Git user/email/CRLF/fetch, GPG signing, shell and external diff/merge integration, AI commit-message prompt. |
| AI Chat | Agents, Chat Tools, Approvals, Instructions, Templates, Providers, MCP Servers, Memory, Scheduled Tasks, Dictation, Workspace, Storage. |
| Compare | Diff-editor and minimap colors, opacity, and minimap width. |
| Editor | C# language features (off by default — bundled language server, restart required). |
| Logging | Debug Logging toggle. |

### Folder Name Customization (under Files & Folders → Folder Names)

| TIA Portal name | Default export name | Configurable |
|-----------------|---------------------|--------------|
| (Device) | Source | ✓ |
| Program blocks | Blocks | ✓ |
| PLC data types | Datatypes | ✓ |
| PLC tags | Tags | ✓ |
| Technology objects | Technology Objects | ✓ |
| Software units | Software Units | ✓ |

The "Create Source folder" checkbox controls whether exports include a Source wrapper:

| Setting | Export path |
|---------|-------------|
| ✓ Enabled | `WorkingDir/Source/PLC_1/Blocks/...` |
| ☐ Disabled | `WorkingDir/PLC_1/Blocks/...` |

This also affects the project tree structure and import path detection.

### File Explorer — Watcher Excludes (under Files & Folders → File Explorer)

The File Explorer tree skips folders that match the **Watcher Excludes** list when scanning the open working folder. Defaults: `.git`, `.vs`, `.idea`, `bin`, `obj`, `node_modules`, `.claude`, `.worktrees`.

Edit the list to:

- **Hide additional folders** — add one folder name per line (e.g. `dist`, `coverage`, `.next`).
- **Reduce file-watcher noise** — heavy build output (`bin/obj`) can flood the operating-system file-change buffer; keeping these in the exclude list prevents wasted scan work on every build.
- **Restore the default list** — clear the text box; the defaults apply on the next refresh.

Changes take effect when the working folder is reopened or refreshed.

### Editor — Right-click context menu

Right-click anywhere inside a code editor tab to open a menu organised into five groups. Entries that don't apply at the current caret position or selection are hidden, so the menu length follows the available actions:

- **AI assistance** — *Open Inline Chat* (Ctrl+I), *Markdown Preview*, *Add File to Chat*, *Explain* (selection-aware), *Review* (selection-aware).
- **Edit** — *Change All Occurrences* (Ctrl+F2, renames every match of the word at the caret in the current document after a quick prompt), *Rename Symbol* (F2, language-server-backed rename that follows the symbol across files in the same workspace; only appears when the active server advertises it), *Format Document* (Shift+Alt+F) and *Format Selection* (Ctrl+K Ctrl+F). When a language server with formatting support is attached (e.g. C# via the bundled server) the editor uses its formatter; SCL falls back to the built-in formatter. Format Selection only appears when the active server supports it and the editor has a selection.
- **Navigation** — *Go to Definition* (F12) and *Find References* (LSP-backed; both appear when the open file's language server advertises the capability).
- **Git** — *Show File History* (Alt+H) switches the activity bar to Version Control, opens the file's repository tab, and lists every revision that touched the file. Files outside a Git repository show a brief status hint instead.
- **Clipboard** — *Cut* (Ctrl+X), *Copy* (Ctrl+C), *Paste* (Ctrl+V), *Select All* (Ctrl+A).

Keyboard shortcuts continue to work without opening the menu — the entries simply expose the same actions for discoverability.

### Editor — C# Language Features

Under **Settings → Editor**, the **Enable C# language features** toggle attaches a bundled language server to `.cs` files opened from the File Explorer. When enabled, the editor:

- Underlines compiler errors and warnings with squiggles inline while you type.
- Lists every diagnostic across all open `.cs` files in the new **Problems** tab at the bottom of the workspace (next to Log Output, Terminal, Git Output). Click a row to jump to the location.
- Surfaces the language server status (starting, ready, restarting, disabled) as a banner above the Problems list.
- Shows a documentation tooltip with type, signature and XML comments when you rest the pointer over a symbol.
- Jumps to a symbol's definition when you press **F12** or **Ctrl+Click** on it; multiple matches open a small picker so you can choose one.
- Lists every call site of a symbol when you right-click the symbol and choose **Find References**. Results appear in a new **References** tab at the bottom of the workspace (file, line, preview). Click a row to jump to the location. The menu entry is hidden when no language session has been negotiated for the current file.
- Shows a small popup with the method signature, including a highlighted active parameter, when you type `(` or `,` inside a call. Press **Escape**, click elsewhere or move the caret out of the call to dismiss it.
- Offers member and symbol suggestions in a completion list as you type. The list opens after the second character, sorts by relevance and dedupes by name. Arrow keys navigate, **Enter** or **Tab** inserts the highlighted entry. SCL, AWL and other Siemens block formats keep their existing keyword-and-word completion; only `.cs` files use the bundled language server's suggestions.
- Offers quick-fixes for diagnostics under the caret. A small lightbulb appears in the editor margin at the caret line when fixes or refactorings are available; click the lightbulb or press **Ctrl+.** to open the action menu. Picking an entry applies the change as a single undoable edit, with the result reported in the status bar (Applying… → Action applied / No quick-fixes available / Could not apply action / Could not load action details).
- Renames a symbol and every reference to it across the workspace through the language server. Place the caret on the identifier and press **F2** (or right-click → **Rename Symbol**); type the new name in the inline overlay and press **Enter** to apply or **Escape** to cancel. The status bar reports Renaming… → Renamed N occurrences across N files / Document changed during rename / Invalid identifier / Rename failed. If the document is edited while the rename is in flight, the change is abandoned and the editor keeps its current state.
- Formats the whole document (**Shift+Alt+F**) or the current selection (**Ctrl+K Ctrl+F**) through the language server. The status bar reports Formatting… → Formatted / Document is already formatted / Format failed / Document changed during formatting. When no language server is bound or it does not advertise formatting, SCL files keep their built-in formatter and other languages show a short status hint.
- Opens decompiled metadata as a read-only buffer when **F12** lands on a symbol in an external library or generated source. The status bar reports Loading external source… → and a new tab opens with the synthesised source (BCL types, NuGet referenced assemblies, source-generator output). The buffer cannot be edited; **F12** inside it resolves further symbols transitively. URI schemes the language server does not handle still surface a short notice.
- Refreshes the Problems panel on demand: a small refresh-icon button in the panel toolbar re-fetches diagnostics for every open `.cs` file in one round-trip. The language server also requests a refresh automatically after package, analyzer or project-state changes, so the Problems list stays current without user action.

The toggle is **off by default** because the bundled language server can consume between 1 GB and 10 GB of memory while indexing very large solutions. Flip it on if you regularly edit C# files in the manager.

**Restart required.** The language server registration is decided at startup, so the change takes effect the next time the application launches.

#### Loading a .NET solution for full IntelliSense

Enabling the toggle alone wakes the language server for single-file features only — you get inline IDE hints (e.g. *Using directive is unnecessary*), syntax colouring, and completion, but cross-file features stay dark: no `CS0246` / `CS0103` compiler errors, no F12 across files, no method-vs-variable distinction in the colouring. To unlock those, the language server has to load a `.sln` (or `.csproj`) so it can build a project graph.

Under **Settings → Editor → C# Language Features**, two additional controls govern solution loading:

- **Load solution automatically** — when on, the language server walks up from the opened `.cs` file to the nearest `.sln`/`.slnx` (and falls back to `.csproj`) and loads it. **Off by default** because loading a solution lets the language server execute analyzer code shipped with the project; only enable this for solutions you trust. After flipping the toggle, restart the application.
- **Explicit solution path** — optional absolute path to a `.sln`, `.slnx`, or `.csproj`. When set, this file is loaded regardless of the auto-load toggle, so you can opt-in for a single trusted solution without enabling walk-up everywhere. Use the **Browse…** button to pick a file. Leave empty to fall back to walk-up search.

With either path active and a project loaded, the editor shows a brief *Project initialization in progress…* status in the Problems panel while the design-time builds finish, then transitions to *Ready*. Cross-file diagnostics, Find References, and metadata-as-source then work as documented above.

C# files keep their normal syntax highlighting, completion, and editing behaviour regardless of these settings; only the live diagnostics and the Problems panel depend on the toggle. SCL, AWL, UDT and other Siemens block formats are unaffected — they use the manager's own editor stack.

### Search

Type into the search box to filter the category tree by section name or by a keyword from a section's descriptive tags. Parent categories stay visible while at least one of their children matches the query.

<!-- feature:eplan start -->
### License

License activation, trial status, hardware ID and the EPLAN add-on are still managed in their own focused window — accessed from the startup prompt, the Trial banner, or the **Manage License** entry-point.

<!-- feature:eplan end -->
### Log Files

When Debug Logging is enabled, detailed logs are created:
- Location: configurable under Files & Folders → Log Directory.
- Format: `TIA_Openness_Log_YYYYMMDD_HHMMSS.txt`

---

## 14. Licensing

### License Tiers

| Feature | Basic (FREE) | Professional (CHF 9.99/mo) | Enterprise (CHF 29.99/mo) |
|---------|--------------|---------------------------|--------------------------|
| Price | Free forever | CHF 9.99/mo or CHF 99.99/year | CHF 29.99/mo or CHF 299.99/year |
| Files per operation | 1 | 1,000 | Unlimited |
| Export/Import | Yes | Yes | Yes |
| Block Compare | Yes | Yes | Yes |
| Code Editor | Yes | Yes | Yes |
| Find Unused | No | Yes | Yes |
| Safety Blocks | No | Yes | Yes |
| Protection Profiles | No | Yes | Yes |
| MCP Server | No | Yes | Yes |
| AI Chat | No | Yes | Yes |
| Project Library | No | Yes | Yes |
| Password Vault | No | No | Yes |
| Unit Testing | No | No | Yes |

### Trial Period

On first launch, you can start a **30-day free trial** with all Enterprise-level features unlocked. After the trial expires, the application falls back to Basic (free) mode.

To start a trial:
1. Click **View → Settings → Manage License**
2. Click **Start 30-Day Trial**
3. All features are available for 30 days

### Activate License (Online)

1. Purchase a subscription (Professional or Enterprise) at https://www.tiaopenessmanager.ch
2. You will receive an activation code via email (format: `ACT-XXXX-XXXX-XXXX`)
3. Open **View → Settings → Manage License**
4. Enter the activation code
5. Click **Activate**
6. The license will be bound to your hardware

**Billing:** You can toggle between monthly and yearly billing in the license dialog. Yearly plans save approximately 17%.

**Important:** The software requires an online license validation **at least every 14 days**. If no internet connection is available, the software can be used **offline for up to 14 days**. After 14 days, a new online validation is required.

### Hardware Binding

Each license is bound to a unique hardware ID generated from:
- CPU ID (Processor Serial Number)
- Motherboard Serial Number
- Primary MAC Address

### Machine Switch Limit

Your license is bound to your **account**, not to a single machine — you can move it between computers without contacting support. The application enforces a rolling limit of **up to 3 different machines per 30-day window**: each new sign-in on a previously-unseen hardware ID counts as one switch. The fourth distinct machine within the same 30-day window is rejected at sign-in time. The window slides — switches that fall out of the past 30 days no longer count against the limit. Sign in on a new machine and the previous machine's binding is released automatically.

The current usage is visible in the License window (see below). When you reach 3/3, an in-panel banner explains the next free slot and when it becomes available.

### License Window

Open the window via **View → Settings → Manage License** (or click the License entry in the main toolbar). The Manage License window now combines two sections in one place:

- **Account & License** (top, visible while signed in) — the same set of rows previously hosted in a separate Settings tab. Use it to review the active subscription and sign out of this machine.
- **Plans & Activation** (bottom, always visible) — the existing Hardware ID display, activation-code field, monthly/yearly pricing cards, and current-plan indicator.

| Row | Meaning |
|-----|---------|
| **Signed in as** | The email address you used to sign in. |
| **Tier** | Active tier — Basic / Trial / Professional / Enterprise. |
| **Status** | Active, Expired, or Validation pending. |
| **Expires at** | The end of the current billing period (Trial: end of the 30-day window). |
| **Hardware ID** | The 16-character ID derived from this machine. |
| **Bound since** | When this machine first activated the license. |
| **Issue date** | When the license was originally issued. |
| **Machine switches** | Switches used in the past 30 days, e.g. *2 of 3 machines used in 30 days*. |
| **Sign out** | Releases this machine's binding. A confirmation dialog ("Sign out and release this machine?") appears first; choose **Sign out** to confirm or **Cancel** to abort. After sign-out the Sign-In dialog re-opens; cancelling that dialog closes the application. |
| **Manage on website** | Opens your account page in the browser to change subscription, view invoices, or transfer the license. |
| **Migrate manually** | Appears only when a local trial signature exists without a bound account, or when an automatic migration attempt has reported a failure. Opens a dialog asking for the legacy 16-character hardware ID under which the trial was originally registered. Recovers DPAPI-corruption and hardware-move cases where the legacy hardware ID can no longer be detected automatically. |

### Manage Subscription

- Click **Manage Subscription** in the License dialog
- Opens the Stripe portal for:
  - Changing payment method
  - Downloading invoices
  - Canceling subscription

### View License Information

In the License dialog, you can see:
- Current license type (Basic/Professional/Enterprise)
- Current period expiry date
- Hardware ID
- Activation code

### Security Alerts

When the app detects an unusual security event, a yellow banner appears at the top of the main window. These alerts stay visible until you dismiss them (click the **×** button) so they are never overwritten by other status messages.

Two event types surface here:

- **Storage integrity warning.** The app could not fully save your license information to the Windows Registry. This is usually a permissions issue on a managed laptop. The app keeps running with your cached license — if the warning appears immediately after activation, try running the app once as Administrator, or contact your IT department.
- **Certificate change warning.** The TLS certificate of `tiaopenessmanager.ch` changed unexpectedly. Your connection is still TLS-protected (otherwise the app would refuse the request entirely), but the change is worth investigating — especially if it coincides with a newly installed corporate proxy. The app continues to work; contact support if the warning does not clear within 24 hours.

Both alerts are informational. Your license stays active while they are visible. The banner automatically disappears the next time the condition clears.

### Trial migration banner

If the app finds a legacy trial on this machine but no account is signed in, a yellow banner at the top of the window invites you to sign in before the deadline. Click **Sign in** in the banner to open the sign-in dialog; once signed in, the trial transfers to your account and the banner is replaced by a "Trial migrated" confirmation. The migration is automatic — there is no manual step beyond signing in.

If the migration fails (server error, expired window, the trial already belongs to a different account), a red banner replaces the original explaining the cause; restart the application and try again, or contact support if the failure persists.

If the automatic migration cannot find the legacy hardware ID (for example after replacing the disk or restoring a Windows backup), open **View → Settings → Manage License** and click **Migrate manually**. Enter the 16-character hardware ID from a backup, a support email, or an old registry export and submit — the manual flow uses the same trial-migration pipeline as the automatic banner, so any failure surfaces the same diagnostic message immediately below the button.

### Account page (browser)

Click **Manage on website** in the License window (or visit `https://tiaopenessmanager.ch/profile` after signing in) to open your browser-based account page. The page covers four operations beyond what the desktop License panel exposes:

- **Profile** — your email, account-creation date, and last sign-in timestamp.
- **Manage subscription** — opens the Stripe customer portal in a new tab to change payment method, download invoices, or cancel.
- **Release this machine** — frees the current machine binding so you can reactivate on a different computer without waiting for the 30-day window. A confirmation prompt appears before the release. The next sign-in on a new machine becomes the new active binding.
- **Delete account** (Danger zone) — permanently deletes your account record, revokes all signed-in sessions, and releases the license. The dialog asks you to type **DELETE** in capitals to confirm. This cannot be undone.

The page is HTTPS-only and requires you to be signed in. After sign-out (from either the desktop app or the page itself), the page redirects you to the sign-in form on the next visit.

**Untrusted Environment (Basic mode)**

If the app detects a debugger attached to its process, or if the main executable is not signed with the expected Certum certificate, the app silently downgrades to Basic tier. This is a defense-in-depth measure against tampering. Release builds always have the correct signature; if you see this behaviour in a normal install, the binary has been modified — reinstall from https://www.tiaopenessmanager.ch.

### Manage Organization License

Volume Pro and Volume Enterprise are multi-seat subscriptions for organizations. The owner (the person who purchased the subscription) manages seats from a web dashboard; team members sign in with their own email and each occupies one seat.

**Owner — Set up the subscription.** Go to https://www.tiaopenessmanager.ch and choose **Volume Professional** or **Volume Enterprise** with the desired seat count (2-200). After Stripe checkout, you receive two emails: a magic-login code for owner sign-in to the desktop app, and an organization confirmation with the org ID and owner role.

**Owner — Invite team members.** After signing in, open the license dialog (**View → Settings → Manage License**) and click **Manage on website**. The web dashboard shows occupied and available seats. Enter a team member's email address and click **Invite** — the team member receives an email with a magic link, valid for 7 days.

**Member — Accept the invitation.** Clicking the magic link opens the web page with the org name and an **Accept** button. After accepting, the account is bound to the organization. In the desktop app, sign in with the same email — the license dialog shows membership with role "Member" and a note that management is handled by the owner.

**Owner — Release a seat.** In the web dashboard, click **Release seat** next to the member row. The seat becomes free immediately and can be reassigned. The former member account falls back to Basic tier (unless they have their own solo subscription).

**Change seat count.** In the Stripe customer portal, you can increase `quantity` at any time — the additional seats are immediately available for invitation. Reductions require enough free seats first; release the right number of seats before lowering `quantity` in the Stripe portal.

<!-- feature:eplan start -->
**Add-ons under the volume model.** The EPLAN add-on can be activated organization-wide — every member inherits access automatically at next sign-in. Owners see this in the license dialog under Add-ons → EPLAN as "Org activated"; members see "Active (Org)" without their own manage button.

### Activate the EPLAN Add-on

The EPLAN add-on is a separately licensed extension for connecting to EPLAN Electric P8. Available for Pro, Enterprise, Trial, and Volume subscriptions.

**Solo activation.** In the license dialog → **Add-ons** section → **EPLAN** card → **Purchase** opens Stripe checkout for CHF 19.99/month or CHF 199.99/year (annual saves 17 %). After payment, the card switches to "Activated"; sign out and back in (or click **Refresh** in the license dialog) to load the new entitlement — the EPLAN tab appears in the left activity bar.

**Volume activation (owner).** In the web dashboard → **Add-ons → EPLAN → Add** opens a Stripe checkout for the organization-wide add-on subscription with `quantity` matching the seat count. After payment, every team member inherits EPLAN access at the next validate cycle.

**Trial accounts.** During the 30-day trial period, the EPLAN add-on is included automatically — no separate activation needed.

**Cancel the add-on.** Solo: end the add-on subscription via the Stripe portal — the EPLAN tab disappears at the next validate cycle. Volume: owner cancels in the web dashboard, all team members lose access simultaneously.

<!-- feature:eplan end -->
---

## 14a. Git Client

The Git Client is a built-in version control interface for managing repositories directly within TIA Openness Manager. It provides a visual Git workflow without leaving the application.

### Activity-Bar Badge

The Git icon in the Activity Bar (left navigation rail) displays a small accent-colored count badge whenever any open repository has uncommitted changes. The badge shows the total number of staged + unstaged + untracked files **summed across all open repository tabs**.

- Values up to 999 render exactly (e.g. `5`, `42`, `999`)
- Values from 1000 to 99,999 render in a compact `K`-format (e.g. `1K`, `10K`, `99K`)
- Values 100,000 and above render as `99K+`
- The badge is hidden when there are no uncommitted changes anywhere

Hovering the Git icon shows a tooltip with the localized count (e.g. *"Version Control (Ctrl+2) — 5 uncommitted changes"*) using the proper plural form for your UI language.

### Opening a Repository

1. Click the **Git** tab in the main navigation
2. On the welcome page, click **Open Repository** and select a folder, or drag a repository folder onto the welcome page
3. Recently used repositories are shown in the list for quick access

**Keyboard shortcut:** Press **Ctrl+Shift+O** anywhere in the Git workspace to open the **Open Local Repository** popup. The popup lets you pick a path, target workspace, and bookmark group in one step — the repository is added to that group on success without needing a separate edit pass.

### Tabs Palette

The **Tabs** icon button next to the workspace selector (or **Ctrl+P** anywhere in the Git workspace) opens a quick-switch palette listing every open repository tab plus recent repositories. Type to filter; press Enter to switch to the highlighted tab; press Escape to close the palette without switching.

### History View

The History view shows the commit graph with branch and tag badges.

**Issue Tracker Links in Commit Subjects**

If your repository is configured with issue tracker rules, commit subject lines automatically display clickable links for matching patterns (e.g. `#123`, `PROJ-456`). Clicking a link opens the corresponding issue page in your browser.

To configure issue tracker patterns:
1. Open the repository settings via the toolbar gear icon
2. Go to the **Issue Tracker** tab
3. Add a rule: enter a regular expression (e.g. `#(\d+)`) and a URL template (e.g. `https://github.com/org/repo/issues/$1`)
4. Choose from built-in presets (GitHub, GitLab, JIRA, etc.) or define a custom rule

### Commit Detail View

Selecting a commit in the History view opens the Commit Detail panel on the right.

The full commit message is displayed with rich formatting:

- **Issue Tracker Links** — References matching your configured issue tracker rules are shown as clickable links. Clicking opens the issue in your browser.
- **URLs** — HTTP(S) and FTP URLs are automatically detected and underlined. Clicking opens the URL in your browser.
- **Commit SHA References** — If the message contains a commit SHA (6–64 hex characters), it is shown as an orange underlined link. Clicking navigates to that commit in the history graph. Hovering shows the commit subject as a tooltip.
- **Inline Code** — Text in backticks (`` `like this` ``) is rendered in monospace with a distinct background.

**Right-click context menu on links:**
- **Copy Link** — Copies the URL to the clipboard
- **Open in Browser** — Opens the URL in the default browser
- **Navigate to Commit** — Navigates to the referenced commit (SHA links only)
- **Copy SHA** — Copies the SHA to the clipboard (SHA links only)

### Working Copy

The Working Copy view shows staged and unstaged changes.

- Stage or unstage individual files or the entire changeset
- Write your commit message and click **Commit**
- Use **Commit Options** checkboxes for Sign-Off, No-Verify (skip hooks), and Reset-Author
- File change states are shown as colored, rounded badges (Modified, Added, Deleted, Renamed, etc.) for quick visual identification
- Right-click any unstaged file for **LFS** operations: Track by filename or extension, and Lock/Unlock. For repositories with multiple remotes, Lock/Unlock shows a submenu per remote

### Branches, Tags, and Remotes

The sidebar on the left shows all local branches, remote branches, tags, worktrees, and submodules. Right-click any item for context menu operations (checkout, merge, push, delete, etc.).

### Command Palette

Press **Ctrl+Shift+P** while working in the Git workspace to open the Command Palette. It provides quick keyboard-driven access to the most common Git operations without navigating menus.

> **Two palettes share Ctrl+Shift+P.** This Git Command Palette is workspace-scoped and lists the 14 Git-only actions below. The global [Quick Open Bar](#3a-quick-open-bar) (also Ctrl+Shift+P, prefilled with `>`) lives in the title bar and routes through prefixes (`>` `@` `#` `git:` `?` `:`). The Git workspace palette takes precedence when the Git tab has focus; in any other tab the Quick Open Bar opens.

**Available commands:**

| Command | What it does |
|---------|-------------|
| Checkout | Switch to a branch |
| Merge | Merge a branch into the current branch |
| Compare | Compare a branch or tag against the current branch |
| Blame | Open the blame view for a file |
| File History | Open the history for a specific file |
| Open File | Open a file from the repository in the editor |
| Create Branch | Create a new branch |
| Create Tag | Create a new tag |
| Fetch | Fetch from a remote |
| Pull | Pull from a remote |
| Push | Push to a remote |
| Stash | Stash current changes |
| Apply Patch | Apply a patch file |
| Configure | Open repository settings |

**Sub-palettes:** Commands that require a branch, tag, or file selection open a secondary picker. Type to fuzzy-filter the list. Press **Backspace** on an empty filter to return to the main palette.

**Closing:** Press **Escape** or click outside the palette to close it.

### Diff Loading Errors

If a revision comparison or a per-file diff fails to load (for example because Git could not enumerate the changes between the two SHAs), an inline error banner appears above the diff pane in the Commit Detail view, the Revision Compare view, and the Submodule Compare window. The previous diff content stays in place; the banner clears automatically as soon as the next selection or comparison succeeds. Technical details (exception type, command output) are written to the application log.

### Submodule Revision Compare

When a commit changes a submodule pointer, the file appears in the Commit Detail view as a **Submodule** entry with the old and new commit SHAs. Clicking **Open Details** on the submodule entry opens a dedicated read-only **Submodule Compare** window. The window shows:

- Two CommitDetail panes side-by-side — the old and new submodule commits with author, date, and message
- A central changes pane that walks the actual changes inside the submodule between the two pointers, with text and binary diff rendering

The window is read-only and never modifies the parent repository or the submodule. Rapid double-clicks on **Open Details** keep a single window — the existing one is brought to the front instead of opening a duplicate.

Keyboard shortcuts on the changed-files list:

- `Ctrl+C` — copy the selected file paths (relative to the submodule root)
- `Ctrl+Shift+C` — copy the absolute file paths
- `Ctrl+F` — focus the search box above the changed-files list

### Submodule Uncommitted Changes Badge

Each submodule in the sidebar now shows an inline badge if the submodule itself has uncommitted local changes (e.g. *"+ 3 uncommitted changes"*). The count reflects what `git submodule status` reports as the trailing `+` marker — uncommitted modifications inside the submodule's own working tree. The badge updates whenever the parent repository or the submodule is refreshed.

### Cloning into a Group with a Bookmark

The **Clone Repository** popup now lets you pick a workspace **Group** and a **Bookmark color** at clone time. On success the cloned repository is inserted as a node in the selected group with the chosen bookmark — no separate edit pass needed. Both fields are optional; leaving them empty places the clone at the workspace root with no bookmark.

### Custom Actions — Argument Format and Branch Selectors

Custom Actions now use a free-form **Argument Format** string instead of a fixed argument list. The format string supports variables that are substituted at run time:

- `${REPO}` — repository root path
- `${BRANCH}` — selected branch name
- `${BRANCH_FRIENDLY_NAME}` — branch friendly name (without remote prefix)
- `${SHA}` — selected commit SHA (when invoked from the History view)
- `${FILE}` — selected file path (when invoked from a file context menu)
- `${REMOTE}` — remote name (when invoked on a remote)
- `${TAG}` — tag name (when invoked on a tag)

A new **Branch Selector** control type feeds `${BRANCH}` and `${BRANCH_FRIENDLY_NAME}`, with separate local-branch and remote-tracking-branch modes. Configure controls via the Custom Action settings dialog (gear → Custom Actions → Configure Controls).

### Stash Diff Toolbar

The Stashes view diff pane includes two toolbar toggles, matching the Working Copy diff:

- **Ignore Whitespace** — recomputes the diff with whitespace-only changes hidden
- **Side-by-Side** — switches between unified and side-by-side diff layout

Clicks while a previous reload is still in flight cancel the in-flight load and start a fresh one — the most recent toggle wins.

### Auto-Fetch

Background auto-fetch is now a single global setting under **Settings → Git → Auto-Fetch** that applies to every open repository. The previous per-repository toggle has been removed and existing per-repo settings are ignored. Adjust the interval (default 10 minutes) under the same setting block. The Git sidebar's auto-fetch indicator is hidden while the setting is off.

---

## 14b. Trace / Signal Visualization

The Trace tab captures OPC UA signal values at a fixed cycle and plots them in real time, similar to a scope. It is the right tool when a number in the Watch Table is not enough and you need to see how a signal changes over time — rising flanks, overshoot, oscillations or drift.

### Opening the Trace Tab

Pick **Trace** in the main tab bar. Before you can record anything you need an active OPC UA session (connect via the OPC UA tab first).

### Adding Signals

Use the signal sidebar on the left:

- **"+ Signal"** opens the OPC UA browser so you can pick a tag from the PLC.
- **"+ Computed"** adds a computed signal whose value is calculated from a formula over the other signals (see below).

Each signal has a checkbox to enable or disable it without removing it from the list, a color swatch, and a delete button.

### Toolbar

| Button | Action |
|--------|--------|
| Start / Stop | Start or stop the trace |
| Mode | **Continuous** keeps the newest samples in a rolling window; **Single trigger** captures a fixed window around a trigger event |
| Cycle time | How often the PLC is polled (100 ms, 200 ms, 500 ms, 1 s, 2 s, 5 s) |
| Window | Time window shown in continuous mode (30 s up to 1 h) |
| Trigger | Configure rising / falling / both edge with threshold plus pre- and post-samples |
| Auto-scale | Toggle automatic y-axis fitting |
| Auto-reconnect | If ON, the trace restarts automatically with the same signals after an OPC UA disconnect |
| Export CSV | Write the recording to a CSV file |

While a recording is running the signal list is read-only. Stop the trace to edit signals, add computed signals or change scaling.

### Plot Interaction (after Stop)

Once a recording is stopped the plot toolbar turns on additional buttons:

- **Pan** — drag to move the viewport
- **Rectangle zoom** — drag a box to zoom into a region
- **Zoom in / Zoom out** — step zoom
- **100 %** — reset both axes to the full recording
- **Fit** — auto-fit the y-axis within the current time window

### Dual Cursors

Click the plot to place cursor **t1**, click again to place cursor **t2**. Further clicks toggle which cursor moves. Drag either cursor to reposition it precisely. Hold **Ctrl** and click anywhere to clear both cursors.

The time difference **Δt** between the two cursors is displayed in the upper-right corner of the plot. Each cursor carries a small **t1** / **t2** badge at the top of the line, and the second cursor also shows the live Δt and ΔY right on the line as you drag it.

The toolbar has a **Show measurement cursors** toggle next to the export button. When you turn it on for the first time after stopping a recording, the cursors auto-place at 25 % and 75 % of the visible time so you see them immediately. Turning the toggle off hides the cursor lines and clears the Y(t1) / Y(t2) / ΔY columns in the signal table — the last cursor positions are remembered and reappear when you turn the toggle back on.

### Signal Table (below the plot)

Every signal gets a row with the following editable columns: **Name**, **Formula**, **Format** (Decimal / Hex / Binary / Bool / Scientific), **Line** (Linear or Step), **Min Y**, **Max Y** and **Scaling group**. Edits take effect live — no trace restart needed. The right-hand columns **Y(t1)**, **Y(t2)** and **ΔY** show the interpolated signal values at the two cursors plus their difference, in the same display format as the signal.

The **Line** column controls how the signal is drawn on the stopped recording: Linear draws a straight line between samples, Step draws a rectangular waveform — which matches how a boolean or bit-style signal actually changes in the PLC. Switching a signal's format to Bool picks Step automatically. You can change the line style manually at any time and the choice is remembered across format changes.

### Scaling Groups

Multiple signals can share a y-axis by putting them into the same scaling group:

- **Main** — the primary left axis (default for new signals)
- **A / B / C / D** — four shared right axes; every signal in the same letter group uses one common axis with a neutral scale label
- **Own** — a dedicated right axis per signal, colored with the signal's own color

Example: put three temperature probes into group **A** to overlay them on one scale while pressure sits on its own axis.

### Computed Signals (Formulas)

A computed signal has no PLC tag of its own. It is computed from the values of earlier signals in the list using a formula you type into the **Formula** column.

**Syntax:**

- `$0`, `$1`, `$2` … refer to signals by their position in the list (zero-based). A computed signal at position *i* can only reference signals **before** it (`$0` … `$(i-1)`), which rules out circular references.
- Basic arithmetic `+`, `-`, `*`, `/` and parentheses.
- Built-in functions: `abs`, `sqrt`, `min(a, b)`, `max(a, b)`, `pow(a, b)`, `sin`, `cos`, `tan`, `log`, `log10`, `exp`, `ceiling`, `floor`, `round`.
- Two time-aware functions: `deriv($i)` returns the numerical derivative `(yₙ − yₙ₋₁) / Δt`, `integ($i)` returns the running integral (trapezoidal rule). Each call keeps its own state, so `deriv($0) + deriv($1)` works as expected. The state is reset every time you start a new trace.

**Examples:**

```
$0 + $1                 # sum of two signals
($0 + $1) / 2           # average
$0 - $1                 # difference
abs($0 - $1) * 2        # twice the absolute difference
deriv($0)               # numerical derivative
integ($0)               # numerical integral
$0 * 0.5 + 1.25         # gain + offset
```

**Validation:** The formula is parsed while you type. An invalid formula paints a red border around the cell and shows the error as a tooltip; the Start button stays disabled until every formula is valid again.

### Export

Click **Export CSV** to save the recording to disk. Every signal (source and computed) becomes a column, every sample a row, with the timestamp in the first column.

<!-- feature:eplan start -->
---

## 14c. EPLAN Integration (Add-on)

The EPLAN integration is an optional, separately licensed add-on. It connects the application to a local installation of **EPLAN Electric P8** (2025.0.3 or compatible) so you can browse and export EPLAN projects without leaving the manager.

### Prerequisites

- A valid EPLAN Electric P8 installation on the same machine.
- An active EPLAN License Manager (ELM) session — the add-on never holds a separate EPLAN license, it uses your existing one.
- The EPLAN add-on enabled on your manager license. The add-on is granted by the licensing back-end and is visible under **License → Add-ons** as a green "Active" badge. Without the add-on, the EPLAN tab is hidden.

### Enabling the Add-on

The add-on is purchased separately. Once granted to your account, sign out and sign back in (or trigger a license re-validate from the License panel) so the new entitlement is fetched. The card under **License → Add-ons → EPLAN** flips from "Not active" to "Active" and the EPLAN tab appears in the activity bar on the left.

### Opening a Project

Click the EPLAN tab. The workspace shows your recent EPLAN projects (most recent first) and an **Open EPLAN project…** button. Pick a `.elk` file via the file picker or click a recent entry — the manager spawns a hidden EPLAN bridge process the first time and then opens the project.

If you have more than one EPLAN variant installed (Electric P8, ProPanel, Preplanning…), a one-time picker lets you select which variant to use. The choice is remembered between sessions; only one bridge / variant runs per application session because of the EPLAN license-server constraint.

The bridge status indicator in the workspace header shows the live state:

- **Connected** — bridge is running and a project is loaded.
- **Connecting…** — bridge is starting up or reconnecting.
- **Disconnected** — no bridge running.

If the bridge crashes mid-session, a banner appears with a **Reconnect** button. Reconnect re-spawns the bridge and re-opens the previously open project automatically.

### Browsing the Project

The right pane is the **Project Explorer**. It groups the project content into two top-level categories:

- **Pages** — every drawing page in the project, with identifier, document type and description.
- **Functions** — main functions extracted from the schematics, with tag (e.g. `=A1+K2-K1`), the parent page identifier and any linked article number.

Type into the filter box at the top to filter both categories by a substring match across all visible columns. The category headers update with the live match count.

### Exporting

The toolbar **Export…** button opens a dialog with two formats:

- **PXF (EPLAN exchange)** — the lossless EPLAN exchange format, suitable for re-import into EPLAN.
- **PDF** — flat PDF of all drawing pages.

Pick a target file via **Browse…** and click **Export**. Long exports run with an indeterminate progress indicator — the EPLAN engine does not emit per-page progress in this version. The exported file lands at the path you picked.

### Recent Projects

Every successful project open is added to the recent-projects list (max 10 visible, 50 stored). Click an entry to re-open it; the small **×** button removes a single entry without affecting the EPLAN file on disk. If the file has moved or been deleted, the manager removes the dead entry from the list with a status hint.

### Page Preview

Double-click a page in the EPLAN tree to open it in the preview tab. The preview supports mouse-wheel zoom, middle-click pan, and a crosshair cursor that follows the pointer across the page surface. The page renders on a white sheet so the page border is visible at any zoom level.

### Limitations in this version

- **Authoring is MCP-tool driven, not direct UI.** Page and function create/delete/rename, symbol insert, parts-list/PDF/label report generation are exposed via AI Chat or external MCP clients only — the workspace itself remains read-only plus export from the toolbar; tag synchronisation with TIA is not yet supported.
- **One EPLAN variant per session.** Because EPLAN's License Manager only licenses one Electric P8 session per machine, switching variants requires restarting the manager.

If you do not see the EPLAN tab even after the add-on appears as "Active" on your license, restart the manager once so the activity bar picks up the new entitlement.

<!-- feature:eplan end -->
---

## 15. Troubleshooting & FAQ

### Common Problems

#### "TIA Portal not found"

**Cause:** TIA Portal is not installed or wrong version.

**Solution:**
1. Check if TIA Portal V15 through V21 is installed
2. Make sure the Openness components are installed
3. Ensure the Bridge process (`TiaOpennessManager.V3.Bridge.exe`) can start

#### "Access denied" when opening

**Cause:** Insufficient permissions to access TIA Portal or the project file.

**Solution:**
1. Run the application as Administrator
2. Ensure the project file is not read-only
3. Check that no other instance has the project open exclusively

#### "ObjectDisposedException" during operation

**Cause:** COM object became invalid.

**Solution:**
1. Close the project
2. Open it again
3. For large projects: Use Attach Mode

#### Export takes very long

**Cause:** Many blocks or slow hard drive.

**Solution:**
1. Export in smaller batches
2. Use an SSD
3. Close other applications

#### "Bridge not connected"

**Cause:** The Bridge process is not running or was blocked.

**Solution:**
1. Ensure `TiaOpennessManager.V3.Bridge.exe` exists in the same directory as the main application
2. Check that antivirus software is not blocking the Bridge process
3. Restart the application

### FAQ

**Q: Can I work in TIA Portal during export?**
A: No. During bulk operations, an ExclusiveAccess dialog appears in TIA Portal that blocks user interaction until the operation completes. This prevents conflicts and ensures data integrity.

**Q: Are comments preserved during export/import?**
A: Yes, all block attributes are stored in the XML file.

**Q: Does the application support Safety projects?**
A: Yes, F-blocks are fully supported. Some operations require Safety login.

**Q: Can I open multiple projects at once?**
A: No, currently only one project at a time is supported.

---

## Support

For further questions or problems, contact support:

- **Email:** [support@tiaopenessmanager.ch]
- **Documentation:** See `Information/` folder
- **Report a Bug or Feature Request:** Help → Report Issue inside the app

### Help → Report Issue

Opens a dialog to file a bug report or feature request directly on GitHub. Fill in a title and description; the app automatically attaches the app version, OS, .NET runtime, active TIA Portal version, language, and license tier. For bug reports you can also include the last 50 lines of recent logs (default: on). Clicking "Open in Browser" launches GitHub with the issue pre-filled — you only need to click "Submit new issue".

---

## Disclaimer

The software is provided "as is". The provider assumes no liability for:
- Damages caused by faulty LLM outputs
- Data loss or production downtime
- Engineering errors or faulty code generation
- Damages caused by improper use

**The user bears full responsibility for reviewing and validating all generated content.**

See EULA and Disclaimer at https://www.tiaopenessmanager.ch for details.

---

**© 2025-2026 AnyAutomation. All rights reserved.**

**End of User Manual**
