# TIA Openness Manager - Changelog

## v3.5.0 (2026-04-24)

### AI Chat
- **AI Chat** — Importing or generating TIA blocks now always asks for explicit confirmation before changes are applied.
- **AI Chat** — Removing or deleting unit tests now always asks for explicit confirmation before changes are applied.
- **Azure OpenAI** — Chat-completions deployments now respect the configured request timeout on long-running calls.
- **Reasoning effort** — Pick per agent how hard the model thinks (Low / Medium / High) from the composer bar or Settings.
- **Provider settings tab** — New Providers section in AI Chat Settings shows GitHub Copilot sign-in status, enterprise domains in use, the reasoning-model policy state, and a catalog-refresh button. Placeholder cards for the other configured providers preview the upcoming Manage Language Models browser.
- **Manage Language Models window** — New cross-provider model browser behind the gear icon in the composer bar. Search by name or ID, filter by provider, see per-model Tool / Vision / Reasoning badges and the Copilot request multiplier, apply a model to the active agent in one click.
- **Manage Language Models window** — Claude models signed in via Anthropic OAuth now appear in the catalog alongside OpenAI, Google, and GitHub Copilot.
- **Manage Language Models window** — Reasoning, Vision, Tool, context-window and max-output badges fall back to the community model catalog when a provider's /v1/models response does not report them.
- **Copilot model policy badges** — The Manage Language Models window now shows per-model Enabled / Failed / Admin-managed status for GitHub Copilot rows, with a right-click retry for failed models.
- **Azure OpenAI — multiple deployments per agent** — Register additional Azure deployments with per-row Add / edit / Remove controls on an Azure agent and they all appear in Manage Language Models.

### Editor
- **Drag & drop from the Project Explorer** — Drop one or several blocks or offline source files onto the code editor or the Welcome tab; each dropped item opens as its own editor tab.

### PLC Explorer
- **PLC Explorer sidebar** — Keep a list of your frequently-used PLCs in a dedicated workspace, see at a glance which ones are reachable, and double-click to open a connection tab with the IP and protocol already filled in.

### Unit Testing
- **Unit Testing** — workspace renamed from "SCL Unit Testing".

### Bug Fixes
- **AI Chat** — Claude context window no longer reports 1 000 000 tokens when the 1M extended-context toggle is off; the composer bar shows the actual 200 000-token limit your plan uses.
- **Output panel** — Maximize now fills the workspace even while the Welcome tab is open.
- **Welcome tab** — Dropping a file from Windows Explorer or the File Tree onto the Welcome tab now opens it in the editor instead of being ignored.
- **Protection profiles** — Active profile stays applied after Import All.
- **Compare** — Dropping items on the right side now lists them on the right instead of defaulting to the left.
- **Compare** — Side-aware drops refresh the file list immediately, dedupe re-exports of the same block, and keep the header in sync with the clicked file.
- **Compare** — Diff backgrounds, highlights, and minimap now follow the active light/dark theme instead of staying dark.
- **Profiles bar** — Selected profile name is vertically centered, and the add-profile field is wide enough to show its full label.
- **Import / Delete errors** — Failed groups now show their real path, and errors are surfaced in the in-app log as well as the log file.
- **File tree icons** — User-defined data types are recognised and shown with their own icon; non-TIA files no longer borrow block icons.
- **Canvas** — Agent-drawn Canvas2D graphics stay visible after the agent finishes: the placeholder message is cleared on first draw, and drawings are re-painted when the Canvas panel is resized.
- **Canvas** — Mouse clicks on agent-drawn Canvas2D shapes now reach the agent's event handlers; A2UI widgets keep receiving clicks unchanged.

## v3.4.0 (2026-04-22)

### Welcome
- **Welcome tab** — interactive introduction with Get Started walkthrough on fresh install.
- **Recent projects** — the Welcome tab now lists your last opened TIA projects and keeps them up to date, whether you open a project file or attach to a running TIA Portal instance.
- **Recent projects — tidier layout** — file name on top, folder path beneath it, list sits directly under the Start actions instead of being pushed to the bottom of the page.

### Compare Panel
- **Redesigned diff editor** — Consolidated toolbar, cleaner change navigation, SCL syntax highlighting, and a streamlined set of actions (Edit, Save, Discard, Merge, Swap, Clear) alongside the built-in diff controls.
- **Context-lines collapse** — Unchanged stretches far from any edit are folded behind a hunk header; buttons increase or decrease how much context is shown, or expand the entire file in one click.
- **Working edit mode** — Toggle Edit to modify either side of the diff in place and save back to the file or PLC from the same toolbar.
- **Preview Diff works on first click** — No more "cache not found" error on fresh checkouts or new working directories; the baseline is built automatically on the first run.
- **Compare** — Block icons in the file list, matching the project tree.
- **Compare** — Symmetric right-side file list with its own show/hide toggle for inspecting the disk side alongside the TIA side.
- **Compare** — Color-coded change strip at the right edge of each file-list row for at-a-glance change classification.
- **Git** — Diff viewer in commit details and revision compare no longer shows unused Compare-panel buttons.

### AI Chat
- **Write Unit Tests** — now supports AWL/STL blocks in addition to SCL.
- **GitHub Copilot** — now a first-class provider with per-model routing, GitHub Enterprise domain support, and accurate context-window limits for Claude models.
- **AI Chat** — requests longer than 100 seconds now respect the configured timeout instead of being cut short.

