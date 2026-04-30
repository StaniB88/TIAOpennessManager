# TIA Openness Manager - Feature Overview

## Product Description

The **TIA Openness Manager** is a powerful tool for Siemens TIA Portal developers that revolutionizes the export, import, and management of PLC program blocks. With an intuitive user interface and advanced features like difference comparison, protection profiles, and AI integration, it significantly increases productivity and reduces errors in project management.

---

## Main Features

### Welcome Tab

- **Welcome Tab** — Interactive introduction with Get Started walkthrough and quick-action shortcuts.
- **Get Started walkthrough** - Four steps (Connect, Project Explorer basics, Export, Choose next area) that check themselves off as you use the app
- **Seven quick-action shortcuts** - Connect, Open Project, Browse Export Folder, Clone Git, New SCL File, Unit Testing, Configure AI Assistant
- **Feature cards** - Single-click jump to AI Chat, Git, Unit Testing, OPC UA, and the What's New changelog
- **Recent projects** - Up to five newest entries, updated after every successful connection (file-open or attach); click to reconnect straight to a project, missing files are hidden automatically
- **Reopen anytime** - Help → Welcome Guide opens the tab regardless of the startup setting

### Quick Open Bar

- **Title-bar search box** — Press **Ctrl+Shift+P** anywhere in the application or click into the search box in the title bar
- **Six prefixes** — `>` Commands · `@` Symbols (current context: PLC, Screen, Unit Test, Trace, OPC UA when connected) · `#` Symbols (whole workspace) · `git:` Git branches · `?` Help · `:` Goto-line in active editor
- **Discovery list on click** — Clicking the search bar without the shortcut shows a seven-entry discovery list of all categories with their prefixes plus your recently opened files, so the right shortcut is one keystroke away
- **Single-click executes** — Up/Down keys, Enter and mouse single-click all run a result; Esc closes the popup
- **Cross-workspace navigation** — Selecting a result switches the active workspace and selects the target where the host view supports it (commands, goto-line, PLC symbols, Screen symbols, Git branch checkout, file open)
- **Recently used results** — Up to 50 entries kept across application restarts, older than 30 days pruned automatically

### Import & Export

- **Export Selected** - Export only the ticked blocks, data types, tag tables, technology objects, or software-unit items. Existing files with the same name are overwritten; other files in the export folder are kept
- **Export All** - Full project export; the PLC export folder is cleared first, then all blocks, data types, tag tables, technology objects, and software units are written fresh
- **XML & SCL Support** - Full support for Simatic ML and SCL files
- **S7DCL Export (V20+)** - Additional text-based export format (.s7dcl) for better version control
- **Folder Structure Preservation** - TIA Portal folder structure is maintained
- **Automatic Compilation** - Automatically compiles and saves after import
- **Configurable Folder Names** - Customize export folder names (Source, Blocks, Tags, etc.)
- **Optional Source Folder** - Enable/disable the Source folder wrapper in exports
- **Import Selected** - Targeted import; only the ticked files are written. Existing blocks with the same name are overwritten, the rest of the PLC is left untouched
- **Import All** - Full project re-import; all existing blocks, data types and tag tables are cleared first, then everything in the Working Directory is imported. Blocks marked in the Protection Profile are preserved

### HMI Export/Import

- **Screen Export** - Export HMI screens as XML
- **Screen Template Export** - Export reusable screen templates
- **HMI Tag Tables** - Export/import HMI tag tables
- **VB Scripts** - Export HMI VB scripts
- **Connections** - Export HMI connection configurations
- **Text Lists & Graphic Lists** - Full support for HMI lists

### Hardware Tab

- **Device List** - Complete overview of all devices (PLCs, HMIs, Drives, Switches)
- **PROFINET Names** - View and edit PROFINET device names directly
- **IP Addresses** - Display IP address configuration for all devices
- **Firmware Versions** - Show firmware version for each device
- **Article Numbers** - Display Siemens article/order numbers
- **I/O Mapping** - Show input/output address ranges
- **CSV Export** - Export complete hardware list to CSV for documentation
- **WinCC Unified Support** - Full support for WinCC Unified HMI panels

### Hardware Export

- **Device Configuration** - Export hardware configuration as XML
- **Module Configuration** - Export individual module settings
- **Network Configuration** - Export network/communication settings

### Watch/Force Tables

- **Table Export** - Export Watch Tables and Force Tables
- **Variable Lists** - Export monitored variable configurations
- **Debug Support** - Preserve debugging setups across projects

### Project Library Management

- **Create Master Copy** - Copy blocks to Project Library for reuse
- **Instantiate from Library** - Create blocks from Master Copies
- **Export Type Versions** - Export committed Library Type versions as XML
- **Folder Organization** - Create folders in library for better structure
- **Rename Items** - Rename Master Copies, Types, and folders
- **Delete Items** - Remove library items with confirmation
- **Clean Up Library** - Remove unused types and versions automatically
- **MCP Integration** - 7 library tools available for AI assistants

### Difference Comparison (Preview Diff)

- **Project-wide scan** - Compiles the PLC first, then compares TIA-Portal fingerprints and file hashes against the cached state from the last export
- **Works on the first click** - No previous export required; the first run silently builds a baseline by temporarily exporting the PLC, then hands off to the fast path for every follow-up comparison
- **Change Detection** - Detects modified, new, and deleted blocks in five categories (Modified / Only in TIA / Only on Disk / Unchanged / Inconsistent)
- **Block icons in the file list** - Every row shows the matching block icon (FC / FB / OB / DB, with safety variants), matching the project tree
- **Symmetric left/right file lists** - The TIA side and the disk side each have their own file list with its own show/hide toggle; modified items appear in both lists, added/inconsistent only on the left, deleted only on the right
- **Change strip per row** - A thin colored bar at the right edge of each file row signals the change type at a glance: green for added, red for deleted, orange for modified, yellow for inconsistent, blue for TIA-only
- **Detailed Diff Viewer** - Shows differences line by line
- **Selective Re-Import** - Tick the checkbox next to each block you want to push back into the PLC; transactional, rolls back on any failure

