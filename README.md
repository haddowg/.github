# haddowg/.github

Shared GitHub Actions for the haddowg JSON:API packages.

`.github/workflows/issue-bot.yml` is a reusable workflow that each package calls on issue events.

1. **Screen.** Every new or edited issue or PR goes through static checks, then a Haiku classifier. High-confidence spam gets closed and locked. Anything that looks like prompt injection, or that the classifier isn't sure about, gets `needs-review` and goes no further. Repo owners and collaborators skip screening.
2. **Triage.** Sonnet labels clean issues and PRs, looks for duplicates across all six repos and tries to reproduce bugs with a failing test. It estimates the size of features. Issues from new accounts get labels only.
3. **Fix.** When the maintainer adds `fix-it`, the issue is screened again and Opus opens a draft PR with the fix.

The screening rules and prompts are fetched from a private repo at runtime.