### Bug Fixes
- **AI Chat** — AWL→SCL conversion preserves the original block header and comments verbatim.
- **AI Chat** — Completed tool approvals collapse to a compact status line instead of keeping the full warning card on screen.
- **OPC UA** — Method-call, matrix-editor, and certificate-management dialogs show their full content without left-edge clipping.
- **Editor** — Empty split panes close automatically when their last tab is closed.
- **Compare** — Preview Diff surfaces export failures in the status bar instead of leaving the editor blank.
- **Compare** — Each block appears only once in the Preview Diff file list regardless of export format.
- **Settings** — Numeric fields accept direct typing without crashing and commit on Enter.
- **AI Chat** — Copilot usage panel refreshes immediately after switching to Copilot instead of requiring a model-dropdown click.
- **Settings** — Context Window Override and 1M-context hints no longer reference specific third-party subscription tiers.

## v3.3.1 (2026-04-21)

### Compare Panel
- **Drag-and-drop ad-hoc compare** — Drop TIA blocks directly into the Compare panel; the block is compiled, exported with the same strip settings as your file-system export, and both XML and source formats land as their own rows for side-by-side comparison against any file you pick on the right.
- **Preview Diff catches uncompiled changes** — The project is compiled before the fingerprint scan so recent edits always show up in the diff.

### OPC UA
- **Workspace remembers the full pane arrangement** — Save/Load now restores where every panel sits, including floating, pinned, and splitter positions.

### Bug Fixes
- **Compare panel — file list is resizable again** — The splitter between the file list and the diff editor drags between 180 and 500 pixels; the chosen width is remembered across show/hide cycles.
- **AI Chat** — Context compaction — safety-critical tool results (deletions, test runs, compilations) are preserved verbatim through compaction instead of being truncated.
- **S7 driver** — Connection reliability and stability improvements.
- **Unit Testing** — PLCSIM Advanced transport reliability and diagnostic improvements.
- **AI Chat settings** — API Key field reliably appears when a provider needs one.
- **AI Chat** — Ctrl+B sub-agent backgrounding works reliably in all chat contexts.
- **AI Chat** — Stalled responses surface as a clear error instead of hanging; timeouts are tuned per model so long-thinking assistants still complete.
- **AI Chat** — Context handling on long conversations is more reliable, with automatic recovery when a request grows too large.
- **AI Chat** — Describe Project and Document Project run more reliably on very large projects and resume cleanly after an interruption.

## v3.3.0 (2026-04-20)

### AI Chat
- **New providers** — xAI (Grok), Groq, Cerebras, DeepSeek, Perplexity, Together AI, Hugging Face, Z.AI, MiniMax, Fireworks AI, Moonshot AI, Vercel AI Gateway, SGLang, vLLM, Qwen, Alibaba Model Studio, Baidu Qianfan, Volcano Engine, BytePlus, Arcee AI, and Kimi Coding. SGLang and vLLM accept a custom OpenAI-compatible URL.
- **Google Antigravity sandbox** — Sign in with Google to use Claude Opus/Sonnet, Gemini 3 Pro/Flash, and GPT-OSS 120B. No separate key needed.
- **Cloudflare AI Gateway proxy** — Route requests through your Cloudflare gateway with Account ID, Gateway ID, and a chosen downstream provider.
- **Region picker for Qwen, Z.AI, MiniMax, Moonshot** — Switch between Global and China endpoints. Qwen and Z.AI also expose Coding Plan endpoints.
- **Faster built-in skills on large projects** — Describe/Document/Explain Block and Describe/Document Project run noticeably faster.
- **Up arrow recalls queued messages** — With the input empty, the Up arrow pulls queued messages back to edit or drop. Esc still cancels.
- **Sub-agent approvals in main chat** — Prompts appear in the main chat with Allowed / Denied / Interrupted states; sensitive arguments show as `[redacted]`.
- **Queue hint shows current activity** — The indicator explains what the assistant is currently doing.
- **Ctrl+B detaches a sub-agent** — Sends a blocking sub-agent to the background; a chat notification arrives when it finishes. A "(background)" badge marks detached agents; a reminder appears if there's nothing to detach.
- **Long conversations on smaller models** — More reliable on models with smaller context windows.
- **Reasoning model recovery** — Automatic retry when a thinking model runs out of reasoning room without producing an answer.
- **Failed tool calls no longer loop** — After a few retries the assistant falls back to a plain response.
- **Reasoning effort for Azure OpenAI** — The reasoning-effort setting now applies to Azure-hosted models.
- **Canvas snapshots open the canvas automatically** — No need to open the panel first.
- **Cleaner provider error messages** — Provider rejections show a short summary instead of a raw server dump.
- **Stricter tool schemas accepted** — Fixed a detail that caused some providers to reject tool definitions.
- **PLC real-number boundary values in tool results** — Tool results containing NaN or Infinity from the PLC are handled correctly.

### TIA Portal
- **Instant project tree refreshes** — After the first load, refreshes are instant and scoped to the changed area.
- **Selective import from Preview Diff** — Tick the blocks to import; failed imports don't leave the project in a partial state.
- **Preview Diff catches source-file edits** — SCL, AWL and DB source changes without a matching XML change now show up.

### Editor
- **Save and Upload split into two buttons** — Save writes to disk; Upload imports into TIA Portal.

