# homebrew-tap

Homebrew formulae for [spavn](https://spavn.dev) — the terminal-native coding agent.

```sh
brew install tugayoktayokay/tap/spavn
```

## Formulae

| Formula | What it is |
| :--- | :--- |
| `spavn` | One Rust binary: coding agent, tool harness, TUI. macOS (arm64, x86_64) and Linux (x86_64) prebuilt; installs `spavn` plus the `spvn` alias. |

## Updating

`Formula/spavn.rb` is **generated**, not hand-edited. It carries one `sha256` per platform, so it can
only be written after the release archives exist:

```sh
sh packaging/homebrew/sync-tap.sh 0.2.0 /path/to/homebrew-tap
```

That script lives in [`spavn-cli`](https://github.com/tugayoktayokay/spavn-cli/tree/main/packaging/homebrew).
It fails closed: if a tag has no archive for a platform, the formula is not written at all rather than
pointing at a URL that 404s.

Linux arm64 is emitted only when that tag published an `aarch64-unknown-linux-gnu` archive; the region
between the `# BEGIN linux-arm` / `# END linux-arm` markers is owned by the script, so a version that
skipped that target silently drops back to the x86_64 bottle.

## Uninstall

```sh
brew uninstall spavn
brew untap tugayoktayokay/tap
```
