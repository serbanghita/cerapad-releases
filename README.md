# CeraPad releases

Binaries for **CeraPad**, the desktop whiteboard. Source is not here; this repository exists only
to distribute signed builds. The web app runs at **[cerapad.com](https://cerapad.com)**, free and
with no download.

## CeraPad (free)

The whiteboard: draw, save, open, export. Boards are files on your own disk. No account, nothing
is uploaded, and the app has no backend. See [cerapad.com/privacy](https://cerapad.com/privacy).

| Platform | Store | Direct download |
|---|---|---|
| macOS | [Mac App Store](https://apps.apple.com/us/app/cerapad/id6805836944) | [`CeraPad-universal.dmg`](https://github.com/serbanghita/cerapad-releases/releases/latest/download/CeraPad-universal.dmg) - universal (Apple Silicon and Intel), macOS 10.15+, signed and notarized with a Developer ID |
| Windows | [Microsoft Store](https://apps.microsoft.com/detail/9pc64pc4scgr) | [`CeraPad-x64.exe`](https://github.com/serbanghita/cerapad-releases/releases/latest/download/CeraPad-x64.exe) - Windows 10/11 (x64); unsigned, so SmartScreen warns on first run - verify with the SHA-256 |
| Linux | - | not yet |

The store is the build to recommend: it updates itself. The direct download is the same app for
whoever cannot or will not use a store account, and it does not update itself - come back here
for a newer one.

The download link above always points at the newest release. Every release carries the same
asset name, so the URL never changes.

## CeraPad Pro

Not available yet. The desktop app plus an AI assistant that can read and edit the board with you.
It will require **your own AI CLI**: the assistant runs the
[Claude Code](https://claude.com/claude-code) or [GitHub Copilot](https://github.com/features/copilot)
CLI already installed on your machine and signed in to your account. CeraPad ships no API key and
never bills you for AI, so without one of those the AI panel will not start. Everything else in
the app works regardless.

That is a deliberate design choice rather than a limitation: your AI usage bills to your own
account, your credentials stay in your own keychain, and no CeraPad server sits between you and
the model.

## Verifying a download

Every download has a SHA-256 beside it. On macOS:

```
shasum -a 256 -c CeraPad-universal.dmg.sha256
```

macOS verifies the signature and notarization itself on first launch, so this is belt and braces
rather than the primary check. To see what Gatekeeper sees:

```
spctl --assess --type open --context context:primary-signature -vvv CeraPad-universal.dmg
```

`source=Notarized Developer ID` is the answer you want.

The Windows `.exe` is unsigned - there is no signature to check, and SmartScreen will warn on
first run - so the SHA-256 is the check that matters. In PowerShell:

```
Get-FileHash CeraPad-x64.exe -Algorithm SHA256
```

The printed hash must match the one in `CeraPad-x64.exe.sha256`.
