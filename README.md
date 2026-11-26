# EazyReader for Linux

A calm, local reader for Markdown, text and PDF. Everything stays on your device.

This is a community preview of EazyReader Basic 1.0.72, built for [Omarchy](https://omarchy.org) (Arch Linux + Hyprland). It also runs on other x86_64 Linux desktops.

Site: [https://eazyreader.ai](https://eazyreader.ai)

This repository holds Linux downloads, checksums and issues. The app source is not published here. EazyReader is proprietary freeware from Dataholm LLC DBA EazyReader. See [LICENSE](LICENSE) and [NOTICE](NOTICE).

## Downloads

Get the files from the [v1.0.72-linux release](https://github.com/Chiadok/eazyreader-linux/releases/tag/v1.0.72-linux) (pre-release).

| File | For |
|------|-----|
| `EazyReader-1.0.72-x86_64.AppImage` | Any distro. Carries its own libraries. |
| `eazyreader-1.0.72-x86_64.tar.gz` | Arch, Omarchy and others with webkit2gtk-4.1. Includes `install.sh`. |
| `eazyreader_1.0.72_amd64.deb` | Debian and Ubuntu. |
| `SHA256SUMS` | Checksums for the files above. |

This build is marked pre-release because it has not yet been tested on a real Hyprland or Omarchy machine with a GPU. It was tested on Arch Linux under X11, Sway and Weston.

## Install

Pick one.

**AppImage** (any distro, carries its own libraries)

    chmod +x EazyReader-1.0.72-x86_64.AppImage
    ./EazyReader-1.0.72-x86_64.AppImage notes.md

Needs FUSE 2 (`sudo pacman -S fuse2` on Arch). Without it, run with
`--appimage-extract-and-run`.

**Tarball** (uses your system WebKitGTK, smallest download)

    tar xzf eazyreader-1.0.72-x86_64.tar.gz
    cd eazyreader-1.0.72-x86_64
    ./install.sh                 # installs to ~/.local, no root
    ./install.sh --set-default   # same, and opens .md files with EazyReader

Needs `webkit2gtk-4.1` and `gtk3` (Arch: `sudo pacman -S --needed webkit2gtk-4.1 gtk3`).
Remove with `./install.sh --uninstall`.

**Debian / Ubuntu**: `sudo apt install ./eazyreader_1.0.72_amd64.deb`

An AUR package (`eazyreader-bin`) is planned. It is not published yet.

## Verify your download

    sha256sum -c SHA256SUMS

## Open files

- From a terminal: `eazyreader file.md other.md`
- From your file manager: double-click any `.md` file once EazyReader is the
  default (`xdg-mime default eazyreader.desktop text/markdown`).
- Opening another file while EazyReader runs sends it to the open window.
- Ctrl+O opens files, Ctrl+, opens Settings.

## Omarchy and Hyprland notes

- On Hyprland, Sway and niri the window has no title bar, so it tiles cleanly.
  Floating desktops (GNOME, KDE) keep a normal title bar.
  Force either with `EAZYREADER_DECORATIONS=1` or `EAZYREADER_DECORATIONS=0`.
- The window class is `eazyreader`, for Hyprland window rules, for example:
  `windowrule = float, class:^(eazyreader)$`
- File dialogs use xdg-desktop-portal when it is running.
- On NVIDIA, EazyReader turns off the WebKit DMA-BUF renderer automatically to
  avoid a blank window. If you still see one, try
  `WEBKIT_DISABLE_COMPOSITING_MODE=1 eazyreader`.

## Known limits

- In-app updates. Update by downloading the new version (or through the AUR, once it is out).
- On-device AI features (they rely on Apple Intelligence on the Mac).
- Moving files to the system Trash. Move to Trash removes a document from
  EazyReader and leaves the file where it is.
- ARM64 builds.
- PDF reading and PDF to Markdown are included but have had less testing on Linux.
- Not yet tested on real Omarchy hardware, NVIDIA, HiDPI scaling, or
  xdg-desktop-portal-hyprland.

## Your data

Your library lives in `~/.local/share/ai.spork.eazyreader.basic`. EazyReader
does not upload your documents.

## Issues and feedback

- [Report a bug](https://github.com/Chiadok/eazyreader-linux/issues/new?template=bug.yml)
- [Send feedback](https://github.com/Chiadok/eazyreader-linux/issues/new?template=feedback.yml)

Please include your distro, desktop (for example Hyprland or GNOME), and how you installed the app (AppImage, tarball, or .deb).