### Unit Testing
- **AI Chat authors test suites end-to-end** — Ask "write tests for FB_X" and the assistant drafts, runs and refines the suite. AI-authored cases carry an "AI" badge. F-CPU (Safety) blocks are refused without confirmation.
- **Inline chat and Accept/Reject diff in the suite editor** — Press `Ctrl+I` for targeted edits streamed as a reviewable diff.
- **AI opens a suite in the editor** — The assistant can open a newly created suite as a tab on request.
- **Variable timeline chart** — Click a test case after a run to plot its watched variables over the cycles.
- **Tag browser with inline edit** — Write tag values from the tag browser with a type-aware editor that validates value ranges.
- **Saved Instances list** — Lists persisted PLCSim instances with Load and Delete actions, including their configured IP addresses.
- **Searchable block picker** — A search box next to the block dropdown filters as you type.
- **Streamlined Connection Settings** — IP address and PLCSIM preparation are shared across transports; switching between PLCSim Advanced and S7 Comm+ keeps the IP.
- **Clearer error for optimized data blocks on PLCSim Advanced** — The suite now reports that the variable isn't reachable and suggests S7 Comm+ instead of a cryptic error code.
- **Open Suite falls back to the project folder** — When no test folder exists yet, the dialog opens in the TIA project folder.
- **Empty state when no project is loaded** — The Test Explorer shows "No TIA Project connected" until a project is open.
- **Virtual-adapter status in the Simulation view** — A status row shows whether the PLCSim virtual adapter is ready.

### Application Shell
- **One app per Windows session** — Opening a file or folder from Explorer activates the running window instead of starting a second copy.
- **Language switch applies to dates and numbers** — Dates, numbers and regional conventions follow the selected language.
- **Correct plural forms per language** — Count-based messages use proper singular/plural in EN/DE/FR/IT; trial dates use each language's short format.

### Trace
- **Zoom and pan stopped recordings** — Drag-pan, rectangle-zoom, step-zoom, reset and fit-y added to the toolbar. Live recording still scrolls.
- **Recording start time on the plot** — Shown as `HH:mm:ss.fff` in the upper-left.
- **Two cursors with Δt** — Click to place t1/t2, drag to move, Ctrl+click to clear; Δt shown in the upper-right.
- **Signal table with per-cursor values** — Shows color, name, tag, format, Y range and Y(t1)/Y(t2)/ΔY; name, format and Y range are editable live.
- **Overview minimap with viewport drag** — Shows the whole recording; drag the rectangle or click to scrub.
- **Frequency spectrum (FFT)** — New FFT tab with Rectangular/Hann/Hamming/Blackman windows, dB and log-Y. Disabled while recording.
- **Shared y-axes (scaling groups)** — Send each signal to Main, one of A–D shared groups, or its own axis.
- **Computed signals from formulas** — "+ Computed" adds a signal defined by an expression referencing `$0, $1, …` with functions like `abs`, `sqrt`, `min`, `sin`, `cos`, `log`, `deriv`, `integ`. Invalid formulas highlight red and block Start.
- **Cursor toggle + labeled readout** — Toolbar toggles both cursors, auto-placing at 25 %/75 %. Each cursor carries a t1/t2 badge; t2 shows live Δt and the first signal's ΔY.
- **Stepped rendering for digital signals** — Pick Linear or Step per signal; Bool switches to Step automatically.
- **Splitter no longer shrinks the plot** — The horizontal splitter correctly resizes the signal table against the plot.

### PLC Online
- **Live connection status dot per tab** — Grey/green/yellow/red dot with a tooltip.


### OPC UA
- **Per-tab workspace persistence** — Each tab keeps its own watch list, subscriptions, event filter and history range. A "don't persist" toggle keeps confidential endpoints out of the workspace file.
- **Workspace auto-restore** — Restores on startup; a Workspace menu lets you save, load or reset workspace files.
- **Edit matrices as a spreadsheet** — "Edit Matrix…" opens a row/column editor; Save writes the whole matrix; read-only matrices are labelled.
- **Certificate Management dialog** — Lists own, trusted and rejected certs; trust/reject/remove pending server certs; regenerate the client cert. An Auto-accept toggle controls automatic trust.
- **Call methods from the Address Space Browser** — "Call Method…" loads arguments, accepts scalars or arrays, runs the call and shows outputs with status.
- **History Chart panel** — Plots historical values over a time range; presets 1h/6h/24h/7d; CSV export.
- **Event Log panel** — Subscribes to events from a notifier node and shows Time / Severity / Source / Event Type / Message; filter by severity; CSV export.
- **References panel** — Shows incoming and outgoing references of the selected node.
- **Node Information grid extensions** — Adds User Access Level and splits Timestamp into Source and Server Timestamp.
- **Workspace as dockable panels** — Address Space Browser, Node Information, Struct Fields and Watch Table are separate dockable panels.
- **Struct fields as expandable tree** — Nested structs and arrays collapse/expand individually; pending edits survive.
- **Array fields in struct writes** — Writing structs with array fields no longer crashes; each element is its own row.
- **Read-only summaries for containers** — Array and nested struct rows show as read-only; only leaf values are editable; writes send only modified fields.
- **Read-only fields surfaced** — PLC-marked read-only fields appear as non-editable text.
- **Struct drops expand in Watch Table** — Dragging a struct adds one row per field; a confirmation asks first for large structs.
- **Copyable read-only cells** — Ctrl+C copies text from read-only cells in Node Information and Struct Fields.
- **Denser grid rows** — Tighter row height and smaller font fit more data on screen.
- **Node Information and Struct Fields side-by-side** — Leaves more vertical space for the Watch Table.

