# CeraPad releases

Binaries for **CeraPad**, the desktop whiteboard. Source is not here; this repository exists only
to distribute signed builds. The web app runs at **[cerapad.com](https://cerapad.com)**, free and
with no download.

## Download

| Name                     | Store                                                               | Direct download                                                                                                                                                                                                     |
|--------------------------|---------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| CeraPad Free for macOS   | [Mac App Store](https://apps.apple.com/us/app/cerapad/id6805836944) | [`CeraPad-universal.dmg` (1.3.1)](https://github.com/serbanghita/cerapad-releases/releases/download/v1.3.1/CeraPad-universal.dmg) - universal (Apple Silicon and Intel), macOS 10.15+, signed and notarized with a Developer ID |
| CeraPad Free for Windows | [Microsoft Store](https://apps.microsoft.com/detail/9pc64pc4scgr)   | [`CeraPad-x64.exe` (1.3.1)](https://github.com/serbanghita/cerapad-releases/releases/download/v1.3.1/CeraPad-x64.exe) - Windows 10/11 (x64); unsigned, so SmartScreen warns on first run - verify with the SHA-256    |
| CeraPad Free for Linux   | -                                                                   | not yet                                                                                                                                                                                                             |
| CeraPad Pro for macOS    | -                                                                   | [`CeraPad-Pro-universal.dmg` (1.3.1)](https://github.com/serbanghita/cerapad-releases/releases/download/v1.3.1/CeraPad-Pro-universal.dmg) - universal (Apple Silicon and Intel), macOS 10.15+, signed and notarized with a Developer ID |
| CeraPad Pro for Windows  | -                                                                   | [`CeraPad-Pro-x64.exe` (1.3.1)](https://github.com/serbanghita/cerapad-releases/releases/download/v1.3.1/CeraPad-Pro-x64.exe) - Windows 10/11 (x64); unsigned, so SmartScreen warns on first run - verify with the SHA-256 |

**1.3.1 is a combined release** - both platforms were built the same day, so this tag carries both
platforms' assets rather than being split per platform. That split still applies whenever the two
builds land on different days: each platform ships under its own tag rather than waiting for the
other, and a tag never mixes assets from two different builds behind one version number.

**CeraPad Pro is free to download and unlocked with a licence key.** It adds the AI assistant -
which drives your own installed Claude Code or GitHub Copilot CLI, on your own account - and
peer-to-peer collaboration. Both stay locked until a licence key is entered under Settings. Pro has
no store listing; this repository is where it ships.

**Peer-to-peer collaboration is not part of the free desktop build.** There, boards are local
files on your disk and nothing else.

### Verifying a download

Every download has a SHA-256 beside it, in `shasum` format. On macOS:

```
shasum -a 256 -c CeraPad-universal.dmg.sha256
```

macOS verifies the signature and notarization itself on first launch, so this is belt and braces
rather than the primary check. To see what Gatekeeper sees:

```
spctl --assess --type open --context context:primary-signature -vvv CeraPad-universal.dmg
```

`source=Notarized Developer ID` is the answer you want.

The Windows `.exe` files are unsigned - there is no signature to check, and SmartScreen will warn
on first run - so the SHA-256 is the check that matters. In PowerShell:

```
Get-FileHash CeraPad-x64.exe -Algorithm SHA256
```

The printed hash must match the one in `CeraPad-x64.exe.sha256` (compare ignoring case). The same
commands work for the Pro files with `CeraPad-Pro-` in the name.