### Ad-hoc Compare (Drag and Drop)

- **Drop blocks into the Compare panel** - The block is compiled and exported with the same strip settings as "Export Selected"; both XML and source-code formats (SCL, DB) land as their own rows
- **Independent left and right drop targets** - Blocks and files can be dropped on either side; the item lands on whichever half you drop onto and additional drops append to that side instead of replacing it
- **Resizable file list** - Splitter between file list and diff editor drags between 180 and 500 pixels; width is remembered across show/hide

### Diff Editor

- **Syntax highlighting** - SCL, AWL, DB, XML, and other languages are recognised by extension
- **Side-by-side and unified** - Switch layout from the toolbar
- **Change navigation** - First / Previous / Next / Last with a `1/N` counter
- **Context-lines collapse** - Fold unchanged stretches behind a hunk header; adjust context width with `+=`/`-=` or expand the entire file
- **Edit mode** - Toggle Edit to modify either side in place; save back to the file or PLC with one click
- **Diff tweaks** - Ignore whitespace, show hidden symbols, toggle word-wrap

### Code Editor

The built-in code editor provides professional editing features for SCL and other file types.

- **Split View** — Split editors horizontally or vertically, drag tabs between groups, dock and pin panels (file tree, markdown preview)
- **Drag & drop from Project Explorer** — Drag one or several blocks or offline source files onto the editor or Welcome tab; each opens as its own editor tab
- **Syntax Highlighting** — SCL, C#, XML, JSON, Python, and 60+ other languages
- **Code Folding** — Collapse/expand code regions, IF/FOR blocks, and VAR sections
- **Auto-Completion** — Type 2+ characters to see SCL keywords, data types, and functions
- **Search** — Press Ctrl+F for find and replace with regex support
- **Code Snippets** — Type `if`, `for`, `while`, `case`, `fb`, `fc`, or `region` and press Tab to insert templates
- **Current Line Highlight** — Visual indicator for the current cursor line
- **Theme Support** — Editor colors automatically adapt when switching between Dark and Light themes
- **Inline Chat (Ctrl+I)** — Press Ctrl+I to open an AI chat directly in the code editor. Optionally select code first, then type your question or request — the AI responds and can propose changes inline. Accept with Tab, reject with Escape
- **Block Details** - Shows metadata like number, language, author
- **Quick Navigation** - Search in project tree

#### Keyboard Shortcuts
| Shortcut | Action |
|----------|--------|
| Ctrl+F | Find and Replace |
| Ctrl+I | Inline AI Chat (SCL Editor only) |
| Tab | Insert snippet (when trigger word is typed) |
| Tab | Accept AI edit |
| Escape | Reject AI edit |

### Protection System (Protected Items)

- **Block Protection** - Protect important blocks from accidental overwriting
- **Export Protection** - Optionally exclude protected blocks from export while preserving folder structure
- **Profiles** - Save and load protection configurations
- **Visual Marking** - Protected blocks are clearly marked with a green shield
- **Hierarchical Protection** - Protect entire folders or individual blocks

### Password Vault

- **Secure Storage** - AES-256-GCM encrypted vault for TIA Portal know-how protection passwords
- **Master Password** - Single master password protects all vault entries (PBKDF2 key derivation)
- **Block Assignment** - Assign vault passwords to blocks or folders via context menu or vault toggle checkboxes
- **Bulk Protect/Unprotect** - Apply or remove know-how protection on all assigned blocks at once
- **Crash Recovery** - Blocks left unprotected due to a crash are automatically re-protected on next project open
- **CSV Export** - Export all vault entries to CSV for backup (includes plaintext passwords, available when vault is unlocked)
- **Localized** - Available in English, German, French, and Italian

### Find in Project (Cross-Reference Search)

- **Project-wide Reference Search** - One search box finds every block, tag, and UDT reference across the open TIA project
- **Hotkey + Right-click** - Press `Ctrl+Shift+F` from anywhere to open the tab, or right-click any block in the project tree and choose "Find References"
- **Click to Navigate** - Double-click any result to open the source block in the SCL editor with the cursor on the matching line
- **Right-click Menu** - Right-click any result row for **Open in Editor** or **Copy reference location** to clipboard
- **Definitions Group** - When the search term itself matches a block name, that block appears as its own group at the top of the result tree
- **Diacritic-Insensitive** - Typing `förder` finds `Förder_DB`; works for all German Umlauts and `ß`
- **Scope Filter** - Restrict to Blocks, Tags, UDTs, or search All
- **Per-PLC Filter** - Optional drop-down narrows results to a single PLC in multi-PLC projects
- **Determinate Progress** - Progress bar shows current candidate / total candidates while scanning
- **Result Cache** - Re-running the same search within 30 seconds returns instantly without round-tripping the bridge
- **Cancel-Friendly** - Each new keystroke cancels the in-flight scan via 250 ms debounce
- **Live Language Switch** - Scope labels and group headers update immediately when you change the application language
- **Result Cap** - Hard cap of 2000 hits with a "refine your search" banner when reached
- **Requires TIA Portal V18 or later** - Earlier versions show an explanatory message in the error footer

