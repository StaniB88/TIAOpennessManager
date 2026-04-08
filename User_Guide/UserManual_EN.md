# TIA Openness Manager - User Manual

**Version:** 3.0
**Date:** February 2026

---

## Table of Contents

1. [Introduction](#1-introduction)
2. [Installation & System Requirements](#2-installation--system-requirements)
3. [User Interface](#3-user-interface)
4. [Project Management](#4-project-management)
5. [Import/Export Tab](#5-importexport-tab)
6. [Project Tab](#6-project-tab)
7. [Protected Items Tab](#7-protected-items-tab)
8. [Password Vault Tab](#8-password-vault-tab)
9. [MCP Tab (AI Integration)](#9-mcp-tab-ai-integration)
9a. [AI Chat](#9a-ai-chat)
9b. [OPC UA Tab](#9b-opc-ua-tab)
9c. [AI Canvas](#9c-ai-canvas)
10. [Project Library Management](#10-project-library-management)
11. [Hardware Tab](#11-hardware-tab)
12. [Find Unused Blocks](#12-find-unused-blocks)
13. [Settings](#13-settings)
14. [Licensing](#14-licensing)
14a. [Git Client](#14a-git-client)
15. [Troubleshooting & FAQ](#15-troubleshooting--faq)

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
│             │  [Project] [Import/Export] [Find Unused]       │
│  Project    │  [MCP] [Hardware]                              │
│  Tree       ├───────────────────────────────────────────────┤
│             │                                               │
│  (Left)     │              Tab Content                      │
│             │                                               │
├─────────────┴───────────────────────────────────────────────┤
│  Bottom Panel: [Log Output] [Terminal] [Compare]             │
├─────────────────────────────────────────────────────────────┤
│  Status Bar: ● Connected | Status Message | MCP: ● Running   │
└─────────────────────────────────────────────────────────────┘
```

### Left Panel - Project Tree

- Shows the structure of the opened TIA Portal project
- Hierarchy: Project → Hardware → Source → PLC → Blocks/Datatypes/Tags
- Checkboxes enable multiple selection for export

### Right Panel - Tabs

- **Project** - Code editor for selected blocks
- **Import/Export** - Main workspace for file operations
- **Find Unused** - Dead code detection and cleanup
- **MCP** - AI integration status and server control
- **Hardware** - Device list with PROFINET names and IP configuration

### Menu Bar

| Menu | Key Items |
|------|-----------|
| File | Connect, Browse Folder, Archive Project, Disconnect, Exit |
| Project | Rescan PLC, Save, Compile, Safety Login/Logoff |
| View | Settings, Terminal, Import/Export Settings, Protection Profiles Folder |
| Help | Documentation, Release Notes, About |

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

The bottom panel contains three tabs:
- **Log Output** - Application log messages with color-coded severity
- **Terminal** - Integrated terminal for command-line operations
- **Compare** - Side-by-side block comparison viewer

The panel can be collapsed, expanded, or maximized using the controls in the top-right corner.

---

## 4. Project Management

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

**Recent Projects:** The dialog remembers your last opened project for quick access.

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

> **Note:** The "Working Directory" in Settings refers to the "Find Unused Blocks" function and is a separate folder.

### Export Operations

#### Export Selected
1. Check the boxes next to the desired blocks in the left tree
2. Click **Export Selected**
3. The selected blocks are exported as XML

#### Export All
1. Click **Export All**
2. ALL blocks, data types, and tag tables are exported

### Import Operations

#### Import Selected
1. Check the boxes next to the desired XML files in the right tree
2. Click **Import Selected**
3. The selected files are imported

#### Import All
1. Click **Import All**
2. ALL XML files in the Working Directory are imported

**Important:** Import overwrites existing blocks with the same name!

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
2. The application compares fingerprints (hashes) of blocks
3. A window shows:
   - **Changed** - Blocks whose content differs
   - **New in TIA** - Blocks that only exist in the project
   - **Deleted** - Blocks that only exist in the Working Directory

### Compare (Manual Comparison)

The Compare function allows a detailed line-by-line comparison between a TIA Portal block and any XML file.

**How to use manual comparison:**

1. Select a block in the left tree (TIA Project)
2. Select an XML file in the right tree (Working Directory)
3. Click **Compare**
4. The Compare window opens and shows:
   - **Left (TIA Portal):** Name of the selected block
   - **Right (Filesystem):** Name of the selected file
5. Click **Start Compare**
6. The diff viewer shows differences line by line

**Advantages of manual comparison:**

- **Free matching** - Compare any block with any file, regardless of name
- **Quick single comparison** - Ideal for targeted checks without scanning all files
- **SCL support** - If available, the more readable SCL file is automatically used

**Note:** Unlike Preview Diff (hash-based), Compare performs a direct text comparison. The block is temporarily exported and compared line by line with the file.

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

Export hardware configuration as AML/XML:

1. Expand the **Hardware** node in the project tree
2. Select devices or modules to export
3. Click **Export Selected**

**Note:** Hardware export creates AutomationML (.aml) files that can be re-imported or used for documentation.

---

## 6. Project Tab

### Code Display

When you select a block in the project tree, its source code is displayed in the code editor.

**Supported Languages:**
- SCL (Structured Control Language)
- STL (Statement List)
- LAD/FBD (as XML representation)

### Block Details Panel

Metadata is displayed next to the code:
- **Block Type:** OB, FB, FC, DB
- **Number:** e.g., OB1, FB10
- **Language:** SCL, STL, LAD, FBD, GRAPH
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
- Search by name
- Search by number
- Case-insensitive

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
- Be marked with a green shield icon
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

## 9. MCP Tab (AI Integration)

### What is MCP?

The Model Context Protocol (MCP) allows AI assistants to access your TIA Portal project.

### MCP Server Status

The tab shows:
- **Server Status:** Running / Stopped
- **Connected Clients:** Number of active connections
- **Available Tools:** List of MCP functions

### Usage with AI Assistants

1. Start the MCP Server in TIA Openness Manager
2. Configure your AI assistant with the MCP server address
3. The AI assistant can now:
   - Query project structure
   - Read block code
   - Perform analyses

---

## 9a. AI Chat

The built-in AI Chat panel provides a conversational interface to an AI assistant that is aware of your project and environment. Configure it via **View → AI Chat Settings**.

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

Four default skills are included and automatically deployed on first launch:

| Skill | Icon | Description |
|-------|------|-------------|
| Explore Project | 🧭 | Analyzes the connected TIA Portal project and generates a context file |
| Explain Block | 💡 | Reads a block's source code and explains its logic |
| Generate SCL | ⌨️ | Generates SCL code following Siemens programming standards |
| Compare Blocks | 🔄 | Compares block versions between project and export folder |

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

**Format:** Each `.json` file defines one agent. Three built-in agents are provided:

| Agent | Purpose |
|-------|---------|
| General Assistant | All-purpose chat with full tool access |
| Git Assistant | Focused on git operations; file tools restricted |
| SCL Expert | Specialized for writing and reviewing SCL/PLC code |

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

Sessions are stored as JSON files in `%LocalAppData%\TiaOpennessManager\ChatSessions\`.

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

### Terminal Mode

Terminal mode embeds a PowerShell terminal directly in the AI Chat panel. Use it to run CLI tools (e.g., Claude CLI, git, or any other command-line tool) with full access to MCP tools connected to TIA Portal.

**Switching modes:**
- Click the **Chat** / **Terminal** toggle in the header bar
- The terminal opens PowerShell in the TIA Portal project directory (if a project is open)

**MCP integration:**
When terminal mode is activated, TIA Openness Manager automatically:
1. Starts the MCP server (if not already running)
2. Writes a `.mcp.json` file to the project directory so CLI tools can discover available MCP tools
3. Optionally writes a `CLAUDE.md` file with project context (PLCs, architecture, AI analysis) — see setting below

**CLAUDE.md generation:**
By default, a `CLAUDE.md` file is written to the TIA Portal project directory whenever you switch to terminal mode. This file contains project context that Claude CLI reads automatically. If you are not using Claude CLI, you can disable this behavior:

1. Open **View → AI Chat Settings**
2. Navigate to the **Context** section
3. Uncheck **Write CLAUDE.md to project directory on terminal start**

**Paste to terminal:**
The AI Chat can paste commands or code into the terminal. When the AI suggests a command, click the paste icon to send it directly to the terminal input.

**Keyboard shortcut:**
- **Ctrl+Shift+V** — Paste clipboard content into the terminal

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
| `Event` | When to run: `PreToolUse`, `PostToolUse`, `Stop`, `UserPromptSubmit` |
| `Matcher` | Tool name pattern (e.g. `tia_*`, `tia_delete_*\|tia_import_*`, `Bash(git *)`) |
| `Type` | `command` (shell) or `http` (POST callback) |
| `Command` | Shell command to execute (receives JSON on stdin, returns JSON on stdout) |
| `Url` | HTTP endpoint for `http` type hooks |
| `TimeoutSeconds` | Maximum execution time (default 60s) |
| `IsBackground` | If `true`, runs fire-and-forget (PostToolUse only) |
| `Enabled` | Set to `false` to disable without removing |

**Shell hook protocol:** The hook receives a JSON object on stdin with `tool_name`, `tool_input`, `tool_output`, `session_id`, and `agent_id`. It should return JSON on stdout with `decision` (`allow`/`deny`/`ask`), optional `reason`, `additionalContext`, or `updatedInput`. Exit code 2 blocks execution.

### Command Queue

You can type and send messages while the AI agent is actively processing. Instead of blocking input during streaming, messages are placed into a priority queue and processed automatically after each turn completes.

**Sending while busy:** Simply type your message and press Enter while the agent is streaming. The message appears as "queued" and the input field clears so you can continue typing. A small indicator next to the input area shows how many messages are waiting (e.g. "2 messages queued").

**Priority levels:**

| Priority | When used | Behavior |
|----------|-----------|----------|
| Next | User messages (default) | Processed after current turn ends |
| Later | Agent notifications | Processed after user messages |

**ESC behavior:**

- **While streaming:** Cancels the current AI response and clears all queued messages
- **While idle with queued messages:** Pops all editable messages from the queue back into the input field, so you can edit or discard them before sending

**Queue processing:** After each AI turn completes, the system automatically checks the queue and processes the next message. If multiple messages are queued, they are processed one at a time in priority order (higher priority first, FIFO within the same priority).

---

### Multi-Session

Run multiple AI chat sessions simultaneously. Each session has its own conversation context, canvas state, and model override.

**Agent Sidebar:** Click the sidebar toggle icon (PanelLeftOpen/PanelLeftClose) in the chat header to toggle the Agent Sidebar. It slides out as an overlay from the left without pushing the chat content. It shows all sessions grouped by status:

- **In Progress** — Sessions where the AI is actively streaming or has been interacted with
- **Completed** — Sessions that finished successfully or with errors

**Creating sessions:** Click the **+** button in the sidebar header to create a new session. The sidebar opens automatically when a second session is created.

**Switching sessions:** Click any session in the sidebar to switch to it. The chat context, canvas, and model override all switch to the selected session.

**Closing sessions:** Click the **X** button on a session item. If the session is still running, a confirmation dialog appears. Closing cancels active streaming, kills sub-agents, and cleans up the session context.

**Unread badges:** When another session receives a message while you are viewing a different session, an unread badge appears on the session item with a brief blink animation.

**Renaming sessions:** Double-click a session name to edit it. Press Enter or click away to save.

**Canvas per session:** Each session maintains its own canvas state. When switching sessions, the WebView is reset and the target session's canvas content is automatically replayed.

**Live model switch:** Use the model picker button in the chat header to change the AI model for the current session only. Other sessions and the global setting are not affected.

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
| Value | Current value |
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

### Live Monitoring (Subscriptions)

Subscriptions let the OPC UA server push value changes to TIA Openness Manager automatically, without repeated polling.

#### Starting a Subscription

1. Set the **Subscription Interval** (in milliseconds) using the interval field — for example, `500` for updates every 500 ms
2. Click **Subscribe** to start monitoring all variables in the watch table
3. Values update automatically as changes occur on the PLC
4. A pulsing indicator shows that a subscription is active

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

The following MCP tools are available for AI assistants:

- `library_create_master_copy` - Create Master Copy from block
- `library_instantiate` - Instantiate Master Copy to PLC
- `library_delete_item` - Delete library item
- `library_rename_item` - Rename library item
- `library_export_type` - Export Type version
- `library_create_folder` - Create new folder
- `library_cleanup` - Clean up unused types

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
Saves modified PROFINET names and IP addresses back to the TIA Portal project.

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

### Opening

Select **View → Settings** from the menu bar.

### Available Settings

| Setting | Description |
|---------|-------------|
| Working Directory | Default export folder for Find Unused Blocks |
| Log Path | Path for log files |
| Language | User interface language (EN, DE, FR, IT) |
| Theme Mode | Dark or Light mode |
| Accent Color | Cyan, Blue, Green, Amber, or Teal |
| Debug Logging | Enables extended logging |
| Check for Updates | Automatically check for updates at startup |
| Create Source Folder | Include a Source folder wrapper in exports |

### Folder Name Customization

Customize the folder names used in export paths and tree view:

| TIA Portal Name | Default Export Name | Configurable |
|-----------------|---------------------|--------------|
| (Device) | Source | ✓ |
| Program blocks | Blocks | ✓ |
| PLC data types | Datatypes | ✓ |
| PLC tags | Tags | ✓ |
| Technology objects | Technology Objects | ✓ |
| Software units | Software Units | ✓ |

### Create Source Folder Option

The **"Create Source folder"** checkbox controls whether exports include a Source folder wrapper:

| Setting | Export Path |
|---------|-------------|
| ✓ Enabled | `WorkingDir/Source/PLC_1/Blocks/...` |
| ☐ Disabled | `WorkingDir/PLC_1/Blocks/...` |

This setting also affects the project tree structure and import path detection.

### Log Files

When Debug Logging is enabled, detailed logs are created:
- Location: Configurable in settings
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
| Multi-User | No | No | Yes |

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

**Important:** The software validates the license every 7 days online. If no internet connection is available, the software can be used **offline for up to 14 days**. After 14 days, a new online validation is required.

### Hardware Binding

Each license is bound to a unique hardware ID generated from:
- CPU ID (Processor Serial Number)
- Motherboard Serial Number
- Primary MAC Address

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

---

## 14a. Git Client

The Git Client is a built-in version control interface for managing repositories directly within TIA Openness Manager. It provides a visual Git workflow without leaving the application.

### Opening a Repository

1. Click the **Git** tab in the main navigation
2. On the welcome page, click **Open Repository** and select a folder, or drag a repository folder onto the welcome page
3. Recently used repositories are shown in the list for quick access

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

- **Email:** [tiaopenessmanager@outlook.com]
- **Documentation:** See `Information/` folder

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
