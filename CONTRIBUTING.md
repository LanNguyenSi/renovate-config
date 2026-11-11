# Contributing

Participation in this project is governed by the
[Code of Conduct](CODE_OF_CONDUCT.md).

This preset is tuned for the LanNguyenSi repositories. You are welcome to
extend it from your own repositories; changes are accepted when they fit the
repositories it was made for.

## Pull requests

- One topic per pull request, and say why the change is needed: which
  update it lets through or holds back, in which repositories.
- Update the "What the preset does" list in `README.md` together with
  `default.json`.
- The `validate` workflow checks `default.json` with a pinned
  `renovate-config-validator` on every pull request; it must pass.
- Every repository that extends the preset picks up a change on its next
  Renovate run, so a change goes in only through a reviewed pull request.

## License

By contributing you agree that your contributions are licensed under the
MIT license of the project.