### Find Unused Blocks

- **Dead Code Detection** - Finds unused blocks
- **Call-Graph Analysis** - Based on actual calls, not just references
- **Safety Block Support** - Also supports F-blocks (F_FB, F_FC, F_DB, F_OB)
- **Configurable Analysis Scope** - Toggle inclusion of Blocks (FC/FB), Data Blocks (DB), UDTs, and Tags individually
- **Exclusion Patterns** - Define wildcard patterns (e.g. `FB_Test*;DB_Temp*`) to exclude items from results
- **Reuse Exports** - Optionally reuse previous XML exports for faster repeated analysis
- **Persistent Settings** - All analysis preferences saved via gear icon in toolbar
- **Export Function** - Export results as text file
- **Copy to Clipboard** - Copy all results for documentation
- **Delete Function** - Remove unused blocks directly

### AI Integration (MCP Server)

- **Model Context Protocol** - Integration with any MCP-compatible AI assistant
- **Project Context** - AI has access to your project structure
- **Code Generation** - AI can generate SCL source code for blocks
- **DB Generation** - AI can create Data Blocks with Simatic ML templates
- **UDT Generation** - AI can create User-Defined Types
- **Tag Table Generation** - AI can create Tag Tables
- **Auto Import** - Generated code can be automatically imported into TIA Portal
- **Block Analysis** - AI can read and analyze existing blocks
- **Live session indicator** - Status bar shows `MCP: <n>` for active proxy-mode AI client connections; click to open the sessions dialog with client details and a built-in setup guide (Claude Desktop, Claude Code, LM Studio, Continue.dev) with copy-ready snippets

### AI Chat