### Bug Fixes
- Fixed Unsubscribe All only clearing the first Watch Table row when several came from the same struct drop.
- Fixed `.db` source files showing a folder icon instead of the data block icon.
- Removed `.spl` and `.s7dcl` from drag-and-drop import targets.
- Fixed log files growing to gigabytes after a cancelled or timed-out operation.
- Fixed Save as Patch in the Git commit history failing when the chosen folder path ended with a backslash.

## v3.2.0 (2026-04-14)

### Unit Testing (BETA)
- **New feature** — Integrated unit test framework for SCL blocks. Write, run and evaluate tests against a live PLCSIM Advanced instance without leaving the app. Requires PLCSIM Advanced V3.0+ (separate Siemens license)
- **Test Explorer** — Tree of all test suites in the project's `.tia-tests/` folder with live status icons (Pass / Fail / Error / Skipped). The explorer auto-detects new, deleted and modified suite files
- **Run tests** — Run Suite, Run Test (single case), Run All, Run Selected from the Test Explorer context menu or the Run button. Live progress streams through phase updates and per-test-case status icons while the run is active
- **Persistent results** — Test results are saved locally and reappear automatically when you reopen the app
- **Search and filter** — Text filter across suite and test case names, plus a "Failed only" toggle that hides all passing suites
- **Test suite editor** — Create test suites with the JSON, Visual or SCL editor modes. Block interface, boundary values and dependencies are extracted from the TIA project with a single click
- **Results panel** — Per-test-case detail grid with Variable, Operator, Expected, Actual and Pass/Fail markers for every assertion
- **Rename and delete suites** — Right-click a test suite in the Test Explorer to rename or delete it. Deleting also clears the run history for that suite
- **Manage test cases** — Right-click a test case to edit its name and description, duplicate it, delete it, or move it up and down in the list
- **PLCSIM Settings dialog** — New toolbar button opens a dialog for per-suite PLCSIM configuration (instance name, IP address, cycle wait time, auto-connect), with an option to save the values as defaults for new suites
- **Failed variable highlighting** — When a test case fails, the affected variable is underlined in red directly in the generated SCL code, with the error message shown on hover
- **Click-to-navigate from results** — Double-clicking a test case in the Results panel jumps to the corresponding position in the suite editor
- **Variable name check before running** — Before a run starts, the manager warns about variable names in the suite that don't exactly match the block interface, including case differences. You can still run the suite after acknowledging the warning
- **Auto-reload of open suites** — Suite files are now automatically reloaded in the editor when they're modified externally, unless there are unsaved local changes
- **One-click test runs for protected projects** — The PLCSIM Settings dialog has a new "Automatic TCP download" preparation mode. Pick it, click Run, and the runner compiles your project, starts a fresh PLCSIM Advanced instance, downloads via TCP over the PLCSIM Virtual Adapter and starts the tests. If your project has master-secret protection enabled, a password field appears in the dialog — check "Remember password" to store it in Windows Credential Manager so every future run picks it up automatically
- **Manage PLCSim instances without leaving the app** — The Unit Testing tab has a new Simulation sub-mode switcher at the top. Switch to Simulation to see every registered PLCSim Advanced instance with inline buttons for Power On, Run, Stop, Memory Reset, Settings, Network and Delete, plus a Tag Browser that connects to any instance and lists its tags with filter, search and auto-refresh
- **Run tests against real hardware or via the PLCSim API** — The Connection Settings dialog (renamed from PLCSIM Settings) now lets each suite pick its transport: PLCSim Advanced for direct API access or S7 Comm+ for real hardware and authenticated TCP access. The S7 Comm+ section owns its own IP, port, rack, slot, TLS, user and password fields, so Unit Testing works independently of any other tab. Passwords are stored in Windows Credential Manager and can optionally be remembered across runs

### AI Chat
- **Removed Terminal Mode from AI Chat**
- **More accurate AI responses** — Built-in agents and skills have been refined to give more reliable results when working with TIA Portal projects
- **Automatic context window sizes** — AI Chat now picks the right context window for every supported model, including brand-new models released after your app version. No more guessing or waiting for an app update when a new model launches
- **Context window override** — Advanced agent settings have a new "Context Window Override" field for setting a custom context window per agent, plus an "Enable 1M context (Anthropic Beta)" toggle that opts Anthropic models into the 1M-token context beta
- **Live sub-agent info in the chat bubble** — Dispatched sub-agents now show their name, current activity, tool count, token usage, elapsed time and a stop button directly in the chat bubble, right where the agent was started. No more jumping between chat and a separate panel to check progress
- **Jump-back button when sub-agents run off-screen** — If you scroll up while a sub-agent is still working, a small pill at the bottom of the chat shows how many agents are running and jumps you back to the first running one when clicked
- **Mouse wheel unsticks auto-scroll reliably** — Scrolling up with the mouse wheel during a streaming response now always stops the chat from auto-scrolling back to the bottom

### Help & Support
- **Report Issue from inside the app** — New Help → Report Issue entry. Pick Bug Report or Feature Request, fill in a title and description, and the app opens GitHub in your browser with the issue pre-filled. System information (app version, OS, TIA Portal version, language) is attached automatically so you don't have to look it up. Bug reports can optionally include recent log lines to help with diagnosis

### Code Editor
- **Syntax Highlighting Persistence** — Fixed syntax highlighting disappearing when switching between editor tabs or rapidly opening blocks. Highlighting now survives tab switches reliably
- **AI inline edits on SCL with special characters** — Fixed AI inline edits failing to match code containing characters like `<`, `>`, `+`, `°`, and quotes. AI edits now work reliably on all SCL code regardless of formatting quirks

