# Webkit2Gtk SDK Extension

IMPORTANT: This package is not maintained by nor endorsed by any of Webkit2Gtk's developers. It is maintained solely by the Flathub community. Any issues you find in using this package should be filed in the issue tracker here first.

## Purpose

This package exposes a `webkit2gtk` library to the `org.freedesktop.Sdk`. It may be useful when running applications such as editors like Zed within a flatpak without sandbox escaping. In order for your flatpak using the `org.freedesktop.Sdk` runtime to find it, you will have to set environment variables appropriately or configure your setup. If using in Zed,

## Configuration

The actual build for webkit2gtk was taken from the [org.geany.Geany flatpak](https://github.com/flathub/org.geany.Geany/tree/188484b197994e9725a04a08143dfb5f877be8f2). A few customizations were added to get the build to complete. Some features have been disabled so please review them to determine if this build will suit your purposes:

```
-DCMAKE_BUILD_TYPE=RelWithDebInfo
-DPORT=GTK
-DUSE_GTK4=OFF
-DUSE_SOUP2=ON
-DUSE_LIBSECRET=OFF
-DUSE_LIBBACKTRACE=OFF
-DENABLE_GAMEPAD=OFF
-DENABLE_INTROSPECTION=OFF
-DENABLE_SPELLCHECK=OFF
-DENABLE_DOCUMENTATION=OFF
-DENABLE_MINIBROWSER=OFF
-DUSE_SYSTEM_SYSPROF_CAPTURE=NO
-DENABLE_BUBBLEWRAP_SANDBOX=OFF
```

## Building locally
The package takes a while to build depending on your system.
```
$ flatpak-builder build-dir dev.zed.Zed.yaml org.freedesktop.Sdk.Extension.webkit2gtk4.0.yaml --repo=repo
# If rerunning
$ flatpak-builder build-dir dev.zed.Zed.yaml org.freedesktop.Sdk.Extension.webkit2gtk4.0.yaml --repo=repo --force-clean
# To limit CPU usage for stability, assuming >12 CPUs
$ flatpak-builder build-dir org.freedesktop.Sdk.Extension.webkit2gtk4-0.yaml --force-clean --repo=r
epo
# You might wan to add ccache
$ flatpak-builder build-dir org.freedesktop.Sdk.Extension.webkit2gtk4-0.yaml --force-clean --repo=r
epo --ccache
```

## Contributing

If you wish to make a change, please open a PR. Please make sure your change compiles but note the package takes a while to build depending on your system.