- **Reasoning Effort** - Pick per agent how hard deep-thinking models think before replying (Low / Medium / High). Switch on the fly from the composer bar's brain chip or under Settings → Agents → Capabilities.
- **Provider Settings Tab** - Cross-agent provider console in AI Chat Settings. GitHub Copilot card shows sign-in status, enterprise domains, reasoning-model policy state, and Retry / Verify buttons. Placeholder cards preview the cross-provider Manage Language Models browser.
- **Manage Language Models** - Cross-provider catalog browser behind the gear icon in the composer bar. Combines GitHub Copilot's catalog, the OAuth catalogs (OpenAI Codex, Google Gemini CLI, Antigravity), a live-fetched list for every API-key agent (Anthropic, OpenAI, OpenRouter, Mistral, XAI, Groq, Cerebras, DeepSeek, Perplexity, Together, HuggingFace, Ollama, LM Studio, and more), plus static AWS Bedrock rows. A Copilot-specific **Policy** column shows Enabled / Failed / Admin-managed status per model with a right-click **Retry Copilot model policy** action for failed rows. Azure OpenAI agents can register multiple deployments per agent and each one appears as its own row. The status bar calls out the live-fetched count; Refresh invalidates the 5-minute cache. Right-click or click **Use in active agent** to apply a model in one step.
- **Context Folders** - Register folders the AI can browse using file read and search tools
- **Instruction Files** - Inject Markdown files into the AI's system prompt automatically at session start
- **Git Integration** - AI is aware of your git repository, branch, and changes; can view status, stage files, commit, push, and pull (mutating operations require user approval)
- **Commit Templates** - Define commit message templates; the AI follows the active template when generating commits
- **Skills** - Place `.md` files in `%LocalAppData%\TiaOpennessManager\skills\` to create reusable prompt commands accessible via the `/` command palette in the chat input; no frontmatter required (just plain text works), optional YAML frontmatter for name, description, and icon
- **Agent Configs** - Place `.json` files in `%LocalAppData%\TiaOpennessManager\agents\` to define AI personas with custom system prompts and tool access; three built-in agents included (General Assistant, Git Assistant, SCL Expert)
- **File Attachments** - Drag and drop images (`.png`, `.jpg`, `.bmp`, `.gif`, `.webp`) or text files (`.cs`, `.xml`, `.json`, `.txt`, `.md`, `.yaml`, `.csv`, `.log`, `.scl`, `.cfg`) into the chat; images are resized and sent as multimodal content
- **Clipboard Paste** - Press Ctrl+V to paste a screenshot from the clipboard directly into the chat; also available via the attach menu
- **Chat Sessions** - Conversations are saved automatically; create new chats, switch between sessions, and resume previous conversations from the history panel
- **Session Archive** - Archive old sessions to keep the session list clean; restore or permanently delete archived sessions
- **Agent Memory** - Each agent has its own persistent memory store across sessions with scope isolation (Local, Project, or User); the agent automatically saves important facts and injects relevant memories into context at session start; supports `memory_store`, `memory_search`, `memory_list`, `memory_update`, and `memory_delete` tools; configurable embedding provider (OpenAI, Google, Ollama, LM Studio) for semantic search, with keyword fallback; Memory Settings panel to view, delete, export (JSON), import, and clean up old memories; Memory Snapshots allow pre-seeding agents with team-shared knowledge via JSON files
- **Sub-Agent Steering** - Agent can dispatch sub-tasks to independent sub-agents (`run_subagent`); up to 5 concurrent sub-agents; manage running sub-agents via `manage_subagents list/kill/steer`; non-blocking mode allows the main agent to continue working while sub-tasks run in the background
- **Hooks** - Configurable event hooks that run before/after AI tool calls; add custom hooks in AI Chat Settings as shell commands or HTTP callbacks; built-in hooks protect safety blocks and log TIA operations; hooks can modify tool input, block execution, or add context to results; configurable timeout per hook (default 60s)
- **Inline Tool Approvals** - Approve or deny each AI tool call directly inside the tool-call message in the chat; the approval buttons are part of the scrollable content, so you can continue reading messages, scrolling history, and switching tabs while an approval is pending; four choices per call: Deny, Allow Once, Allow for Session, or Always Allow (persisted to disk); if the application is closed during an approval, the session can be resumed safely
- **Tool Call Transparency** - Each AI tool call in the chat shows the operation and its target at a glance (e.g. *"Read (src/main.cs · lines 1-50)"*, *"Git Status"*); completed calls show a green check with a short summary, errors show a red X, and rejected approvals show an amber shield — so you always know what the assistant did without expanding the bubble
- **Permission Modes** - Cycling toggle button next to the send button selects how write operations are approved: **Default** asks for every write, **Accept Edits** auto-approves file edits while still asking for shell commands and destructive operations like delete or force-push, **Auto** auto-approves everything except dangerous operations (PowerShell, process access, network writes); the current mode is shown with a colored icon and tooltip; Plan Mode is a separate dedicated toggle that forces the AI to submit an approved plan before any writes
- **Inline Plan Approval** - When the AI submits an execution plan, the plan appears as an editable text area directly inside the chat with Approve and Reject buttons; you can modify the plan before approving; non-blocking — scroll history or switch tabs while reviewing
- **Command Queue** - Send messages while the AI agent is working; messages are queued with priority levels (Now/Next/Later) and processed automatically after each turn; queue indicator shows pending message count; ESC cancels the current operation and clears the queue, or pops queued messages back into the input field when idle
- **Multi-Session** - Run multiple AI chat sessions simultaneously; the Agent Sidebar (toggle via PanelLeftOpen/PanelLeftClose icon) slides out as an overlay from the left and shows all sessions grouped by status (In Progress / Completed); each session has its own chat context, canvas, and agent/provider; sub-agents are routed to their parent session automatically; unread message badges with blink animation notify you of activity in other sessions; double-click a session name to rename it; close sessions via the X button (with confirmation if still running); the canvas state is preserved per session and replayed on switch; live preview text under each session name shows incoming messages and responses from other sessions
- **Per-Session Agent** - Each session remembers its agent/provider/model selection independently; switch to a different provider in one session without affecting other sessions; the agent switches automatically when you change sessions
- **Cross-Session Communication** - Agents can send messages to other sessions via send_agent_message; target sessions auto-resume without manual input; the AI sees all active sessions with their provider/model in the system prompt
- **Scheduled Tasks** — schedule autonomous AI agent runs on cron expressions, with read-only-tool sandboxing and 24-hour catch-up after offline periods.
- **Workspace File-System Access Control** - The AI's `fs` tool (read/write/create/edit/delete/list/search) is gated by a 5-layer policy plus a hardcoded blocklist. The current TIA project directory and your Desktop/Documents/Temp folders are auto-allowed. Add additional folders in **AI Chat Settings → Workspace** to grant persistent access. Out-of-scope paths trigger an inline approval dialog with **Allow Once / Allow This Session / Allow Permanently / Deny** buttons; permanent grants show a warning with the exact directory that will be persisted. Vault, license, chat database, agent memory, app settings, SSH/AWS/Azure/Kubernetes credentials, Windows/Program Files/AppData internals, browser/OS lock files are always refused — even if the AI requests them via a parent folder you previously allowed. Symlinks and junctions are resolved before the blocklist check, so an attacker cannot bypass via reparse points. UNC paths, `\\?\`, `\\.\` device paths are rejected outright.
- **External MCP Server Plugins (Stdio + HTTP with OAuth 2.1)** - Add external MCP servers to the AI Chat under **AI Chat Settings → MCP Servers**. Stdio (local subprocess) and HTTP (remote URL) transports are both supported. HTTP servers pick an Auth Mode: **None**, **Static header** (fixed bearer token), or **OAuth 2.1** (full RFC-compliant browser-based PKCE login with auto-discovery via RFC 9728 PRM and RFC 8414 AS-Metadata, RFC 7591 Dynamic Client Registration, RFC 8707 Resource-Indicators, automatic refresh-token rotation, sign-out wipes the local credential, Add-flow cancel rolls back tokens). Tokens are stored in Windows Credential Manager. Localized status row reports per-step failures (DiscoveryFailed, ServerOpen, DcrFailed, UserCanceled, StateMismatch, TokenExchangeFailed, NotAuthorized, Network) with actionable hints.

### Git Client

- **Integrated Git UI** - Full visual Git workflow built into the application
- **Activity-Bar Badge** - Git icon shows a count badge for uncommitted changes summed across all open repository tabs; compact format up to 99K+; tooltip names the count with proper plural form per UI language; badge hidden when zero
- **Commit History** - Visual commit graph with branch and tag badges, author, date, and subject
- **Issue Tracker Links** - Commit messages show clickable links for issue references matching configurable patterns (e.g. `#123`, `PROJ-456`); opens the issue page in your browser; configure patterns per repository via Repository Settings → Issue Tracker tab; built-in presets for GitHub, GitLab, JIRA, and more
- **Clickable URLs** - HTTP(S) and FTP URLs in commit messages are auto-detected and open in the browser on click
- **Commit SHA Navigation** - SHA references in commit messages are clickable and navigate to the referenced commit in the history graph
- **Inline Code Rendering** - Backtick code spans in commit messages rendered in monospace with a distinct background
- **Rich Context Menus on Links** - Right-click links to: Copy Link, Open in Browser, Navigate to Commit, Copy SHA
- **Working Copy** - Stage/unstage files, write commit messages, commit with Sign-Off / No-Verify / Reset-Author options
- **Diff View** - Unified and side-by-side diff with TextMate syntax highlighting and hunk-level staging/discarding
- **Stash** - Create, apply, pop, and drop stashes; stash detail view with diff preview
- **Branches & Tags** - Visual branch tree, create/delete/rename/merge/rebase branches, push/pull tags
- **Remotes** - Fetch, pull, push, manage remotes
- **Submodules & Worktrees** - Full support for git submodules and worktrees
- **GitFlow** - GitFlow workflow support (init, start, finish feature/release/hotfix)
- **File History & Blame** - Per-file commit history and git blame view
- **Interactive Rebase** - Visual interactive rebase with drag-and-drop commit ordering
- **Branch Descriptions** - Branch descriptions visible in tooltips
- **Bisect** - Good/bad markers per commit for binary search debugging
- **Colored Status Badges** - File change states (Modified, Added, Deleted, Renamed, etc.) in the Working Copy and Commit Detail views are displayed as colored, rounded badges instead of plain text
- **LFS File Operations** - Right-click any file in the Working Copy to access LFS Track (by filename or extension) and LFS Lock/Unlock; for repositories with multiple remotes, lock/unlock shows a submenu per remote
- **Command Palette** - Press Ctrl+Shift+P inside the Git workspace to open a fuzzy-searchable palette with 14 quick actions (checkout, merge, compare, blame, file history, open file, create branch, create tag, fetch, pull, push, stash, apply patch, configure); commands requiring branch/tag/file selection open a secondary picker; Backspace on an empty filter returns to the main palette; Escape or backdrop click closes. Workspace-scoped — outside the Git tab the same shortcut opens the global Quick Open Bar instead
- **GPG Signature Verification** - Commits show a colored shield badge (green = good, orange = expired/revoked, red = bad) in the commit detail SHA row; hover the badge to see signer identity and key ID; configure GPG signing per repository in Repository Settings
- **Rich Commit Message Editor** - AvaloniaEdit-based editor with subject line guide (dashed "SUBJECT END" line), subject character counter with warning when exceeding 72 characters, column position indicator, and auto-completion for 13 Git trailers (Signed-off-by, Co-authored-by, etc.); toolbar with commit template/history picker and conventional commit builder
- **External Diff/Merge Tools** - Configure an external diff/merge tool per repository in Repository Settings → Diff / Merge Tool tab; supports 13 tools on Windows, 9 on macOS, 9 on Linux (VS Code, Visual Studio, KDiff3, Beyond Compare, WinMerge, Meld, and more); use from context menus on changed files in Working Copy and Commit Detail
- **Stash Apply with Options** - Right-click a stash to apply or pop with options: "Restore index" (--index) re-stages previously staged changes, "Drop after apply" combines apply + drop into a pop operation
- **Stash Diff Toolbar** - Stash diff pane carries Ignore-Whitespace and Side-by-Side toggles; rapid clicks cancel the previous load and start a fresh one, last-toggle-wins
- **Multi-Branch Merge** - Select multiple branches in the sidebar or multiple commits in the history, then merge them all at once with strategy selection (Default, Octopus, or Ours) and optional auto-commit
- **Revision File Syntax Highlighting** - Files browsed at any commit in the "Files" tab are displayed with full TextMate syntax highlighting (consistent with the diff view)
- **Open Local Repository (Ctrl+Shift+O)** - Dedicated popup picks path, target workspace, and bookmark group in one step; the new repository is added to the chosen group on success without an extra edit pass
- **Submodule Revision Compare Window** - "Open Details" on a submodule pointer change opens a read-only compare window with two CommitDetail panes (old and new submodule commits) and a central diff view that walks text, binary, nested-submodule, and Git LFS payload changes between the two pointers
- **Submodule Uncommitted-Changes Badge** - Each submodule in the sidebar shows an inline badge whenever the submodule itself has uncommitted local changes; count tracks the trailing `+` from `git submodule status`
- **Clone with Group + Bookmark** - Clone Repository popup lets you pick a workspace group and bookmark color at clone time; the cloned repository is inserted under the chosen group with the chosen bookmark on success — no separate edit pass
- **Custom Action Argument Format** - Custom Actions use a free-form Argument Format string with `${REPO}`, `${BRANCH}`, `${BRANCH_FRIENDLY_NAME}`, `${SHA}`, `${FILE}`, `${REMOTE}`, and `${TAG}` substitution; a new Branch Selector control type feeds `${BRANCH}` / `${BRANCH_FRIENDLY_NAME}` with local and remote-tracking modes
- **Global Auto-Fetch** - Background auto-fetch is configured under Settings → Git → Auto-Fetch as a single global toggle that applies to every open repository (replaces the previous per-repository setting); the interval (default 10 minutes) is set in the same settings block

