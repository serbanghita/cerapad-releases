# CeraPad releases

Binaries for **CeraPad**, the desktop whiteboard. Source is not here; this repository exists only
to distribute signed builds. The web app runs at **[cerapad.com](https://cerapad.com)**, free and
with no download.

## Download

| Name                     | Store                                                               | Direct download                                                                                                                                                                                                                 |
|--------------------------|---------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| CeraPad Free for macOS   | [Mac App Store](https://apps.apple.com/us/app/cerapad/id6805836944) | [`CeraPad-universal.dmg` (1.1.4)](https://github.com/serbanghita/cerapad-releases/releases/download/v1.1.4/CeraPad-universal.dmg) - universal (Apple Silicon and Intel), macOS 10.15+, signed and notarized with a Developer ID |
| CeraPad Free for Windows | [Microsoft Store](https://apps.microsoft.com/detail/9pc64pc4scgr)   | [`CeraPad-x64.exe` (1.1.2)](https://github.com/serbanghita/cerapad-releases/releases/download/v1.1.2/CeraPad-x64.exe) - Windows 10/11 (x64); unsigned, so SmartScreen warns on first run - verify with the SHA-256              |
| CeraPad Free for Linux   | -                                                                   | not yet                                                                                                                                                                                                                         |

**1.1.2 is a Windows-only release**, the opt-in firewall rule for direct P2P connections. The
macOS `.dmg` on it is the 1.1.1 build, byte for byte, carried forward so the download link keeps
working; the two platforms are built on different machines and do not always move together. Its
SHA-256 is unchanged, so a checksum you saved before still matches.

### Verifying a download

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
