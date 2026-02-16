# TIA Openness Manager - User Manual

**Version:** 1.2
**Date:** January 2026

---

## Table of Contents

1. [Introduction](#1-introduction)
2. [Installation & System Requirements](#2-installation--system-requirements)
3. [User Interface](#3-user-interface)
4. [Project Management](#4-project-management)
5. [Import/Export Tab](#5-importexport-tab)
6. [Project Tab](#6-project-tab)
7. [Protection System](#7-protection-system)
8. [MCP Tab (AI Integration)](#8-mcp-tab-ai-integration)
9. [Hardware Tab](#9-hardware-tab)
10. [Find Unused Blocks](#10-find-unused-blocks)
11. [Settings](#11-settings)
12. [Licensing](#12-licensing)
13. [Troubleshooting & FAQ](#13-troubleshooting--faq)

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
| TIA Portal | V15, V16, V17, V18, V19, or V20 |
| .NET Framework | 4.8 or higher |
| RAM | Minimum 4 GB (8 GB recommended) |
| Disk Space | 500 MB |

> **Note:** TIA Portal version is detected automatically when you open a project or connect to a running instance. No manual configuration required.

### Installation

1. Download the TiaOpennessManager archive
2. Extract the archive to a folder of your choice (e.g., `C:\Tools\TiaOpennessManager`)
3. Run `TiaOpennessManager.exe`

> **Note:** No separate installation is required. The application is portable. TIA Portal must be installed on the system.

---

## 3. User Interface

### Main Window Overview

The application is divided into several areas:

```
┌─────────────────────────────────────────────────────────────────────────────┐
│  TIA Openness Manager - V20          [User Guide] [About] [Settings] [_][□][X] │
├─────────────────────────────────────────────────────────────────────────────┤
│  [Archive] [Disconnect] [Rescan] [Save] [Compile] [Safety Login] [Safety Logoff] │
├─────────────┬───────────────────────────────────────────────────────────────┤
│             │  [Project] [Import/Export] [Find Unused] [MCP] [Hardware]     │
│  Project    ├───────────────────────────────────────────────────────────────┤
│  Tree       │                                                               │
│             │              Tab Content                                      │
│  (Left)     │                                                               │
│             │                                                               │
├─────────────┴───────────────────────────────────────────────────────────────┤
│  Status Bar with Progress Indicator                                         │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Left Panel - Project Tree

The project tree supports two modes, selectable via radio buttons at the top:

- **TIA Project Mode** - Shows the structure of the connected TIA Portal project
- **Offline Folder Mode** - Browse a local folder of exported XML files

**Tree Features:**
- Hierarchy: Project → Hardware → Source → PLC → Blocks/Datatypes/Tags
- Green checkboxes for export selection (left of each item)
- Protection checkboxes for import protection (right of each item)
- "Selected" badge shows count of items selected for export
- "Protect" badge shows count of protected items
- Search bar with Find Previous/Find Next navigation
- Refresh button to reload the tree from TIA Portal

### Right Panel - Tabs

- **Project** - Code editor for selected blocks, with block details
- **Import/Export** - Main workspace for file operations with category tabs
- **Find Unused** - Dead code detection and cleanup
- **MCP** - AI integration status and tools
- **Hardware** - Device list with PROFINET names and IP configuration

## 4. Project Management

### Toolbar Buttons

| Button | Function |
|--------|----------|
| **Archive Project** | Create a compressed archive (.zap) |
| **Disconnect** | Close the current project connection |
| **Rescan PLC** | Refresh the project tree |
| **Save** | Save the project |
| **Compile** | Compile the project |
| **Safety Login** | Login with Safety credentials for F-blocks |
| **Safety Logoff** | Logoff from Safety mode |

### Connect to TIA Portal

When no project is connected, an empty state overlay appears in the project tree area with a **Connect** button. Clicking it opens the Connect dialog.

The Connect dialog offers two ways to open a project via tab buttons:

**Tab 1: Attach to Running**
1. The dialog shows a list of currently running TIA Portal instances
2. Select the desired instance from the list
3. Click **Connect**
4. Use the **Refresh** button to update the list if a new instance was started

**Advantages of Attach Mode:**
- Faster connection (no project loading required)
- You can work in TIA Portal simultaneously
- Changes are immediately visible in both applications

**Tab 2: Open Project**
1. Click **Browse...** to navigate to your TIA Portal project file
2. Select the file (`.ap15`, `.ap16`, `.ap17`, `.ap18`, `.ap19`, `.ap20`, `.apx`)
3. Click **Connect**

The TIA Portal version is detected automatically from the project file extension. Open Project starts TIA Portal in the background without a visible user interface (Headless Mode).

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

### Safety Logoff

Click **Safety Logoff** to log out of Safety mode. This is required after you have finished working with safety blocks.

### Close Project

Click **Disconnect** to close the project connection.

---

## 5. Import/Export Tab

The Import/Export Tab is the heart of the application.

### Layout

The Import/Export tab is organized with a vertical toolbar on the left and a file browser on the right:

```
┌───────────────┬──────────────────────────────────────┐
│  Selection: 5 │  Right Folder: C:\Export\...         │
│  [Cancel]     │  [Refresh] [Preview Diff] [Compare] [⚙] │
│               │                                      │
│  ┌─────────┐  │  🔍 [Search___________] [×] [↑] [↓] │
│  │Software │  │                                      │
│  │HMI      │  │  □ Blocks/                           │
│  │Safety   │  │    □ Main [OB1].xml                  │
│  │Watch    │  │    □ Motor [FB1].xml                  │
│  │Hardware │  │  □ Datatypes/                         │
│  ├─────────┤  │  □ Tags/                              │
│  │Export → │  │                                      │
│  │Export All│  │                                      │
│  │← Import │  │                                      │
│  │← Import All│                                      │
│  └─────────┘  │                                      │
└───────────────┴──────────────────────────────────────┘
```

### Category Tabs

The left toolbar organizes operations into category pill tabs:

| Category | Operations |
|----------|-----------|
| **Software** | Export Selected, Export All, Import Selected, Import All |
| **HMI** | Export HMI Selected, Export HMI All, Import HMI Selected, Import HMI All |
| **Safety** | Export F-Signatures |
| **Watch/Force** | Export Watch Tables, Export Force Tables, Import Tables |
| **Hardware** | AML Export, AML Import |

Select a category tab to see the relevant export/import buttons.

### Right Directory (Export/Import Directory)

The Right Directory is the folder on your file system where exported files are stored and from which files are imported.

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

### Import/Export Settings

Click the **gear icon** (⚙) in the toolbar to open the Import/Export Settings dialog. This dialog lets you customize how blocks are imported and exported.

#### Import Options

These settings control how blocks are imported into your TIA Portal project:

| Option | What it does |
|--------|--------------|
| **IgnoreStructuralChanges** | Allow import even if the block structure has changed (e.g., interface modifications). Use with caution as this may cause runtime issues. |
| **IgnoreMissingReferencedObjects** | Import blocks even if referenced objects (called blocks, UDTs) are missing. Missing references will need to be resolved manually. |
| **Fault Tolerant (continue on errors)** | Continue importing remaining files even if some files fail to import. Allows partial imports instead of stopping on first error. |

#### Export Options (Per-Type)

These settings control how different block types are exported. Each type can be configured separately:

**Data Blocks (DBs):**
| Option | What it does |
|--------|--------------|
| **None** | Export DBs without default values or read-only attributes |
| **With Defaults** | Include default parameter values in DB exports |
| **With ReadOnly** | Include read-only properties in DB exports |

**User Defined Types (UDTs):**
| Option | What it does |
|--------|--------------|
| **None** | Export UDTs without default values or read-only attributes |
| **With Defaults** | Include default parameter values in UDT exports |
| **With ReadOnly** | Include read-only properties in UDT exports |

**Tags:**
| Option | What it does |
|--------|--------------|
| **None** | Export tag tables without default values or read-only attributes |
| **With Defaults** | Include default values in tag table exports |
| **With ReadOnly** | Include read-only properties in tag table exports |

#### Export Protected Files

| Option | What it does |
|--------|--------------|
| **Export Protected Files** | When enabled (default), all items are exported including protected ones. When disabled, protected items are skipped during export but the folder structure is preserved. |

This option works together with the Protection System (see [Protection System](#7-protection-system)). If you have blocks marked as protected and want to export only unprotected blocks (e.g., to share with external partners without including protected proprietary blocks), uncheck this option.

**Behavior:**
- **Checked (default):** All blocks are exported, regardless of protection status
- **Unchecked:** Protected blocks, types, tag tables, and technology objects are skipped. Folder directories are still created to maintain the project structure.

#### Additional S7DCL Export (V20+ only)

S7DCL files are text-based source documents that are easier to read and compare than XML. They provide better readability for version control and code reviews.

| Option | What it does |
|--------|--------------|
| **SCL + S7DCL** | Additionally export SCL blocks as S7DCL format (.s7dcl) alongside .scl and .xml. Requires TIA Portal V20+. |
| **AWL + S7DCL** | Additionally export AWL/STL blocks as S7DCL format (.s7dcl) alongside .awl and .xml. Requires TIA Portal V20+. |
| **LAD/FBD + S7DCL** | Additionally export LAD/FBD/GRAPH blocks as S7DCL format (.s7dcl) alongside .xml. Enables text export for graphical languages. Requires TIA Portal V20+. |

**Why use S7DCL export?**
- **Better readability** - S7DCL files are plain text, ideal for diff comparison
- **Version control** - See exactly what changed between versions in Git or SVN
- **Code review** - Easier to review changes line by line
- **Graphical languages** - Get text-based representation of LAD/FBD blocks

> **Note:** S7DCL files are for viewing and version control only. They cannot be re-imported into TIA Portal. This option requires TIA Portal V20 or later.

#### Version Control Options

These settings help create cleaner exports for Git, SVN, or other version control systems. They remove data that changes even when the actual code hasn't changed.

| Option | What it does |
|--------|--------------|
| **Exclude Document Info (recommended)** | Uses TIA Portal API DocumentInfoOptions.None to exclude timestamps and InstalledProducts from exports. Enabled by default for clean version control diffs. |
| **Normalize Timestamps** | Set all dates to 2000-01-01 to reduce Git diff noise |
| **Clear Installed Products** | Remove machine-specific product version info from exports |
| **Remove Object List** | Remove ObjectList for code blocks with source files (.scl, .awl, .db) |
| **Normalize Whitespace** | Trim whitespace in MultiLanguageText elements |
| **Export Fingerprints** | When enabled, extracts and saves fingerprints for change detection. Disable to skip fingerprint extraction during export (speeds up export when change detection is not needed). |

> **Tip:** If you use Git or SVN, enable all Version Control options except "Export Fingerprints" if you don't need Preview Diff functionality. This prevents "false changes" where files look different but the actual code is unchanged.

### Preview Diff

The Preview Diff function shows differences between the TIA Portal project and the Working Directory:

**Prerequisites:**
- You must have previously exported blocks with the **Export Fingerprints** option enabled
- This option can be found in the **Import/Export Settings** dialog (gear icon ⚙) under **Version Control**
- Without exported fingerprints, Preview Diff cannot detect changes

**How to use:**
1. Click **Preview Diff**
2. The application compares fingerprints (hashes) of blocks
3. A window shows:
   - **Changed** - Blocks whose content differs
   - **New in TIA** - Blocks that only exist in the project
   - **Deleted** - Blocks that only exist in the Working Directory

> **Tip:** If you don't need Preview Diff functionality, you can disable "Export Fingerprints" in the Import/Export Settings to speed up exports.

### Compare (Manual Comparison)

The Compare function allows a detailed line-by-line comparison between any two items - blocks, files, or any combination.

**How to use manual comparison:**

1. Select an item in the left tree (TIA Project block or exported file)
2. Select an item in the right tree (Working Directory file or TIA block)
3. Click **Compare**
4. The Compare window opens and shows:
   - **Left:** Name of the selected left item
   - **Right:** Name of the selected right item
5. Click **Start Compare**
6. The diff viewer shows differences line by line

**Cross-Comparison Feature:**

- **Any-to-Any** - Compare anything with anything: block↔file, file↔file, block↔block
- **Format Matching** - The comparison automatically matches formats (SCL↔SCL, XML↔XML, AWL↔AWL)
- **Free matching** - Compare any item with any other item, regardless of name or type
- **Quick single comparison** - Ideal for targeted checks without scanning all files

**Note:** Unlike Preview Diff (hash-based), Compare performs a direct text comparison. Blocks are temporarily exported in the matching format and compared line by line.

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

### Hardware Export

Export hardware configuration as AML/XML:

1. Expand the **Hardware** node in the project tree
2. Select devices or modules to export
3. Click **Export Selected**

**Note:** Hardware export creates AutomationML (.aml) files that can be re-imported or used for documentation.

---

## 6. Project Tab

### Code Display

When you select a block in the project tree, its source code is displayed in the Project tab's code editor.

**Supported Languages:**
- SCL (Structured Control Language)
- STL (Statement List)
- LAD/FBD (as XML representation)

### Code and Graphical Tabs

The editor has two tabs:

**Code Tab:**
- Displays text-based source code (SCL, STL, AWL)
- Syntax highlighting for better readability
- Search functionality with Match case and Whole word options

**Graphical Tab:**
- Displays LAD/FBD/GRAPH blocks graphically
- **Requires:** SIMATIC Automation Compare Tool (SIMATIC ACT) to be installed
- Click "Open in SIMATIC ACT" or switch to the Graphical tab to view the block
- If SIMATIC ACT is not installed, the graphical view will not be available

> **Note:** The SIMATIC Automation Compare Tool is a free tool from Siemens that can be downloaded from the Siemens support website.

### Block Details Panel

Metadata is displayed next to the code:
- **Block Type:** OB, FB, FC, DB
- **Number:** e.g., OB1, FB10
- **Language:** SCL, STL, LAD, FBD, GRAPH
- **Author:** If available
- **Last Modified:** Timestamp

### Project Tree Search

Use the search field above the project tree to quickly find blocks:
- Search by name
- Search by number
- Case-insensitive

### Create New Block

The code editor supports creating new SCL blocks from scratch:

1. Click the **+ New** button in the code editor toolbar
2. Write your SCL code in the editor
3. Click one of the create buttons to generate the block:
   - **Create FC** - Create a Function
   - **Create FB** - Create a Function Block
   - **Create DB** - Create a Data Block
   - **Create UDT** - Create a User-Defined Type
   - **Create Tag Table** - Create a Tag Table
4. Click **Cancel** to discard

### Save and Discard

When you edit an existing block's code, Save and Discard buttons appear:

- **Save** - Write the modified code back to TIA Portal
- **Discard** - Revert to the original code

---

## 7. Protection System

### Concept

The protection system prevents important blocks from being accidentally overwritten during import operations. Protection is managed directly in the project tree - there is no separate tab.

### Protecting Blocks

In the project tree, each block has a protection checkbox on the right side:

1. Click the protection checkbox next to any block, data type, or tag table
2. The checkbox uses three states:
   - **Unchecked** - Not protected
   - **Checked** - Protected (block will be skipped during import)
   - **Indeterminate** - Some child items are protected (for folder nodes)

### Protection Badges

The project tree header shows two badges:

- **"Selected: N"** (green) - Number of items selected for export
- **"Protect: N"** (orange) - Number of protected items, with a clear button to remove all protection

### Protection Options for Organization Blocks (OBs)

When you protect an OB (Organization Block), additional checkboxes appear next to it:

| Checkbox | Icon | What it does |
|----------|------|--------------|
| **Allow SCL code updates** | C | When checked, allows the SCL source code of this protected OB to be updated during import, while still protecting other attributes. |
| **Allow Attribute updates** | A | When checked, allows block attributes (comments, title, etc.) to be updated during import, while protecting the actual code. |

**Use Cases:**
- **Both unchecked:** Full protection - block is completely skipped during import
- **C checked only:** Import updates to the code, but keep original attributes
- **A checked only:** Import attribute changes, but keep original code
- **Both checked:** Allow full updates (equivalent to not protecting the block)

> **Note:** These additional checkboxes are only shown for protected OBs. FBs, FCs, and DBs use standard full protection.

### Profiles

Profiles save your protection and export selection configuration. The Profiles bar is located above the project tree.

**Save Profile:**
1. Configure your protected blocks and export selections
2. Enter a name in the Profile Name field
3. Click **Save Profile**

**Load Profile:**
1. Select a profile from the dropdown
2. Click **Apply**

**Delete Profile:**
- Select a profile and click **Delete**

**Reload Profiles:**
- Click **Reload** to refresh the profiles list

**Browse Profiles Folder:**
- Click the folder icon to open the profiles folder in Explorer
- Useful for sharing profiles between machines or team members

---

## 8. MCP Tab (AI Integration)

### What is MCP?

The Model Context Protocol (MCP) allows AI assistants to access your TIA Portal project. When running, AI clients can list blocks, read code, export/import files, and perform analysis.

### MCP Server Status

The tab shows:
- **Server Status:** Running / Stopped
- **Connection Settings** button to configure the server

### Connection Settings

Click **Connection Settings** to open the MCP Connection Info dialog:

**Server Connection:**
- **Named Pipe:** `\\.\pipe\TiaOpennessMcp` - The connection address for MCP clients
- **Status:** Shows if the server is running or stopped
- **Available Tools:** Number of MCP tools available (e.g., 23 tools)

**Security Settings:**
| Option | Description |
|--------|-------------|
| **Allow Write Operations** | Enable Import, Delete, Compile, Save operations via MCP |
| **Require User Approval** | When enabled, a confirmation dialog appears for each write operation |

**Client Configuration Tabs:**
The dialog provides ready-to-use configuration for different AI clients:
- **LM Studio** - Configuration for LM Studio MCP settings
- **Ollama** - Configuration for Ollama
- **Continue.dev** - Configuration for Continue.dev extension
- **Claude Desktop** - Configuration for Claude Desktop app

Each tab shows:
- The JSON configuration to add to your client
- A **Copy Config** button to copy the configuration
- Step-by-step setup instructions

### Usage with AI Assistants

1. Open a TIA Portal project in TIA Openness Manager
2. Go to the **MCP** tab
3. Click **Connection Settings**
4. Select your AI client tab (e.g., Claude Desktop)
5. Click **Copy Config** and paste into your client's MCP settings
6. Restart your AI client
7. The AI assistant can now:
   - Query project structure
   - Read and analyze block code
   - Export/import files (if write operations enabled)
   - Generate code for your project

---

## 9. Hardware Tab

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

## 10. Find Unused Blocks

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

### Notes

- OBs (Organization Blocks) are never marked as "unused" since they are entry points
- Safety blocks require Safety login for complete analysis
- Deleting safety blocks requires confirmation due to safety implications

---

## 11. Settings

### Opening

Click the **Gear icon** in the upper right corner.

### Available Settings

| Setting | Description |
|---------|-------------|
| **Language** | User interface language (English, German, French, Italian). Requires restart to take effect. |
| **Working Directory** | Default folder for "Find Unused Blocks" exports |
| **Log Path** | Where to save log files when Debug Logging is enabled |
| **Debug Logging** | Enable detailed logging for troubleshooting |
| **Auto-Update Check** | Automatically check for new versions when the application starts |

> **Note:** TIA Portal version is now detected automatically when you open a project or connect to a running instance. No manual selection is needed.

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

## 12. Licensing

### License Tiers

| Feature | Basic (FREE) | Pro (CHF 9.99/mo) | Enterprise (CHF 29.99/mo) |
|---------|--------------|---------------------|---------------------------|
| Price | Free forever | CHF 9.99/mo or CHF 99.99/year | CHF 29.99/mo or CHF 299.99/year |
| Files | 1 | 1,000 | Unlimited |
| Export/Import | Yes | Yes | Yes |
| Block Compare | Yes | Yes | Yes |
| Code Editor | Yes | Yes | Yes |
| Find Unused | No | Yes | Yes |
| Safety Blocks | No | Yes | Yes |
| Protection Profiles | No | Yes | Yes |
| MCP Server | No | Yes | Yes |
| Multi-User | No | No | Yes |

### Activate License (Online)

1. Purchase a subscription (Pro or Enterprise)
2. You will receive an activation code via email
3. Click **License** in the toolbar
4. Enter the activation code
5. Click **Activate**
6. The license will be bound to your hardware

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
- Current license type (Basic/Pro/Enterprise)
- Current period expiry date
- Hardware ID
- Activation code

---

## 13. Troubleshooting & FAQ

### Common Problems

#### "TIA Portal not found"

**Cause:** TIA Portal is not installed or compatible version not available.

**Solution:**
1. Check that TIA Portal V15, V16, V17, V18, V19, or V20 is installed
2. Make sure the Openness components are installed (part of TIA Portal installation)

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

**© 2026 AnyAutomation. All rights reserved.**

**End of User Manual**
