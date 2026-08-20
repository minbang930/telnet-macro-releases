# Telnet Macro Releases

Public binary distribution repository for Telnet Macro.

The source code remains in the private `minbang930/telnet-macro` repository. This repository contains only release assets and the update manifest consumed by the application.

## Publishing a release

1. In the private source repository, run `./release.ps1` from the release branch.
2. Confirm the full build/test suite succeeds.
3. Create a GitHub Release here with the tag printed by the script, for example `v26.08.21.1`.
4. Upload `dist/TelnetMacro.exe` as an asset named exactly `TelnetMacro.exe`.
5. Confirm the uploaded asset is downloadable.
6. Copy the generated `dist/latest.txt` into this repository as `latest.txt` and commit it **last**.

Publishing `latest.txt` last prevents installed clients from seeing an update before the executable is available.

## Version format

New releases use `YY.MM.DD.REV`, for example `26.08.21.1`. Revision starts at `0` for the first build of a date and increments for additional releases on the same date.

The updater also accepts the older three-part `YY.MM.DD` manifest format and treats it as revision `0` for backward compatibility.

## Update manifest

`latest.txt` uses a small key/value format:

```text
version=26.08.21.1
url=https://github.com/minbang930/telnet-macro-releases/releases/download/v26.08.21.1/TelnetMacro.exe
sha256=<64 lowercase hexadecimal characters>
```

The application only accepts HTTPS download URLs under this repository's GitHub Releases path and verifies the downloaded executable against the SHA256 value before applying it.

`latest.example.txt` is a template only; clients read `latest.txt`.
