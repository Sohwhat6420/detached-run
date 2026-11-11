# Changelog

Dates are in Singapore time. The project is pre-1.0, so commands may change between minor versions.

## 0.1.0 (11 Nov 2026)

The first tagged release. It is also part of [headless-kit](https://github.com/Sohwhat6420/headless-kit).

- `start <name> [--cwd DIR] -- <exe> [args...]` asks WMI to create a supervisor, so the job's parent is
  `WmiPrvSE.exe`, not you. The supervisor starts the real command with `windowsHide: true` and logs its output to
  `~/.detached-run/<name>.log`.
- `status`, `stop` and `list`. Liveness is the PID **plus** its creation time, so a recycled PID never reads as alive.
- **Fixed (11 Nov):** `stop` and the supervisor's exit handler could race on the run record's rename on Windows
  (`EPERM`). Each writer now uses its own temp file and retries.
- **Tests:** a 50 ms window watcher with a positive control proves that no window appears. They run serially on
  purpose. CI runs on `windows-latest`.

## Before 0.1.0

- **7 Nov 2026:** published, generalised for a public repo.
- **19 to 26 Oct 2026:** written and proven in a folder that was not a git repository. [DEVLOG.md](DEVLOG.md) has the
  dated story.
