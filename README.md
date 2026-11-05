# homebrew-tap

Homebrew formulae for [spavn](https://spavn.dev) and friends.

```sh
brew install tugayoktayokay/tap/spavn
brew upgrade spavn
```

## Formulae

| Formula | What it is |
| :--- | :--- |
| `spavn` | Terminal-native coding agent, one Rust binary |

## Updating a formula

Release first, then bump the tap — the formula pins published archives by SHA-256, so a version
that is only tagged but not released would 404.

```sh
# after `git tag vX.Y.Z && git push --tags` and the Release workflow finishes
for a in aarch64-apple-darwin x86_64-apple-darwin x86_64-unknown-linux-gnu; do
  printf '%s  ' "$a"
  curl -sL "https://github.com/tugayoktayokay/spavn-cli/releases/download/vX.Y.Z/spavn-$a.tar.gz.sha256"
done
```

Paste the three new digests into `Formula/spavn.rb`, bump `version`, run
`brew audit --strict Formula/spavn.rb`, and commit.
