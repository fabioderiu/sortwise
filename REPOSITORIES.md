# Repository workspace

## Layout

- Control checkout: `/Users/fabio/workspaces/sortwise/Sortwise`
- Feature and fix worktrees: `/Users/fabio/workspaces/sortwise/worktrees`
- Expected remote: `git@github.com:fabioderiu/sortwise.git`
- The neutral parent `/Users/fabio/workspaces/sortwise` is not a Git repository.

Keep the control checkout clean on `main`, tracking `origin/main`. Product and operational context starts in [README.md](README.md), Python packaging is defined by [`pyproject.toml`](pyproject.toml), installation and native-app commands live in [`Makefile`](Makefile), and the macOS app source lives in [`macos-app/`](macos-app/).

## Feature and fix workflow

1. Open the **Sortwise** project in Nimbalyst.
2. In the clean control checkout, fetch and fast-forward `main` from `origin/main`.
3. Create one dedicated branch and linked worktree under `/Users/fabio/workspaces/sortwise/worktrees`.
4. Bind one Nimbalyst session to that worktree. Use one branch, one worktree, and one session per feature or fix.
5. Never implement in the control checkout, and never treat changing a terminal's current directory as transferring a session.
6. Before editing or committing, verify `pwd`, the Git top level, Git common directory, branch, origin URL, status, and the task or issue.
7. Read [AGENTS.md](AGENTS.md), this file, the relevant project documents, and the task-specific brief.
8. Validate in an ignored `.venv` with safe offline Python compilation or tests. Commit, push, and open or update the PR from that exact worktree.
9. Remove the worktree only after its work is merged or otherwise safely retained.

Python virtual environments remain local to each worktree and ignored. Pip reuses the machine-level cache reported by `python3 -m pip cache dir`; do not commit or relocate cache contents from a repository task.

Do not use validation to install Sortwise, modify `/Applications`, load launchd jobs, move personal files, or invoke AI classification. Never create `v*` tags casually: they trigger GitHub releases and can update the Homebrew Sortwise tap.