### Import / Export
- **Auto-Compile before Export Selected** — Pressing "Export Selected" now automatically compiles the PLC before exporting, so blocks are always up-to-date. If compilation fails, the export continues and skips any still-inconsistent blocks

### Bug Fixes
- Fixed GitHub Copilot chat returning "Misdirected Request" errors for Business and Enterprise Copilot accounts — chat requests are now sent to the account's correct host
- Fixed Project Explorer Disconnect leaving the "Protect: N" badge and the selected protection profile visible after closing the project — both now clear together with the project tree
- Fixed "Clear Protection" leaving the code and attribute toggles visible on blocks — clearing the protection selection now also resets the protection mark and options
- Fixed Project Explorer still showing the project tree after disconnecting while a search filter was active
- Fixed AI Chat responses sometimes appearing with missing code blocks at the end of a message
- Fixed Import/Export settings opened from the View menu showing default values instead of your saved settings, and changes made there being silently discarded
- Fixed MCP Server "Allow Write Operations" toggle resetting to off on every app restart — the setting is now remembered
- Fixed AI Chat Memory settings always showing "0 memories" — the panel now displays memories for the active agent
- Fixed AI Chat agent URLs being silently reset on every app start and whenever the Settings dialog was opened or closed — your configured endpoints are now stable across sessions
- Fixed Git Preferences: date format, 24-hour clock, and "Ignore CR at EOL" settings had no effect — changes are now applied immediately
- Fixed Git Preferences: "Max History Commits" slider had no effect — history now respects the configured limit
- Fixed Git Preferences: "Open in Terminal" always opened cmd.exe instead of the shell configured in Integration settings
- Fixed Git Preferences showing empty Install Path and version 0.0.0 after startup
- Fixed crash when selecting certain protection profiles from the dropdown

## v3.1.0 (2026-04-10)

### AI Chat
- **Inline Tool Approvals** — Tool-call approval buttons now appear directly inside the tool-call message in the chat, instead of a fullscreen popup. You can continue scrolling, reading messages, and working in other tabs while an approval is pending
- **Permission Modes** — New permission mode toggle next to the send button cycles between three levels: Default (ask for every write), Accept Edits (auto-approve file edits, still ask for shell commands), and Auto (auto-approve all non-dangerous tools). The current mode is shown with a colored icon
- **Inline Plan Approval** — Execution plans submitted by the AI now appear inline in the chat with an editable text box, instead of a blocking popup
- **AI sees the editor automatically** — You no longer need to attach a block to the chat for the AI to read it. Ask "Can you see the current block?" and the AI reads the active editor tab directly. Attaching still works if you want the code embedded in the conversation history
- **AI sees all open tabs** — When you have multiple blocks open, the AI can list them, read any specific one by name, and edit any of them without you having to switch tabs first. Ask "What blocks do I have open?" or "Compare FB_Motor and FB_Pump and suggest a refactor"
- **Non-disruptive multi-block edits** — When the AI edits multiple blocks in one response, your current tab stays focused. Edited tabs show a dirty indicator (●) in the tab header so you know they're waiting for review. Switch to each tab to see the inline diff and accept or reject
- **Per-tab Inline Chat (Ctrl+I)** — Each editor tab has its own inline chat. Open the inline chat in one tab, switch to another, open a separate chat there, switch back — both conversations are preserved

### Bug Fixes
- Fixed auto-update installing a corrupted file when the download was interrupted — the app now verifies the download is complete before installing and allows retrying instead of entering a restart loop
- Fixed session and sub-agent elapsed-time counters in the AI Chat sidebar continuing to count after the AI response was finished or when a sub-agent failed to start

### Code Editor
- **Tabbed Editor** — Opening blocks or files now creates individual tabs that can be closed, rearranged, and split side by side. Multiple blocks and files stay open simultaneously without losing context
- **Unified Editor** — Files from File Explorer and SCL blocks from TIA Project now open in the same editor area. Switch between TIA Project and File Explorer using the Activity Bar — open tabs persist across sidebar switches
- **Enhanced Status Bar** — The editor status bar now shows cursor position (Ln/Col), a language selector dropdown, and a Word Wrap toggle alongside the existing line and character counts

### Project Explorer
- **Integrated Toolbar** — Project actions (Rescan, Save, Compile, Safety Login/Logoff) and Protection Profiles are now located directly in the Project Explorer sidebar, keeping them closer to the project tree they operate on
- **File Explorer as sidebar** — Clicking File Explorer in the Activity Bar now swaps only the sidebar (TIA Project Tree ↔ Folder Tree) while keeping all open editor tabs visible. No more losing your editor context when browsing files

## v3.0.11 (2026-04-09)

### Improvements
- Error and warning messages in the Application Log are now color-coded (red for errors, amber for warnings) for easier identification
- **File Explorer: Git Status** — Opening a folder that contains a Git repository now shows file status directly in the tree: modified files appear yellow (M), new files green (U), deleted red (D). Folders show a small colored dot when they contain changed files. Status updates automatically after commits, checkouts, or other Git operations

### Import
- **Transaction Rollback on Error** — When "Fault Tolerant" is disabled in settings, import errors now trigger an automatic transaction rollback, restoring the project to its original state instead of leaving it in an inconsistent state
- **Fault Tolerant Mode** — The "Fault Tolerant" checkbox now controls error behavior: disabled = abort and rollback on first error, enabled = continue importing remaining files

