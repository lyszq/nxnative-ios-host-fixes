# Reviewed, game-free host build input

This folder contains only a source patch, its manifest and a macOS workflow.
It contains no game code, game data, shader exports, keys, saves or IPA.

The workflow combines public upstream commit
`337186cf3ce778dd1b89092e8958652cb4d7ceb3` with fork commit
`59492c868416d82cdd5b57fbbf78753d044412d9` using the release's overlay and
patch procedure, applies the reviewed changes, runs
source integration and native ownership tests, and builds the unsigned/ad-hoc
shell with its Increased Memory Limit entitlement. It publishes a temporary
Actions artifact; it does not publish a release, install an app or sign with
a developer account. Guest.framework, existing game shaders and RomFS remain
on the user's Windows machine for local repacking after the host build.

The native test executes the actual extracted source-load branch against a
fake Metal device and real Foundation/mmap. It covers success and decode/
compile failure cleanup without a GPU. It does not establish GPU correctness.

This repository is a public, game-free build capsule authorized by its owner.
The workflow uses the existing public fork as its base and produces only a
shell build input. The resulting game IPA is assembled locally and is not
uploaded here. No Apple developer signing identity is used by this workflow.

The base project is Copyright (c) 2026 seedds and is distributed under the
MIT license included in LICENSE. The Windows shell route comes from
[xinerqu/ns2ios-shell](https://github.com/xinerqu/ns2ios-shell).
