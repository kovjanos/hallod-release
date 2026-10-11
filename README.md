# Hallod releases

This repository is the release feed of **Hallod**, a local dictation app for macOS that lives in the menu bar. There is no source here. The source repository is private.

Each release holds two assets:

- `Hallod-<version>.dmg`: the installer, which is also the archive the in-app updater downloads.
- `appcast.xml`: the feed an installed Hallod reads.

## How an installed Hallod uses it

Hallod reads `releases/latest/download/appcast.xml` from this repository, which GitHub resolves to the feed of the newest release. Hallod asks on its second launch whether it may check for updates automatically, and it makes no automatic check before it has asked. You can also choose Check for Updates… in its menu, and turn the automatic checks on or off in Settings → About.

Hallod rejects a feed without a valid signature. It verifies the EdDSA signature of a downloaded update against the public key built into it before it mounts or extracts the DMG.

## Installing by hand

Open the newest `Hallod-<version>.dmg` and drag Hallod into Applications before you open Hallod. macOS keeps the Accessibility permission with the copy you open, so a Hallod opened from the disk image leaves the one in Applications asking for it.

Hallod is signed with a Developer ID certificate, notarized and stapled, so Gatekeeper accepts it. Requirements: macOS 26 or later on Apple silicon.

## License

Hallod is MIT licensed: see [LICENSE](LICENSE). The licenses of its third-party components are listed in Settings → About, and the DMG carries their notices in `THIRD_PARTY_NOTICES.md` next to the app.
