# AGENTS.md

Guidance for coding agents in this repository. `CLAUDE.md` only includes it.
Project-wide decisions (ADRs), plans and conventions live in
[haltia-de/haltia](https://github.com/haltia-de/haltia) (`docs/conventions.md`
for releases and packages).

## What this is

Alpine's `community/libnice` APKBUILD moved to a newer libnice
(`packaging/alpine/`), built for armv7 by haltia-de/ci's apk workflow. No
libnice sources live here: the APKBUILD fetches the release tarball and
checks its sha512.

## Rules

- Keep Alpine's package name and subpackages: the point is that `apk`
  replaces Alpine's libnice by version. The version must stay above
  Alpine's; drop this repository once Alpine catches up.
- A release is a `vX.Y.Z` tag equal to `pkgver` (with `pkgrel=0`); the
  workflow builds, signs and attaches the apk files.
- After a release, pin it in device-lenovo-b8000h's
  `linux-port/apps/packages.lock`; haltia-de/gst-webrtc builds against it.
- Patches carry a short header saying why; keep them LF.

## Build by hand

```sh
docker run --rm --platform linux/arm/v7 -e WANT_ARCH=armv7 \
  -v "$PWD:/src" -v /path/to/haltia-de/ci:/ci:ro alpine:3.24 sh /ci/build-apk.sh
```

(armv7 on x86 needs qemu-arm registered in binfmt_misc.) The build runs the
test suite under emulation; it takes a while.
