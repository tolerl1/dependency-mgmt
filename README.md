# dependency-mgmt

A library of files copied into other repos. Nothing here is run from this repo.

## Files
- `dependency-update.md` - instructions for the GitHub Copilot CLI to update a
  uv-managed repo's dependencies: one PR with the updates judged safe, one issue
  listing what is blocked and why.

## Use
1. Copy `dependency-update.md` into the target repo, e.g. `.github/prompts/`.
2. From the repo root (with `gh`, `uv` and the Copilot CLI authenticated):
   `copilot -p "Follow the instructions in .github/prompts/dependency-update.md"`
   (tool-permission flags may be needed; see `copilot --help`).
