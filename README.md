# CeraPad Pro releases

Binaries for **CeraPad Pro**, the CeraPad desktop app. Source is not here; this repository exists
only to distribute signed builds.

Download the latest macOS build:

**[CeraPad-Pro-universal.dmg](https://github.com/serbanghita/cerapad-releases/releases/latest/download/CeraPad-Pro-universal.dmg)**

Universal (Apple Silicon and Intel), macOS 10.15 or later. Signed and notarized by Apple, with
the notarization ticket stapled, so it opens offline and on a machine that has never seen it.

## You need your own AI CLI

CeraPad Pro's assistant runs the [Claude Code](https://claude.com/claude-code) or
[GitHub Copilot](https://github.com/features/copilot) CLI **already installed on your Mac and
signed in to your account**. CeraPad ships no API key and never bills you for AI, so without one
of those the AI panel will not start. Everything else in the app works regardless.

This is a deliberate design choice, not a limitation to work around. Your AI usage bills to your
own account, your credentials stay in your own keychain, and no CeraPad server sits between you
and the model.

## Verifying a download

Every release publishes a SHA-256 beside the `.dmg`:

```
shasum -a 256 -c CeraPad-Pro-universal.dmg.sha256
```

macOS verifies the signature and notarization itself on first launch, so this is belt and
braces rather than the primary check. If you want to see what Gatekeeper sees:

```
spctl --assess --type open --context context:primary-signature -vvv CeraPad-Pro-universal.dmg
```

`source=Notarized Developer ID` is the answer you want.

## Your data

Boards are files on your disk. There is no account, nothing is uploaded, and the app has no
backend. See [cerapad.com/privacy](https://cerapad.com/privacy).

## Other platforms

Windows and Linux are next. macOS is first because it was the one that could be signed and
notarized end to end.

## Reporting a problem

Open an issue here. Include your macOS version, whether you are on Apple Silicon or Intel, and
which AI CLI you have installed if the problem involves the assistant.