### OPC UA Client

- **Direct Connection** - Connect to any OPC UA server by endpoint URL (e.g., `opc.tcp://192.168.0.1:4840`)
- **Auto-Discovery** - Automatically detect PLC OPC UA endpoints from the connected TIA Portal project
- **Authentication Modes** - Anonymous, Username/Password, and Certificate-based authentication
- **Dockable Workspace Layout** - Address Space Browser, Node Information, References, Struct Fields and Watch Table each live in their own dockable panel that can be floated, pinned, rearranged or stacked via the drag-grip on each title bar
- **Address Space Browser** - Browse the full OPC UA address space in a TreeView with node class icons
- **Node Refresh** - Toolbar Refresh button re-fetches the selected node's children from the server, bypassing the local cache, for picking up server-side changes since the last expand
- **Node Search** - Filter address space nodes by name to quickly locate variables
- **Node Information Panel** - Selecting a node shows every OPC UA attribute including Node Id, Browse Name, Display Name, Node Class, Description, Write/User-Write Masks, and for variables Data Type, Value Rank, Array Dimensions, Access Level, User Access Level, Minimum Sampling Interval, Historizing, current Value, Status Code, and Source/Server Timestamp (matches UaExpert)
- **References Panel** - Dedicated panel listing every incoming and outgoing reference of the selected node with direction, reference type, browse name, node class and target node id columns
- **Event Log Panel** - Subscribe to OPC UA events from a notifier node and watch them stream into a Time / Severity / Source / Event Type / Message grid; severity range filter, CSV export with formula-injection guard, and a 5000-entry FIFO ring with bounded UI dispatch under flood
- **History Chart Panel** - Load raw historical values for a variable node over a time range and plot them on a date-time scatter chart; quick 1h / 6h / 24h / 7d presets, calendar pickers for custom ranges, CSV export, and safe handling of out-of-range timestamps / non-numeric values / hostile-server payload sizes
- **Server Diagnostics Panel** - Live read-out of the standard OPC UA server-object hierarchy (server status, capabilities, diagnostic counters, active subscriptions, active sessions) with a configurable 1–60 s poll interval persisted per connection; servers that do not expose the diagnostic subtree show a "Not exposed" placeholder instead of empty rows, transient outages surface in an inline error strip, and exponential back-off avoids hammering a struggling server
- **Auto-Reconnect Banner** - When the keep-alive watchdog detects a lost connection, a yellow banner in the connection header counts the elapsed reconnect time live and offers a Cancel button to stop trying without waiting out the 5-minute timeout
- **Recent Endpoints Dropdown** - The Endpoint URL field is an autocomplete of the last 10 successful connections (per installation, surviving restart); URL variants that resolve to the same scheme + host + port are merged into one entry instead of cluttering the list with duplicates
- **Keyboard Shortcuts** - Ctrl+Enter Connect, Ctrl+D Disconnect, F5 Refresh selected node, Ctrl+W Write the selected Watch Table row — all bound on the OPC UA tab and routed to the active connection
- **Copy NodeId / Copy Browse Path** - Right-click any Address Space node to copy the canonical Node Id or the human-readable browse path to the clipboard
- **View Menu** - Top-toolbar entry on the OPC UA tab that re-opens any tool tab that was closed (Address Space, Type Definitions, Node Attributes, References, Struct Fields, CPU Protection, Watch Table, Event Log, History Chart, Server Diagnostics) without resetting the workspace
- **Call Method Dialog** - Right-click a method node in the Address Space Browser to open a modal dialog that lists input and output arguments with per-type editors (scalar text boxes, array-row editor), runs the call, and shows the returned values and status; closing the dialog cancels any call still in flight
- **Certificate Management Dialog** - Review the client's own certificate plus every server certificate this client has trusted or rejected in a three-tab modal (Own / Trusted / Rejected); trust pending server certificates, reject previously trusted ones, remove obsolete entries, or regenerate the client certificate. A companion Auto-accept toggle in the OPC UA settings flyout switches between automatic trust (default) and manual per-server approval
- **Matrix Editor Dialog** - Right-click a matrix-typed variable in the Address Space Browser to open a spreadsheet-style editor with row and column headers; edit cells individually, track dirty changes, and save the whole matrix back to the server in one write. Read-only matrices stay visible but disable the Save button; matrices with more than two dimensions report an honest "rank not supported" error instead of silently flattening the data
- **Struct Fields Panel** - Read and edit complex struct/UDT values with nested expansion, per-index array rows and dirty-field write-back
- **Watch Table** - Add variables via double-click or drag-and-drop; view Name, Node ID, Data Type, Value, Status, and Timestamp per row
- **Read Values** - Read all watch table variables with a single server request, or read individual rows on demand
- **Write Values** - Write values directly to PLC variables by editing watch table cells
- **Live Subscriptions** - Subscribe to value changes with a configurable interval (in milliseconds); values update automatically without polling
- **Per-Variable Subscribe** - Subscribe to a selection of rows independently of the full watch table
- **Save/Load Configuration** - Save and restore watch table configurations (endpoint URL + variable list) as `.opcua-watch` JSON files
- **Workspace Persistence** - The whole OPC UA workspace (panel layout + open connections + watch table) is restored automatically the next time the app opens. Every open connection tab keeps its own watches, subscriptions, event filter and history range — not only the active tab. A per-tab **Don't persist this connection in workspace** toggle in each connection's Settings flyout lets you exclude a tab from the workspace file and the auto-restore when an endpoint must stay private. A dock-toolbar **Workspace** menu offers **Save Workspace As…**, **Load Workspace…** (accepts both new `.opcua-workspace` and legacy `.json` watch files), and **Reset Workspace**. Passwords stay out of the workspace file — operators re-enter them on reconnect
  - Pane arrangement, splitter positions, and floating / pinned tool windows survive save/load.
