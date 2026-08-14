# Agent instructions

Read [README.md](README.md) and [REPOSITORIES.md](REPOSITORIES.md) before changing this repository.

## Repository rules

- `pyproject.toml` defines the Python package. `Makefile` owns installation, native app, and launchd commands; `macos-app/` owns the native application.
- `macos-app/Sortwise` is a generated native executable. Keep it ignored and never commit it.
- Validate with an ignored `.venv` and safe offline Python compilation or tests.
- Migration validation must not install the application, modify `/Applications`, load or unload launchd jobs, move personal files, or invoke AI classification.
- Never run `make app`, `make install`, `make launchd-install`, or `sortwise --move` for migration validation.
- Tags beginning with `v` trigger releases and updates to the separate Homebrew Sortwise tap. Treat tags, releases, app installation, file moves, AI calls, and launchd changes as external effects.
- Never implement directly in the clean control checkout. Use the worktree workflow in [REPOSITORIES.md](REPOSITORIES.md).