### AI Chat — Skills
- **Skills write to project folder** — Analysis results, documentation, and reports are now saved directly into the TIA Portal project folder instead of cluttering the chat with hundreds of lines of text
- **One-click skill execution** — All skills now auto-send when clicked, matching the behavior of slash commands
- **Automatic sub-agent dispatch** — Skills automatically route tasks to the best specialized AI agent (e.g., SCL Expert for code generation, TIA Analyzer for documentation)
- **Skill version management** — Built-in skills update automatically when a new app version includes improved skill prompts

### AI Chat — Sub-Agents
- **Full tool access** — All sub-agents now have access to all available tools, preventing "missing tool" errors during complex tasks
- **Mandatory agent routing** — The AI reliably delegates specialized tasks (SCL code, block analysis, AWL conversion) to the appropriate sub-agent instead of attempting them directly
- **SCL Expert: UDT support** — The SCL Expert now creates UDTs for complex data structures instead of monolithic blocks with dozens of flat variables. UDTs are generated first, then blocks that reference them
- **SCL Expert: Correct block structure** — Generated blocks now follow the exact TIA Portal import format. Block header comments are placed inside the BEGIN section where TIA Portal preserves them

### AI Chat — Steering
- **Send messages during generation** — You can now type and send messages while the AI is working. The Send button and Stop button appear side by side. Press Enter to steer the AI or add instructions without stopping the current generation

### Code Editor
- **Improved create templates** — New FB and FC templates now include all VAR sections (VAR_INPUT, VAR_OUTPUT, VAR_IN_OUT, VAR, VAR_TEMP, VAR CONSTANT)

### Bug Fixes
- Fixed skills showing full prompt text in chat instead of executing silently
- Fixed skill invocations in one session leaking into other concurrent sessions
- Fixed "Describe Project" overwriting its own generated documentation file with a short summary
- Fixed sub-agents not receiving per-agent instruction files (e.g., Siemens Programming Styleguide for SCL Expert)
- Fixed Send button and Enter key not working during AI generation — steering messages can now be sent at any time
- Fixed Import All failing with "object already exists" error when the default tag table had a different filename than its block name (e.g., Safety Unit default tag tables)
- Fixed operations (Export, Import, Find Unused, etc.) not starting again after cancelling — previously required an app restart
- Fixed editor minimap staying visible with stale content after pressing Clear
- Fixed TIA Portal connection showing false warning messages in the log on first Connect
- Fixed Inline Chat (Ctrl+I) not opening — the shortcut now works reliably regardless of editor focus state
- Fixed syntax highlighting not working in the Code Editor tab
- Fixed AI Chat tool categories (Visual Context, Agent Memory, Skills) missing from Settings — toggling them in Settings now works the same as in the chat dropdown
- Fixed AI tools found via "Search Tools" failing with "Function not found" when the AI tried to use them in the same response

## v3.0.10 (2026-04-07)

### AI Chat — Providers & Authentication
- **Sign In via OAuth** — All major AI providers now supported via OAuth login in addition to API keys. Choose per agent: use your subscription, no more API keys required for these flows. One click "Sign in with X", tokens stored securely in Windows Credential Manager, automatic refresh, switch back to API key anytime.
- **Full Enterprise Provider Coverage** — Added Mistral, Azure OpenAI, Google Vertex AI, and AWS Bedrock as first-class providers alongside the existing Anthropic/OpenAI/Google/Ollama/LMStudio/OpenRouter/GitHub Copilot options. Choose EU-based Mistral for GDPR workloads, Azure OpenAI with your own deployment name for compliance-bound data residency, Vertex in europe-west regions with GCP credentials, or Bedrock (Claude/Llama/Mistral/Titan/Nova) with AWS IAM.
- **Prompt Caching** — Significant token cost reduction via stable system prompt architecture. Anthropic achieves 98–99% cache hit rate from the second request onward (~60% cost savings per session). OpenAI/Copilot benefit from automatic caching via stable prefix ordering.

### AI Chat — Multi-Session & Agents
- **Multi-Session Support** — Run multiple AI chat sessions simultaneously. A new Agent Sidebar (toggle with sidebar button) shows all active and completed sessions with live status, elapsed timers, and unread badges. Sub-agents appear indented under their parent session. Create new sessions anytime — even while the AI is working.
- **Per-Session Agent & Provider** — Each session can use a different agent and provider independently. Switch agents mid-workflow without affecting other running sessions.
- **Session Isolation** — Creating a new session during active AI generation no longer interferes with the running session. The old session continues generating in the background while the new session is immediately usable.
- **Cross-Session Auto-Resume** — Sessions automatically resume where they left off when reopened.
- **Inter-Agent Communication** — Sub-agents can send messages to each other and to the main agent bidirectionally, enabling collaborative multi-agent workflows.
- **Named Sub-Agents** — Sub-agents now have display names for easier identification in the Agent Sidebar and session history.
- **Fork Sub-Agent with Worktree Isolation** — Sub-agents can work in isolated git worktrees (separate branches), preventing file conflicts when multiple agents edit code simultaneously.
- **Sub-Agent Permission Inheritance** — Sub-agents inherit tool permissions from the parent agent and can bubble new grants back up.

