# libnice

[libnice](https://libnice.freedesktop.org/) 0.1.24 packaged for Alpine 3.24
armv7 under Alpine's own names (`libnice`, `libnice-gstreamer`,
`libnice-dev`, `libnice-dbg`), so `apk` upgrades Alpine's 0.1.22 to it.

GStreamer's WebRTC element (`webrtcbin`, in gst-plugins-bad) needs libnice
0.1.23 or newer; Alpine 3.24 ships 0.1.22, so its gst-plugins-bad is built
without it. With this package [haltia-de/gst-webrtc](https://github.com/haltia-de/gst-webrtc)
builds `webrtcbin` for voice calls on the Haltia tablet (Lenovo YOGA
Tablet 10, [device-lenovo-b8000h](https://github.com/haltia-de/device-lenovo-b8000h)).

The APKBUILD is Alpine's `community/libnice` with the new version and one
patch for musl in a test helper. The update goes to Alpine aports too; when
Alpine ships 0.1.23 or newer, this repository is retired.

Packages come from the signed Haltia apk repository
(haltia-de/packages). License: LGPL-2.1-or-later (libnice itself is
LGPL-2.1-or-later and MPL-1.1).
