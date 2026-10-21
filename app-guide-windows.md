# Using AtomicIQ on Windows

Platform-specific startup and local file details for Windows. For the shared
application walkthrough (Chat, Library, Validator, Marketplace, Curator,
Account, Settings), see [Using AtomicIQ](app-guide.md).

## Install

1. Visit [atomizer.ai/get-started](https://atomizer.ai/get-started), select
   Windows, and download the Windows installer package
   (`AtomicIQ_<version>_x64-setup.exe`). Use the package supplied by your
   organization if you have been given a specific build.
2. Run the `.exe` and follow the setup prompts. AtomicIQ installs for your
   Windows user account and includes the local backend and `llama.cpp`
   runtime. No separate Python installation is required.
3. If setup requests administrator approval to install the bundled Microsoft
   Visual C++ x64 Redistributable, approve that prerequisite installation.
   AtomicIQ itself remains a per-user installation. Restart Windows before
   launching AtomicIQ if setup reports that a restart is required.
4. Open **AtomicIQ** from the Start menu.

Use 64-bit Windows and allow free disk space for the embedded corpus store,
source documents, and downloaded models (a few GB). Internet access is needed
for WebView2 setup if it is missing and for first-launch model downloads.

## Start and reopen the interface

Launch **AtomicIQ** from the Start menu. The desktop app starts the bundled
local service automatically and opens the interface when the service is
healthy. The first startup can take several minutes while AtomicIQ
initializes its corpus store and downloads its model.

Keep AtomicIQ running while you use the interface. The local service is
available at `http://127.0.0.1:8880/` by default and listens only on the local
machine. If startup reports that port `8880` is already in use, close the
conflicting service and relaunch AtomicIQ. Quitting AtomicIQ stops its bundled
backend.

For the next steps, see [Quickstart](quickstart.md#3-create-or-sign-in-to-your-account).

## Local files

AtomicIQ stores user-specific runtime state under:

```text
%LOCALAPPDATA%\ATK\
```

Paste that path into File Explorer's address bar to open it.

| File or directory | Purpose |
|---|---|
| `config.env` | Persistent local configuration, created on first launch |
| `models\` | Downloaded models |
| `iq-stores\default\` | Default embedded corpus store |
| `logs\atk.log` | Launcher log |
| `logs\atk.server.log` | Backend output |
| `logs\atk.err.log` | Backend error output |

These files are operational state, not an integration interface. External
applications should call the [HTTP API](api-reference.md) instead of reading
or modifying the embedded store.
