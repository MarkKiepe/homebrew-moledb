# MoleDB

Homebrew cask for [MoleDB](https://moledb.com/), a local-first desktop SQL client.

The cask installs `MoleDB.app` from the Apple Silicon disk image on GitHub Releases (`MoleDB-<version>-arm64.dmg`). It does not download the website `.pkg`.

## Install

```bash
brew install --cask markkiepe/moledb/moledb
```

This cask is Apple Silicon (`arm64`) only. An Intel (`x64`) disk image is not published yet, so `brew install` stops on Intel Macs.

If you previously tapped `MarkKiepe/database-viewer` or installed the `database-viewer` cask, run `brew update` and then `brew upgrade --cask moledb`. GitHub redirects the old tap repository to `MarkKiepe/homebrew-moledb`, and this tap's `cask_renames.json` migrates the old cask token to `moledb`. You can also untap the old name and install with the command above.

## Upgrade

```bash
brew update
brew upgrade --cask moledb
```

A Developer ID build also checks GitHub Releases from inside the app.

## Uninstall

```bash
brew uninstall --cask moledb
```

To remove the app and its local data (saved connections under `~/Library/Application Support/database-viewer`, plus the older `databae-viewer` and `Database Viewer` folders):

```bash
brew uninstall --cask --zap moledb
```

## After a release

Tag the release on `MarkKiepe/database-viewer` first. From a checkout of this tap, pass that version:

```bash
bash scripts/bump-cask.sh 0.1.8
```

The script reads the sha256 digest of `MoleDB-<version>-arm64.dmg` from the GitHub release asset. If the digest is missing, it downloads that DMG and hashes it, then updates `Casks/moledb.rb`. Add `--print-only` to print the version and checksum without editing the cask.
