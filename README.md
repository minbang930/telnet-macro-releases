# Telnet Macro Releases

Public binary distribution repository for Telnet Macro.

The source code remains in the private `minbang930/telnet-macro` repository. This repository contains only release assets and the update manifest consumed by the application.

## Publishing a release

1. In the private source repository, run `./release.ps1` from the release branch.
2. Confirm the full build/test suite succeeds.
3. Create a GitHub Release here with the tag printed by the script, for example `v26.08.21`.
4. Upload `dist/TelnetMacro.exe` as an asset named exactly `TelnetMacro.exe`.
5. Confirm the uploaded asset is downloadable.
6. Copy the generated `dist/latest.txt` into this repository as `latest.txt` and commit it **last**.

Publishing `latest.txt` last prevents installed clients from seeing an update before the executable is available.

## Update manifest

`latest.txt` uses a small key/value format:

```text
version=26.08.21
url=https://github.com/minbang930/telnet-macro-releases/releases/download/v26.08.21/TelnetMacro.exe
sha256=<64 lowercase hexadecimal characters>
```

The application only accepts HTTPS download URLs under this repository's GitHub Releases path and verifies the downloaded executable against the SHA256 value before applying it.

`latest.example.txt` is a template only; clients read `latest.txt`.
