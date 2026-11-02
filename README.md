# renovate-config

Shared [Renovate](https://docs.renovatebot.com/) preset for aklinkert repositories.

Use it from a repository's `renovate.json`:

```json
{
  "$schema": "https://docs.renovatebot.com/renovate-schema.json",
  "extends": ["local>aklinkert/renovate-config"]
}
```

## Policy

- Builds on `config:best-practices`: GitHub Actions and Docker images are pinned to digests.
- Runs once a week, before 6am on Monday (Europe/Berlin).
- Automerges minor, patch, pin, digest and lock file updates once all status checks pass. Repositories without CI keep these PRs open.
- Major updates and `go` directive bumps always wait for review.
- Waits 3 days after a release before proposing it. Pins, digests and security fixes skip the wait.
- Groups non-major GitHub Actions and Go module updates into one PR each.
- Tracks versions annotated with `# renovate: datasource=<datasource> depName=<name>` above a `*_VERSION` variable in workflows, Dockerfiles, Makefiles and shell scripts.
