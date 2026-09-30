# CI for the VIM3 kernel fork

This branch holds only CI: it is the repository's default branch so that scheduled
workflows run, and it keeps workflow files out of the kernel branches.

- `.github/workflows/rebase-gki.yml` — every Monday, rebases `lineage-23.0` (GKI
  `android16-6.12-lts` + our fork commits after `.gki-fork-base`) onto the latest
  upstream tip, checks that no fork line was lost (`.github/scripts/verify_rebase.py`),
  bumps the marker and force-pushes with a lease. On conflict or content loss it files
  an issue instead. Also runnable by hand (Actions → Weekly GKI rebase → Run workflow).

After it has pushed, update a local checkout with
`git fetch gschuurman && git reset --hard gschuurman/lineage-23.0` (no local work on it first!).
