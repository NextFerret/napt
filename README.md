
<img width="1079" height="566" alt="napt (1)" src="https://github.com/user-attachments/assets/38786448-1d2c-410a-bc56-240a4a10bf5c" />

# napt — New Advanced Packaging Tool

`napt` is the next-generation package manager for **NextFerret Linux**. Built from the ground up in C++, it combines the robust sandboxing capabilities of `apt-nf-tree` with a refined syntax and native repository management.

The core philosophy of `napt` is **system safety**: operations are performed in a controlled sandbox environment and are only committed to the host system once the transaction is verified as successful.

## Key Features
* **Sandbox-First Execution:** Installs, removals, and upgrades are tested in an isolated environment before affecting the host.
* **C++ Core:** High performance and low memory overhead.
* **Enhanced Syntax:** Simplified commands for modern Linux workflows.
* **Custom Repository Support:** Easily extend your software sources via standard list files.

---

## Usage

```bash
napt [command] [options]
```

### Commands
| Command | Description |
| :--- | :--- |
| `install` | Installs packages in a chroot; syncs to host only on success. |
| `remove` | Removes packages in a chroot; syncs to host only on success. |
| `sync` | Updates local repository metadata. |
| `upgrade` | Upgrades specific or all packages using the sandbox-first method. |
| `dist-upgrade` | Performs a full distribution release upgrade. |
| `purge` | Removes packages along with their configuration files. |
| `clean` | Clears the `napt` download cache to save disk space. |

### Options
* `--apply-host`: Bypasses the sandbox and applies changes directly to the host system (use with caution).
* `-v`: Displays version information.
* `--vb`: Enables verbose logging for debugging `libapt` transactions.

---

## Managing Repositories

To add new software sources, edit the configuration file at `/etc/napt/sources.list`. 

**Format:**
```bash
# [type] [url] [distribution]
deb https://nextferretdur.github.io/repo-nflinux-1/ mustela
```
