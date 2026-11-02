# renovate-config

Shared [Renovate](https://docs.renovatebot.com/) preset for the LanNguyenSi repositories.

Use it from a repository's `renovate.json`:

```json
{
  "$schema": "https://docs.renovatebot.com/renovate-schema.json",
  "extends": ["github>LanNguyenSi/renovate-config"]
}
```

## What the preset does

- Runs weekly, Monday before 06:00 (Europe/Berlin).
- Waits until a release is at least 7 days old before proposing it (`minimumReleaseAge`), so a compromised or quickly retracted release is unlikely to land.
- Groups all npm patch and minor updates into one pull request per repository, and GitHub Actions patch, minor and digest updates into another.
- Breaking non-major updates (0.x minors, prerelease jumps) go into a separate group that is created only after approval on the Dependency Dashboard.
- Raises dependency ranges in `package.json` together with the lockfile (`rangeStrategy: bump`); `engines`, Docker tags and `setup-node` keep their precision, and `engines` is never changed.
- Never touches npm `overrides`: those are security pins maintained by the CVE sweeps.
- Never merges on its own (`automerge: false`); every pull request goes through the repository's normal review and CI.
- Major updates appear only on the Dependency Dashboard issue and are created only after approval there; `prisma` and `@prisma/*` majors come as one group.
- Never proposes a major for `@types/node` or the Node runtime (Docker `node` image, `setup-node`, `.nvmrc`); those follow the planned runtime upgrades.
- Lockfile maintenance is off.
- Security fixes from GitHub vulnerability alerts bypass the schedule and the release-age wait and arrive as their own pull requests; they need Dependabot alerts enabled on the repository.

## Changing the preset

The `validate` workflow checks `default.json` with a pinned `renovate-config-validator` on every push and pull request. Every repository that extends the preset picks up a change on its next Renovate run.
