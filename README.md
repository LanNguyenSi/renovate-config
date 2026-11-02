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
- Raises the range in `package.json` together with the lockfile (`rangeStrategy: bump`), so the declared floor matches what is installed.
- Never merges on its own (`automerge: false`); every pull request goes through the repository's normal review and CI.
- Major updates appear only on the Dependency Dashboard issue and are created only after approval there.
- Never proposes a major for `@types/node` or the Node runtime (Docker `node` image, `setup-node`); those follow the planned runtime upgrades.
- Lockfile maintenance is off.

## Changing the preset

The `validate` workflow checks `default.json` with a pinned `renovate-config-validator` on every push and pull request. Every repository that extends the preset picks up a change on its next Renovate run.
