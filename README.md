# Linux Package Log Monitor & CLI Analytics (Bash)

A modular Shell/Bash system administration utility designed for Debian/Ubuntu-based Linux distributions. The tool parses system-level package logs (`/var/log/dpkg.log`), indexes package history and states within `/var/local/PackageMonitor`, calculates total installed disk memory, and maintains an LRU (Least Recently Used) deletion cache.

---

## Features & Architecture

* **Log Parsing & Analytics Engine (`monitor.sh`):** Scans and filters `/var/log/dpkg.log` within user-defined date ranges using regular expressions, `awk`, and `grep`.
* **Database & File Indexing (`/var/local/PackageMonitor`):** Stores structured per-package execution logs (`istoric.log`), state persistent files (`stare_curenta.dat`), and aggregated daily indexes.
* **LRU Deletion Cache:** Implements a Least Recently Used eviction policy (`undo_cache.log`) to store and display the last 10 package removal events.
* **Disk Space Tracking:** Queries package metadata via `dpkg-query` to maintain a dynamic total disk footprint log (`total_size.dat`).
* **Interactive CLI Interface (`frontend.sh`):** User-friendly command-line menu providing instant queries for installed packages, historical state changes, partial installs, and size metrics.

---

## Tech Stack & Requirements

* **Language:** Bash / Shell Scripting
* **Target OS:** Linux (Ubuntu / Debian-based OS)
* **System Utilities:** `dpkg-query`, `awk`, `grep`, `cut`, `sort`, `uniq`
* **Permissions:** Root access (`sudo`) required for writing to `/var/local` and reading system logs.

---

## Installation & Usage

1. Clone the repository:
   git clone [https://github.com/](https://github.com/)<YOUR_USERNAME>/dpkg-package-monitor.git
   cd dpkg-package-monitor

2. Set execution permissions:
   chmod +x monitor.sh frontend.sh helper_functions.sh

3. Run the log parser (Engine) to process `dpkg` logs within a desired date range (format: `YYYY-MM-DD`):
   sudo ./monitor.sh

4. Launch the Interactive CLI Frontend to inspect indexed data:
   sudo ./frontend.sh

---

## Project Structure

* `monitor.sh` - Main log parser & indexing daemon
* `frontend.sh` - Interactive CLI menu
* `helper_functions.sh` - Core logic & query functions
* `README.md` - Project documentation
