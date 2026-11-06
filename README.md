# Zouaouid File Manager

**Zouaouid File Manager** is a fast, modern file manager for Windows built as a daily-driver Explorer replacement. It keeps the familiar navigation pane and details view, then adds tabs, multiple windows, the real Windows right-click menus, Shell thumbnails, and an adaptive copy engine that picks the fastest strategy on its own.

The interface stays smooth in folders with thousands of files because the file list is fully virtualized and all Shell work runs off the UI thread.

---

## Key Features

### Navigation
- **Tabs** with independent folder, history, sort and filter state. Pin a tab to keep it open, or right-click it to close, close other tabs, or duplicate it.
- **Multiple windows**, each with its own tabs and history. Open any folder in a new window from its right-click menu.
- **Session restore**: choose a fixed startup folder, or restore every window and tab from the last session.
- **Quick access** with Desktop, Downloads, Documents, Pictures, Music and Videos, plus any folder or drive you pin. Pins can be reordered by dragging.
- **This PC** page listing every drive with its Shell icon, volume name, type and free space.
- **Breadcrumb address bar** with an inline path editor, and long paths that collapse into a "..." menu like Explorer.
- Resizable navigation pane with a lazily expanded folder tree and real Shell icons.

### Files and folders
- **Adaptive copy engine** with progress, speed and Cancel. The progress window only appears when an operation lasts more than a second, so quick copies finish silently with a status-bar message.
- **Copy, cut and paste** using the standard Windows file clipboard, including files copied in Explorer.
- **Drag and drop** selected items onto a folder to move them; hold Ctrl to copy. An optional confirmation prompt can be enabled.
- **Delete** to the Recycle Bin, or **Shift+Delete** to delete permanently, with a themed confirmation.
- **Rename** by slow-clicking a selected name, or inline in the file list, or in a rename window. Hidden extensions stay out of the edit box and are restored on commit.
- **New folders** and files created from the Windows New menu start in rename mode, like Explorer.
- **Real Windows context menus** for files, folders, drives, empty space and the navigation pane, including shell extensions such as 7-Zip, Git and editors, themed to match the app.
- Open, open file location, properties, open in new tab and open in new window.
- **Rubber-band selection** by dragging on empty space, with Ctrl to add to the current selection.

### Views
- Eight layouts: **extra large, large, medium and small icons, List, Details, Tiles and Content**.
- **Shell thumbnails** in the Medium, Large and Extra large icon layouts for pictures, video, PDFs, Office documents and any file type with a thumbnail provider. Video thumbnails carry the default player's icon, as in Explorer.
- Shell icons rendered at 16, 32, 48, 96 and 256 pixels, with custom folder icons taken from the Shell.
- Each folder remembers its own layout.
- Capacity bars and free space on drive rows in Tiles and Content.
- Arrow keys follow the visual grid in the icon, tile and list layouts.

### Interface
- **Dark, Grey and Light themes** with a neutral, Explorer-style selection colour.
- **Folder Options** for hidden files and folders, protected operating system files, and "Always show icons, never thumbnails".
- Settings organised into General, File operations and Tabs.
- **Auto-hiding top-edge menu** that never permanently uses screen space.
- Status bar with item and selection counts plus a quick view switcher.
- System tray support: run at startup, run minimized, minimize to tray, close to tray, and optional run as administrator.

### Keyboard shortcuts
- `Ctrl+C` / `Ctrl+X` / `Ctrl+V` — copy, cut, paste
- `Delete` / `Shift+Delete` / `F2` — recycle, delete permanently, rename
- `Ctrl+Shift+N` — new folder
- `Ctrl+T` / `Ctrl+W` — new tab, close tab
- `F5` / `Ctrl+L` / `Ctrl+F` / `Ctrl+O` — refresh, edit path, search, open folder
- `Alt+Left` / `Alt+Right` / `Alt+Up` — back, forward, up
- `Ctrl+Shift+1` … `Ctrl+Shift+8` — extra large, large, medium and small icons, List, Details, Tiles, Content

---

## The Adaptive Copy Engine

Windows copies a folder one file at a time, so a folder with thousands of small files spends most of its time on per-file overhead. Zouaouid File Manager chooses a strategy from the number of files and keeps the I/O pipeline busy — no configuration needed.

| Strategy | Method | When it is used |
|---|---|---|
| **A** | `CopyFileEx` | A single file, with native progress |
| **B** | Parallel async streams | Under 1,000 files, up to 8 workers |
| **C** | Channel / IOCP | Under 100,000 files, up to 24 concurrent operations |
| **D** | Batched stream / archive mode | 100,000+ files |

Cut and move use the same engine, and the source is deleted only after a successful copy. Existing names are never overwritten: the engine keeps them as `name - Copy` or `name - Copy (2)`.

Copy options: Settings → File operations → **Do not copy empty folders** and **Close copy dialog when complete**.

> **Note:** the fast copy engine does not preserve file timestamps or ACLs.

---

## Requirements

- Windows 10 or Windows 11 (64-bit).
- .NET 10 Desktop Runtime when the build is framework-dependent. If it is missing, Windows prompts you to install it.

The app installs per-user with no administrator rights required. It does not install drivers, background services, scheduled tasks or kernel components.

---

## Install

Download the installer from the [Releases page](https://github.com/tetteykn/Zouaouid-File-Manager/releases).

The Microsoft Store listing will be linked here once it is published.

---

## 💳 Pricing & Trial

- Zouaouid File Manager includes a **free trial** with full functionality.
- After the trial, a **one-time purchase** activates the app permanently on your device.
- **No subscriptions. No recurring fees.**
- **Online recognition**: if the device is connected and a previous purchase is recognised, the app activates automatically — no key entry required.
- **Offline or server unavailable**: enter your activation key manually. Once activated, the app works fully offline.
- One license is active on one computer at a time, and the license is non-transferable.

---

## 📞 Support & Contact

**Email** — zouaouidtech@gmail.com

[![YouTube](https://img.shields.io/badge/YouTube-Demo-red?logo=youtube)](https://www.youtube.com/channel/UCksGhlnuOhirbMzMG3yYJmg)

[![Discord](https://img.shields.io/badge/Discord-Join-5865F2?logo=discord)](https://discord.com/invite/jRnaeTJ)

---

Copyright © 2026 Zouaouid Tech. All rights reserved. See [LICENSE.md](LICENSE.md).
