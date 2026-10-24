# Bumeter Homebrew tap

```bash
brew install --cask bumeter/tap/bumeter
```

## Casks

| Cask | What it is |
|---|---|
| `bumeter` | [Bumeter](https://bumeter.cc) — see where your AI coding tokens go, per conversation, turn and skill |

Bumeter is installed from its [GitHub releases](https://github.com/bumeter/bumeter/releases) and
updates itself from there afterwards. The app is not signed with an Apple Developer ID, so macOS
quarantines the download: open it once with right-click → Open, or

```bash
xattr -dr com.apple.quarantine "/Applications/Bumeter.app"
```

That is why this cask lives in a personal tap instead of `homebrew/cask`, which requires notarized
applications.

## Updating a cask

The files here are generated in the Bumeter repository, then copied over:

```bash
cd ../bumeter
./scripts/packaging.py --version v1.0.6   # hashes the release assets
cp packaging/homebrew/bumeter.rb ../homebrew-tap/Casks/bumeter.rb
cd ../homebrew-tap && git commit -am "bumeter 1.0.6" && git push
```

There is no `livecheck` block: the version and the SHA256 come from the release, so the cask is
bumped in one command above rather than guessed from a page.
