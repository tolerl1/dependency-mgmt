# dependency-mgmt

Dependabot opens the upgrade PRs; a reusable GitHub Actions workflow runs
`pip check`, `pip-audit` and your tests, then a Claude agent reviews each PR and
comments a compatibility report (compatible / needs changes / breaking, why, and
the exact changes needed).

## Setup per project
1. Copy `templates/consumer/dependabot.yml` to `.github/dependabot.yml`.
2. Copy `templates/consumer/dependency-review.yml` to `.github/workflows/`.
3. Add `ANTHROPIC_API_KEY` as a **Dependabot secret** (Settings > Secrets and
   variables > Dependabot). Dependabot-triggered runs cannot read regular
   Actions secrets.
4. If this repo is private, enable Settings > Actions > "Accessible from
   repositories owned by the user" so other repos can call the workflow.
5. Start with `allow-fix-commits: false` (report only).

## Notes
- Verdicts are only as good as your tests and upstream changelogs.
- Review major bumps manually; don't automerge agent-modified PRs.
