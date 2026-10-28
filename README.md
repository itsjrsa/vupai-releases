# Vupai downloads

Installers and signed updates for **Vupai**, a workspace for coding agents and
project tools.

[Website](https://vupai.dev) · [Releases](https://github.com/itsjrsa/vupai-releases/releases) · [Help](SUPPORT.md)

**The first public release is being prepared. No installers have been published
in this repository yet.**

## Desktop app

The initial desktop distribution targets **macOS 13.5 or later on Apple Silicon**
(M-series Macs). The installer includes the Vupai app and its local daemon.

When a release is available:

1. Open [Releases](https://github.com/itsjrsa/vupai-releases/releases) and read its
   notes, including any known issues. Releases marked **Pre-release** are testing
   builds.
2. Download the `.dmg` from that release's **Assets**.
3. Open the disk image, drag **Vupai.app** into **Applications**, and launch it
   from there. For a manual upgrade, save your work and quit Vupai first.

## In-app updates

Updater-enabled builds will download and verify updates in the background.
You choose **Restart & update** when ready, or **Later** to keep working.

The restart confirmation explains the impact on active panes across all projects
using the local daemon. Restarting ends their running processes. Save unsaved
work first; afterward, use Vupai's workspace resume flow to continue.

Existing users will need to install an updater-enabled DMG once before subsequent
in-app updates work. The first updater release is still undergoing release
validation; this repository's preparation does not enable updates in older builds.

## What lives here

Release assets include desktop installers, updater archives, detached signatures
and checksum metadata. The app checks its update feed separately; no GitHub login
will be required for public downloads.

The application source is maintained separately. Installers include the applicable
licenses and third-party notices, also available in the app's **About & support**.

See [Help](SUPPORT.md) for installation and update problems, and
[Release guidance](RELEASES.md) for the distribution process.