- **CSV Export** - Export watch table data to CSV with all columns (Name, Node ID, Data Type, Value, Status, Timestamp)
- **JSON Export** - Export watch table data to structured JSON with full metadata
- **MCP Integration** - Unified `opcua` tool with 9 subcommands for AI assistants: connect, disconnect, browse, read, read_complex, write, write_complex, get_types, subscribe

### S7 Native (S7 Comm+)

- **Direct S7 Comm+ connection** - TLS 1.3-secured native S7 protocol access to S7-1200 (FW ≥ 4.3) and S7-1500 (FW ≥ 2.9) without OPC UA
- **Authentication** - Legacy password and TLS user/password authentication via the built-in driver
- **Symbolic browsing** - Browse all block types (DB/FB/FC/OB) with tag/UDT expansion; absolute addresses (I0.0, MW10, QD20) resolved via manual address dialog
- **TIA tag import** - Import PLC tags from the active TIA Portal project as a "PLC Tags" tree node; IP-based PLC matching
- **Live Watch Table** - Native S7 Comm+ subscriptions push value changes with configurable cycle time; the old fixed-interval polling path is gone
- **Connection status dot** - A coloured dot in every PLC tab header signals the PLC state live (grey = not connected, green = running, yellow = stopped or reconnecting, red = unreachable) with a hover tooltip
- **Automatic reconnection with visible progress** - A "Reconnecting…" banner surfaces under the connection bar while the app restores a lost connection; Watch Table values fade to half opacity and switch to `???` until fresh values arrive; all recovery is handled in the background
- **CPU Protection tile** - Right-dock tab shows the current protection level (None/Read/Write/Full) and password-required flag for the active S7-1500 / S7-1500F CPU; refreshes automatically once on connect
- **Diagnostic Buffer tile** - Right-dock tab lists the most recent CPU diagnostic events (timestamp / event ID / class / priority / OB) read from SSL `0xA0`; firmware-gated to V3.0+ CPUs (older CPUs see a clear unsupported-firmware message instead of a log-spam loop)
- **CPU Identity tile** - Right-dock tab shows MLFB, order number, serial number, hardware version and firmware version read from the PROFINET I&M0 record; works on V2.x and V3.0+
- **Memory Usage tile** - Right-dock tab shows live load/work/retain memory utilization (used vs. total in megabytes plus 0–100 % progress bars); refreshes automatically once on connect