### AI Chat — UX & Input
- **Unified Skills & Slash Commands** — Skills and slash commands are now a single system. Type `/` to see all available commands and skills in a combined popup with Tab autocomplete. Clicking a skill in the palette or typing `/skill-name` invokes it the same way — the command name appears in accent color, while the AI receives the full skill instructions behind the scenes. The AI discovers available skills automatically and can invoke them proactively when a task matches. Supports both flat `.md` files and `SKILL.md` directory format.
- **@-Mention File Picker** — Type `@` to open a directory-navigation file picker. Browse folders, click to attach files directly as context for the AI.
- **Command Queue** — Send messages while the AI is still working. Messages are queued with priority (now/next/later) and processed automatically after the current response completes. No more waiting for the AI to finish before typing the next instruction.
- **Voice Dictation** — Speak to the AI using Whisper speech recognition (local model or API). Choose push-to-talk or toggle mode. Configure language, model, and hotkey in Settings → Dictation.
- **Skill Template Engine** — Skills now support `{{variables}}` and `{{#if}}` conditionals for dynamic prompt templates that adapt to context.
- **Channel Notifications** — External systems (OPC UA subscriptions, MCP server notifications) push real-time events into active AI chat sessions. The AI can react to PLC alarms, value changes, and MCP events automatically — e.g., an OPC UA overtemperature alarm triggers AI diagnosis.

### AI Chat — Context & Memory
- **Agent Memory** — The AI remembers facts, preferences, and project context across sessions. Memory is stored locally and searchable.
- **Per-Agent Memory Scope** — Memory can be scoped to local (this session), project, or user level. Different agents can have independent memory spaces.
- **Context Window Guard** — A 4-tier visual warning system shows context usage with color-coded indicators: normal (gray), warning at 80% (yellow), error at 90% (red), auto-compact at 93%. The AI automatically compacts context before hitting the limit.
- **Tool Loop Detection** — The AI automatically detects repetitive tool-call patterns (generic repeat, ping-pong, no-progress) and breaks out of infinite loops with a circuit-breaker mechanism.
- **Compaction Improvements** — Context compaction now preserves more relevant information and updates summaries incrementally instead of replacing them.
- **Tool Output Guard** — Large tool outputs (e.g., huge git logs or file reads) are automatically truncated to prevent context overflow from a single oversized response.

### AI Chat — Agent Configuration
- **Model Failover Chain** — Configure fallback models per agent in Settings → Agents. If the primary model fails (rate-limit, server error), the AI automatically tries the next fallback model. Supports cross-provider failover (e.g. Anthropic → OpenAI).
- **Auth Rotation** — Add multiple API keys per agent in Settings → Agents. Keys are rotated automatically via round-robin; rate-limited keys receive a cooldown period. Increases effective rate limits without manual intervention.
- **Per-Agent MCP Servers** — Each agent can have its own dedicated MCP server connections defined inline or by reference, enabling specialized tool sets per agent.
- **Per-Agent Hooks** — Define event-driven automation rules per agent (e.g., auto-format after file edits, validation before commits). Supports event, pattern, and decision hooks.
- **Deferred Tool Loading** — Tools are loaded on demand. Sub-agents only receive the tools they actually need, reducing token usage and improving response quality.

### AI Chat — SCL & Code
- **SCL Expert** — Enhanced SCL code generation with Siemens Programming Styleguide compliance, integrated code review, and direct editor integration for AI-generated code.
- **AWL→SCL Converter** — New agent and skill for AI-assisted migration of STL (AWL) code to SCL. Drop AWL source files into the chat for automatic conversion.
- **NF003 Block Headers** — AI-generated SCL code now includes standardized NF003-compliant block headers with title, version, author, and description fields.

### Git Integration
- **Colored Status Badges** — File change indicators in the Working Copy and Commit Detail views are now displayed as colored, rounded badges (Modified, Added, Deleted, Renamed, etc.) instead of plain text labels.
- **Shared "Deal with Local Changes" Control** — Checkout Branch, Checkout & Fast-Forward, and Create Branch dialogs now use a consistent shared control for selecting how to handle local changes (Keep, Stash & Reapply, Discard), replacing duplicated radio button groups.
- **LFS File Operations in Context Menus** — Right-clicking a file in the Working Copy now shows LFS Track (by filename or extension) and LFS Lock/Unlock options when LFS is enabled. For repositories with multiple remotes, Lock/Unlock shows a submenu per remote.
- **Issue Tracker Links** — Commit messages now show clickable links for issue references (e.g. `#123`, `PROJ-456`). Configure patterns and URL templates per repository via Repository Settings → Issue Tracker tab. Supports multiple tracker rules simultaneously.
- **Clickable URLs in Commit Messages** — HTTP(S) and FTP URLs in commit messages are automatically detected and open in the browser on click.
- **Commit SHA Navigation** — Commit SHA references in full commit messages are clickable and navigate directly to that commit in the history graph. Right-click shows options to copy the SHA or navigate to it.
- **Inline Code Formatting** — Backtick code spans (`` `like this` ``) in commit messages are rendered in monospace with a distinct background.
- **Hunk Staging** — Stage, unstage, or discard individual change hunks directly in the diff view (unified and side-by-side).
- **Stash Detail View** — Selecting a stash now shows its changes and a full diff preview in a 3-pane layout.
- **Syntax Highlighting in Diff** — TextMate-powered language-aware coloring in the diff view.
- **Commit Options** — Sign-Off, No-Verify, and Reset-Author checkboxes in the commit area.
- **History Improvements** — Ahead/behind indicators per commit, bisect good/bad markers, show/hide tags toggle, scroll-to-top button, loading indicator, and empty state tips.
- **Layout Switcher** — History view now supports horizontal (side-by-side) and vertical (top/bottom) layout.
- **Keyboard Shortcuts** — Ctrl+Shift+Enter (auto-stage + commit), Ctrl+F (search), Ctrl+O (open file).
- **Branch Descriptions** — Branch descriptions (via `git branch --edit-description`) now visible in tooltips.
- **Compact Folders** — Tree views in the working copy can now display compact/collapsed folder paths.

