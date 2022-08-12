# sclix_list_projects

A sample CLI extension which lists projects in your Snyk account.

## Building an extension

An extension must produce an appropriately named, os/architecture specific binary in an output folder name `_bin` when running `make build`.

The format of the output files should be `<extension-name>_<OS>_<ARCH>`, where `<extension-name>` is the `name` in the `extension.json`.

Specifically, the following files should be generated in the appropriate situation:

| OS        | Arch     | Executable Binary Output file    | Notes
|:----------|:---------|:---------------------------------|:--------------------------------------------------------|
| macOS     | amd64    | <extension-name>_darwin_amd64    |                                                         |
| macOS     | arm64    | <extension-name>_darwin_amd64    | Note that this output file is `amd_64` and not `arm_64` |
| linux     | amd64    | <extension-name>_linux_amd64     |                                                         |
| linux     | arm64    | <extension-name>_linux_arm64     |                                                         |
| windows   | amd64    | <extension-name>_windows_arm64   |                                                         |

The makefile must also have `make test` target which runs any tests and exists with a zero exit code on success.

The makefile must also have `make install prefix=<prefix>` target, where `<prefix>` is a relative path like `bin`, that copies the binary and the `extension.json` to the given relative path.
