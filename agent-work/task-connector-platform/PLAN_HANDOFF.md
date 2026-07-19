# Task Connector Platform planning handoff

## Verified planning baseline

- Repository: `zhilsinger/orca`
- Base branch: `main`
- Feature branch: `feature/task-connector-platform`
- Starting commit: `80e632282c87fce15ea80a7db4105ea68a509f6b`
- Planning date: 2026-07-19

The complete implementation-planning package was generated outside the repository because this session had no verified access to the user's local clone and the GitHub connector could not safely upload the complete archive as repository content.

## Package inventory

The verified package contains:

- 46 Markdown files
- 12 required architecture, migration, security, testing, and validation documents
- 33 independently executable task files
- 455 indexed implementation paths
- 218 existing files planned for modification
- 230 new files planned for creation
- 7 existing files explicitly verified but planned to remain unchanged

Archive SHA-256 values:

- ZIP: `a6c54447674feafeefbe117580158751679820087642d7299511246e17e349f3`
- TAR.GZ: `55fbbb08e9456006c7269f116ad9c9abf3c24e0b9f56421b9e97bdeb4ee84cec`

## Materialize into a verified local worktree

Run these commands from the actual local Orca clone. They derive paths from Git rather than assuming the clone location.

```bash
repo_root="$(git rev-parse --show-toplevel)"
base_branch="$(git -C "$repo_root" symbolic-ref --short refs/remotes/origin/HEAD | sed 's#^origin/##')"
feature_branch="feature/task-connector-platform"
worktree_path="$(dirname "$repo_root")/orca-task-connector-platform"

git -C "$repo_root" status --short --branch
git -C "$repo_root" branch --list "$feature_branch"
git -C "$repo_root" worktree list --porcelain
test ! -e "$worktree_path"
git -C "$repo_root" fetch origin
git -C "$repo_root" worktree add "$worktree_path" "$feature_branch"
git -C "$worktree_path" status --short --branch
git -C "$worktree_path" rev-parse HEAD
```

After downloading the verified planning archive from the associated ChatGPT response, extract its contents into the worktree root so that the final files appear under:

```text
agent-work/task-connector-platform/
```

Then verify the archive and commit the materialized plan:

```bash
# Substitute the actual downloaded archive path.
archive_path="/verified/path/orca-task-connector-platform-plan.zip"

echo "a6c54447674feafeefbe117580158751679820087642d7299511246e17e349f3  $archive_path" | sha256sum --check
unzip "$archive_path" -d "$worktree_path"

git -C "$worktree_path" status --short
git -C "$worktree_path" diff --check
git -C "$worktree_path" add agent-work/task-connector-platform
git -C "$worktree_path" commit -m "docs: add task connector platform implementation plan"
git -C "$worktree_path" push -u origin "$feature_branch"
```

On Windows PowerShell, use `Get-FileHash -Algorithm SHA256` to verify the ZIP before extraction.

## Implementation gate

Implementation begins only after:

1. The complete package is materialized in the verified worktree.
2. `04_FILE_TASK_INDEX.md` and all 33 task files are present.
3. Baseline install, typecheck, lint, and applicable tests are captured locally.
4. Repository-wide legacy-provider searches are rerun locally against the pinned branch.
5. Any new matches are assigned to an existing task or added to the index before code changes begin.
