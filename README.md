# CeraPad Pro releases

Binaries for **CeraPad Pro**, the CeraPad desktop app. Source is not here; this repository exists
only to distribute signed builds.

## No downloads yet

There is no public build available at the moment. The first release was withdrawn pending
licensing, and this repository will carry builds again once that is in place.

Meanwhile, **[cerapad.com](https://cerapad.com)** runs the whiteboard in your browser, free and
with no download.

## What CeraPad Pro will be

The desktop app: the same whiteboard, plus an AI assistant that can read and edit the board with
you. macOS first, universal (Apple Silicon and Intel), signed and notarized by Apple. Windows and
Linux after that.

It will require **your own AI CLI**. The assistant runs the
[Claude Code](https://claude.com/claude-code) or [GitHub Copilot](https://github.com/features/copilot)
CLI already installed on your machine and signed in to your account. CeraPad ships no API key and
never bills you for AI, so without one of those the AI panel will not start. Everything else in
the app works regardless.

That is a deliberate design choice rather than a limitation: your AI usage bills to your own
account, your credentials stay in your own keychain, and no CeraPad server sits between you and
the model.

## Your data

Boards are files on your disk. There is no account, nothing is uploaded, and the app has no
backend. See [cerapad.com/privacy](https://cerapad.com/privacy).

## Verifying a download, when there is one

Every release publishes a SHA-256 beside the `.dmg`:

```
shasum -a 256 -c CeraPad-Pro-universal.dmg.sha256
```

macOS verifies the signature and notarization itself on first launch, so this is belt and braces
rather than the primary check. To see what Gatekeeper sees:

```
spctl --assess --type open --context context:primary-signature -vvv CeraPad-Pro-universal.dmg
```

`source=Notarized Developer ID` is the answer you want.