### Find Unused Blocks
- **Settings Dialog** — New gear icon opens a settings dialog. Configure which item types to include (Blocks, DBs, UDTs, Tags), toggle export reuse, and define exclusion patterns with wildcards (e.g. `FB_Test*;DB_Temp*`). Settings persist across restarts.
- **Compile + ExclusiveAccess** — Analysis now compiles the PLC first and runs snapshots + export inside ExclusiveAccess for data consistency and a native TIA Portal progress dialog.
- **PLC Selector** — Dropdown to choose which PLC to analyze. Exports go to PLC-specific subfolders, so multi-PLC projects don't conflict.
- **Project Save after Deletion** — TIA Portal project is automatically saved after deleting unused items.
- **Deletion Progress** — Progress bar now shows per-item deletion progress instead of staying on "Preparing".
- **Deletion Log** — Timestamped log file written to working directory after each deletion with success/failure per item.

### Import
- **Protected Block Options** — Import Selected and Import All now respect per-block AllowCodeUpdates and AllowAttributeUpdates settings from protection profiles. Protected blocks with AllowCodeUpdates can have their SCL code updated; protected OBs with AllowAttributeUpdates get CyclicTime/PhaseOffset updates via SetAttribute.
- **SCL Folder Placement** — New blocks imported via SCL in Import Selected now land in the correct TIA Portal folder matching the disk structure, instead of always going to root "Program blocks" (V17+).

### Explorer
- **Split View** — Split editors horizontally or vertically, drag tabs between groups, dock and pin panels
- **Auto-Completion** — IntelliSense for SCL: type 2+ characters to see keywords, data types, built-in functions, and document words. Works for all file types in the File Explorer.
- **Code Folding** — Collapse and expand REGION, IF/FOR/WHILE blocks, VAR sections, and FUNCTION_BLOCK declarations. Brace-based folding for C#, JSON, and other languages.
- **Built-in Search** — Ctrl+F opens find and replace with regex, match case, and whole word support (replaces the old search toolbar).
- **SCL Snippets** — Type `if`, `for`, `while`, `case`, `fb`, `fc`, or `region` and press Tab to insert code templates with editable placeholders.
- **Theme Switching** — Editor colors now automatically adapt when switching between Dark and Light themes.
- **Current Line Highlight** — Visual indicator for the active cursor line.
- **Column Rulers** — Vertical guidelines at 80 and 120 characters.

### MCP Tools
- **Tool Consolidation** — Reduced from 81 to 22 MCP tools with multi-category support and dynamic permissions. Less token usage, better AI tool selection.

### Bug Fixes
- Fixed Cancel button not working for Export, Import, and Find Unused operations — pressing Cancel now immediately stops the running operation
- Fixed Import All ignoring AllowCodeUpdates for protected blocks — SCL files were incorrectly filtered out even when code updates were allowed
- Fixed empty export folders created next to PLC folder instead of inside it when "Create Source Folder" was disabled
- Fixed sub-agents unable to send messages back to the main AI agent — inter-agent messaging now works bidirectionally
- Fixed instruction file @include not recognizing bare relative paths (e.g. `@docs/rules.md`)
- Fixed long tool descriptions overflowing UI tooltips

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
The AI Chat has been rebuilt from the ground up.
- **New provider system** — Switch between Anthropic, OpenAI, Google, Ollama, OpenRouter, and GitHub Copilot with provider icons and per-provider settings (temperature, top-p, timeout, custom endpoints)
- **Skills** — Quick-access prompt templates with the scroll icon in the chat input bar. Includes built-in skills (Explore Project, Explain Block, Generate SCL, Compare Blocks) and supports custom user-created skills
- **File attachments** — Drag and drop files directly into the chat. The AI reads text files (Markdown, JSON, source code) via the built-in file read tool
- **Visual Context** — The AI can see and interact with your screen: list windows, capture UI elements, read visual trees, and automate clicks and keyboard input
- **AI Connect** — The AI can connect to TIA Portal on its own via `tia_connect`, running the exact same connection flow as the manual Connect button (tree refresh, profile loading, HMI detection)
- **Chat history** — Conversations are persisted locally with branching (edit/retry), session list, and token usage stats
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
- **Auto-refresh local changes** — File changes are now detected automatically. No more manual refresh needed — changes appear within ~1 second.
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
- **Settings are persisted** — Auto-fetch, interval, default remote, and other repository settings are saved per repository and restored when reopening.
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
- **Commit context menu icons** - All menu items now show SVG icons
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
- **Improved file lists in Working Copy** — Unstaged/Staged file lists now support tree, list, and grid display modes with search
- **Rich commit messages** — Commit subjects now render with highlighted conventional commit prefixes, issue links, and inline code
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

- **New UI** - Modern desktop application with dark theme
- **MCP Server** - Built-in Model Context Protocol server for AI assistant integration
- **OPC UA Client** - Browse and read OPC UA server address spaces with struct support
- **Improved Localization** - Runtime language switching (EN, DE, FR, IT) without restart
- **Auto-Updates** - In-app update mechanism
- **Password Vault** - Encrypted credential storage for TIA Portal connections
- **Enhanced Export** - Source code generation, structured export paths, fingerprint caching

