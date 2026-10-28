# Release guidance

This repository distributes Vupai installers and signed updater artifacts.
Application source, builds and signing keys are maintained separately.

## Current state

Public repository visibility, publishing a release and promoting an update feed
are separate actions. Each waits for the maintainer's explicit go-ahead. Opening
the repository does not publish an installer or enable an update feed.

## Keep application source out

Keep only README.md, SUPPORT.md, RELEASES.md and .gitignore in Git. Never push an
application-source branch or its history here.
Upload finalized installers and updater packages as Release assets; do not commit
build output. GitHub's generated source archives contain this small documentation
repository, not the application source.

The .gitignore uses a documentation-only allowlist. It is a convenience guard,
not a security boundary: forced adds and pushes can bypass ignore rules. Review
changes before pushing and keep this repository's checkout separate from the
application source checkout. Before opening visibility or publishing artifacts,
audit every branch, tag and historical tree for unexpected files. Deleting a file
from the latest commit does not remove it from Git history.

## Artifact contract

| Asset | Purpose |
| --- | --- |
| Versioned `.dmg` | First installation and manual upgrades. |
| `Vupai.app.tar.gz` | The finalized, signed and notarized app used by the updater. |
| `Vupai.app.tar.gz.sig` | Detached updater signature. |
| `Vupai.app.tar.gz.json` | Archive version, platform and SHA-256 provenance. |

The initial updater target is `darwin-aarch64`. Release tags use the app's numeric
version, such as `v0.x.y`; every updater release must advance that version.
Testing builds are marked **Pre-release**. Never replace artifacts under an
existing release tag: publish a new version for a correction and retain prior
releases for recovery.

The updater feed is hosted separately from this repository. It contains the
version, release notes, public archive URL and signature. The legacy tester feed
and the desktop updater feed have separate deployment destinations.

## Before the first public release

1. Confirm ownership of the exact HTTPS feed endpoint before building an
   updater-enabled app. An unclaimed hostname is not a release endpoint.
2. Securely provision and back up the updater signing key. Embed only its public
   key in the app; keep all private keys and signing credentials outside this repo.
3. Build the complete app, finalize signing and notarization, then create and sign
   the updater archive. Include the applicable licenses and third-party notices.
4. Rehearse a real signed old-to-new upgrade, including **Later**, active-pane
   impact, workspace resume, failed downloads/signatures, disk and permission
   failures, recovery, relaunch and macOS permission persistence.
5. Review the exact artifacts and release notes. Clearly identify testing status,
   supported systems, known issues and any restart or migration impact.
6. With the maintainer's explicit approval, make this repository public and publish
   the reviewed assets. Provide an updater-enabled DMG for existing users.
7. Verify anonymous artifact downloads, archive checksums and signatures before
   promoting the update feed. A GitHub upload alone must not announce an update.
8. Update the README and support guidance to reflect the actual published release.

## Future releases

Use the same build, validation and promotion gates. Installation remains the
user's decision; publishing an update must never force a restart or silently end
active work. Retain the previous installer and account for recovery-copy storage
when testing repeated failed installation attempts.

This repository intentionally contains no automatic build or publishing workflow.