### Unit Testing (Enterprise)

Integrated unit test framework for TIA blocks — write, run and evaluate tests without TIA Portal Test Suite. Requires PLCSIM Advanced V3.0+.

- **Test Explorer** — Tree of all test suites in the project's `.tia-tests/` folder, auto-detects new/deleted/modified files via FileSystemWatcher (500 ms debounce)
- **Live status icons** — Each test case shows its current status during and after execution: ✓ Pass, ✗ Fail, ⊘ Skipped, ⚠ Error
- **Persistent results** — Latest test results are stored in SQLite and reappear automatically in the Explorer on next app start
- **Suite context menu** — Run Suite, Open (as document tab)
- **Test case context menu** — Run Test (single-case execution via TestCaseFilter — remaining cases are marked Skipped)
- **Double-click on suite** — Opens the suite as a document tab in the editor
- **Run All / Run Selected** — Sequential batch execution of multiple suites (PLCSIM single-instance limitation)
- **Search filter** — Live text search across suite and test case names (case-insensitive substring match)
- **Failed-only toggle** — `✗ Failed` button hides all passing suites and shows only those with Fail/Error cases — useful for large test histories
- **Live progress** — While a test is running, phase, current test case and completed/total counters update in real time
- **Result detail grid** — For each test case, all assertions are shown with variable, operator, expected, actual and pass/fail marker
- **Stop mid-run** — Active test execution can be cancelled at any time
- **Automatic block analysis** — Interface, boundary values and dependencies are extracted from the TIA project with a single click
- **Multi-phase test steps** — Optional `act.steps` array authors `write` / `wait` / `assert` sequences directly in the case (e.g. *reset → wait 500 ms → start → wait 2 s → check*). Visual editor exposes per-step **+ Write / + Wait / + Assert** buttons plus per-step **↑ / ↓** reorder and **−** remove. Per-step assertion failure aborts the case immediately with a `Step <N> (assert): …` message; top-level `assertions[]` still runs as a final gate
- **Run History** — Second tab in the right results panel listing every persisted run with status, counts, suite, PLC, hostname and TIA version. Right-click for Open Results · Compare To · Delete · Export HTML · Open Manifest. Project paths are stored as SHA-256 hashes only — never plain text
- **Real-PLC test execution** — New "Real PLC (no PLCSim)" preparation mode runs tests directly against live S7-1200 / S7-1500 hardware via the S7 Native transport. The PLCSim lifecycle is bypassed entirely. Each run is gated by an acknowledgement dialog with a defense-in-depth checkbox so a stray click cannot start a write sequence; safety blocks remain hard-blocked regardless of mode
- **S7 Native label parity** — The S7 transport in the Connection Settings dialog is now labelled "S7 Native" to match the PLC Online tab; the underlying protocol is unchanged
- **Compare Runs** — Third tab opened on demand from Run History. Diffs two runs with summary pills (regressions / fixed / new / removed / stable), filter bar, Swap action, and color-coded case rows showing change-kind, message and duration delta
- **Dock layout** — Test Explorer, analysis tools, test editors and results panel are freely movable dock tools

### Trace / Signal Visualization

Real-time scope for OPC UA signals. Capture PLC values at a fixed cycle, see them as live graphs, and analyse stopped recordings with scope-style tools.

- **Continuous and single-trigger modes** — Continuous keeps the newest samples in a rolling window (30 s to 1 h), single-trigger captures a fixed window around a rising, falling or both-edge condition with configurable pre- and post-samples
- **Auto-reconnect** — If the OPC UA session drops, the trace restarts automatically with the same signals when the session comes back
- **Multi-signal plotting with scaling groups** — Put signals on the main axis, one of four shared right-hand axes (A / B / C / D) or a dedicated own axis per signal
- **Dual cursors with delta** — Click to place t1, click again for t2, drag either one to reposition. The time difference Δt is shown on the plot; the signal table shows Y(t1), Y(t2) and ΔY per signal in the chosen display format
- **Toolbar toggle for cursors** — Show or hide both cursors with a single toolbar button. When turned on for the first time after stopping a recording, the cursors auto-place at 25 % and 75 % of the visible time. Each cursor carries a small t1 / t2 badge; the second cursor shows the live Δt and ΔY right on the line as you drag
- **Per-signal format** — Decimal, Hex, Binary, Bool or Scientific, editable directly in the signal table and applied live to cursor readouts
- **Linear or stepped rendering per signal** — The signal table has a Line column to pick Linear (diagonals between samples) or Step (rectangular waveform, matches how a boolean or bit-style signal actually changes). Switching a signal's format to Bool picks Step automatically
- **Computed signals from formulas** — Combine source signals with `+`, `-`, `*`, `/`, parentheses, built-in math (`abs`, `sqrt`, `min`, `max`, `sin`, `cos`, `log`, ...) and time-aware `deriv` / `integ`; invalid formulas are flagged inline with a red cell border, the error as a tooltip, and the Start button stays disabled until every formula is valid
- **Overview minimap** — Compact strip below the main plot shows the whole recording at a glance; drag the highlighted rectangle to scrub, zoom or pan the main plot — the rectangle follows
- **FFT tab after stop** — Stopped recordings offer a Frequency tab with Rectangular / Hann / Hamming / Blackman windows plus optional dB and logarithmic y-axis
- **Plot interaction** — Pan, rectangle zoom, step zoom in/out, 100 % reset, fit-to-current-window — all available after stop
- **CSV export** — Write the full recording (source and computed signals) with ISO-8601 timestamps to disk
- **MCP integration** — `tia_trace` tool with start / stop / status / export; AI agents can wire source and computed signals directly

### Issue Reporting

Report bugs and request features without leaving the app. The Help menu's "Report Issue" entry opens a dialog where you describe the problem; the app collects system information (app version, OS, .NET runtime, active TIA Portal version, language, license tier) and recent logs, then opens GitHub in your browser with the issue pre-filled. No GitHub account login is required from inside the app — you submit on GitHub yourself.

### One Window per Windows Session

Only one instance of TIA Openness Manager runs per Windows session. Opening a file or folder from Windows Explorer while the app is already running activates the existing window and opens the item there, instead of starting a second copy. Double-clicking the application icon or launching the executable a second time also brings the running window to the front. Different Windows users (including separate RDP sessions) each get their own independent instance.

---

## Supported TIA Portal Versions

| Version | Status |
|---------|--------|
| TIA Portal V15 | Supported |
| TIA Portal V16 | Supported |
| TIA Portal V17 | Supported |
| TIA Portal V18 | Fully supported |
| TIA Portal V19 | Fully supported |
| TIA Portal V20 | Fully supported |
| TIA Portal V21 | Fully supported |

---

## Supported Block Types

### PLC Blocks
- **OB** - Organization Blocks (incl. F_OB)
- **FB** - Function Blocks (incl. F_FB)
- **FC** - Functions (incl. F_FC)
- **DB** - Data Blocks (Global, Instance, Array, incl. F_DB)
- **UDT** - User-Defined Data Types
- **Tag Tables** - Variable Tables
- **Technology Objects** - Motion Control, PID Controllers, Counters, etc.
- **Software Units** - V18+ Software Unit containers

### HMI Elements
- **Screens** - HMI screens and popups
- **Screen Templates** - Reusable screen templates
- **HMI Tag Tables** - HMI-specific tag tables
- **VB Scripts** - VB script functions
- **Connections** - PLC/HMI connections
- **Text Lists** - Multi-language text lists
- **Graphic Lists** - Graphic/symbol lists

### Hardware
- **Device Configuration** - Hardware setup as AML/XML

---

## License Options

### Basic (FREE)
- **Free forever** - No trial period, no expiration
- 1 file export/import per operation
- Block Compare
- Code Editor
- Hardware Overview

### Professional (CHF 9.99/month or CHF 99.99/year)
- **1,000 files** export/import per operation
- **Annual plan saves 17%** (2 months free)
- Everything in Basic, plus:
- Find Unused Blocks
- Safety Block Support (F_FB, F_FC, F_DB, F_OB)
- Protection Profiles
- MCP Server Integration
- AI Chat
- Project Library Operations
- Priority Support

### Enterprise (CHF 29.99/month or CHF 299.99/year)
- **Unlimited files**
- **Annual plan saves 17%** (2 months free)
- Everything in Professional, plus:
- Password Vault
- Unit Testing
- Multi-user licenses
- Dedicated support
- Volume discounts

### Trial Period
- **30-day free trial** with all Enterprise-level features
- No credit card required
- After 30 days, falls back to Basic (free)

---

## Activation

### Online Activation
1. Purchase subscription at: https://www.tiaopenessmanager.ch
2. Receive activation code via email
3. Enter code in the program under **View → Settings → Manage License**
4. License is bound to your hardware

### Manage Subscription
- Click "Manage Subscription" in the License dialog
- Opens Stripe portal for payments, invoices, and cancellation

---

- **Multi-language** - German, English, French, Italian

---

## Disclaimer

The software is provided "as is". The provider assumes no liability for damages caused by use. The user bears full responsibility for reviewing all generated content. See EULA at https://www.tiaopenessmanager.ch

---

**Contact:** For questions, contact us at [support@tiaopenessmanager.ch]

**© 2025-2026 AnyAutomation. All rights reserved.**
